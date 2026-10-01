# MCP Productivity Operations Agent

An AI-powered personal productivity agent built with n8n and Model Context Protocol (MCP).

The system allows an AI Agent to orchestrate multiple productivity services through separate MCP servers instead of relying on a single workflow or API integration.

## Connected Services

- Google Calendar
- Gmail
- Google Drive
- Google Tasks

## What It Can Do

- Check and retrieve calendar events
- Search and retrieve emails
- Send emails
- Search and retrieve Drive files
- Create and manage tasks
- Combine multiple services to complete multi-step requests

For example, a request such as:

> "Prepare me for tomorrow's meeting."

can require the agent to check Calendar, find relevant Gmail messages, locate documents in Drive, and work with Tasks.

## Architecture

```text
User
  ↓
Frontend
  ↓
n8n AI Agent
  ↓
MCP Client Tools
  ↓
┌──────────────┬──────────────┬──────────────┬──────────────┐
│ Calendar MCP │   Gmail MCP  │   Drive MCP  │   Tasks MCP   │
└──────────────┴──────────────┴──────────────┴──────────────┘
  ↓              ↓               ↓               ↓
Google Calendar  Gmail       Google Drive     Google Tasks
