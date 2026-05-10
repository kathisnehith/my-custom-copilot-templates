---
name: create-implementation-plan
description: 'Create a new implementation plan file for new project , features, refactoring existing code or upgrading packages, design, architecture or infrastructure.'
---

# Create Implementation Plan

## Primary Directive

Your goal is to create a new implementation plan file. Your output must be machine-readable, deterministic, and structured for autonomous execution by other AI systems or humans.

## Execution Context

This prompt is designed for AI-to-AI communication and automated processing. All instructions must be interpreted literally and executed systematically without human interpretation or clarification.

## Core Requirements

- Generate implementation plans that are fully executable by AI agents or humans
- Use deterministic language with zero ambiguity
- Structure all content for automated parsing and execution
- Ensure complete self-containment with no external dependencies for understanding

## Plan Structure Requirements

Plans must consist of discrete, atomic phases containing executable tasks. Each phase must be independently processable by AI agents or humans without cross-phase dependencies unless explicitly declared.

## Phase Architecture

- Each phase must have measurable completion criteria
- Tasks within phases must be executable in parallel unless dependencies are specified
- All task descriptions must include specific file paths, function names, and exact implementation details
- No task should require human interpretation or decision-making

## AI-Optimized Implementation Standards

- Use explicit, unambiguous language with zero interpretation required
- Structure all content as machine-parseable formats (tables, lists, structured data)
- Include specific file paths, line numbers, and code references where applicable
- Define all variables, constants, and configuration values explicitly
- Provide complete context within each task description
- Use standardized prefixes for all identifiers (REQ-, TASK-, etc.)
- Include validation criteria that can be automatically verified



## Template Validation Rules

- All front matter fields must be present and properly formatted
- All section headers must match exactly (case-sensitive)
- All identifier prefixes must follow the specified format
- Tables must include all required columns
- No placeholder text may remain in the final output




### Example Template to USE

```md
---
plan_id: PLAN-001
project: <project-name>
type: <new-project|feature|refactor|upgrade>
status: <draft|ready|in-progress|done>
root_folder: <project-root>
goal: <one-line goal>
---

# Implementation Plan

## Project
- Name: <project-name>
- Type: <new-project|feature|refactor|upgrade>
- Goal: <what should be built>
- Root folder: <project-root>

## Project Dependencies
| DEP_ID | Dependency | Version | Purpose | Status |
|---|---|---|---|---|
| DEP-001 | <name> | <version> | <why needed> | <todo|done> |
| DEP-002 | <name> | <version> | <why needed> | <todo|done> |

## Requirements
| REQ_ID | Requirement |
|---|---|
| REQ-001 | <system must do X> |
| REQ-002 | <system must do Y> |

## Phases

### PHASE-001 - Setup
**Goal:** <setup goal>  
**Status:** <todo|in-progress|done>

| TASK_ID | Task | Feature | Layer | File/Folder | Tags | REQ | Status |
|---|---|---|---|---|---|---|---|
| TASK-001 | <create project structure> | <setup> | <setup> | <src/> | <setup> | <REQ-001> | <todo> |
| TASK-002 | <add base config> | <config> | <config> | <package.json> | <setup,config> | <REQ-001> | <todo> |

### PHASE-002 - Core
**Goal:** <main feature goal>  
**Status:** <todo|in-progress|done>

| TASK_ID | Task | Feature | Layer | File/Folder | Tags | REQ | Status |
|---|---|---|---|---|---|---|---|
| TASK-003 | <implement feature> | <auth> | <service> | <src/services/auth.service.ts> | <feature> | <REQ-002> | <todo> |
| TASK-004 | <add api/controller> | <auth> | <controller> | <src/controllers/auth.controller.ts> | <feature,api> | <REQ-002> | <todo> |

### PHASE-003 - Validation
**Goal:** <testing and verification goal>  
**Status:** <todo|in-progress|done>

| TASK_ID | Task | Feature | Layer | File/Folder | Tags | REQ | Status |
|---|---|---|---|---|---|---|---|
| TASK-005 | <add tests> | <auth> | <test> | <tests/auth.test.ts> | <testing> | <REQ-002> | <todo> |
| TASK-006 | <update docs> | <docs> | <docs> | <README.md> | <docs> | <REQ-001> | <todo> |




```

