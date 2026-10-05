# Tester Feedback Coverage Analysis

## Analysis Metadata

- Status: **COMPLETE**
- Coverage: **COMPLETE** — all five registered sources were readable and reviewed in full against questionnaire version 1.2.
- Generated: `2026-10-05T23:10:06.648Z`
- ADR mode: **disabled**
- Output: `docs/analysis/tester-feedback-coverage.md`
- Analysis boundary: the caller-supplied tester feedback was assessed only against S1-S5. No ADRs, code, specifications, plans, or unregistered files were inspected.

## Sources

| ID | Source | Coverage and role |
|---|---|---|
| S1 | `AGENTS.md` | Complete. Governing scope, evidence, privacy, provider, and release constraints. |
| S2 | `README.md` | Complete. Current project status, proposed v0.1 outcome, safety boundary, and technical direction. |
| S3 | `docs/context/project-candidate.md` | Complete. Candidate problem, primary user, discovery gate, vertical slice, and exclusions. |
| S4 | `docs/discovery/questionario-validazione.md` | Complete, current version **1.2 - 6 ottobre 2026**. Questionnaire governance, workflow elicitation, safe observation, synthetic-example viability, prioritization, and interviewer handling. [S4:L30-L53] [S4:L594-L605] [S4:L662-L690] |
| S5 | `docs/kickoff.md` | Complete. Approved kickoff package, discovery thresholds, candidate release boundary, acceptance criteria, timeline, and future spec-driven workflow. |

The kickoff package is approved, but it authorizes discovery and later spec-driven work subject to gates; it is not an approved v0.1 specification. The repository remains in discovery/specification with no implementation started, and S5 says a future `spec-define` step must create a DRAFT that becomes `DEFINED` only after explicit approval. [S2:L10-L19] [S5:L3-L6] [S5:L285-L291] [S5:L482-L490]

## Actors and Goals

| Actor | Evidenced goal or responsibility |
|---|---|
| Italian real estate agent | Prepare a property sheet for publication while reducing repeated transcription, missing-information searches, follow-up, and conflict reconciliation. [S3:L11-L20] [S5:L50-L57] |
| Design-partner agency/professionals | Supply interviews, reconstructed cases, terminology, workflow evidence, safe software observation where authorized, and willingness evidence for the discovery gate. [S3:L11-L12] [S3:L32-L43] [S4:L684-L690] [S5:L96-L114] |
| Human professional reviewer | Inspect evidence, disposition every field, preserve uncertainty/conflicts, and alone create `confirmed`; extracted values cannot become final automatically. [S1:L16-L24] [S2:L28-L31] [S5:L173-L178] |
| Research participant | Voluntarily describe the pre-publication workflow, storage, attachment intake, professional checks, burden, and representative cases without providing identifiable or confidential material. [S4:L15-L27] [S4:L30-L51] [S4:L106-L211] [S4:L266-L370] |
| Research lead/interviewer | Explain response use, obtain verbal confirmation to continue, keep any recontact list separate, prevent or remove identifiers, use only aggregate results, observe software only with authorization and fictitious/redacted screens, and track the required interview/case counts. [S4:L662-L690] |
| Property Evidence Copilot | Act as a narrow evidence workspace that proposes values, retains provenance, surfaces uncertainty and contradictions, requires human confirmation, and exports confirmed data. It is not a due-diligence or compliance-certification system. [S2:L3-L8] [S5:L55-L59] [S5:L123-L127] |

## Functional Requirements

### A. Governing project boundary

