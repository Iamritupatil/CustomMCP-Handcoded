# CustomMCP

> **Create custom MCP servers with simple prompts or guided inputs.**

CustomMCP is an open-source developer tool that makes it easier to create custom **Model Context Protocol (MCP) servers** for applications and APIs that don't already provide MCP support.

Instead of manually implementing an MCP server, users can describe what they want in a prompt or configure it through simple inputs. CustomMCP handles the underlying MCP and API integration and generates a ready-to-use MCP server.

---

## ✨ What is CustomMCP?

CustomMCP is designed to sit between an application or API and an AI client.

```text
                 Application / API
                        │
                        │
                        ▼
                   CustomMCP
                        │
                 Generates / Builds
                        │
                        ▼
                   MCP Server
                        │
                        │ MCP
                        ▼
                    AI Client
```

The goal is simple:

> **If an application has an API, creating an MCP server for it should be easy.**

---

## 💬 Create an MCP with a Prompt

Instead of writing an MCP server manually, users can describe what they need.

For example:

```text
Create an MCP server for my task management API.

The AI should be able to:

- list tasks
- create tasks
- update tasks
- delete tasks
- mark tasks as completed

The API uses bearer-token authentication.
```

CustomMCP can turn that description into an MCP server configuration and generated code.

---

## ⚙️ Or Configure It Manually

Users can also provide structured information:

```text
Application:
My Task API

Base URL:
https://api.example.com

Authentication:
Bearer Token

Tools:

✓ List Tasks
✓ Create Task
✓ Update Task
✓ Delete Task
✓ Complete Task
```

CustomMCP uses this information to create the corresponding MCP tools.

---

## 🔌 API → MCP

A common use case is connecting an existing REST API to an MCP server.

For example, an API might provide:

```text
GET    /users
GET    /projects
POST   /projects
PATCH  /projects/{id}
DELETE /projects/{id}
```

CustomMCP can represent these capabilities as MCP tools:

```text
list_users
list_projects
create_project
update_project
delete_project
```

The resulting architecture becomes:

```text
AI Client
    │
    │ MCP
    ▼
MCP Server
    │
    │ HTTP
    ▼
Application API
```

---

## 🚀 User Experience

The intended experience is to install CustomMCP and use it directly from the terminal.

```bash
pip install custommcp
```

Then:

```bash
custommcp create
```

CustomMCP can guide the user through creating their server:

```text
CustomMCP

How would you like to create your MCP?

1. Describe it with a prompt
2. Configure it manually
3. Import an OpenAPI specification

Select:
>
```

A generated project could look like:

```text
my-task-mcp/
├── server.py
├── tools.py
├── api_client.py
├── auth.py
├── config.py
└── README.md
```

The user can then run their generated server.

```bash
cd my-task-mcp
custommcp run
```

> **The exact CLI commands and installation process are subject to change during development.**

---

## 🧠 How It Works

At a high level:

```text
                    User
                     │
                     ▼
              Prompt / Inputs
                     │
                     ▼
                CustomMCP
                     │
          ┌──────────┴──────────┐
          │                     │
          ▼                     ▼
       Parser              Configuration
          │                     │
          └──────────┬──────────┘
                     ▼
                Tool Builder
                     │
                     ▼
             MCP Generator
                     │
                     ▼
              MCP Server
                     │
                     ▼
                AI Client
```

For API-based MCPs:

```text
MCP Tool
    │
    ▼
API Client
    │
    ▼
Authentication
    │
    ▼
HTTP Request
    │
    ▼
External API
    │
    ▼
Response
```

---

## 🎯 Why CustomMCP?

MCP provides a standardized way for AI applications to interact with external tools and services.

However, building an MCP server manually can require knowledge of:

* MCP
* APIs
* HTTP
* authentication
* JSON
* server architecture
* tool definitions
* error handling
* configuration

CustomMCP aims to reduce that barrier.

Instead of starting with:

```text
Learn MCP
   ↓
Write an MCP server
   ↓
Implement tools
   ↓
Connect the API
   ↓
Implement authentication
   ↓
Test everything
```

the goal is to make it closer to:

```text
Describe what you need
        ↓
    CustomMCP
        ↓
Configure
        ↓
Generate
        ↓
  MCP Server
```

---

## 🛠️ Planned Features

CustomMCP is being designed to support:

* 🗣️ Natural-language MCP creation
* ⚙️ Guided MCP configuration
* 🔌 REST API integration
* 📄 OpenAPI import
* 🧰 Automatic tool generation
* 🔐 API authentication
* 🔑 Environment-based secrets
* 📝 Custom tool definitions
* 🧪 MCP server validation
* ▶️ Local MCP server execution
* 📦 Generated MCP server projects
* 💻 Command-line interface
* 🐍 Python-based generated servers

---

## 📦 Installation

Once published, CustomMCP will be installable through Python's package ecosystem:

```bash
pip install custommcp
```

For development, the repository can be cloned directly:

```bash
git clone https://github.com/iamritupatil/custommcp.git
cd custommcp
```

> Installation instructions will be updated as the project reaches a usable release.

---

## 💻 CLI

The planned CLI will provide commands similar to:

```bash
custommcp create
custommcp generate
custommcp validate
custommcp run
```

Run:

```bash
custommcp --help
```

to discover available commands.

The CLI is expected to become the primary interface for CustomMCP.

---

## 🏗️ Project Architecture

CustomMCP will be built as a modular system.

```text
custommcp/
│
├── CLI
│
├── Configuration
│
├── Prompt / Input Processing
│
├── API Parser
│
├── Internal Models
│
├── Tool Generator
│
├── MCP Generator
│
├── API Client
│
├── Authentication
│
└── Generated MCP Servers
```

The architecture will evolve as the project develops.

---

## 🔮 Future Vision

CustomMCP is not intended to be limited to one application or one API format.

The long-term vision is:

```text
             ┌── REST API
             │
             ├── OpenAPI
             │
             ├── Custom API
             │
             ├── User configuration
             │
             └── Natural-language prompt
                       │
                       ▼
                  CustomMCP
                       │
                       ▼
                MCP Server
                       │
                       ▼
                  AI Client
```

The user shouldn't need to understand every implementation detail to create a useful MCP server.

---

## 🤝 Open Source

CustomMCP is an open-source project.

Contributions, ideas, integrations, bug reports, documentation, and experiments are welcome.

Whether you're interested in MCP, AI tooling, APIs, Python, or developer tools, contributions are encouraged.

---

## 📜 License

Apache License 2.0

---

## 💡 Vision

> **Make custom MCP creation accessible to everyone.**

From:

```text
"I have an API."
```

to:

```text
"I have an MCP server."
```

with as little friction as possible.

**CustomMCP — describe it, configure it, create it.**

Made with 💗 and 🤚🏻.
