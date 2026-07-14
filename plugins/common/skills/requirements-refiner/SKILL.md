---
name: requirements-refiner
description: Use when the user provides a PRD, feature brief, or ambiguous requirements and wants help resolving ambiguities, aligning terminology, or rewriting them into an implementation-ready specification for frontend or engineering work.
---

# Requirement Refiner

## Overview

Use this skill to transform informal or ambiguous product requirement into clear, implementable requirement specifications. Focus on disambiguating terminology, clarifying state and process rules, and listing the minimal unresolved issues needed to advance engineering work.

<!-- When possible, first normalize the input into a fixed requirement template, then perform analysis to ensure consistent output across different documents. -->

## Workflow

### 1. First, Read the Project Rules

- Before reading the user's requirements document, identify which web application it belongs to. If the repository contains multiple web apps, choose the target app first, then load that app's `docs/index.md` if it exists, followed by the project business rules from `docs/` within that app.

- Understand these project business rules so that when comparing with the requirements document later, you base your analysis on project facts rather than assumptions, especially `docs/glossary.md` and `docs/decisions.md`.

### 2. Then, Carefully understand the product requirements input by the user.

- Identify business goals, target users, business functions, and main workflows.

- Distinguish core behaviors from nice-to-have details.

- Note any assumptions that seem to be made but are not explicitly stated in the document.

- If the input is not yet structured, first organize it into a standard requirements template before proceeding with in-depth analysis.

### 3. Standardize Terminology

- Extract all domain terms, objects, states, and actions.

- Mark aliases, overloaded terms, and words that should not be confused.

- If a term changes meaning across different sections or conflicts with project business rules, clearly point it out.

### 4. Build Object and State Models

- List core entities and their key attributes.

- For each important interaction, write a state machine or lifecycle that describes state transitions or availability.

- Record the transition rules, allowed actions, and prohibited actions for each state.

### 5. Validate Interaction Details

- Clarify entry points, layout, empty states, loading states, and error states.

- When the document mentions "backend processing" or "frontend processing", specify which side is actually responsible for the logic.

### 5.1 Interaction Design Analysis

- Extract user-visible functions and translate them into interaction elements.

- Using state machine thinking, represent each flow as "user action → system response → page change".

- Clearly identify empty data, error prompts, constraints, and other boundary states.

- Output the results in a structured list, including:

  - Function name

  - User action

  - System feedback

  - Preconditions

  - Exception handling

- The analysis should focus on interaction behavior, not implementation details, unless an interface contract is needed to explain the behavior.

### 6. Clarify Development Boundaries and Scope

- Sort out which tasks are frontend development work and which are backend development work.

- The final output should be a requirements document oriented towards frontend development needs.

### 7. Drill Down

- For requirements or designs, ask questions in batches, but only for branches that still change the spec after checking project docs and code.

- Resolve each branch that affects behavior, UI, ownership, or acceptance criteria before moving on. Provide a recommended answer for each question.

- If a branch cannot be answered from the repository and does not block the implementation-ready spec, capture it in "Pending Issues" instead of looping.

- If a question can be answered by exploring the codebase, prioritize doing so before asking the user.

### 8. Generate Clear Product Requirement Specifications

- Must follow the existing standard template in `references/prd-template.md` for document writing, and supplement missing content when necessary.

- Before finalizing, load `references/checklist.md` and use it as the delivery gate for the refined specification.

- Ensure the document content is a structure that the engineering team can directly implement.

- Keep language concise, consistent, and testable.

- Add a dedicated "Pending Issues" or "Ambiguity Markers" section for unresolved items.

- Where possible, prioritize clear rules over paragraph descriptions.

## Never Do

- Never analyzing existing code to understand the current functionality; instead, understand it through existing documentation.

- Never rewrite an assumption as a fact; label it as a question or a pending issue.

- Never merge distinct domain terms into one label just to shorten the document.

- Never mix frontend responsibility and backend responsibility in the same rule without naming the owner.

- Never invent states, acceptance criteria, or error paths that are not supported by project rules or source material.

- Never keep asking questions after the remaining uncertainty no longer changes the structure of the spec.
