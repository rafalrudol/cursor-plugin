# PagerDuty Cursor Plugin

A Cursor plugin that connects your AI assistant to PagerDuty's remote MCP server, enabling incident management, on-call lookups, service management, and more.

## Overview

This plugin connects Cursor to PagerDuty's remote MCP server, enabling incident management, on-call lookups, service management, and more directly from your IDE.

The default endpoint is `https://mcp.pagerduty.com/mcp` (US). EU service-region accounts set the **PagerDuty MCP URL** plugin variable to `https://mcp.eu.pagerduty.com/mcp`. The API token stays in the **PagerDuty API Token** variable. Cursor substitutes both when it starts the server and does not rewrite `mcp.json`. Do not paste the token into that file.

PagerDuty does not support Dynamic Client Registration. The EU URL does not make the OAuth Sign in button able to register a Cursor client. Use the API token.

## Installation

1. Open Cursor Settings
2. Navigate to **Plugins**
3. Click **Browse Marketplace**
4. Search for **PagerDuty**
5. Click **Install**

## Support

- PagerDuty MCP Server Documentation: https://developer.pagerduty.com/docs/mcp-tooling-remote-server
- PagerDuty Support: https://support.pagerduty.com
- PagerDuty Local MCP Server: https://github.com/PagerDuty/pagerduty-mcp-server
