# MCP Productivity Operations Agent

An AI-powered personal productivity agent built with **n8n** and **Model Context Protocol (MCP)**. The system connects multiple productivity services and allows an AI Agent to orchestrate them through separate MCP servers.

## Overview

The MCP Productivity Operations Agent is designed as a central AI workspace for managing everyday productivity tasks.

Instead of connecting every service directly to one large workflow, the project uses separate MCP servers to expose specialized tools. A central AI Agent can then select and orchestrate the appropriate tools based on the user's request.

### Connected Services

- Google Calendar
- Gmail
- Google Drive
- Google Tasks

A dedicated web frontend provides a single interface for interacting with the agent.

## Features

### Google Calendar

- Retrieve upcoming events
- Check schedules
- Find relevant calendar events
- Work with event information
- Support scheduling-related requests

### Gmail

- Search emails
- Retrieve individual emails
- Find relevant messages
- Send emails

### Google Drive

- Search files
- Find documents by name or keyword
- Retrieve files
- Access relevant file information

### Google Tasks

- Create tasks
- List tasks
- Search tasks
- Update tasks
- Complete tasks
- Delete tasks

## Multi-Tool AI Orchestration

The main purpose of this project is to allow an AI Agent to determine which tools are required for a request and orchestrate multiple services when necessary.

For example:

> "Prepare me for tomorrow's FYP meeting."

The agent can:

1. Check Google Calendar for the meeting.
2. Search Gmail for relevant conversations.
3. Search Google Drive for related documents.
4. Check or create relevant tasks in Google Tasks.
5. Combine the retrieved information into a single response.

This makes the system more than a simple chatbot. It acts as a productivity operations agent capable of coordinating multiple external services.

## Architecture

    User
      ↓
    Frontend
      ↓
    n8n Webhook
      ↓
    AI Agent
      ↓
    MCP Client Tools
      ↓
    ┌─────────────────────────────────────────────┐
    │                                             │
    ├── Calendar MCP → Google Calendar            │
    │                                             │
    ├── Gmail MCP → Gmail                         │
    │                                             │
    ├── Drive MCP → Google Drive                 │
    │                                             │
    └── Tasks MCP → Google Tasks                 │
                                                  │
    └─────────────────────────────────────────────┘

Each service is exposed through its own MCP server, while the central AI Agent uses MCP Client Tools to access and orchestrate those capabilities.

## Workflow Structure

    workflows/
    ├── main-ai-agent.json
    ├── calendar-mcp.json
    ├── gmail-mcp.json
    ├── drive-mcp.json
    └── tasks-mcp.json

### Main AI Agent

The main workflow contains the central AI Agent, memory, chat model, MCP Client Tools, webhook handling, and response handling.

The AI Agent acts as the orchestration layer between the user and the available MCP tools.

### Calendar MCP Server

Provides Google Calendar capabilities to the AI Agent through MCP.

### Gmail MCP Server

Provides Gmail search, retrieval, and sending capabilities.

### Drive MCP Server

Provides Google Drive search and file retrieval capabilities.

### Tasks MCP Server

Provides Google Tasks management capabilities.

## Frontend

A dedicated frontend was created instead of relying only on the n8n interface.

The interface includes:

- AI assistant workspace
- Productivity dashboard
- Calendar section
- Tasks section
- Gmail section
- Google Drive section
- Activity section
- Quick actions
- Natural-language interaction with the AI Agent

The frontend communicates with the n8n webhook and displays the agent's responses.

## Technology Stack

| Technology | Purpose |
|---|---|
| n8n | Workflow automation and orchestration |
| Model Context Protocol | Tool and service communication |
| AI Agent | Natural-language reasoning and tool selection |
| Google Calendar | Calendar management |
| Gmail | Email management |
| Google Drive | File management |
| Google Tasks | Task management |
| Webhooks | Frontend-to-n8n communication |
| HTML | Frontend structure |
| CSS | Frontend styling |
| JavaScript | Frontend interaction |

## Example Requests

    Show me my schedule for today.

    Find the emails related to my FYP.

    Find my latest FYP documents in Drive.

    Create a task to review my FYP documentation.

    Send an email to my supervisor.

    Prepare me for tomorrow's meeting.

The final example demonstrates the main concept of the project: a single request can require multiple productivity tools.

## Project Structure

    mcp-productivity-operations-agent/
    ├── workflows/
    │   ├── main-ai-agent.json
    │   ├── calendar-mcp.json
    │   ├── gmail-mcp.json
    │   ├── drive-mcp.json
    │   └── tasks-mcp.json
    │
    ├── frontend/
    │   └── index.html
    │
    ├── screenshots/
    │   ├── dashboard.png
    │   ├── ai-agent.png
    │   └── mcp-workflows.png
    │
    ├── README.md
    └── .gitignore

## Setup

### 1. Import the Workflows

Import the workflow JSON files from the `workflows` directory into n8n.

### 2. Configure Google Credentials

Configure the required Google credentials for:

- Google Calendar
- Gmail
- Google Drive
- Google Tasks

### 3. Configure MCP Connections

Connect the MCP Client Tools in the main AI Agent workflow to their corresponding MCP Server workflows.

### 4. Activate the Workflows

Activate the required MCP server workflows and the main AI Agent workflow.

### 5. Configure the Frontend

Update the webhook URL inside the frontend JavaScript with the production webhook URL of the main n8n workflow.

### 6. Run the Frontend

Open the frontend in a browser and interact with the AI Agent.

## Security

Credentials and sensitive configuration should not be included in the repository.

Before publishing the workflows:

- Remove API keys and tokens.
- Remove private credentials.
- Remove sensitive webhook URLs if necessary.
- Reconnect credentials after importing the workflows into n8n.

Never commit passwords, OAuth tokens, API keys, or other sensitive credentials.

## Key Concepts Demonstrated

- Model Context Protocol
- MCP client/server architecture
- AI Agent tool orchestration
- Multi-service automation
- n8n workflow architecture
- Google service integrations
- Webhook-based applications
- Natural-language task execution
- Frontend integration with AI workflows

## Future Improvements

Potential extensions include:

- Slack MCP integration
- Notion MCP integration
- GitHub MCP integration
- More advanced scheduling
- Persistent conversation history
- Expanded productivity analytics
- Additional MCP servers

## Author

**Muhammad Abdullah Shujaat**

BS Software Engineering  
SZABIST University
