# Property Evidence Copilot

Property Evidence Copilot is a proposed evidence-first pre-publication workflow
for small Italian real estate agencies. The v0.1 goal is deliberately narrow:
upload a small, discovery-approved set of synthetic property documents, extract
a bounded field taxonomy through deterministic adapters, review every field
with visible provenance, and export confirmed data as JSON and a human-readable
report.

The project is currently in discovery and specification. No application has
been scaffolded and no implementation has started.

## Current Status

- Kickoff package: approved and recorded in [`docs/kickoff.md`](docs/kickoff.md)
- Candidate context: [`docs/context/project-candidate.md`](docs/context/project-candidate.md)
- Specifications: [`specs/`](specs/)
- Implementation plans: [`plans/`](plans/)
- Next gate: discovery with at least five interviews and 15 representative cases

## Safety Boundary

Development, testing, and demonstrations must use only synthetic or properly
anonymized documents. Do not commit, log, or send real names, complete
addresses, tax identifiers, signatures, bank details, identity documents,
floor plans, or other sensitive document content to a model provider.

This tool must not certify cadastral, planning, energy, regulatory, or legal
compliance and must not replace a notary, surveyor, engineer, lawyer, or real
estate agent. No extracted value may be treated as final without explicit human
confirmation.

## Approved Technical Direction

Subject to the discovery go/no-go gate, v0.1 will use one Next.js TypeScript
application, pnpm, local SQLite persistence, local gitignored file storage,
Zod contracts, deterministic fake OCR/extraction providers, Vitest, React
Testing Library, and Playwright Chromium. AWS, Textract, Bedrock, real documents,
portal integrations, and deployment are excluded from v0.1.

Verified local package-manager setup:

- pnpm `12.3.4` is installed through Corepack.
- The user installed Node.js 24 through nvm and upgraded Corepack to support
  pnpm 12.
- A shell may still select another nvm Node version; bootstrap must verify
  `node --version`, `corepack --version`, and `pnpm --version` before scaffolding.

## Documents

The complete approved scope, architecture, timeline, workflow, bootstrap
commands, testing strategy, working prompts, Definition of Done, post-v0.1
roadmap, and approval decisions are in [`docs/kickoff.md`](docs/kickoff.md).
