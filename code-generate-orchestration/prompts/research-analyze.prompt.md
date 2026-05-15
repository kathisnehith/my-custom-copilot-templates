---

description: "Analyze attached source materials (PDFs, code, notebooks, docs) and produce a structured business research document"
---

# Research & Analysis Request

## Objective
Analyze the attached source materials and produce a comprehensive, structured research document inside `/business-research-doc/`.

## Focus Area
${input:What specific topic, feature, or system should the analysis focus on?}

## Instructions
1. Review **all attached files** thoroughly — these are your primary source of truth.
2. Cross-reference findings across the attached materials for consistency.
3. Extract business logic, workflows, data transformations, validations, decision points, and dependencies.
4. Identify gaps, ambiguities, or conflicting information in the sources.
5. Produce a research document following the standard research template structure:
   - Abstract, Source Inputs, Business Context, Key Findings, Workflow Analysis, Data Model, Risks & Gaps, Recommendations.
6. Save the output to `/business-research-doc/` with an appropriate file name.
7. Present key findings and any open questions for user confirmation before saving.

## Source Priority
1. Attached files and direct user input (highest)
2. Workspace source code and tests
3. Workspace documentation and configuration
4. Derived inference (label clearly)

> **Attach your source files** (PDFs, `.py`, `.ipynb`, `.md`, code files, design docs) to this prompt before running.
