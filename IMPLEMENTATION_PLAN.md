# Three-Day MVP Implementation Plan

## Day 1 — Foundation
- Create the repository structure and Python environment.
- Build FastAPI health endpoint and PDF upload endpoint.
- Validate extension, MIME type, and file size.
- Extract text page-by-page with PyMuPDF.
- Return a useful error for empty or unreadable PDFs.

**Done when:** a text-based PDF can be uploaded and extracted text retains page numbers.

## Day 2 — Evidence-grounded analysis
- Define a structured output schema with Pydantic.
- Prompt the chosen LLM to extract claims, requirements, action items, ambiguities, and potential gaps.
- Require each finding to provide a source page and short evidence excerpt.
- Check that quoted excerpts occur in the extracted source text.
- Mark unsupported findings as unverified rather than silently accepting them.

**Done when:** the API returns valid structured results and evidence can be traced back to the document.

## Day 3 — Demo and polish
- Build a basic upload/results interface or a simple API demo if time is tight.
- Display findings, page references, evidence, and uncertainty.
- Add sample fictional documents and test cases.
- Test invalid file, empty PDF, long page, and unsupported claim cases.
- Add setup instructions, screenshots, known limitations, and a short demo script.

**Done when:** a reviewer can understand the value of the system in a short live demonstration.

## Priority order
1. PDF upload and extraction
2. Evidence-backed structured findings
3. Clear result display
4. Error handling and tests
5. Export, OCR, advanced retrieval, and polish as stretch goals
