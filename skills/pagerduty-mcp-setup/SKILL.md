---
name: pagerduty-mcp-setup
description: REQUIRED setup for how to use the PagerDuty MCP server. Read this before calling PagerDuty tools. The API token and, for EU accounts, the MCP URL are plugin variables. Do not edit mcp.json.
---

The PagerDuty plugin talks to the hosted MCP server. Cursor substitutes plugin variables into `mcp.json` when it starts the server. It does not rewrite that file.

`mcp.json` keeps these placeholders after the plugin is configured:

- `Authorization` is `Token ${PAGERDUTY_API_TOKEN}`
- `url` is `${PAGERDUTY_MCP_URL:-https://mcp.pagerduty.com/mcp}`

Seeing `${PAGERDUTY_API_TOKEN}` in the file does not mean the token is missing. Do not paste a token into `mcp.json`. Plugin updates restore that file, and the token belongs in the plugin variable.

### Configure

In Cursor, open the PagerDuty plugin settings (Customize, or Dashboard → Plugins → Configure):

1. Set **PagerDuty API Token** to the user API token. Enter only the token. The header already includes the `Token ` prefix. Do not ask the user to send you the token. Instructions: `https://support.pagerduty.com/main/docs/pagerduty-mcp-server-integration-guide#generate-your-pagerduty-api-token`
2. Leave **PagerDuty MCP URL** at the US default `https://mcp.pagerduty.com/mcp` unless the account is in the EU service region. EU accounts must use `https://mcp.eu.pagerduty.com/mcp`. An EU token is rejected by the US host.
3. Reload the window after changing either value. On macOS the command is `Reload Window` from the Command Palette (`⌘⇧P`). On Windows and Linux use `Ctrl+Shift+P`.

This plugin does not turn on OAuth Dynamic Client Registration. PagerDuty does not support DCR. The Sign in button can fail before an account form appears. Use the API token variable instead.

### Check that it works

Do not decide configuration by reading `mcp.json`. Make one read-only call, for example `browse_incidents` with action `list` and limit 1, or `browse_services` with action `list` and limit 1.

- A normal tool result means the plugin is configured.
- HTTP 401, or an authentication error, means the token is missing or the MCP URL does not match the account region.
- A 403 that names a product the account does not have (for example incident workflows) is not an authentication failure. Try another read-only tool.

### Reference

- EU hosted MCP: `https://support.pagerduty.com/main/docs/pagerduty-mcp-server`
- Token setup: `https://support.pagerduty.com/main/docs/pagerduty-mcp-server-integration-guide#generate-your-pagerduty-api-token`
- Developer docs: `https://developer.pagerduty.com/docs/mcp-tooling-remote-server`
