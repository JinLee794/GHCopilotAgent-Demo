# GitHub Cloud Copilot Agent + Azure DevOps MCP Setup

This repository includes a custom agent definition at:
- `.github/agents/azure-devops-mcp.agent.md`

It also includes repository instructions for cloud coding agent sessions at:
- `.github/copilot-instructions.md`

## 1) Prerequisites

- GitHub repository with Copilot coding agent enabled.
- Azure DevOps Personal Access Token (PAT).
- Access to your Azure DevOps organization and project.

## 2) Configure Copilot Coding Agent MCP on GitHub

Open repository settings:
- `https://github.com/<owner>/<repo>/settings/copilot/coding_agent`

In **MCP configuration**, paste this JSON:

```json
{
  "mcpServers": {
    "azure-devops": {
      "type": "local",
      "command": "npx",
      "args": [
        "-y",
        "azure-devops-mcp-server@latest"
      ],
      "tools": [
        "*"
      ],
      "env": {
        "AZDO_ORG_URL": "https://dev.azure.com/<your-organization>",
        "AZDO_PAT": "<your-pat>",
        "AZDO_DEFAULT_PROJECT": "<your-project>",
        "AZDO_HTTP_TIMEOUT": "300000"
      }
    }
  }
}
```

## 3) Optional: On-Prem Azure DevOps Server (TFS)

If you use Azure DevOps Server/TFS instead of dev.azure.com, use this package:
- `azure-devops-mcp@latest`

And use env vars expected by that server:
- `AZURE_DEVOPS_URL`
- `AZURE_DEVOPS_PAT`
- `AZURE_DEVOPS_COLLECTION`
- `AZURE_DEVOPS_PROJECT`

## 4) Use the Custom Agent

In Copilot chat, invoke the custom agent and include the Azure DevOps artifact:
- "Use Azure DevOps MCP Agent to implement work item 12345"
- "Use Azure DevOps MCP Agent to investigate failed pipeline 987"

## 5) Security Notes

- Prefer short-lived PATs with minimum read scopes needed.
- Do not commit PATs to the repository.
- Rotate PATs regularly.
