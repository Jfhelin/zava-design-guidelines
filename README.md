# zava-design-guidelines

This repository provides workshop design guidance for the Zava sample company used during the GitHub Copilot workshop.

It is intended for authoring-time grounding through GitHub MCP. It is not presented as an official Microsoft or Zava brand repository.

## How It Is Used

- participants use the `zava-designer` skill during Block 4
- the design agent retrieves files and issue guidance from this repository through GitHub MCP
- prompts like `add a logo` should cause the agent to fetch the approved logo asset and logo usage guidance from this repository before editing the app

## Repository Contents

- `brand/`: design language, layout rules, logo usage, and tokens
- `assets/`: source assets that can be inserted into apps
- `issues/seed/`: issue templates to publish as GitHub issues for MCP retrieval

The markdown files in `issues/seed/` are templates. The intended MCP issue source is the published GitHub issues created from those files.

## Retrieval Map

Use these sources by default depending on the design task:

- Overall visual direction:
  - `brand/zava-style.md`
  - published GitHub issue created from `issues/seed/01-zava-design-guidance.md`
- Layout structure, header blocks, body blocks, footer blocks:
  - `brand/page-structure.md`
  - `brand/zava-ui-patterns.md`
  - published GitHub issue created from `issues/seed/05-zava-layout-blocks.md`
- Colors, radii, typography, borders, shadows:
  - `brand/tokens.json`
- Logo placement and logo constraints:
  - `brand/logo-usage.md`
  - published GitHub issue created from `issues/seed/02-zava-logo-usage.md`
  - `assets/logo-primary.png`
- Copy tone and wording:
  - published GitHub issue created from `issues/seed/03-zava-copy-tone.md`
- Guardrails and anti-patterns:
  - published GitHub issue created from `issues/seed/04-zava-do-not-do.md`

## Request Mapping

When a design agent receives one of these requests, these are the sources it should pull first through GitHub MCP:

- `add a logo`, `brand this`, `add branding`:
  - `brand/logo-usage.md`
  - `assets/logo-primary.png`
  - published GitHub issue created from `issues/seed/02-zava-logo-usage.md`
- `make it look like Zava`, `restyle this`, `apply Zava design`:
  - `brand/zava-style.md`
  - `brand/tokens.json`
  - `brand/page-structure.md`
  - `brand/zava-ui-patterns.md`
- `improve the header`, `make the hero look right`, `fix the top of the page`:
  - `brand/page-structure.md`
  - `brand/tokens.json`
  - `brand/logo-usage.md`
- `improve the footer`:
  - `brand/page-structure.md`
  - published GitHub issue created from `issues/seed/05-zava-layout-blocks.md`
  - `brand/tokens.json`
- `fix the colors`, `adjust spacing`, `make the controls match`:
  - `brand/tokens.json`
  - `brand/zava-ui-patterns.md`
- `fix the copy`, `make the tone match`:
  - published GitHub issue created from `issues/seed/03-zava-copy-tone.md`

## Retrieval Rules

- Prefer GitHub MCP file and issue retrieval over public-web fetching
- Treat files in `issues/seed/` as templates for published GitHub issues, not as the live issue source
- Retrieve only the sources needed for the current change
- Start with the most specific source for the task
- If guidance conflicts, prefer:
  1. asset file
  2. brand markdown file
  3. issue guidance

## Asset Policy

- `assets/logo-primary.png` is the canonical logo asset currently sourced from the reference site
- no other branding asset should be treated as canonical unless it can be traced to a provided reference
- if additional assets are needed later, they should be added from verified sources rather than reconstructed from memory
