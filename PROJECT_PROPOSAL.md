# ProofPilot AI — Project Proposal

**Tagline:** From documents to decisions—with evidence.  
**Category:** Open AI Applications

## 1. Project Overview and Problem Statement
People review project briefs, proposals, research papers, policies, and other PDFs to make decisions. Manual review can be slow, and a generic AI summary may omit important requirements or present unsupported conclusions. Reviewers need a way to see not only what an AI system concludes, but also where the source document supports that conclusion.

## 2. Proposed Solution
ProofPilot AI is an evidence-grounded document review assistant. A user uploads a PDF, and a staged pipeline extracts page-aware text, identifies key claims and requirements, checks whether each finding is supported by source passages, and produces a report with page references. It can flag potential omissions, ambiguous wording, and possible contradictions for a human to inspect.

The core differentiator is traceability: findings are paired with source evidence and uncertainty labels instead of being presented as unquestionable facts.

## 3. Objectives and Expected Outcomes
- Reduce the effort required for a first-pass document review.
- Make AI-generated findings easier to verify with page-level references.
- Surface missing requirements, unclear statements, and possible inconsistencies.
- Provide a readable report that supports—not replaces—human judgment.
- Deliver a working, demonstrable MVP with a clear path for future improvement.

## 4. Target Users
- Students reviewing assignment briefs, proposals, and research papers.
- Project teams checking whether plans address stated requirements.
- Researchers screening papers and extracting claims.
- Small organizations reviewing internal, non-sensitive documents.

## 5. Key Features / Deliverables
1. PDF upload and validation.
2. Page-aware text extraction.
3. Structured extraction of claims, requirements, and action items.
4. Evidence excerpts and page references for each finding.
5. Potential gap, ambiguity, and contradiction flags.
6. Uncertainty labels and a human-review reminder.
7. Exportable Markdown or JSON report.
8. Demo PDF and test cases using fictional/non-sensitive content.

## 6. Implementation Plan and Timeline
| Day | Work | Deliverable |
|---|---|---|
| Day 1 | Set up repository, PDF extraction, API skeleton, and upload validation | Upload-to-text path |
| Day 2 | Implement structured LLM analysis, evidence matching, and report schema | End-to-end review pipeline |
| Day 3 | Build results UI, test edge cases, polish demo, and document limitations | Demo-ready MVP |

## 7. Resources or Requirements
- Python 3.11+ and a virtual environment.
- FastAPI, Uvicorn, PyMuPDF, Pydantic, and pytest.
- React + Vite for the user interface, if time permits.
- Access to an LLM API and a protected API key.
- Sample PDFs that contain no private or sensitive information.
- Git and GitHub for version control.

## 8. Potential Challenges or Risks
- **Hallucinated findings:** require evidence excerpts and mark unsupported output as unverified.
- **Incorrect page references:** retain page metadata during extraction and test references manually.
- **Scanned PDFs:** disclose the limitation; treat OCR as optional stretch work.
- **Long documents:** limit file size and pages for the MVP; chunk by page or section.
- **API cost and latency:** use a small demo document and avoid unnecessary calls.
- **Sensitive content:** provide a clear warning and avoid retaining uploaded files by default.
- **Prompt injection in documents:** treat extracted content as untrusted data, never as system instructions.
- **Over-scoping:** prioritize upload, extraction, evidence-backed findings, and a clear report.

## MVP success criteria
A demo is considered successful when it can accept a supported PDF, produce structured findings, show a relevant evidence excerpt and page number for each supported finding, label uncertain items, and handle invalid files without crashing.