1. Discovery must establish the actual workflow, incumbent software coverage, document availability, frequent document types, field taxonomy, measurable burden, safe evaluation data, and willingness to try the workflow before implementation. [S3:L32-L47] [S5:L94-L118]
2. The candidate v0.1 must create one local case, accept supported synthetic PDFs, use deterministic fake OCR/extraction, review every proposed field with visible provenance, preserve `present`, `missing`, `uncertain`, `conflicting`, and `confirmed`, export confirmed data, and delete all original and derived artifacts. [S3:L52-L64] [S5:L133-L159]
3. Every proposed value must retain source document, page or source region, source text when available, extraction method/version, and review status; observed content, normalization, provider inference, user correction, and confirmed output must remain separate. [S1:L16-L22] [S5:L173-L178]
4. Contradictions must remain visible with all candidates/citations, and final export must remain blocked until every field has a human disposition. [S1:L20-L22] [S5:L157-L159] [S5:L175-L178]
5. v0.1 must not become or replace a CRM or portal integration and must not issue cadastral, planning, energy, regulatory, or legal compliance conclusions. Agency-server integration is not included or approved in the current boundary; it is not categorized as forbidden by S1. [S1:L11-L12] [S1:L23-L24] [S2:L28-L31]

### B. Current questionnaire coverage

The current S4 elicits:

1. storage location, per-property folders/subfolders, who creates and classifies them, reclassification, and common attachment problems; [S4:L158-L196]
2. workflow states such as `in attivazione / pending` and `attivato`, state transitions, and sale/rent differences; [S4:L126-L140] [S4:L386-L388] [S4:L429-L431] [S4:L472-L474]
3. native/digital PDFs, third-party scans, agent scans/images, photographs, and paper not yet digitized; [S4:L182-L190]
4. building/urban-planning practices plus cadastral, floor-plan, APE, provenance, condominium, engagement, privacy/AML, and other categories; [S4:L266-L285]
5. both most-consulted and highest-manual-burden document rankings, each capped at `Massimo 3`; [S4:L288-L299]
6. professional-check decomposition for APE validity, building/urban-planning completeness and coherence, floor-plan/current-state comparison, and provenance-deed review, including evidence, deciding role, missing/conflicting states, external access, site visit, and licensed-professional needs; [S4:L337-L370]
7. a clarified recontact metric counting each new request or reminder after the first collection; [S4:L242-L254] [S4:L408-L408] [S4:L451-L451] [S4:L494-L494]
8. explicit separation of the first version from the agency server, folders, and CRM, with manual upload of no more than three example document types; [S4:L577-L584]
9. whether an invented example can preserve the real workflow problems—missing documents, contradictory data, and poor scans—without real data, documents, or floor plans, and which problems matter most to reproduce; [S4:L594-L605]
10. bounded first-prototype prioritization of one case, at most three document types, and 30-50 fields; [S4:L638-L651]
11. safe observation of the current software using an authorized fictitious property or screens without real data, with a verbal reconstruction fallback; and [S4:L684-L687]
12. separate tracking of at least five interviews and 15 cases, with additional cases collected separately when a participant provides fewer than three. [S4:L688-L690]

These are discovery questions and operating instructions, not approved product requirements. Answers still must be collected, aggregated, used for GO/NO-GO/PIVOT, and converted into an explicitly approved specification and plan before implementation. [S1:L7-L12] [S5:L474-L490]

## Quantified Non-Functional Requirements

### Questionnaire and discovery measurements

