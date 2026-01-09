---
title: Use ERP Analytics MCP in Visual Studio Code
description: This article provides step-by-step instructions for configuring and using the Dynamics 365 ERP Analytics MCP server with GitHub Copilot in Visual Studio Code.
author: wei-msft
ms.author: zhuw
ms.topic: how-to
ms.date: 01/09/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.form: business-performance-analytics
---

# Use ERP Analytics MCP in Visual Studio Code

This article provides step-by-step instructions for configuring and using the Dynamics 365 ERP Analytics MCP server with the GitHub Copilot Agent in Visual Studio Code.

## Prerequisites

Before you begin, ensure you have:

- Visual Studio Code installed with the latest updates
- [GitHub Copilot subscription](https://github.com/features/copilot)
- Your [Power Platform environment ID](/power-platform/admin/determine-org-id-name)

For complete environment and system prerequisites, see [ERP Analytics MCP Technical Details](erp-analytics-mcp-technical-details.md).

## Configure the MCP server

1. Apply the latest updates for Visual Studio Code.
2. In Visual Studio Code, run command (Ctrl + Shift + P), and select **MCP: Add Server…**
3. Select **HTTP** to connect to a remote HTTP server.
4. In the **URL of the MCP server** box, enter your MCP endpoint URL in the following format:

   ```
   https://agent365.svc.cloud.microsoft/mcp/environments/<ENVIRONMENT_ID>/servers/msdyn_ERPAnalyticsMCPServer
   ```

   Replace `<ENVIRONMENT_ID>` with your [Power Platform environment ID](/power-platform/admin/determine-org-id-name).

5. Provide a **Server ID** value. For example, D365 Analytics MCP, or accept the default.

6. Select the destination where the MCP server is available in:
   - **Workspace** - Available in this workspace only (recommended for isolating configurations).
   - **Global** - Available in all workspaces.

7. Once selected, the mcp.json file is created with the server configuration. This configuration shows the server status and the number of tools retrieved from the server. You can also start/restart the connection to the server as needed.

8. When the server is started, you will need to authenticate to the server using the credentials for your Power Platform environment.

For more information on MCP support in Visual Studio Code, see [Use MCP servers in VS Code](/copilot/customization/mcp-servers.md).

## Configure the agent chat

1. In Visual Studio Code, run command (Ctrl + Shift + P) and select **Chat: Open Chat**.
2. In the chat pane select **Agent** from the mode selection list.
3. In the **Model selection** list, select your preferred model (Claude Sonnet 4+ recommended).
4. (Optional) Disable all VSCode built-in tools so you're only using the tools from the ERP Analytics MCP server:
   - Select the **Tools** menu.
   - Uncheck all tools not included in the ERP Analytics MCP server you configured.
   - Select the "eye" icon on files listed in the chat box to disable the current file context, removing the context from the chat.

5. Begin prompting in the chat.

## Using natural language queries

The MCP server supports natural language queries for analytical operations on your Business performance analytics data. This includes:
- Aggregations and summaries - What were total sales by region last quarter?
- Trend analysis - Show me revenue trends over the past 12 months.
- Comparative analysis - Compare vendor performance between Q1 and Q2.
- Top/bottom performers - Who are my top 10 customers by revenue?
- Anomaly detection - Identify purchase invoices that deviate from normal patterns.
- Complex calculations - Calculate inventory turnover ratios by product category.

The agent uses the schema tool to understand your data model, then generate appropriate DAX queries to answer your questions. Results are returned as structured data that agents can analyze and present.

### Structured prompts for complex analysis

For more complex analytical scenarios, you can provide structured prompts that give the agent more context and guidance. This is particularly useful when:

- You need specific calculations or business logic applied.
- You want to ensure specific data granularity (daily vs monthly).
- You need to combine multiple analytical perspectives.
- You want to format results in a specific way.

Example structured prompt:

```
Analyze vendor performance for Q4 2024:

Metrics to calculate:
- On-time delivery rate (OTIF)
- Average invoice amount
- Number of purchase orders
- Total spend

Group by: Vendor name
Filter: Only vendors with >5 orders in the period
Sort: By total spend descending
Top: 10 vendors

Format results as a table
```

### Tips for effective prompts
 - Be specific about time periods - last quarter vs Q4 2024 vs October through December 2024.
 - Specify granularity when needed - Show daily trends vs monthly aggregates.
 - Request specific visualizations - Create a bar chart showing... or Generate a trend line for...
 - Iterate based on results - Start with broad questions, then refine based on initial insights.

## Troubleshooting

### Server connection issues

If the MCP server shows as disconnected:
- Verify your environment ID is correct.
- Ensure you're authenticated to your Power Platform environment.
- Check that Business performance analytics v2.4.3224 or higher is installed.
- Restart the MCP server connection from the mcp.json file.

### Authentication problems
If authentication fails:
- Ensure you have the basic user role in Dynamics 365 finance and operations.
- Verify you haveBusiness performance analyticsBPA user role permissions.
- Try re-authenticating through the authentication prompt.

### No tools appearing
If the server connects but shows 0 tools:
- Verify Business performance analytics is properly installed and configured.
- Check that the MCP server feature is enabled in your environment.
- Contact your administrator to verify environment configuration.

### Query timeouts

If queries consistently timeout:
- Reduce the time range in your query.
- Request aggregated data rather than detailed transactions.
- Break complex analyses into multiple simpler queries.
- Consider whether your data volume requires optimization.

## Next steps

- [Back to overview](erp-analytics-mcp-overview.md)
- [Review technical details and limitations](erp-analytics-mcp-technical-details.md)
- [See frequently asked questions](erp-analytics-mcp-faq.md)

## See also

- [Use MCP servers in VS Code](https://code.visualstudio.com/docs/copilot/customization/mcp-servers)
- [GitHub Copilot documentation](https://docs.github.com/en/copilot)
- [Business performance analytics overview](business-performance-analytics-home-page.md)
- [Model Context Protocol specification](https://spec.modelcontextprotocol.io/)
