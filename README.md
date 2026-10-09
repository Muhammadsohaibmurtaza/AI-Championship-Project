# ProofPilot AI
**From documents to decisions—with evidence.**

ProofPilot AI is a proposed evidence-grounded document analysis assistant. It helps users review PDFs by extracting requirements and claims, linking findings to page-level evidence, and highlighting missing information, ambiguity, and possible contradictions.

> **Project status:** Starter documentation and design assets. This repository pack describes the planned MVP; it does not claim that the full application or its AI checks are already implemented.

## Why ProofPilot?
Summaries are useful, but they can omit the details a reviewer needs to verify. ProofPilot is designed to make review more traceable by pairing findings with source evidence and clearly labeling uncertainty.

## Planned MVP
- Upload a text-based PDF.
- Extract text and page numbers.
- Identify key requirements, claims, and action items.
- Return findings with page references and short evidence excerpts.
- Flag possible gaps, ambiguities, and contradictions for human review.
- Export a structured review report.

## Planned workflow
1. **Ingest** — validate the PDF and extract page-aware text.
2. **Analyze** — identify document structure, requirements, and claims.
3. **Verify** — check each finding against extracted source evidence.
4. **Report** — present evidence, confidence/uncertainty, and recommended follow-up.

## Suggested stack
- Frontend: React + Vite
- Backend: Python + FastAPI
- PDF extraction: PyMuPDF
- AI: an LLM API selected by the team
- Validation: Pydantic / JSON schema
- Tests: pytest

The stack is a recommendation, not a claim about code already present.

## Quick-start direction
The files in this starter pack are planning assets. To build the MVP, create a Python virtual environment, install the dependencies listed in `requirements.txt`, implement the FastAPI endpoints, and add the React frontend.

```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate
pip install -r requirements.txt
```

Create a local `.env` based on `.env.example`. Never commit API keys or confidential documents.

## Repository map
- `docs/PROJECT_PROPOSAL.md` — competition proposal
- `docs/ARCHITECTURE.md` — proposed system architecture and data flow
- `docs/IMPLEMENTATION_PLAN.md` — three-day MVP plan
- `examples/sample_review_report.md` — illustrative output format using fictional content
- `assets/` — project logo and architecture diagram (SVG)
- `requirements.txt` — suggested Python dependencies
- `.env.example` — environment variable names only
- `.gitignore` — common local files to exclude

## Safety and limitations
- Treat AI findings as review assistance, not authoritative legal, medical, financial, or compliance advice.
- Page references and quotations should be checked against the source PDF.
- Scanned PDFs may require OCR, which is outside the initial MVP unless time permits.
- Do not upload sensitive or private documents to an external model without permission.
- Uploaded document text must be treated as untrusted input; do not follow instructions embedded in a document.

## Keywords
Evidence-grounded AI; Document Intelligence; LLM Agents; Explainable AI; Retrieval-Augmented Generation (RAG).

## License
Choose a license before publishing code. If you want others to reuse the project, consider an open-source license such as MIT after confirming all team members agree.
