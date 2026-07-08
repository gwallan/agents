# Requirements Refinement Checklist

## 1. Terminology

- Define one canonical term per core concept.
- List aliases and banned words.
- Call out meanings that change by section.

## 2. Entities and States

- Identify core objects and their key attributes.
- Define state transitions and allowed actions.
- Separate default/system categories from user-defined categories.

## 3. Flow and Interaction

- Map each user action to a backend API or a local behavior.
- Specify loading, empty, error, and recovery states.
- State whether updates happen immediately or on refresh/polling.

## 4. Output

- Rewrite into an implementation-ready spec.
- Include unresolved questions in a dedicated section.
- Keep wording concise, testable, and unambiguous.

## 5. Delivery Gate

- Use this checklist only at the end, after the draft spec is written.
- If any item fails, revise the spec before handing it off.
- Do not load this file unless the work has reached final review.
