---
name: linear-issue-workflow
description: >
  Use this skill when small teams need automated Linear issue workflows that
  reduce communication overhead between engineering, product, and QA through
  configurable teams, templates, labels, states, and issue formatting rules.
metadata:
  version: "1.0.0"
  versioning: semver
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
4. Apply the selected template's defaults, including labels, state, and description template.
5. If the request is understandable, create the issue directly.
6. If a key detail is missing, ask only one short question.
7. Add priority only when obvious.

## Issue Format

### What

What needs to be built, fixed, or changed.

### Why

Why this matters.

### Acceptance Criteria

- The expected result is clear.
- Important edge cases are covered if mentioned.

### Notes

Relevant links, screenshots, pages, components, API details, or extra context.

## Priority

- High: production-blocking bugs, authentication, billing, data loss, or critical user workflows.
- Medium: normal features or user-facing bugs.
- Low: copy tweaks, small UI polish, cleanup.

## Response

After creating or updating an issue, reply with:

- Issue title
- Linear URL
- Priority if set