- The current questionnaire estimates **30-45 minutes** to complete. [S4:L13-L13]
- Current-response retention is deletion within **90 days** of the decision whether to proceed and in all cases no later than **12 months** after collection. [S4:L48-L51]
- The current notice is version **1.2 - 6 ottobre 2026**. [S4:L53-L53]
- Respondent experience bands are **Meno di 2**, **2-5**, **6-10**, and **Oltre 10** years; agency-size bands are **1 persona**, **2-5 persone**, **6-15 persone**, and **Oltre 15 persone**. [S4:L72-L85]
- New-property volume bands are **0-5**, **6-15**, **16-30**, and **Oltre 30** per month. [S4:L90-L96]
- Active preparation-time bands are **Meno di 15 minuti**, **15-30 minuti**, **31-60 minuti**, **61-120 minuti**, **Oltre 120 minuti**, or **Non misurato / molto variabile**. [S4:L216-L224]
- Missing-information and conflicting-source bands are **Mai o quasi mai**, **Meno di 1 caso su 10**, **Tra 1 e 3 casi su 10**, **Tra 4 e 6 casi su 10**, and **Più di 6 casi su 10**. [S4:L226-L240]
- Recontact bands are **0**, **1**, **2**, **3-5**, **Oltre 5**, and **Non misurato / molto variabile**. [S4:L242-L254]
- The questionnaire requests **tre casi** recenti/rappresentativi, permits at most **3** selected solution supports, and uses `Massimo 3` for both consultation and manual-burden document rankings. [S4:L288-L299] [S4:L375-L377] [S4:L525-L533]
- If one participant describes fewer than **tre casi**, the interviewer must collect additional cases separately. [S4:L688-L690]
- Minimum perceived-value choices are **Almeno 5 minuti per immobile**, **Almeno 10 minuti per immobile**, **Almeno 20 minuti per immobile**, and **Almeno il 20% del tempo attuale**. [S4:L561-L567]
- The discovery gate requires at least **five interviews** and **15 representative cases**; S5 prefers **two agencies**, requires at least **three interviewees** to identify the same recurring problem, documents in at least **12 cases**, a credible path to save at least **20% active time or ten minutes/case**, and at least **one agency** willing to try the workflow. S4 now repeats the **at least five interviews and 15 cases** tracking requirement. [S2:L15-L19] [S4:L688-L690] [S5:L96-L114]

### v0.1 scope and acceptance thresholds

- v0.1 is limited to **one** discovery-approved case, no more than **three document types**, and **30-50 fields**. Candidate planning uses approximately/about **35 fields** with a hard limit of **50**. [S1:L9-L12] [S3:L24-L27] [S5:L133-L150] [S5:L587-L591]
- Fake-contract release thresholds are **zero** confirmed-without-evidence values, **zero** nonexistent citations, **zero** document-content log exposures, **zero** unreviewed values in exports, **zero** unsupported claims, **100%** conflict detection on designed conflicts, **100%** abstention on designed missing/unsupported evidence, and **100%** golden schema validity, fake exact match, and fake citation correctness. [S5:L451-L463]
- The versioned synthetic dataset must include at least **five** normal cases, **two** missing-field cases, **two** degraded scans, **one** rotated case, **two** contradictory cases, **one** unsupported document, **one** corrupted PDF, and **one** protected PDF. [S5:L440-L444]
- The v0.1 cloud/provider cost target is **EUR 0**. [S5:L237-L249] [S5:L453-L463]
- The recommended schedule is **8-12 hours/week** over **10 weeks**; the accelerated variant is **seven weeks**, uses about **30 fields** and usually **two documents**, and the conservative variant is **twelve weeks**. Checkpoints occur after the **week-6** demonstration, **week-8** safety hardening, and **week-9** evaluation. [S5:L254-L275] [S5:L599-L599]
- Recorded toolchain constraints include pnpm **12.8.1**, Node.js **24**, and a kickoff-recorded Next.js minimum of Node.js **20.9 or later**. These are kickoff context/approved direction, not evidence that a scaffold exists. [S5:L9-L19] [S5:L195-L209]

## Constraints and Assumptions

### Cited facts and governing constraints

