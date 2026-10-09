# ProofPilot AI
## Project Proposal — 4th International AI Championship
**Category:** Open AI Applications  
**Project Type:** AI-agent-powered document analysis and verification  
**Planned MVP duration:** 2–3 days

---

## 1. Project Overview and Problem Statement

People regularly need to understand lengthy or complex documents such as research papers, assignment briefs, project proposals, policies, and application guidelines. Basic AI chatbots can summarize these documents, but summaries may omit important requirements, provide answers without clear evidence, or fail to identify missing information and contradictions. Users may then spend additional time manually checking the source document.

**ProofPilot AI** is an evidence-grounded document analysis application that uses a coordinated workflow of specialized AI agents to turn a user-uploaded document into a structured, actionable report. Rather than simply generating a summary, it identifies key requirements and claims, checks findings against the available document text, highlights gaps or potential inconsistencies, and provides page-level references wherever possible.

The project addresses the following problem:

> How can users extract reliable, traceable, and actionable information from complex documents without manually reviewing every page or blindly trusting an AI-generated answer?

The MVP will focus on a clearly bounded use case: reviewing project briefs, proposals, and research-style PDFs. The architecture can later be adapted to other document types.

## 2. Proposed Solution

ProofPilot AI will provide a web interface where users upload a PDF and select an analysis mode. A coordinated agent workflow will process the document in stages:

1. **Document Intake Agent:** Extracts text from the PDF, preserves page boundaries, and checks whether enough readable text is available.
2. **Requirements and Structure Agent:** Identifies the document's purpose, important points, requirements, deadlines, deliverables, and constraints.
3. **Evidence Checker Agent:** Examines proposed findings against relevant source passages, attaches page references, and marks unsupported or uncertain claims instead of presenting them as verified facts.
4. **Gap and Risk Agent:** Compares extracted requirements with the document's stated content or with information supplied by the user, then flags missing items, ambiguities, and possible contradictions.
5. **Report Agent:** Combines the results into a concise report with evidence, priorities, and recommended next actions.

The agents will operate as a controlled pipeline rather than being allowed to act without limits. Each stage will receive a defined input and produce structured output for the next stage. The application will display the stages and their statuses so users can understand how the result was produced.

**Important limitation:** Evidence checking can improve traceability, but it does not guarantee that every conclusion is correct. The MVP will distinguish between supported findings, uncertain findings, and items requiring human review.

## 3. Objectives and Expected Outcomes

### Objectives
- Build a working, browser-based AI application within 2–3 days.
- Demonstrate an agent workflow with distinct responsibilities and visible intermediate results.
- Extract key information and requirements from PDF documents.
- Ground findings in source passages and page references.
- Identify missing information, ambiguity, and potential contradictions.
- Generate an organized report that helps users decide what to review or do next.

### Expected outcomes
- A functional end-to-end demonstration using sample PDFs.
- A structured analysis report containing a summary, requirements checklist, evidence references, and prioritized issues.
- A transparent interface that shows which workflow stages completed and which findings need human review.
- A codebase that can be extended with additional document types and integrations.

Success will be evaluated through practical tests on a small set of sample documents. The team will check whether extracted requirements are relevant, page references point to the correct source material, and the application clearly labels unsupported or uncertain findings. Results will be reported honestly; no accuracy percentage will be claimed without testing.

## 4. Target Users

- **Students:** Reviewing assignment briefs, rubrics, research papers, and project requirements.
- **Researchers:** Extracting key claims, methods, limitations, and references from papers.
- **Project teams and applicants:** Checking proposals against a list of requested deliverables.
- **Small organizations:** Reviewing internal guidelines, procedures, and non-sensitive policy documents.

For the championship MVP, students and project teams will be the primary target users because their document-review needs are easy to demonstrate in a short live presentation.

## 5. Key Features and Deliverables

### Core features
1. **PDF upload and text extraction** — Upload a PDF and extract readable text while preserving page numbers.
2. **Selectable analysis mode** — Choose a focused review such as “Check against requirements” or “Research paper overview.”
3. **Visible agent workflow** — Show the progress and output of each agent stage.
4. **Evidence-linked findings** — Include source excerpts and page references for key findings.
5. **Requirements checklist** — Present requirements as complete, missing, unclear, or requiring review, when the source provides enough information to make that assessment.
6. **Gap and inconsistency alerts** — Flag possible omissions, ambiguous statements, and conflicting information for human inspection.
7. **Actionable report** — Generate a readable report with key findings, evidence, priorities, and recommended next steps.
8. **Copy or download report** — Allow the user to copy the report or download it as Markdown or text.

### Deliverables
- A working web application.
- A multi-stage AI-agent workflow.
- PDF parsing and page-aware evidence display.
- At least two sample document demonstrations.
- Source code with setup instructions and environment-variable guidance.
- A short demo script and a list of known limitations.

