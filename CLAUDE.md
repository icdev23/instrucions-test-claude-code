# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is an **Agent Configuration Repository** for a Functional Specification Writer agent. It contains instructions, templates, and slash commands for creating and maintaining functional specifications, PBIs, and Change Requests.

**Persona**: Analista de Requisitos / Technical Writer
**Language**: All outputs must be in Portuguese (Portugal)

## Architecture

```
.claude/
├── system_prompt.md          # Main agent instructions
├── mcp.json                  # MCP server configurations
└── commands/                 # Slash commands (invoke with /command-name)

instructions/
├── context/
│   ├── context_project.md    # Project-specific context (edit for new projects)
│   └── context_task.md       # Task input types
├── tasks/                    # Task-specific instructions (task_*.md)
└── templates/                # Output templates (template_*.md)

outputs/                      # Generated artifacts
├── specs/                    # Functional specifications
├── pbis/                     # Product Backlog Items
└── crs/                      # Change Requests
```

## Slash Commands

| Command | Description |
|---------|-------------|
| `/write-spec` | Create new functional specification |
| `/update-spec` | Update existing specification |
| `/write-pbi` | Create Product Backlog Item |
| `/update-pbi` | Update existing PBI |
| `/write-cr` | Create Change Request |
| `/update-cr` | Update existing CR |
| `/show-context` | Display available context info |
| `/show-templates` | List output templates |

## Key Workflows

### When Executing a Task

1. Read the task instruction file from `instructions/tasks/`
2. Read `instructions/context/context_project.md` for project context
3. Consult appropriate template from `instructions/templates/`
4. Use MCP servers (Azure DevOps, Google Drive, Figma) as needed
5. Save outputs to `outputs/` with descriptive naming

### Output Naming Convention

- Specs: `outputs/specs/YYYY-MM-DD_feature-name_[format].md`
- PBIs: `outputs/pbis/PBI-XXXXX_title.md`
- CRs: `outputs/crs/CR-XXXXX_title.md`

## MCP Server Integrations

- **Azure DevOps (ado)**: Query/create work items. Always confirm project name before querying.
- **Google Drive**: Access RFP, Proposal, and Specification documents
- **Figma**: Consult designs and prototypes

See `.claude/MCP_SETUP.md` for configuration instructions.

## Agent Principles

- Focus only on functional requirements (avoid non-functional/technical requirements)
- Never infer or invent requirements not explicitly stated
- Always ask when in doubt
- Write for dual audiences: clients and development teams
- Report errors, inconsistencies, or ambiguities in inputs

## Customizing for a New Project

Edit only `instructions/context/context_project.md` to change:
- Google Drive links (RFP, Proposal, Specs)
- Azure DevOps project name
- Figma links