- No scaffolding or implementation is allowed until discovery returns GO and the v0.1 spec and plan are explicitly approved. [S1:L7-L12]
- v0.1 must not become a CRM, portal integration, valuation product, compliance tool, mobile app, or autonomous workflow. [S1:L11-L12]
- The product must not certify cadastral, planning, energy, regulatory, or legal compliance and must not replace a notary, surveyor, engineer, lawyer, or agent. [S1:L23-L24] [S2:L28-L31]
- Only synthetic or properly anonymized fixtures may be used; real names, complete addresses, tax identifiers, signatures, bank details, identity documents, floor plans, and other sensitive content must not be committed. [S1:L28-L31]
- No document content, OCR text, extracted value, prompt, response, correction, or user-supplied filename may appear in logs. [S1:L32-L36]
- Deterministic provider contracts/fakes come first; AWS, Textract, Bedrock, paid services, real-document processing, and AWS deployment require later approval or are excluded from v0.1. [S1:L42-L49] [S2:L35-L39]
- No approved v0.1 specification exists in S1-S5. `APPROVED` applies to the kickoff package; specification definition and approval remain future gated steps. [S2:L10-L19] [S5:L3-L6] [S5:L285-L291] [S5:L482-L490]
- S4 makes participation voluntary, limits response access/use, sets deletion and correction/withdrawal rules, and permits verbal confirmation after the interviewer explains response use; it also requires checking whether the agency needs an additional privacy notice. [S4:L30-L53] [S4:L662-L667]
- S4 forbids collecting attachments or recordings and requires accidental identifiers to be removed before saving; results must use only aggregate, non-identifying descriptions. [S4:L668-L683]

### Evidenced assumptions not yet validated

S5 labels the following as unvalidated: the workflow consumes enough time and occurs often enough; required documents are available before publication; three document types cover meaningful work; incumbent software does not already solve the problem; cases can be represented safely; agents inspect evidence rather than accepting suggestions blindly; export without portal integration is useful; review-adjusted extraction saves net time; and a later pilot's privacy/security posture is acceptable. [S5:L62-L75]

### Analyst inferences

- The tester's attachment families are discovery candidates, not authorization to widen v0.1. Results must rank them and select no more than three document types. [S4:L266-L299] [S1:L9-L12]
- “Property is in order” can fit only as a human professional's externally made conclusion supported by visible evidence; it cannot be a system-generated compliance result. [S1:L16-L24] [S4:L337-L370] [S4:L522-L539]
- The questionnaire distinguishes the existing server/folder/CRM workflow from the proposed prototype and therefore does not imply server or CRM integration. [S4:L158-L211] [S4:L577-L584] [S1:L11-L12]
- Version 1.2 contains no remaining substantive questionnaire-content gap evidenced by the tester feedback or S1-S5. Remaining uncertainty concerns actual answers, safe observation, synthetic-example viability, scope choice, and later approval—not another questionnaire expansion. [S4:L126-L211] [S4:L266-L370] [S4:L577-L605] [S4:L638-L690]

## Feedback Coverage Matrix

