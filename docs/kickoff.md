# Property Evidence Copilot v0.1 Kickoff

Status: **APPROVED**

No application files or dependencies are part of this package. The package
authorizes discovery and subsequent spec-driven work, subject to the gates
below.

## Verified Context

- Host: macOS on Apple Silicon.
- Git repository: existing `main` branch.
- pnpm `12.3.4` is installed through an updated Corepack after installing
  Node.js 24 with nvm.
- Shells may select different nvm versions, so application bootstrap must first
  verify `node --version`, `corepack --version`, and `pnpm --version`.
- Docker and a PostgreSQL CLI were not available during kickoff inspection.
- SQLite CLI was available.
- Current Next.js documentation requires Node.js 20.9 or later and supports
  TypeScript, App Router, ESLint, `src/`, and pnpm through `create-next-app`.
- Textract supports Italian printed-text detection and PDF/TIFF/JPEG/PNG, but
  its Queries feature is documented as English-only. Protected PDFs are not
  supported and synchronous multipage handling is constrained.
- Bedrock model availability, routing, access, retention, and pricing vary by
  model and region. No model is approved for v0.1.

Official references:

- [Next.js installation](https://nextjs.org/docs/app/getting-started/installation)
- [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app)
- [Node.js releases](https://nodejs.org/en/about/previous-releases)
- [pnpm installation](https://pnpm.io/installation)
- [Vitest](https://vitest.dev/guide/)
- [Playwright](https://playwright.dev/docs/intro)
- [Prisma SQLite](https://www.prisma.io/docs/orm/overview/databases/sqlite)
- [Zod](https://zod.dev/)
- [Textract overview](https://docs.aws.amazon.com/textract/latest/dg/what-is.html)
- [Textract limits](https://docs.aws.amazon.com/textract/latest/dg/limits-document.html)
- [Textract pricing](https://aws.amazon.com/textract/pricing/)
- [Bedrock regional availability](https://docs.aws.amazon.com/bedrock/latest/userguide/models-region-compatibility.html)
- [Bedrock pricing](https://aws.amazon.com/bedrock/pricing/)
- [Bedrock data protection](https://docs.aws.amazon.com/bedrock/latest/userguide/data-protection.html)
- [Bedrock data retention](https://docs.aws.amazon.com/bedrock/latest/userguide/data-retention.html)
- [GDPR](https://eur-lex.europa.eu/eli/reg/2016/679/oj)

## 1. Critical Assessment

### Problem, User, and Value

The primary user is an Italian real estate agent preparing an existing
residential property for publication. The hypothesis is that facts required by
a property sheet are fragmented across PDFs, scans, notes, and agency software,
causing repeated transcription, follow-up, and conflict resolution.

The proposed value is an evidence workspace, not AI due diligence: gather a
small set of frequent documents, propose structured values, retain evidence,
surface uncertainty and contradictions, require human confirmation, and export
a traceable property sheet.

### Unvalidated Assumptions and Risks

- The workflow consumes enough time and occurs frequently enough.
- Required documents are available before publication.
- Three document types cover meaningful work.
- Current CRM or portal software does not already solve the problem.
- Representative cases can be expressed safely as synthetic/anonymized data.
- Agents inspect evidence rather than accepting suggestions blindly.
- Export without portal integration is useful.
- Review-adjusted extraction quality creates a net time saving.
- An agency can accept the privacy/security posture of a later pilot.

Primary risks are weak demand, incumbent coverage, unavailable documents,
incorrect domain taxonomy, hallucinated citations, sensitive-data exposure,
regulatory overclaim, excessive review burden, provider dependence, and scope
creep into CRM functionality.

### Alternatives and Differentiation

Alternatives include agency CRMs, portal tools, drives/email/spreadsheets,
generic OCR, general-purpose LLMs, CASAFARI-style property intelligence,
PriceHubble-style valuation/intelligence, and manual professional review.

The plausible differentiated boundary is:

> A small Italian pre-publication workspace where every property-sheet field
> has visible provenance, uncertainty is preserved, contradictions are
> surfaced, and export is impossible until a human reviews every field.

This boundary remains unvalidated. Direct inspection of the design partner's
software is required before making a commercial differentiation claim.

### Discovery Plan and Go/No-Go

Before implementation:

1. Interview at least five agency professionals, preferably across two agencies.
2. Observe or reconstruct at least 15 recent pre-publication cases.
3. Measure active/elapsed preparation time, document availability, missing and
   contradictory information, follow-up contacts, consequential errors, fields,
   and source systems.
4. Inspect the current CRM and portal workflow directly.
5. Rank document types by frequency and manual-work contribution.
6. Draft a 30-50-field taxonomy and review its terminology with the partner.
7. Confirm cases can be represented without retaining identifying data.

Proceed only if all conditions hold:

- five interviews and 15 cases are complete;
- at least three interviewees identify the same recurring problem;
- relevant documents are available before publication in at least 12 cases;
- current median preparation time and follow-up burden are measured;
- a credible path exists to save at least 20% active time or ten minutes/case;
- at least one agency is willing to try the workflow;
- existing software does not already solve the evidence/review problem;
- representative synthetic or safely anonymized evaluation fixtures are viable.

Declare no-go or pivot if existing software is adequate, documents normally
arrive too late, evaluation material cannot be used safely, or value depends
mainly on inaccessible portal integrations.

### Must Not Build

Do not build a complete CRM, portal publication, scraping, valuation,
comparables, certification, compliance conclusions, autonomous actions, lead or
contract management, unsupported marketing claims, learning from corrections,
advanced multi-tenancy, mobile/iOS, AR, OpenCV, Rust, Snowflake, or AWS
deployment in v0.1.

## 2. First-Release Definition

### Vertical Slice and Capabilities

For one existing residential-apartment sale, an agent creates a case, uploads
up to three supported synthetic document types, runs deterministic fake
extraction, reviews each proposed field with its evidence, resolves missing,
uncertain, and conflicting values, exports confirmed data, and deletes the case.

v0.1 capabilities are limited to:

1. Create and delete a single-user property case.
2. Upload, validate, deduplicate, and list supported synthetic PDFs.
3. Process documents through versioned OCR/extraction interfaces and fakes.
4. Store proposed fields with complete provenance and review status.
5. Review, correct, reject, or confirm every field while preserving conflicts.
6. Export confirmed values as versioned JSON and a printable report.
7. Run a reproducible golden-dataset evaluation.

Candidate defaults, pending discovery, are an existing residential-apartment
sale and approximately 35 fields. Candidate documents are visura catastale,
APE, and an agency property-information sheet; discovery may replace them.

### Happy Path

The user creates a case, uploads supported synthetic files, receives validated
fake proposals, inspects every citation, gives every field an explicit
disposition, exports confirmed values, and deletes every case artifact. Export
stays disabled while any field is unreviewed.

### Failure Paths

Required typed behavior covers unsupported and oversized files, MIME/signature
mismatch, corrupted and protected PDFs, empty OCR, timeout, malformed provider
responses, bounded retries, duplicate upload, partial results, contradictory
values, missing/nonexistent citations, export before review, content leakage to
logs, and deletion during processing.

### Acceptance Criteria

| ID | Observable criterion |
|---|---|
| AC-01 | Supported synthetic PDFs upload; unsupported, oversized, corrupted, and protected inputs produce distinct errors. |
| AC-02 | Re-uploading identical bytes creates and processes no second document. |
| AC-03 | Every proposal retains source document, page, optional region, available source text, method/version, and status; invalid evidence is rejected. |
| AC-04 | Observed text, normalized value, provider inference, and user correction are stored and displayed separately. |
| AC-05 | `present`, `missing`, `uncertain`, `conflicting`, and `confirmed` exist; only explicit human action creates `confirmed`. |
| AC-06 | Contradictory documents produce `conflicting`, retain all candidates/citations, and never auto-confirm a winner. |
| AC-07 | Every taxonomy field receives a human disposition before final export. |
| AC-08 | Versioned JSON/report exports contain only confirmed values and confirmation metadata. |
| AC-09 | Corrections append an actor/timestamp/prior-value/correction/evidence audit event and never trigger learning. |
| AC-10 | Case deletion covers originals and every derived layer; late results cannot restore data. |
| AC-11 | Logs contain no document text, extracted values, sensitive content, prompts, responses, or user filenames. |
| AC-12 | One command reports OCR, extraction, citation, conflict, abstention, completeness, latency, and cost separately. |
| AC-13 | All required timeout, schema, retry, empty, duplicate, partial, and deletion races have automated tests. |
| AC-14 | Golden workflows complete through the UI with keyboard review, visible provenance, and no review bypass. |

OCR, classification, extraction, latency, timeout, malformed output, partial
results, and provider usage/cost are deterministic fakes in v0.1.

## 3. Minimal Stack and Architecture

### Stack

| Concern | Approved direction |
|---|---|
| Application | Next.js App Router with TypeScript |
| Runtime/package manager | Node.js selected through nvm; Corepack and pnpm `12.3.4` |
| UI | Semantic React/HTML and plain project CSS |
| Validation | Zod |
| Persistence | SQLite through Prisma |
| Files | Gitignored local `.data/files/` |
| Unit/integration | Vitest |
| Components | React Testing Library |
| E2E | Playwright, Chromium only |
| Property tests | fast-check only for high-value invariants |
| Providers | Versioned contracts and deterministic fakes |
| Evaluation | TypeScript using the application contracts |

Next.js is justified by routing, server-side upload handling, exports, and one
deployable full-stack unit. A standalone React application would still need a
backend. SQLite avoids a local service; PostgreSQL remains a later migration if
a real pilot needs it. No separate backend or microservice is justified.

### Data Flow and Separation

```text
Browser -> Next.js routes/actions -> domain workflow
                               |-> OCR adapter -> deterministic fake
                               |-> extraction adapter -> deterministic fake
                               |-> Prisma -> local SQLite
                               `-> local opaque-ID file store
```

Validate file type/size/signature, hash bytes for deduplication, store under an
opaque ID, persist a processing attempt, validate fake OCR output, store
observations, validate extraction output, normalize deterministically, validate
citations, detect conflicts, collect human dispositions, export confirmed
values, and delete all layers atomically or with tested compensating cleanup.

Keep these layers separate: original document, observed text/regions,
deterministic normalization, provider inference, user correction, confirmed
output, and audit event.

### Privacy, Security, and Cost

- Minimize document count, size, pages, and extracted taxonomy.
- Synthetic data only; database/file store are gitignored.
- No custom cryptography. A real pilot requires TLS, encrypted storage/database,
  encrypted backups, managed key access, authentication, authorization, and
  agency isolation.
- No third-party analytics or remote observability in v0.1.
- Logs use only opaque IDs and operational metadata.
- Deletion covers all original, derived, temporary, and exported artifacts.
- v0.1 cloud cost target is EUR 0.

Before an AWS trial, explicitly approve region/residency, service and model
availability, access, terms, retention, observed page/token cost, budget alerts,
least privilege, lifecycle settings, resource inventory, and cleanup procedure.

AWS, Snowflake, Rust, OpenCV, Swift/iOS, and real generative AI add no approved
value to the first local vertical slice and are excluded.

## 4. Timeline

Recommended timeline at 8-12 hours/week:

| Week | Focus | Deliverable and check |
|---|---|---|
| 1 | Discovery | Interview guide, 3 interviews, 5 cases |
| 2 | Discovery gate | 5+ interviews, 15 cases, software comparison, explicit go/no-go |
| 3 | Specification | Privacy spec and approved `DEFINED` v0.1 spec |
| 4 | Plan/setup | Approved plan; scaffold builds and smoke test passes |
| 5 | Core RED/GREEN | States, evidence, conflicts, export policy, persistence tests pass |
| 6 | Fake processing/UI | First demonstrable upload-to-review synthetic case |
| 7 | Export/audit/deletion | No unreviewed export; deletion tests pass |
| 8 | Failure/privacy | Required failure and log tests pass |
| 9 | E2E/evaluation/buffer | E2E and all blocking evaluation gates pass |
| 10 | Documentation/release | Clean setup reproduces demo, evaluation, and deletion |

Checkpoints occur after discovery, spec approval, the week-6 demonstration,
week-8 safety hardening, and week-9 evaluation. Reduce document types or fields
if needed; never remove provenance, human review, deletion, or log safety.

An accelerated seven-week variant combines discovery, uses about 30 fields and
usually two documents, and keeps no AWS work. A conservative twelve-week
variant adds discovery, terminology, design-partner walkthrough, and integration
buffer without adding capabilities.

## 5. Spec-Driven Workflow

The available `spec-define`, `spec-plan`, `spec-implement`, and `code-review`
skills were inspected.

1. Record aggregated discovery evidence and decide GO/NO-GO/PIVOT.
2. Approve the local-first architecture boundary.
3. Invoke `spec-define`; recommended slug `property-evidence-v0-1`. It writes a
   DRAFT and changes it to DEFINED only after explicit approval.
4. Review domain terminology, taxonomy, provenance, states, export, privacy,
   deletion, and failure criteria.
5. Invoke `spec-plan` only for a DEFINED spec. Approve task sizes/risk tags and
   map every task to criterion IDs.
6. Bootstrap only after spec and plan become PLANNED.
7. Implement task-by-task RED then minimum GREEN; refactor only after GREEN.
8. Use full `/implement`, not `/implement-lite`, if delegating the approved plan
   as one workflow because security/data/deletion risks require full review.
9. Run deterministic evaluation and fail on blocking safety conditions.
10. Run `code-review`: spec review first, quality review only after spec PASS.
11. Document one complete example and prepare a local release checklist.
12. Do not commit, tag, push, publish, deploy, or process real data without
    explicit approval.

## 6. Bootstrap Commands

These commands are approved for a later bootstrap session, not this package.
Inspect current CLI help before use because `@latest` changes over time.

### Prerequisites

```bash
sw_vers
uname -m
node --version
npm --version
corepack --version
pnpm --version
git --version
sqlite3 --version
git status --short --branch
```

### Scaffold

```bash
pnpm dlx create-next-app@latest --help
pnpm dlx create-next-app@latest . \
  --typescript \
  --eslint \
  --app \
  --src-dir \
  --import-alias "@/*" \
  --use-pnpm \
  --empty \
  --disable-git \
  --no-tailwind
```

This creates files and requires npm-registry network access. It creates no
account or paid resource.

### Dependencies

```bash
pnpm add zod @prisma/client @prisma/adapter-better-sqlite3
pnpm add --save-dev \
  prisma \
  vitest \
  @vitest/coverage-v8 \
  jsdom \
  @testing-library/react \
  @testing-library/dom \
  @testing-library/user-event \
  @testing-library/jest-dom \
  @playwright/test \
  fast-check \
  prettier \
  tsx
pnpm exec playwright install chromium
```

These download packages/browser binaries but create no account or cloud cost.

### Persistence

```bash
pnpm exec prisma init --datasource-provider sqlite --output ../src/generated/prisma
pnpm exec prisma migrate dev --name init
pnpm exec prisma generate
```

Use a gitignored SQLite path. Confirm current Prisma syntax with `--help`.

### Lint, Format, Tests, Fixtures, Build, and Run

The scaffold session must configure equivalent scripts for:

```bash
pnpm lint
pnpm typecheck
pnpm test
pnpm test:coverage
pnpm test:e2e
pnpm format:check
pnpm fixtures:generate
pnpm fixtures:verify
pnpm build
pnpm dev
```

`fixtures:*` scripts are later deliverables. Minimum environment proof is:

```bash
node --version && corepack --version && pnpm --version
```

Minimum scaffold proof is:

```bash
pnpm lint && pnpm typecheck && pnpm test && pnpm build
```

Final v0.1 proof is:

```bash
pnpm verify && pnpm fixtures:verify && pnpm evaluate
```

Minimal structure:

```text
docs/{context,decisions,discovery,evaluation,privacy}/
fixtures/golden/v1/{documents,expected,manifests}/
plans/
prisma/
specs/
src/{app,components,domain,generated,server/{adapters,db}}/
tests/e2e/
scripts/
```

No AWS/Snowflake account, Xcode/device, OpenCV/C++ bridge, Docker, or hosted
database is required for v0.1.

## 7. Testing and Evaluation

| Criteria | Unit/property | Integration/contract | UI/E2E | Evaluation/manual |
|---|---|---|---|---|
| AC-01/02 | file policy, hashing | routes, store, transaction | upload failures/duplicate | counts |
| AC-03/04 | citation/model invariants | fake contract, round trip | evidence/layer labels | citation scoring/domain review |
| AC-05/06 | state sequences/conflicts | multi-document case | review/conflict journey | conflict rate |
| AC-07/08 | export policy/schema | route denial/export | disabled gate/download | exact match |
| AC-09/10 | event/deletion plan | append-only and cancellation | correction/delete journeys | storage inspection |
| AC-11 | redaction properties | captured logger | error journeys | log scan |
| AC-12/13 | scorer/retry tests | dataset and fault adapters | selected failures | reproducible report |
| AC-14 | component behavior | full local stack | Chromium + mobile viewport | partner walkthrough |

Use unit, integration, adapter-contract, component, and Chromium E2E tests.
Use property tests only for state transitions, export invariants, citation
bounds, path safety, and redaction. Snapshot only versioned export/report
structures, not broad UI markup.

The versioned synthetic dataset must contain at least five normal cases, two
missing-field cases, two degraded scans, one rotated case, two contradictory
cases, one unsupported document, one corrupted PDF, and one protected PDF.
Each fixture needs an ID/version, generation method, author/date, approved
license, no-real-person/property statement, expectations, and checksum.

Evaluate OCR, fields, citations, conflicts, completeness/abstention, latency,
and cost separately. Deterministic scorers are mandatory. LLM-as-judge is
excluded. Human review remains necessary for terminology, source support,
professional meaning, privacy, usability, and real time savings.

Release thresholds for the fake-contract v0.1:

- zero confirmed-without-evidence values;
- zero nonexistent citations;
- zero document-content log exposures;
- zero unreviewed values in exports;
- zero unsupported claims;
- 100% conflict detection on designed conflicts;
- 100% abstention on designed missing/unsupported evidence;
- 100% golden schema validity, fake exact match, and fake citation correctness;
- all fields explicitly disposed before export;
- all required E2E cases complete;
- EUR 0 provider cost.

Fake scores validate contracts, not real OCR or LLM quality.

## 8. Ordered Working Prompts

Use these objectives in order. Every later session must inspect the repository,
read `AGENTS.md`, this kickoff, relevant accepted ADR/spec/plan files, preserve
unrelated changes, avoid scope expansion, run the listed verification, and not
commit or push unless the user adds that instruction.

1. **Discovery and go/no-go.** Write
   `docs/discovery/problem-validation.md`; aggregate at least five interviews
   and 15 cases without identifiable data. Complete only with evidence-based
   GO/NO-GO/PIVOT. Verify: `git diff --check && test -f docs/discovery/problem-validation.md`.
2. **Architecture boundary.** Compare only Next.js versus split frontend/backend,
   SQLite versus PostgreSQL, and fake versus cloud providers. Write proposed
   `docs/decisions/0001-v0-1-architecture.md`. No code. Verify:
   `git diff --check && test -f docs/decisions/0001-v0-1-architecture.md`.
3. **Specification definition.** Invoke `spec-define` for
   `property-evidence-v0-1`, assign stable criterion IDs, and cover every
   approved behavior/failure/privacy gate. Complete only at `DEFINED`. Verify:
   `git diff --check && test -f specs/property-evidence-v0-1.md`.
4. **Specification review.** Read-only review for missing, ambiguous,
   contradictory, untestable, or extra requirements. Complete only after all
   findings are resolved/accepted and the user approves. Verify: `git diff --check`.
5. **Implementation planning.** Invoke `spec-plan`, map small ordered tasks to
   criteria, assign size/risk, and recommend full implementer. Complete only at
   `PLANNED`. Verify: `git diff --check && test -f plans/property-evidence-v0-1.md`.
6. **Application bootstrap.** Create only the approved Next.js/pnpm/SQLite/test
   scaffold and smoke test. Verify: `pnpm lint && pnpm typecheck && pnpm test && pnpm build`.
7. **First RED tranche.** Write tests only for evidence, layer separation,
   states, human confirmation, conflicts, and export policy. Complete only when
   targeted tests fail for intended assertions. Verify: `pnpm test -- src/domain`.
8. **GREEN core.** Implement minimum domain/persistence behavior without adding
   UI or providers. Verify: `pnpm test -- src/domain && pnpm typecheck`.
9. **Provider contracts/fake.** RED/GREEN versioned OCR/extraction contracts and
   deterministic failure-capable fakes; no network/AWS. Verify:
   `pnpm test -- src/server/adapters fixtures`.
10. **Upload/review UI.** RED/GREEN responsive, semantic, keyboard-operable
    upload-to-review workflow with visible provenance. Verify:
    `pnpm test && pnpm test:e2e -- --grep "review workflow"`.
11. **Export/audit/deletion/hardening.** RED/GREEN confirmed-only exports,
    append-only audit, complete deletion, retries, malformed/partial/duplicate
    and log-safety cases. Verify: `pnpm lint && pnpm typecheck && pnpm test`.
12. **E2E/evaluation.** Create licensed synthetic fixtures, manifests,
    checksums, deterministic scorers, and report. Verify:
    `pnpm fixtures:verify && pnpm test:e2e && pnpm evaluate`.
13. **Documentation/example.** Reproduce setup-to-export-to-deletion and document
    privacy, limitations, and zero-cost boundary. Verify:
    `pnpm verify && pnpm evaluate && git diff --check`.
14. **Acceptance review.** Invoke read-only `code-review` initial spec mode with
    complete envelope/diff/proof. Quality must not run before spec PASS. Verify:
    `pnpm verify && pnpm fixtures:verify && pnpm evaluate`.
15. **Quality/security review.** Read-only review of state/transaction/file/path/
    schema/retry/deletion/log/export/accessibility quality. Complete with no
    unresolved Important finding or explicit user disposition. Verify:
    `pnpm verify && pnpm evaluate`.
16. **Release v0.1.** Prepare release notes, checklist, limitations, synthetic
    demo, and traceability. Check tracked files for secrets/real data. Do not
    tag, publish, deploy, commit, or push. Verify:
    `pnpm install --frozen-lockfile && pnpm verify && pnpm fixtures:verify && pnpm evaluate`.

Each working prompt must state whether its output is documents, tests,
application code, infrastructure, or review; name the files to read; keep one
main objective; report observed command proof; and declare completion only when
its stated gate is met.

## 9. Definition of Done

Mandatory v0.1 requirements:

- one approved case, at most three document types, and 30-50 approved fields;
- supported synthetic upload, validation, deduplication, and fake processing;
- provenance for every proposal and strict separation of all data layers;
- all five statuses, human-only confirmation, and conflict preservation;
- explicit disposition of every field before confirmed-only JSON/report export;
- append-only correction audit without learning;
- complete deletion, including deletion during processing;
- all specified unit/integration/contract/component/Chromium tests passing;
- versioned synthetic golden data and separate reproducible metrics;
- zero blocking safety failures;
- lint, formatting, typecheck, tests, E2E, and production build passing;
- spec review PASS, no extra scope, and no unresolved Important quality finding;
- synthetic-only repository, gitignored runtime data, no credentials, safe logs;
- documented single-user/non-production-authentication boundary;
- EUR 0 cloud/provider cost;
- reproducible README example, privacy/architecture docs, limitations, release
  notes, and acceptance traceability;
- local release candidate reproducible with pnpm, without requiring deployment,
  publication, tagging, committing, or pushing.

Post-v0.1 only: Textract/Bedrock, real OCR/model claims, AWS, production auth,
PostgreSQL, real-document pilot, portal integration, description generation,
additional cases/documents, learning, pricing, or billing.

Stop/archive signals include failed discovery, no willing agency, adequate
incumbent software, no measured time saving, unavailable documents, unsafe
evaluation data, correction burden exceeding benefit, blind confirmation,
unsustainable privacy/security burden, portal-dependent value, unreliable
citation/deletion safety, excessive per-case cost, or disproportionate
maintenance.

## 10. Lightweight Post-v0.1 Roadmap

1. **Hardening:** prepare a secure bounded design-partner pilot only if v0.1
   saves measurable time, an agency requests it, and privacy/auth/isolation/
   retention can be approved.
2. **Same-use-case extension:** evaluate one real OCR/extraction configuration
   only if contracts are stable, safe representative documents exist, extraction
   is the remaining bottleneck, and AWS region/retention/access/limits/cost pass.
3. **New direction or stop:** pivot only if discovery identifies a stronger
   adjacent pre-publication problem; otherwise archive when recurrence or pilot
   willingness is absent.

Keep SQLite/PostgreSQL, local/object file storage, provider, taxonomy/documents,
identity, and export presentation reversible through explicit contracts and
migrations, not speculative abstractions. Detailed post-v0.1 planning is
deferred to `career-tech-analysis/14-prompt-post-mvp.md`.

## 11. Approved Decisions

| Decision | Approved direction |
|---|---|
| Discovery | Five interviews and 15 cases before scaffolding |
| Initial case | Existing residential-apartment sale, subject to discovery |
| Documents | Candidate visura/APE/intake sheet; at most three after discovery |
| Taxonomy | About 35 fields, hard limit 50, finalized by discovery |
| Provider | Deterministic fake only |
| Architecture | One Next.js TypeScript application, no separate backend |
| Persistence | Prisma/SQLite and gitignored local file storage |
| Package manager | Corepack with pnpm `12.3.4` |
| Authentication | Explicit local single-user identity; synthetic-only |
| Export | Versioned JSON plus printable report; confirmed fields only |
| Listing description | Excluded |
| Cloud | No AWS SDK, resources, deployment, or paid calls |
| Timeline | Ten weeks recommended; seven accelerated; twelve conservative |
| Workflow | Approved spec/plan, RED/GREEN, deterministic evaluation, spec-first review |
| Release | Complete synthetic workflow and zero blocking safety failures |
| Real-data gate | Separate approval plus auth, isolation, privacy, cost, retention, cleanup |
| Name | Keep `property-evidence-copilot` as neutral internal name |
