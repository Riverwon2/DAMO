# Development Process

## Role Definition

Codex acts as the project process owner and Windows-side developer.

The process owner is responsible for keeping the MVP small, turning product ideas into implementation tasks, checking that work is testable, and preventing the team from adding non-MVP complexity too early.

## MVP Scope

The first MVP includes:

- Host meeting creation
- Place candidate storage
- Exactly four candidates selected for voting
- Member web voting link
- Three-round A/B voting flow
- Weighted vote aggregation
- Host result view
- Final place confirmation

The first MVP excludes:

- Native map API integration
- In-app chat
- AI-based recommendation
- App Store launch
- SMS invitation
- Advanced reservation or coupon partnerships

## Weekly Rhythm

At the start of each week:

- Pick three to five concrete tasks.
- Confirm which tasks belong to macOS/iOS and which belong to Windows/web/backend.
- Define the demo target for the end of the week.

Every work session:

- State the current task.
- Keep one active task per developer.
- Stop expanding scope unless it directly unblocks the MVP.

At the end of each week:

- Demo a working flow.
- Record bugs and missing states.
- Move unfinished work back into the backlog with clearer acceptance criteria.

## Branching

Use one branch per feature.

Examples:

- `feature/create-meeting`
- `feature/place-candidates`
- `feature/web-voting`
- `feature/vote-aggregation`
- `feature/final-decision`

Do not commit directly to `main` or `master` once active development starts.

## Pull Request Checklist

Each pull request should include:

- What changed
- How to test it
- Screenshots for UI changes
- Known limitations
- Any database migration or environment variable changes

## Definition Of Done

A task is done only when:

- The feature runs locally.
- The happy path works.
- Empty, loading, and error states are handled at a basic level.
- Data written by one surface can be read by the other surface when relevant.
- The implementation is small enough for the other developer to review.

## Review Rules

The macOS developer reviews:

- Whether backend/web changes fit the iOS user flow
- Whether API responses are easy for the mobile app to consume
- Whether voting state can be rendered clearly on mobile

The Windows developer reviews:

- Whether mobile screens map to real data
- Whether state transitions are explicit
- Whether the implementation keeps MVP scope intact
- Whether database and shared types stay consistent
