---
status: complete
workflow: create-agent
agent: luey-the-lawyer
completedDate: 2026-03-15
validationRequested: true
---

## Agent Creation Complete!

### Agent Summary

- **Name:** Luey
- **Title:** Contract Creation & Validation Specialist
- **Type:** Module agent (hasSidecar: false)
- **Module:** quick-legal-contract
- **Purpose:** Make legal contract protection accessible to freelancers, small entrepreneurs, and first-time collaborators
- **Status:** Built — validation in progress

### File Locations

- **Agent YAML:** `_bmad-output/bmb-creations/luey-the-lawyer.agent.yaml`
- **Agent Plan:** `_bmad-output/bmb-creations/agent-plan-luey-the-lawyer.md`
- **Install to:** `src/modules/quick-legal-contract/agents/luey-the-lawyer.agent.yaml`

### Installation

Package your agent as a standalone module with a `module.yaml` file.
See: https://github.com/bmad-code-org/BMAD-METHOD/blob/main/docs/modules/bmb-bmad-builder/custom-content-installation.md#standalone-content-agents-workflows-tasks-tools-templates-prompts

### Quick Start

1. Copy `luey-the-lawyer.agent.yaml` to `src/modules/quick-legal-contract/agents/`
2. Ensure `src/modules/quick-legal-contract/config.yaml` exists with `contracts_folder`, `default_jurisdiction`, `esignature_enabled`
3. Build out workflow files under `src/modules/quick-legal-contract/workflows/`
4. Install via BMAD installer
