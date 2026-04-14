# Prompt Template : Requirements to User Stories Generator

## How to Use This Template

This file contains ready-to-use prompt templates for invoking the `User story generator agent-instruction` agent. Copy the relevant template into GitHub Copilot Chat and replace all `{{PLACEHOLDER}}` values before sending.

\---

## Template 1 — Standard Invocation (File Reference)

Use this when you have a requirements file open or available in the workspace.

```
@story-generator

Please analyse the requirements document at {{FILE\_PATH}} and generate a complete set of Agile user stories.

Follow these instructions:
1. Read and parse the full document before generating any output.
2. Identify all functional requirements, non-functional requirements, constraints, and assumptions.
3. Group stories under Epics if multiple feature domains are present.
4. Use the standard user story format: "As a \[actor], I want \[action], so that \[value]."
5. Include at least 3 acceptance criteria per story.
6. Provide a traceability matrix mapping each requirement to its story/stories.
7. Flag any ambiguous, incomplete, or contradictory requirements.

Output everything inline in this chat. Do not create any files.
```

**Replace:**

* `{{FILE\_PATH}}` → e.g., `@requirements.txt` or `./docs/project-requirements.txt`

\---

## Template 2 — Pasted Requirements Text

Use this when you want to paste requirements directly into the chat.

```
@story-generator

Please analyse the following requirements and generate a complete set of Agile user stories.

--- REQUIREMENTS START ---
{{PASTE\_REQUIREMENTS\_HERE}}
--- REQUIREMENTS END ---

Instructions:
1. Read and parse all requirements above before generating output.
2. Identify actors, functional requirements, NFRs, constraints, and assumptions.
3. Group stories under Epics if the requirements span multiple feature areas.
4. Use the standard user story format: "As a \[actor], I want \[action], so that \[value]."
5. Include at least 3 acceptance criteria per story.
6. Provide a traceability matrix at the end.
7. Flag all ambiguities and gaps in a dedicated section.

Output everything inline in this chat.
```

**Replace:**

* `{{PASTE\_REQUIREMENTS\_HERE}}` → Paste the raw requirements text

\---

## Template 3 — Focused Domain Analysis

Use this when you want stories generated for a specific feature domain only.

```
@story-generator

Please analyse the requirements document at {{FILE\_PATH}} and generate user stories specifically for the "{{DOMAIN\_NAME}}" feature domain only.

Context:
- Target Domain: {{DOMAIN\_NAME}}
- Primary Actor(s): {{PRIMARY\_ACTORS}}
- Sprint Goal (optional): {{SPRINT\_GOAL}}

Instructions:
1. Extract only the requirements related to {{DOMAIN\_NAME}}.
2. Generate user stories for those requirements only.
3. Note any dependencies on requirements outside this domain.
4. Include acceptance criteria, priority, and effort estimate for each story.
5. Provide a mini traceability matrix for this domain.
```

**Replace:**

* `{{FILE\_PATH}}` → Path to the requirements file
* `{{DOMAIN\_NAME}}` → e.g., `User Authentication`, `Payment Processing`, `Reporting`
* `{{PRIMARY\_ACTORS}}` → e.g., `End User, Admin, System`
* `{{SPRINT\_GOAL}}` → e.g., `Enable users to log in and manage their profile`

\---

## Template 4 — Re-analysis / Refinement Pass

Use this after an initial story generation to refine or fill gaps.

```
@story-generator

I have already generated an initial set of user stories. Please perform a refinement pass based on the following feedback:

Original requirements file: {{FILE\_PATH}}
Feedback / Change Request: {{FEEDBACK\_OR\_CHANGE}}

Specifically:
1. Revise story {{STORY\_ID}} to address: {{REVISION\_DETAIL}}
2. Add missing stories for requirement {{REQUIREMENT\_ID}}.
3. Split story {{STORY\_ID}} into smaller, more granular stories if it is too large for a single sprint.
4. Re-check and update the traceability matrix.

Output only the revised/new stories and the updated traceability matrix. Do not regenerate the full set.
```

**Replace:**

* `{{FILE\_PATH}}` → Path to the requirements file
* `{{FEEDBACK\_OR\_CHANGE}}` → Your specific feedback
* `{{STORY\_ID}}` → e.g., `US-004`
* `{{REVISION\_DETAIL}}` → What specifically needs changing
* `{{REQUIREMENT\_ID}}` → e.g., `REQ-012`

\---

## Template 5 — Quick Single Story (Ad-hoc)

Use this for a fast, single-story generation from one requirement.

```
@story-generator

Generate a single user story for the following requirement:

"{{SINGLE\_REQUIREMENT\_TEXT}}"

Actor: {{ACTOR}}
Priority: {{PRIORITY}}

Include: title, story statement, 3 acceptance criteria, effort estimate, and any notes.
```

**Replace:**

* `{{SINGLE\_REQUIREMENT\_TEXT}}` → The specific requirement text
* `{{ACTOR}}` → e.g., `registered user`, `admin`, `system`
* `{{PRIORITY}}` → `Must Have` / `Should Have` / `Could Have` / `Won't Have`

\---

## Effort Estimate Reference

Use this guide when estimating story size:

|Size|Points|Typical Complexity|
|-|-|-|
|XS|1|Trivial UI change, config update|
|S|2|Simple CRUD operation, single form|
|M|3–5|Feature with validation, basic integration|
|L|8|Complex feature, multiple components|
|XL|13+|Epic-level, should be split|

## Priority Reference (MoSCoW)

|Priority|Meaning|
|-|-|
|Must Have|Critical — system fails without it|
|Should Have|Important — significant value, not critical|
|Could Have|Nice to have — include if time permits|
|Won't Have|Out of scope for this iteration|



