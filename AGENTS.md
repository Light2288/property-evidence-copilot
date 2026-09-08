# Property Evidence Copilot Instructions

These project-specific rules supplement the global instructions.

## Scope Gate

- Do not scaffold or implement the application until discovery returns GO and
  the v0.1 spec and plan are explicitly approved.
- v0.1 covers one discovery-approved Italian real estate case, no more than
  three document types, and a taxonomy of 30-50 fields.
- Do not expand v0.1 into a CRM, portal integration, valuation product,
  compliance tool, mobile app, or autonomous workflow.

## Evidence and Human Review

- Every extracted value must retain source document, page or source region,
  source text when available, extraction method/version, and review status.
- Keep observed data, deterministic normalization, provider inference, user
  corrections, and confirmed output separate.
- Preserve `present`, `missing`, `uncertain`, `conflicting`, and `confirmed`.
- Only explicit human action may create `confirmed`.
- Never export unconfirmed inference or automatically resolve a conflict.
- The product must not certify cadastral, planning, energy, regulatory, or
  legal compliance.

## Data and Privacy

- Use only synthetic or properly anonymized documents and fixtures.
- Never commit real names, complete addresses, tax identifiers, signatures,
  bank details, identity documents, floor plans, or other sensitive content.
- No document content, OCR text, extracted value, prompt, response, correction,
  or user-supplied filename may appear in application or observability logs.
- Logs may contain only opaque identifiers, status, duration, size/page count,
  cost, retry count, provider/method identifier, and error category.
- Case deletion must cover original files, extracted text, provider results,
  corrections, audit events, temporary data, and exports. Late processing
  results must not recreate deleted data.

## Providers and Cloud

- Implement provider contracts and deterministic fakes first.
- Do not add Textract, Bedrock, AWS resources, credentials, or paid services
  without explicit approval after local fixtures and evaluation work.
- Do not process real documents or deploy to AWS during v0.1.
- Do not claim offline operation if a later configuration depends on cloud OCR
  or model inference.

## Release Gates

The following are blocking failures:

- a value presented as confirmed without evidence;
- a nonexistent citation;
- unreviewed inference in a final export;
- document content in logs.

The v0.1 release requires a complete synthetic workflow, human review of every
field, visible provenance, uncertainty/conflict handling, export, deletion, and
a reproducible evaluation report.