### Optional stretch features (only if the core MVP is stable)
- Export a polished PDF report.
- Compare a document against a separately supplied checklist.
- Add a question-and-answer panel that answers only from the uploaded document and shows evidence.
- Save previous analyses locally or in a database.

## 6. Implementation Plan and Timeline

The schedule assumes one developer using AI coding agents to accelerate scaffolding, implementation, and debugging. Scope should be reduced rather than sacrificing end-to-end reliability.

| Time | Tasks | Expected result |
|---|---|---|
| **Day 1 — Morning** | Finalize the MVP; create the web interface; set up the backend and environment variables. | Application skeleton and upload screen. |
| **Day 1 — Afternoon** | Implement PDF text extraction with page boundaries; connect the LLM API; define structured output formats. | Uploaded PDFs can be processed and key information extracted. |
| **Day 2 — Morning** | Implement the agent stages: structure/requirements, evidence checking, and gap analysis. | The backend produces a structured analysis with source references. |
| **Day 2 — Afternoon** | Build the results dashboard, workflow status display, checklist, and report view. | A complete user journey from upload to report. |
| **Day 3 — Morning** | Test with sample PDFs; fix parsing, API, and evidence-reference errors; add empty-state and failure handling. | More reliable demonstration and clear limitations. |
| **Day 3 — Afternoon** | Prepare sample inputs, rehearse the live demo, document setup, and capture screenshots or a backup recording. | Championship-ready MVP and demo materials. |

### Suggested MVP acceptance checklist
- A user can upload a supported PDF and receive a clear error for unsupported or unreadable files.
- The application extracts text while retaining page boundaries.
- The workflow displays distinct processing stages.
- Key findings include a source excerpt and page number when available.
- Unsupported or uncertain findings are labelled rather than presented as confirmed.
- The report can be copied or downloaded.
- API keys are kept in environment variables and are not exposed in frontend code.
- The demo works with pre-tested sample documents and has a backup plan in case the API or network fails.

## 7. Resources or Requirements

### Software and services
- **Frontend:** React with Vite, or another familiar lightweight web framework.
- **Backend:** Python with FastAPI, or Node.js/Express. Choose one backend rather than building both.
- **AI model:** An available LLM API that supports structured responses; use a model and provider accessible to the team.
- **PDF extraction:** PyMuPDF or a comparable PDF text-extraction library.
- **Validation:** Pydantic or equivalent schema validation for structured agent outputs.
- **Version control:** Git and GitHub.
- **Development assistance:** AI coding agents for scaffolding, implementation, test generation, and debugging.

### Hardware and access
- A laptop or desktop capable of running the development environment.
- Internet access for model API calls, unless a compatible local model is used.
- An API key and sufficient available usage quota.
- Two or more non-sensitive sample PDFs for testing and demonstration.

### Suggested architecture
**Browser UI → Backend API → PDF text extraction → Agent pipeline → Evidence validation → Report renderer**

For a 2–3 day MVP, use a simple sequential workflow with clear input/output schemas. A complex autonomous multi-agent framework, vector database, authentication system, and production deployment are not necessary unless time remains.

## 8. Potential Challenges or Risks

| Challenge / risk | Mitigation |
|---|---|
| **Hallucinated findings** | Require source evidence for important claims; label uncertain findings; ask the user to verify critical decisions. |
| **Incorrect page references** | Preserve page boundaries during extraction and test citations against known passages. |
| **Scanned or image-only PDFs** | Detect when extracted text is insufficient; display a clear message. OCR can be a stretch feature if time allows. |
| **Long documents exceeding model limits** | Limit the MVP's document size; split text by page or section; summarize chunks before the final synthesis if necessary. |
| **Inconsistent agent outputs** | Use structured schemas, validate outputs, and provide safe fallbacks for invalid responses. |
| **API latency, rate limits, or cost** | Keep prompts concise, limit document size, cache results during development if appropriate, and prepare a pre-tested demo document. |
| **Sensitive document content** | Use public or synthetic sample documents for the demo; disclose that text may be sent to the selected AI provider; avoid uploading confidential documents without authorization. |
| **Overambitious scope** | Prioritize upload, evidence-grounded analysis, checklist, and report. Treat optional features as stretch goals. |
| **Prompt injection inside uploaded files** | Treat document contents as untrusted data, not instructions; keep tool access restricted and do not let document text override system rules or trigger external actions. |

## Conclusion

ProofPilot AI aims to make document analysis more useful and transparent by combining specialized AI-agent stages with evidence-linked findings and practical next steps. Its scope is deliberately designed for a 2–3 day implementation window, with a working demonstration prioritized over unnecessary complexity. The project will showcase an applied AI workflow while acknowledging that generated findings still require human review.

**Proposed tagline:** *From documents to decisions—with evidence.*
