# Windows Developer Role

## Primary Ownership

The Windows-side developer owns the parts of DAMO that do not require macOS or Xcode:

- Supabase database design
- Supabase API usage patterns
- Web voting link
- Vote session state model
- Vote scoring and aggregation algorithm
- Shared TypeScript types
- Documentation
- GitHub task hygiene

The Windows developer can also edit Expo app code, but final iOS simulator or device verification belongs to the macOS developer.

## Main Deliverables

### Database

Design the first schema around these entities:

- `meetings`
- `place_candidates`
- `vote_sessions`
- `vote_rounds`
- `vote_results`
- `final_decisions`

The schema should preserve the difference between:

- The real candidate ID
- The displayed A/B slot
- The randomized candidate order for a voter

### Web Voting

The member web link must:

- Open without app installation
- Ask for a name or nickname
- Show exactly two choices per round
- Run exactly three rounds
- Randomize candidate order per vote session
- Randomize A/B slot placement per round
- Prevent duplicate round submission
- Save all vote rounds for later aggregation

### Voting Algorithm

The MVP algorithm is:

1. Host selects exactly four candidates.
2. Each voter receives a randomized candidate order.
3. Round 1 compares candidate 1 and candidate 2.
4. The winner remains active.
5. The next candidate enters against the active winner.
6. Round points are `1`, `2`, and `3`.
7. Candidate totals are aggregated across all voters.

Tie breakers:

1. More final-round wins
2. More total selections
3. More unique voters who selected the candidate at least once
4. Host manual decision

### Shared Types

Shared TypeScript types should define:

- Meeting
- PlaceCandidate
- VoteSession
- VoteRound
- VoteScore
- RankedCandidate

These types should be imported by both the mobile app and the web voting app.

## Codex Working Pattern

For Windows-side work, Codex should generally work in this order:

1. Define or update the data model.
2. Add shared types.
3. Implement pure functions first.
4. Add UI only after the function shape is clear.
5. Add small test fixtures or sample data.
6. Document any manual setup.

Avoid asking Codex to build a whole feature in one prompt. Prefer narrow requests such as:

- Build the vote aggregation function and include sample input/output.
- Create the Supabase table draft for vote sessions and vote rounds.
- Implement the three-round web voting state machine.
- Add a mobile-friendly voting result page.

## Coordination With macOS Developer

For each backend or web task, hand off:

- The expected input data
- The expected output data
- Example JSON
- Any environment variables
- A short test path

The macOS developer should not need to infer API shapes from implementation details.
