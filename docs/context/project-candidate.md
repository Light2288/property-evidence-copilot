# Project Candidate: Property Evidence Copilot

## Candidate

`property-evidence-copilot` is the neutral internal name for a focused
pre-publication evidence workflow for a small Italian real estate agency. It is
not assumed to be the final commercial name.

## Primary User

An Italian real estate agent preparing a property sheet for publication. A real
estate professional available for interviews, observation, and feedback is the
first design partner.

## Problem Hypothesis

Facts needed for a property sheet are distributed across PDFs, scans, notes,
and agency software. Agents may spend avoidable time transcribing values,
finding missing information, contacting owners, and reconciling contradictions.
The hypothesis has not yet been validated.

## Proposed Value

For one discovery-approved real estate case and no more than three frequent
document types, the application proposes a bounded set of structured fields,
retains verifiable evidence for every value, exposes uncertainty and conflicts,
requires explicit human review, and exports confirmed data without depending on
portal APIs.

## Discovery Gate

Before implementation:

- complete at least five interviews;
- observe or reconstruct at least 15 representative cases;
- measure current property-sheet preparation time;
- measure missing and contradictory information;
- count follow-up contacts and consequential errors;
- inspect the design partner's current agency software;
- confirm documents available before publication;
- identify one case type and at most three frequent document types;
- derive and review a taxonomy of 30-50 fields;
- obtain willingness from at least one agency to try the workflow.

Stop or pivot if current software already solves the problem adequately,
required documents are unavailable before publication, representative data
cannot be evaluated safely, or value depends mainly on inaccessible portal
integrations.

## v0.1 Boundary

The intended vertical slice is:

1. Create one local property case.
2. Upload supported synthetic PDFs.
3. Process them through deterministic OCR and extraction fakes.
4. Review every proposed field with visible provenance.
5. Preserve `present`, `missing`, `uncertain`, `conflicting`, and `confirmed`.
6. Export confirmed fields as versioned JSON and a printable report.
7. Delete the case and every original and derived artifact.

Observed document data, deterministic normalization, provider inference, user
correction, and confirmed output remain separate.

## Exclusions

v0.1 excludes a general CRM, portal publication, listing scraping, valuation,
unsupported marketing claims, electronic signatures, payments, advanced
multi-tenancy, mobile/iOS, AR, OpenCV, Rust, Snowflake, AWS deployment,
autonomous agents, and automatic learning from corrections.

## Source Documents

The candidate was selected and refined from:

- `/Users/davide/Personal/Projects/opencode_notes/career-tech-analysis/10-catalogo-progetti.md`
- `/Users/davide/Personal/Projects/opencode_notes/career-tech-analysis/11-shortlist-progetti.md`
- `/Users/davide/Personal/Projects/opencode_notes/career-tech-analysis/12-top-20-progetti.md`
- relevant context in `06-verticali-prodotto.md`,
  `09-shortlist-e-piano-operativo.md`, and `14-prompt-post-mvp.md`

The approved operational interpretation is recorded in
[`../kickoff.md`](../kickoff.md).
