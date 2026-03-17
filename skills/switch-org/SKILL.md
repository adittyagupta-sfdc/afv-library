---
name: switch-org
description: Switches the active Salesforce org (default org) using the Salesforce CLI. Supports username or alias input, defaults to local project scope, and optionally sets the global default.
---

# switch-org

A global Agentforce Skill that switches the active Salesforce org (default org) using the Salesforce CLI (sf). This Skill performs a CLI-only workflow (no project file edits) and supports either a username or an alias.

## Purpose

- Switch to a specified Salesforce org for subsequent CLI operations.
- Confirm the selection via `sf config get target-org`.

## Usage

- Invoke this Skill whenever a user asks to "switch org", "change default org", or specifies a username/alias directly.
- Input: a username or alias (e.g., `user@example.com` or `myAlias`), and an optional scope indicator.
- Default scope: **local** (updates `.sf/config.json` in the current project directory).
- Use `--global` scope only if the user explicitly asks to set the global default (e.g., "set globally", "change global org").

### Examples

- “Switch to this org: user@example.com”
- “Use alias myAlias”
- “Change default org to myDev”

## Behavior

1. Set the default org using the provided alias or username:
   - Local (default): `sf config set target-org=<orgIdentifier>`
   - Global (only if user explicitly requests): `sf config set target-org=<orgIdentifier> --global`
2. Verify selection:
   - `sf config get target-org --json`
   - Parse and display the confirmed value and scope (Local or Global).

## Steps (pseudocode)

1) Read input: `orgIdentifier`, and whether the user wants global scope (default: false)
2) Execute:
   - If global: `sf config set target-org=<orgIdentifier> --global`
   - Otherwise: `sf config set target-org=<orgIdentifier>`
   - If this fails, report the error and suggest running `sf org login web` if the org may not be authorized.
3) Verify:
   - `sf config get target-org --json`
   - Output confirmation: `Switched org (<scope>): <value>`
4) If verification fails, report the error and advise running `sf config get target-org`.

## Official Documentation

- Salesforce CLI config (unified) reference (sf):
  https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_config_commands_unified.htm\#cli_reference_config_set_unified

## Canonical sf config set Examples

- Set project-local default (default behavior):
  sf config set target-org=ALIAS_OR_USERNAME

- Set global default (only when explicitly requested):
  sf config set target-org=ALIAS_OR_USERNAME --global

- Verify current effective value:
  sf config get target-org
  sf config get target-org --json

Notes:
- Unified CLI uses keys like target-org and target-dev-hub. Legacy sfdx keys (defaultusername, defaultdevhubusername) are deprecated in this context.
- Flags like --local or --scope are not part of current unified docs; do not use them.


