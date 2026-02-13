---
name: Notion Connector
description: Connect Claude Cowork to your Notion workspace so skills can read your notes and create pages directly where you work.
---

# Notion Connector

## What This Does

This connects your agent to Notion. Once connected, your agent can read your Notion pages and create new ones. That means work shows up where you already work — not in a chat window.

## Before You Start

- You need a Notion account (free is fine)
- You need at least one database or page you want the agent to access

## Setup Steps

1. Go to [notion.so/my-integrations](https://www.notion.so/my-integrations) and create a new integration.
2. Name it "Cowork Agent" and copy the API key.
3. In Notion, open the page or database you want to share. Click "..." then "Connections" then add your "Cowork Agent" integration.
4. In Cowork, go to Settings > Integrations > add Notion with your API key.

> **Using MCP?** You can add the Notion MCP server directly in your Claude settings instead. Same API key, different wiring.

## Test It

Ask your agent:

> "List my Notion pages"

If it shows your pages, you're connected.

Then try:

> "Create a test page in Notion called Hello from Cowork"

If it appears in Notion, you're good.

## What Your Agent Can Now Do

- Read any Notion page or database you've shared
- Create new pages
- Update existing pages
- Search across your workspace
- Drop finished work directly into Notion databases

This is the foundation. Newsletter skills, social content skills, and project trackers all build on this connection.

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Can't see pages? | You forgot to share the page with the integration in Step 3. |
| Connection failed? | Double-check the API key. Copy it fresh from the integrations page. |
| Only seeing some pages? | Each page needs to be individually shared with the integration. Parent sharing does not always flow down. |
