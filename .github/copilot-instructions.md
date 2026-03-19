# Copilot Instructions for Azure DevOps MCP

This repository is configured for GitHub Copilot coding agent in GitHub cloud.
Default behavior should align with the Azure DevOps MCP custom agent.

## Operating Rules

- Treat Azure DevOps as the source of truth for planning and delivery metadata.
- Use MCP tools to gather work item, wiki, test plan, and pipeline context before coding.
- Keep edits small and traceable to one or more Azure DevOps artifacts.
- Propose tests that match acceptance criteria from the related work item.
- Avoid destructive operations unless explicitly approved.

## Response Shape

- Start with a short findings summary.
- List concrete implementation steps.
- Make code changes.
- Report validation results and any follow-up needed in Azure DevOps.

## MCP Fallback

If Azure DevOps MCP is not reachable:
- Explain that MCP context is unavailable.
- Continue with repository-only analysis.
- Provide exact data the user should supply to proceed.
