---
name: research-documentation-template
description: 'Structured research analysis template for documenting findings from source review, business logic extraction, and implementation guidance. Use this skill when summarizing research output into a standardized analysis note.'
---

# Research Documentation Template

## Purpose

This template provides a standardized structure for capturing and organizing research findings. Use it to produce a comprehensive analysis note after reviewing source materials such as documentation, specifications, or stakeholder inputs.

The resulting document should serve as a handoff artifact — clear enough for implementation planners, developers, or other AI agents to act on without needing to re-read the original sources.

## Instructions

- Fill in each section based on what was discovered during research.
- Leave sections empty or mark as "N/A" if not applicable.
- Be precise and factual — avoid speculation unless explicitly noted.
- Use bullet points for clarity and machine readability.

## Template

# Analysis Summary


## 1. Abstract
Briefly describe what was reviewed and why it matters.

## 2. Source Inputs
- Files reviewed:
- Key source areas:
- Source types:
- Confidence notes:

## 2.1 Source Coverage
- Fully reviewed:
- Partially reviewed:
- Not accessible / missing:

## 3. Business Context
- Problem being solved:
- Intended users or stakeholders:
- Business goal or outcome:
- Scope boundaries:

## 4. Core Business Logic
- Main rules:
- Decision points:
- Validations or constraints:
- Exceptions / edge cases:

## 5. Workflow Structure
1. Trigger / starting point
2. Main processing steps
3. Decision branches
4. End states / outputs

## 6. Data and Transformations
- Inputs:
- Outputs:
- Data mappings:
- Transformations / calculations:
- External integrations:

## 7. Implementation Observations and Guidance
- Current implementation pattern:
- Recommended guidance:
- Reusable components or services:
- Risks / technical concerns:

## 8. Gaps and Questions
- Missing information:
- Ambiguities:
- Items requiring stakeholder confirmation:

## 8.1 Confidence
- Confidence level:
- Reason for confidence level:

## 9. End-to-End Flow
Provide one concise, one-direction, high-level flow from input to final outcome.
- use the mermaid syntax for flow diagrams if helpful.
- keep it brief and focused on the main path, not every edge case.
- avoid overcomplicating with too many branches or details.
- focus on the core flow that would be most useful for implementation planning.