| Tester feedback | Governing project boundary | Current S4 coverage | Remaining decision |
|---|---|---|---|
| Server with manually created per-property folders/subfolders | Understanding the incumbent workflow is required. Becoming or replacing a CRM or portal integration is outside v0.1; agency-server integration is not included or approved in the current boundary. [S3:L39-L47] [S1:L11-L12] | **Fully covered for discovery.** S4 asks storage location, server/local/cloud/CRM, creator, standard subfolders, categories, classifier, and reclassification. [S4:L158-L196] | Discovery must determine whether the separate manual-upload prototype still offers value and may safely observe/reconstruct current software use. [S4:L577-L584] [S4:L684-L687] |
| Pending/active properties; rent versus sale | One discovery-approved case must be selected; both tracks are not automatically v0.1 scope. [S1:L9-L12] | **Fully covered for discovery.** S4 asks state transitions and sale/rent differences globally and repeats destination/state in all three cases. [S4:L126-L140] [S4:L386-L388] [S4:L429-L431] [S4:L472-L474] | Discovery must select the one initial case and define its state semantics. [S4:L638-L651] |
| Agents manually collect and classify attachments | Manual-work contribution is a required discovery ranking; attachment automation is not yet approved. [S5:L96-L103] | **Fully covered for discovery.** S4 asks collection roles, folder/category ownership, reclassification, intake problems, and manual-burden ranking. [S4:L116-L124] [S4:L168-L196] [S4:L294-L299] | Interviews must quantify which steps recur and create material burden. [S5:L96-L114] |
| Urban/building, condominium, floor plan, cadastral, other, engagement, privacy, AML categories | At most three document types may enter v0.1. [S1:L9-L12] | **Fully covered for discovery.** The current table contains all requested families, with privacy/AML limited to category-level description. [S4:L266-L285] | Discovery must distinguish folder category from implementable document type and choose at most three. [S4:L638-L651] |
| Native PDFs, third-party scans, and agent-made scans | Synthetic supported PDFs and deterministic fakes are the candidate v0.1 boundary. [S3:L52-L64] | **Fully covered for discovery.** S4 distinguishes digital third-party PDFs, third-party scans, agent scans/images, photos, and undigitized paper, then asks about quality/version/classification problems. [S4:L182-L196] | Discovery must identify which problems an invented example can reproduce without real data and later choose supported synthetic input variants. [S4:L594-L605] [S5:L440-L444] |
| APE “valid” | Evidence extraction/review is in scope; an energy-validity certification is **forbidden**. [S1:L23-L24] | **Fully covered as professional-check elicitation.** S4 asks evidence, deciding role, missing/conflicting handling, external/site/professional needs, and the concrete meaning of `valido`. [S4:L337-L370] | Discovery must identify objective extractable fields versus conclusions reserved to a professional. [S4:L356-L363] |
| Building/urban-planning practices “complete and coherent” | Missing/conflicting evidence may be surfaced; planning-compliance certification is **forbidden**. [S1:L20-L24] | **Fully covered as professional-check elicitation.** The document row and decomposed check are present, including concrete definitions and professional authority. [S4:L279-L279] [S4:L337-L363] | Discovery must determine required sources, fields, external access, and professional responsibility; the answer is not yet known. [S4:L347-L363] |
| Floor plan conforms to current physical state | Evidence support is potentially in scope; cadastral/planning conformity certification is **forbidden**, and real floor plans must not be collected/committed. [S1:L23-L31] | **Fully covered as a privacy-safe process question.** S4 asks the evidence/role decomposition and a generic or invented description without floor plans, photos, or identifiers. [S4:L337-L370] | Discovery must establish whether useful support and invented fixtures are viable without unsafe data and what still requires a site visit/professional. [S4:L347-L370] [S4:L594-L605] |
| Provenance deeds are “correct” | Provenance evidence/review may be supported; legal correctness certification is **forbidden**. [S2:L28-L31] | **Fully covered as professional-check elicitation.** S4 includes the deed row and decomposed check, including who may conclude it. [S4:L278-L284] [S4:L337-L363] | Discovery must define fields, sources, and authority; the product cannot make the legal conclusion. [S4:L347-L363] |
| Overall outcome: property is “in order” | **Deliberately out of scope/forbidden if asserted by the product.** The approved boundary is an evidence workspace, not due diligence/certification. [S5:L55-L59] [S5:L123-L127] | **Properly reframed.** S4 states non-certification twice and asks which evidence supports remain useful under that limit. [S4:L337-L345] [S4:L513-L539] | Discovery/spec may define a traceable evidence/review state, never a product-issued “in order” declaration. [S1:L16-L24] |

## Questionnaire Remediation Status

