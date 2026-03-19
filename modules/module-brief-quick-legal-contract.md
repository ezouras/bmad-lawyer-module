# Module Brief: quick-legal-contract

**Date:** 2026-03-15
**Author:** Evie
**Module Code:** quick-legal-contract
**Module Type:** Standalone
**Status:** Ready for Development

---

## Executive Summary

Quick Contract provides fast, tailored, legally-sound contracts for real deals — through a full creation and validation loop. Luey the Lawyer interviews the user about their specific deal, generates a custom document, validates its own work for legal completeness, and delivers a PDF the user can trust. Speed and confidence together — not one or the other.

**Module Category:** Legal / Document Generation
**Target Users:** Freelancers, entrepreneurs, and collaborators making real deals in the US
**Complexity Level:** Moderate (1 agent, 7 workflows, 3 external integrations)

---

## Module Identity

### Module Code & Name

- **Code:** `quick-legal-contract`
- **Name:** `Quick Contract`

### Core Concept

Quick Contract fills the gap between the expensive lawyer and the useless generic template. It's for the person who made a real deal — profit share, service agreement, NDA — and needs it documented fast, affordably, and correctly. The module guides users through a smart intake interview, generates a contract tailored to their specific situation, validates the output for legal soundness, and delivers a signed PDF both parties can rely on.

### Personality Theme

Luey the Lawyer — enthusiastic about every contract being built, knowledgeable enough to break down any legal jargon on request, and approachable enough to make the intimidating feel accessible. Luey makes legal protection feel exciting, not scary.

---

## Module Type

**Type:** Standalone

Quick Contract is a brand new, independent module with its own identity and domain. It does not extend or depend on any existing BMAD module. It is self-contained — installable alongside other modules — and covers the full lifecycle of legal contract creation, validation, signing, and storage.

---

## Unique Value Proposition

**What makes this module special:**

"For freelancers, entrepreneurs, and collaborators making real deals, Quick Contract provides fast, tailored, legally-sound contracts — unlike generic templates or expensive lawyers — because Luey interviews you about your specific deal, builds a custom document, then validates its own work before handing you a PDF you can actually trust."

**Why users would choose this module:**

| Alternative | The Problem | Quick Contract's Edge |
|---|---|---|
| Generic templates | One-size-fits-none, no guidance | Tailored to your specific deal |
| Hiring a lawyer | Expensive, slow, overkill for simple deals | Fast and affordable |
| Nothing / handshake | No recourse when things go wrong | Documented, enforceable agreement |
| LegalZoom etc. | Still form-filling, no intelligent review | Conversational + self-validating |

The "aha!" moment: when Luey finishes the validation and says "Here's what each clause protects you from" — and the user realizes they actually understand their own contract.

**Legal Disclaimer:** Every document includes a clear disclaimer — Quick Contract is not a substitute for licensed legal counsel. It provides legally-informed, best-effort documents for straightforward agreements.

---

## User Scenarios

### Target Users

**Primary — "The Dealmaker"**
A freelancer, entrepreneur, or collaborator making a real agreement with another person. No legal background. Needs something fast and trustworthy. Pain point: informal agreements fall apart, templates are generic and confusing, lawyers are expensive. Success: downloads a PDF in under 10 minutes and feels confident both parties are protected.

**Secondary — "The Other Party"**
The person who receives and signs the contract. May have no idea what module was used — they just receive a document. Cares that it is clear, fair, and explains what they're agreeing to.

### Primary Use Case

Alex is a developer who built a website for someone on a profit-share deal — 5% of profits, no upfront pay. They've been burned before. This time, they load Quick Contract before the work begins, document the agreement, both parties sign electronically, and Alex has a legally-grounded PDF that protects them if the other party doesn't follow through.

### User Journey

1. **Problem** → Alex makes a real deal; needs it documented fast before work begins
2. **Load module** → Luey greets them: *"Let's make this deal bulletproof!"*
3. **`select-contract-type`** → Luey asks 3 questions and recommends the right contract type
4. **`create-contract`** → Luey interviews Alex about the specific deal, generates a tailored draft
5. **`validate-contract`** → Luey reviews it: *"This looks airtight — here's what each clause means"*
6. **`sign-contract`** → Both parties sign via DocuSign, timestamp captured
7. **Output** → Signed PDF downloaded; Luey reminds both parties to store it somewhere safe
8. **Result** → Alex feels confident the deal is documented and enforceable

