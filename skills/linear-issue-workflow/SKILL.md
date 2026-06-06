---
name: linear-issue-workflow
description: >
  Use this skill when small teams need automated Linear issue workflows that
  reduce communication overhead between engineering, product, and QA through
  configurable teams, templates, labels, states, and issue formatting rules.
---

# Linear Issue Workflow

Use this skill to create or update Linear issues for small-team automation workflows.
The goal is to reduce communication overhead between engineering, product, and QA by turning requests into consistent, actionable issues with project-specific configuration kept outside the main instructions.

## Configuration

Before creating or updating issues, look for `references/linear-config.yaml`.
If it does not exist, use `references/linear-config.example.yaml` to understand the expected shape and ask one short question for any required missing value.

Use the configured workspace, team, default template, and available templates as the source of truth.

## Creating Issues

When the user asks to create a Linear issue:

1. Use the team defined in `references/linear-config.yaml` when available.
2. Select the requested template when the user names one.
3. If no template is requested, use the configured default template.
4. Generate a concise, action-oriented title from the request.
5. Apply the selected template's defaults, including project, assignee, priority, labels, state, links, and description template.
6. If the request includes URLs, screenshots, Figma links, DOM context, or reproduction steps, place them in the matching template sections.
7. If the request is understandable, create the issue directly.
8. Ask at most one short question before creating the issue, and only when a required team, template, or title cannot be determined.
9. Add priority only when obvious or configured.

## Issue Format

Use the selected team's template from `references/linear-config.yaml` as the issue format.
The selected template's `description_template` is the source of truth for the issue body.

When using a template:

1. Preserve the template's section structure.
2. Replace guidance text with the user's actual issue details.
3. Keep section headings when information is missing, but do not keep instructional placeholder text as final issue content.
4. Do not include template-only instructions such as "Tip for humans" in the final issue body.

## Priority

- High: production-blocking bugs, authentication, billing, data loss, or critical user workflows.
- Medium: normal features or user-facing bugs.
- Low: copy tweaks, small UI polish, cleanup.

## Response

After creating or updating an issue, reply with:

- Issue title
- Linear URL
- Priority if set
- Template name
