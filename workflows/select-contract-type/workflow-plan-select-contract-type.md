---
stepsCompleted: ['step-01-discovery', 'step-02-classification', 'step-03-requirements', 'step-04-tools', 'step-05-plan-review', 'step-06-design', 'step-07-foundation', 'step-08-build-step-01', 'step-09-build-step-02', 'step-09-build-step-03', 'step-10-confirmation', 'step-11-completion']
created: 2026-03-15
completionDate: 2026-03-15
status: COMPLETE
approvedDate: 2026-03-15
confirmationDate: 2026-03-15
confirmationType: new_workflow
coverageStatus: complete
---

# Workflow Creation Plan: select-contract-type

## Discovery Notes

**User's Vision:**
A lightweight decision tool that helps users identify the correct contract type for their deal before creation begins. Solves the "wrong contract type" problem by running a short intake interview and recommending from five supported types with clear reasoning.

**Who It's For:**
Luey the Lawyer's users — freelancers, small business owners, first-time collaborators who may not know which contract they need.

**What It Produces:**
A contract type recommendation (non-document output) passed to the create-contract workflow. Explains *why* the type was recommended, not just what.

## Classification Decisions

**Workflow Name:** select-contract-type
**Target Path:** `src/modules/quick-legal-contract/workflows/select-contract-type/`

**4 Key Decisions:**
1. **Document Output:** false — recommendation only, no file produced
2. **Module Affiliation:** quick-legal-contract
3. **Session Type:** single-session — 3 steps, short intake interview
4. **Lifecycle Support:** create-only — steps-c/ only

**Structure Implications:**
- Single `steps-c/` folder, no steps-e/ or steps-v/
- No step-01b-continue.md needed
- No document template needed
- 3 step files: step-01-gather-deal-info.md, step-02-recommend-type.md, step-03-confirm-selection.md

---

## Requirements

**Flow Structure:**
- Pattern: linear
- Phases: intake → analysis → recommendation → confirmation
- Estimated steps: 3

**User Interaction:**
- Style: highly collaborative — Luey drives conversation, user answers
- Decision points: user must confirm recommendation before workflow exits
- Checkpoint frequency: confirmation at end only

**Inputs Required:**
- Required: description of deal, number of parties, whether money/compensation is involved
- Optional: US state (defaults to `{default_jurisdiction}`)
- Prerequisites: none

**Output Specifications:**
- Type: decision/recommendation
- Format: conversational — contract type name + plain-English explanation of why
- Supported types: business partnership agreement, service agreement, mutual NDA, one-way NDA, freelance contract
- Frequency: single recommendation per session

**Success Criteria:**
- User understands which contract type fits their deal
- User understands why that type was recommended
- User is confident and ready to proceed to create-contract

**Instruction Style:**
- Overall: intent-based — Luey adapts naturally, feels like talking to a lawyer not filling a form
- Notes: questions should be conversational, not form-like

---

## Tools Configuration

**Core BMAD Tools:**
- **Party Mode:** excluded — decision tool, not creative exploration
- **Advanced Elicitation:** excluded — simple 3-step flow, no quality gates needed
- **Brainstorming:** excluded — not applicable

**LLM Features:**
- **Web-Browsing:** excluded — recommendations based on static legal knowledge
- **File I/O:** excluded — non-document, purely conversational output
- **Sub-Agents:** excluded — single-agent workflow
- **Sub-Processes:** excluded — linear flow, no parallelism

**Memory:**
- Type: single-session
- Tracking: none needed beyond conversation context

**External Integrations:** none

**Installation Requirements:** none

---

## Workflow Design

**Step Outline:**

| File | Type | Menu Pattern | Goal |
|------|------|-------------|------|
| step-01-gather-deal-info.md | Init (non-continuable) | Auto-proceed | Ask 3-5 questions conversationally |
| step-02-recommend-type.md | Middle (simple) | Auto-proceed | Map answers to contract type taxonomy |
| step-03-confirm-selection.md | Final | C-only | Present recommendation + reasoning, confirm |

**Flow:**
```
step-01 (gather) → auto-proceed → step-02 (analyze) → auto-proceed → step-03 (confirm) → chain to create-contract
```

**Interaction Patterns:**
- Step 01: conversational intake, no form-like questions, auto-proceeds once all inputs collected
- Step 02: AI-autonomous analysis, no user input, auto-proceeds
- Step 03: C-only, handles reconsider branch if user disagrees

**Data Flow:**
- Step 01 collects: deal description, party count, money involved, US state (optional)
- Step 02 maps to: one of 5 contract types + prepares plain-English reasoning
- Step 03 outputs: contract type + reasoning → conversational handoff to create-contract

**File Structure:**
```
src/modules/quick-legal-contract/workflows/select-contract-type/
├── workflow.md
└── steps-c/
    ├── step-01-gather-deal-info.md
    ├── step-02-recommend-type.md
    └── step-03-confirm-selection.md
```

**Workflow Chaining:**
- No required prior workflow inputs
- Step 03 final: recommends create-contract with selected type pre-loaded

**Subprocess Optimization:** not applicable

**Special Handling:**
- Step 03 reconsider branch: if user disagrees, Luey asks what feels off and adjusts
- 5 contract type taxonomy + selection logic embedded in step-02

---

**Key Insights:**
- 3-step flow: gather-deal-info → recommend-type → confirm-selection
- Supported types: business partnership agreement, service agreement, mutual NDA, one-way NDA, freelance contract
- Anchor use case: the "wrong contract type" scenario (Scenario 3 from module brief)
- On-ramp to create-contract, not a standalone deliverable
- Should educate the user, not just label them