| Earlier gap or requested change | Version 1.2 status |
|---|---|
| Response governance and voluntary participation | **Addressed.** The short opening states voluntariness, limited access/use, deletion within 90 days and no later than 12 months, correction/withdrawal via participant code, and version/date. The appendix permits verbal confirmation and requires checking for any agency-specific additional notice. [S4:L30-L53] [S4:L662-L667] |
| Storage/server and folder/subfolder workflow | **Addressed.** [S4:L158-L180] |
| Pending/active state and rent/sale distinction | **Addressed.** [S4:L126-L140] [S4:L386-L388] [S4:L429-L431] [S4:L472-L474] |
| Native PDF, third-party scan, and agent-scan intake | **Addressed.** [S4:L182-L196] |
| Urban/building-practices row plus engagement, privacy, and AML categories | **Addressed.** [S4:L266-L285] |
| Manual-work contribution ranking | **Addressed.** [S4:L288-L299] |
| Professional-check decomposition and non-certification boundary | **Addressed.** [S4:L337-L370] [S4:L513-L539] |
| Ambiguous follow-up-contact count | **Addressed.** S4 defines a recontact as each new request/reminder after first collection and captures it in all three cases. [S4:L242-L254] [S4:L408-L408] [S4:L451-L451] [S4:L494-L494] |
| Bounded first-prototype prioritization | **Addressed.** [S4:L638-L651] |
| Risk of implying server/CRM integration | **Addressed.** S4 tests a separate first version with manual upload of at most three example document types. [S4:L577-L584] |
| Safety and realism of invented fixtures | **Addressed.** S4 asks whether invented examples can retain real missing/conflicting/poor-scan problems without real data and which problems matter to reproduce. [S4:L594-L605] |
| Safe software observation | **Addressed.** The appendix authorizes only agency-approved observation with a fictitious property or screens free of real data, otherwise verbal reconstruction. [S4:L684-L687] |
| Required discovery sample tracking | **Addressed.** The appendix requires separate tracking of at least five interviews and 15 cases and supplementation when a participant gives fewer than three cases. [S4:L688-L690] |

No substantive questionnaire gap remains in the supplied evidence. This is a content-coverage conclusion, not evidence that discovery has been executed or that the questionnaire's response-governance wording has received external legal/privacy approval. [S4:L30-L53] [S4:L662-L690]

## Contradictions

1. **Material conflict only if the desired outcome is automated.** A system conclusion that a property is “in order,” an APE is valid, building practices are complete/coherent, a floor plan conforms, or a deed is legally correct conflicts with the explicit certification ban. S4 resolves the questionnaire framing by asking about evidence and professional decisions instead. [S1:L16-L24] [S4:L337-L370] [S4:L522-L539]
2. **Material scope conflict if all attachment families are expected in v0.1.** S4 deliberately surveys more categories than the product limit; it says a row does not imply first-prototype inclusion and later asks respondents to choose at most three document types. [S1:L9-L12] [S4:L266-L299] [S4:L638-L651]
3. **CRM/portal integration would be a material scope conflict; agency-server integration would be an unapproved scope addition.** S1 explicitly excludes expansion into a CRM or portal integration. It does not categorically forbid agency-server integration, but no such integration is included or approved in the current boundary, and S4 tests a first version separate from the server, folders, and CRM. [S1:L11-L12] [S4:L577-L584]
4. **Apparent approval-status tension, not an approved spec.** S5 is `APPROVED` only as a kickoff package authorizing gated work. S2 says the project is still in discovery/specification, and S5 places `DEFINED` specification approval later. [S2:L10-L19] [S5:L3-L6] [S5:L285-L291] [S5:L482-L490]

## Ambiguities

1. S4 asks respondents to define `valido`, `completo`, `coerente`, `conforme`, and `corretto`, but S1-S5 contain no completed responses. Their operational meanings remain unresolved discovery outputs. [S4:L356-L363]
2. S4 captures state names and transitions, but no evidence yet shows whether agencies use the same meanings for pending/active or whether sale and rent differ materially. [S4:L126-L140]
3. A folder category may contain multiple document types, and one document may serve multiple categories. Discovery must define the unit to which the three-document cap applies. [S4:L168-L180] [S1:L9-L12]
4. S4 asks who can conclude each professional check, but the authorized roles and external-source dependencies are not yet answered. [S4:L337-L363]
5. It remains unknown which one case, three document types, and 30-50 fields will be selected; S4 collects that prioritization but contains no results. [S4:L638-L651]
6. It remains unknown whether invented examples can reproduce the workflow's consequential missing, conflicting, and degraded-scan problems faithfully enough for evaluation; S4 now asks the question, but contains no answers. [S4:L594-L605]

## Gaps

### C. Remaining discovery and specification work

