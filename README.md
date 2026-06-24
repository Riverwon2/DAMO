# DAMO

DAMO is an MVP for helping recurring groups decide the next meeting place.

The product flow is intentionally narrow:

1. A host creates a meeting.
2. The host saves at least four place candidates.
3. Members open a web voting link.
4. Each member makes three A/B choices.
5. DAMO aggregates weighted votes and shows the result to the host.

## Operating Model

Codex currently owns two responsibilities for this project:

- Development process manager: scope control, backlog, task breakdown, review criteria, and delivery sequencing.
- Windows-side developer: database design, web voting flow, scoring algorithm, shared TypeScript types, documentation, and integration support for the macOS/iOS developer.

The macOS-side developer owns iOS runtime verification, Expo mobile screens, device testing, and final app demo stability.

## Recommended Stack

- Mobile app: Expo React Native + TypeScript
- Web voting link: Vite + React + TypeScript
- Backend and database: Supabase
- Hosting: Cloudflare Pages
- Repository workflow: GitHub branches and pull requests
- Design: Figma

## Project Docs

- [Development Process](docs/development-process.md)
- [Windows Developer Role](docs/windows-developer-role.md)
- [Initial Backlog](docs/backlog.md)