---

## Agent Architecture

### Agent Count Strategy

Single agent. Luey the Lawyer handles the entire module — intake, creation, validation, explanation, and signing coordination. The two-phase flow (create → validate) is a workflow concern, not an agent concern. A single consistent voice creates a more cohesive and trustworthy experience for the user.

### Agent Roster

| Agent | Name | Role | Expertise |
|-------|------|------|-----------|
| luey-the-lawyer | Luey | Contract Creation & Validation Specialist | Legal document drafting, US contract law, plain-English explanation, deal intake |

### Agent Interaction Model

Single agent — no inter-agent coordination required. Luey orchestrates all workflows sequentially within one conversation. The user always speaks to Luey from start to finish.

### Agent Communication Style

Enthusiastic and confident. Luey is excited about every contract being built. Knowledgeable but never condescending — breaks down legal jargon clearly when asked. Reassuring and trustworthy. Makes the user feel like they have a friend who happens to be a lawyer.

---

## Workflow Ecosystem

### Core Workflows (Essential)

| Workflow | Purpose | Flow |
|---|---|---|
| `create-contract` | Interview user and generate a tailored contract | Intake questions → select clauses → draft document → PDF output |
| `validate-contract` | Review contract for legal completeness and soundness | Load document → check clauses → flag issues → validation report |

### Feature Workflows (Specialized)

| Workflow | Purpose | Flow |
|---|---|---|
| `explain-contract` | Break down any clause in plain English | Select clause → Luey explains it simply |
| `amend-contract` | Add, remove, or modify terms post-creation | Load contract → specify changes → revised PDF |
| `review-existing-contract` | Validate a contract the user brings in (not created by this module) | Upload document → run validation → findings report |
| `sign-contract` | Send document to both parties for e-signature | Load PDF → DocuSign integration → capture consent + timestamp → return signed PDF |

### Utility Workflows (Support)

| Workflow | Purpose | Flow |
|---|---|---|
| `select-contract-type` | Help user identify which contract type fits their deal | 3-question interview → recommend contract type (partnership, NDA, service agreement, freelance) |

**Typical sequence:** `select-contract-type` → `create-contract` → `validate-contract` → `sign-contract` → optionally `explain-contract` or `amend-contract`

---

## Tools & Integrations

### MCP Tools

- **File system access** — write and save generated PDF output
- **PDF generation** — render final contract as a formatted PDF with signature lines, headers, and legal disclaimer

### External Services

- **DocuSign API** (or equivalent e-signature service) — ESIGN Act compliant electronic signatures, captures consent, identity, and timestamp
- **Legal clause knowledge base** — reference set of standard US contract clauses by type (partnership, NDA, service agreement, freelance)
- **State-specific law references** — knowledge base for US state-specific contract requirements to strengthen validation

### Integrations with Other Modules

None. Quick Contract is fully standalone.

---

## Creative Features

### Personality & Theming

Luey has a consistent and memorable voice throughout:
- **Opener:** *"Let's make this deal bulletproof!"*
- **Validation pass:** *"This contract is looking airtight — Luey approves!"*
- **Issues found:** *"Whoa, hold on — we need to talk about this clause..."*
- **Storage reminder:** *"Save this somewhere safe — cloud drive, email it to yourself and the other party. You want this findable if you ever need it."*

### Easter Eggs & Delighters

- **Handshake response:** If the user types "I just want to shake on it" — Luey responds: *"I respect the hustle, but let's shake on paper. Future you will thank us both."*
- **Small amount quip:** If the deal involves an extremely small dollar amount, Luey quips about it being the most legally protected dollar ever spent.

### Module Lore

Luey is a lawyer who got tired of watching people get burned on handshake deals. After years in practice, Luey realized that the people who needed legal protection the most — freelancers, small-time entrepreneurs, first-time collaborators — were exactly the people who couldn't afford a lawyer. So Luey built Quick Contract: legal protection for everyone, not just those who can pay $500/hour.

---

## Next Steps

1. **Review this brief** — Ensure the vision is clear
2. **Run create-module workflow** — Build the module structure
3. **Create agents** — Use create-agent workflow for Luey the Lawyer
4. **Create workflows** — Use create-workflow workflow for each of the 7 workflows
5. **Test module** — Install and verify functionality

---

_brief created on 2026-03-15 by Evie using the BMAD Module workflow_
