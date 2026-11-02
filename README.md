# GitLab CI/CD ChatOps Agent (n8n + MCP)

An AI-driven ChatOps workflow for n8n that automatically debugs GitLab CI/CD pipeline failures using the Model Context Protocol (MCP) and OpenAI. 

![Architecture](architecture.png)

## 🚀 What it does
When a developer drops a failed GitLab Job URL into chat, this AI agent automatically:
1. Extracts the Job ID and Pipeline ID.
2. Fetches the job output logs.
3. Analyzes recent commits and diffs to find the root cause.
4. Categorizes the issue as **Developer-side** (e.g., syntax error, failed tests) or **Operation-side** (e.g., runner out of memory, expired secrets).
5. Suggests an actionable fix directly to the developer.

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

## 🔌 Setting up the GitLab MCP Connection
This workflow relies on the **GitLab MCP Server** connected via SSE (Server-Sent Events). After importing the template, you must configure the MCP credentials in n8n:

1. In your n8n left sidebar, go to **Credentials** -> **Add Credential**.
2. Search for **MCP Client (SSE API)**.
3. Configure the connection based on where your GitLab MCP server is hosted:
   * **Server URL:** Enter the URL of your deployed GitLab MCP SSE endpoint.
   * **Authentication:** Pass your GitLab Personal Access Token (PAT) or required headers as defined by your MCP server configuration.
4. Save the credential.
5. Open the imported workflow, double-click any of the blue **MCP Client Tool** nodes (like `Search Repositories`), and select your newly created MCP credential from the dropdown. n8n will automatically fetch the available GitLab tools!

## 💡 Customization
You can modify the trigger node to connect to your preferred communication platform (Slack, Microsoft Teams, Rocket.Chat, Telegram, etc.) by replacing the standard Chat Trigger with the respective app trigger.