1. **Execute discovery:** complete and separately track at least five interviews and 15 representative cases; supplement case counts when a participant supplies fewer than three; aggregate results without identifiable data; and record GO/NO-GO/PIVOT. [S4:L662-L690] [S5:L96-L118] [S5:L474-L490]
2. **Observe or reconstruct incumbent software safely:** use an agency-authorized fictitious property or screens without real data, otherwise reconstruct the process verbally; determine whether incumbent software already solves the evidence/review problem. [S4:L684-L687] [S5:L106-L118]
3. **Initial scope selection:** choose one case, at most three document types, and 30-50 fields; decide whether the candidate residential-apartment sale, visura/APE/intake sheet, and approximately 35 fields remain appropriate. [S4:L638-L651] [S5:L133-L150]
4. **Professional-check model:** determine which objective fields/dates/statuses can be extracted, which sources are required, who may review/conclude, and which missing/conflicting states the system may present for APE, urban/building practices, floor-plan comparison, and provenance deed. S4 asks these questions but provides no answers. [S4:L337-L370]
5. **Synthetic-example viability:** determine whether invented examples can preserve the actual missing-document, conflicting-data, and degraded-scan problems without using real data, documents, or floor plans; use the answers to define safe representative fixtures. [S4:L594-L605] [S5:L440-L444]
6. **Prototype value without integration:** establish whether manual upload to a separate tool still produces measured value relative to the existing server/CRM workflow. [S4:L202-L211] [S4:L577-L584] [S5:L106-L118]
7. **Approved specification and plan:** no approved v0.1 spec or plan exists. Candidate capabilities, complete questionnaire coverage, and approved kickoff directions cannot substitute for `DEFINED` and `PLANNED` approvals. [S1:L7-L12] [S5:L285-L291] [S5:L482-L490]

These are discovery-execution and approval gaps, not reasons to expand the questionnaire further.

## Recommended Questionnaire Changes

No further substantive questionnaire change is supported as necessary by S1-S5. Version 1.2 covers the tester feedback, prior governance issue, safe software observation, sample tracking, and invented-example viability. Remaining actions should execute the instrument rather than add speculative questions. [S4:L30-L53] [S4:L126-L211] [S4:L266-L370] [S4:L577-L605] [S4:L638-L690]

Operational recommendations:

1. **Administer version 1.2 as written.** Explain voluntariness and response use, obtain verbal confirmation, and check whether the agency requires an additional privacy notice. [S4:L662-L667]
2. **Follow the handling controls.** Keep recontact details separate, collect no attachments or recordings, remove accidental identifiers before saving, honor correction/withdrawal, and report only aggregate non-identifying results. [S4:L668-L683]
3. **Use only the safe observation route.** Observe software only with agency authorization and a fictitious property or data-free screens; otherwise reconstruct verbally. [S4:L684-L687]
4. **Track and complete the sample.** Maintain separate interview/case counts and collect additional cases when needed to reach at least five interviews and 15 cases. [S4:L688-L690]
5. **Use answers to select scope and fixtures.** Rank the case, at most three document types, 30-50 fields, and the workflow problems that invented examples must preserve. [S4:L594-L605] [S4:L638-L651]
6. **Do not add a “property in order” product outcome.** Keep the current evidence-support and non-certification framing; derive professional roles and objective evidence needs from responses. [S4:L337-L370] [S4:L513-L539]
7. **Move to specification only after evidence-based GO and explicit approval.** Questionnaire completeness does not satisfy the discovery gate or create an approved spec. [S1:L7-L12] [S5:L474-L490]

## Input Issues

- None. S1-S5 were readable, resolved to the caller-supplied canonical paths, and were covered completely.
- No inputs were skipped.
- ADR mode was disabled; no ADR path or content was read.
- The tester feedback was supplied by the caller as an assessment input rather than a registered documentary source. Factual conclusions about project and questionnaire coverage were anchored to S1-S5; recommendations and interpretations are explicitly labeled as analyst inference where applicable.
