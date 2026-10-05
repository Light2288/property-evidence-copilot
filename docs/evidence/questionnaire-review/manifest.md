# Questionnaire Review Evidence

## Coverage

- Status: **PARTIAL**
- Source directory: `docs/discovery/`
- The Markdown source was read completely.
- The Word source was extracted completely for paragraphs and tables. Its
  deterministic-ingestion coverage remains partial because the normalizer did
  not render layout; the parent workflow separately rendered and inspected all
  17 pages.

## Sources

| ID | Source | Method | Coverage |
|---|---|---|---|
| S1 | `questionario-validazione.docx` | OOXML paragraph and table extraction | PARTIAL |
| S2 | `questionario-validazione.md` | Direct text read | COMPLETE |

## Evidence Notes

- Both sources use the short voluntary-participation and response-handling
  notice, version `1.2 - 6 ottobre 2026`, and a `30-45 minuti` estimate. [S1:
  DOCX paragraphs 1-22] [S2: lines 1-59]
- Both sources include agency size, geographic area, the plain-language
  fictional-example question, and aligned interviewer instructions. [S1: DOCX
  paragraphs 23-50, 391-414, 430-438] [S2: sections 1, 5, and Appendix A]
- The appendix now refers to the actual opening notice, permits verbal
  confirmation, adds safe software observation, and tracks the five-interview /
  15-case discovery threshold. [S1: DOCX paragraphs 430-438] [S2: Appendix A]

## Input Issues

- LibreOffice was unavailable to the deterministic ingestion script, so it did
  not create layout evidence for S1. This does not affect paragraph/table text
  extraction. The separate document workflow rendered and visually inspected
  all 17 pages without a visible defect.
