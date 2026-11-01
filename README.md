# GitLab CI/CD ChatOps Agent (n8n + MCP)

An AI-driven ChatOps workflow for n8n that automatically debugs GitLab CI/CD pipeline failures using the Model Context Protocol (MCP) and OpenAI. 

![Architecture](architecture.png)

## 🚀 What it does
When a developer drops a failed GitLab Job URL into chat, this AI agent automatically:
1. Extracts the Job ID and Pipeline ID.
2. Fetches the job output logs.
3. Analyzes recent commits and diffs to find the root cause.
4. Categorizes the issue as **Developer-side** (e.g., syntax error) or **Operation-side** (e.g., runner out of memory).
5. Suggests an actionable fix.

## 🛠 Prerequisites
* [n8n](https://n8n.io/) instance (version supporting MCP & Advanced AI).
* OpenAI API Key.
* GitLab Personal/Project Access Token.
* A configured GitLab MCP server.

## 📥 Installation
1. Download the `workflow-template.json` file from this repository.
2. Open your n8n instance and create a new workflow.
3. Click the `...` menu in the top right corner and select **Import from File**, or simply paste the JSON directly onto the canvas.
4. Configure your **OpenAI** and **GitLab MCP** credentials inside the nodes.
5. Activate the workflow!

## 💡 Customization
You can modify the trigger node to connect to your preferred communication platform (Slack, Microsoft Teams, Rocket.Chat, etc.) by replacing the Chat Trigger with the respective app trigger.
