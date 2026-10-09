# Proposed Architecture

This describes the intended MVP architecture; it is not a claim that all components are implemented.

```text
User
  |
  v
React UI ---- PDF upload ----> FastAPI backend
                                  |
                                  v
                           File validation
                                  |
                                  v
                         PyMuPDF page extraction
                                  |
                                  v
                       Page-aware text chunks
                                  |
                                  v
                        LLM structured analysis
                                  |
                                  v
                       Evidence / citation checks
                                  |
                                  v
                      Pydantic response validation
                                  |
                                  v
                     Findings + uncertainty labels
                                  |
                                  v
                    UI report / Markdown or JSON
```

## Core design principles
- **Traceability:** retain page numbers with extracted text throughout the pipeline.
- **Structured output:** validate model responses against a fixed schema.
- **Evidence before confidence:** findings without a matching excerpt should be marked unsupported or omitted.
- **Human review:** phrase potential contradictions and gaps as suggestions to inspect.
- **Privacy by default:** avoid storing uploaded files unless storage is necessary and explicitly documented.

## Suggested API
- `GET /health` — service health check.
- `POST /api/review` — accept one PDF and return structured review results.
- Optional future endpoint: `GET /api/reports/{id}` — only if persistence is later added.

## Example finding schema
```json
{
  "type": "missing_requirement",
  "title": "Evaluation plan may be incomplete",
  "summary": "The document mentions a model but does not specify an evaluation metric.",
  "evidence": [
    {
      "page": 2,
      "quote": "The system will classify the submitted text."
    }
  ],
  "status": "needs_human_review"
}
```

The example is illustrative. A real implementation should validate page bounds and verify that quoted evidence is present in extracted text.
