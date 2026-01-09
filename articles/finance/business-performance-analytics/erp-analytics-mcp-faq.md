---
title: Dynamics 365 ERP Analytics MCP frequently asked questions
description: This article answers common questions about the Dynamics 365 ERP Analytics Model Context Protocol server.
author: wei-msft
ms.author: zhuw
ms.topic: faq
ms.date: 01/09/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.form: business-performance-analytics
---

# Dynamics 365 ERP Analytics MCP frequently asked questions

This article answers common questions about the Dynamics 365 ERP Analytics MCP server.

## General Questions

### What is the ERP Analytics MCP server?

The ERP Analytics MCP server is a [Model Context Protocol](https://www.anthropic.com/news/model-context-protocol) implementation that enables AI agents to access and analyze [Business performance analytics](business-performance-analytics-home-page.md) data through natural language. It allows users to ask analytical questions in plain English and receive data-driven insights without writing queries or navigating complex reporting interfaces.

### How is this different from Business performance analytics reports?

Business performance analytics reports provide pre-built visualizations and dashboards with fixed layouts. The ERP Analytics MCP server enables dynamic, conversational analytics where you can ask any question about your data and receive customized insights. The agent generates appropriate DAX queries on-demand based on your specific questions, rather than being limited to pre-configured report views.

### What data can I analyze?

The MCP server exposes all data available in your Business performance analytics environment across three key value chains:
- **Record-to-Report**: Financial data, P&L, budgets.
- **Procure-to-Pay**: Purchase orders, vendor management.
- **Order-to-Cash**: Sales orders, invoicing, receivables.

The specific tables, measures, and dimensions available depend on your Business performance analytics configuration and installation.

### Do I need to know DAX?

No. The AI agent automatically generates DAX queries based on your natural language questions. You simply describe what insights you need in plain English, and the agent handles the technical query construction.

## Technical questions

### What are the prerequisites?

See [ERP Analytics MCP Technical Details](erp-analytics-mcp-technical-details.md) for complete system and environment prerequisites.

### How do I get my environment ID?

Your Power Platform environment ID can be found in the Power Platform admin center. See [Determine your organization ID and name](/power-platform/admin/determine-org-id-name) for detailed instructions.

### Can I use this with Microsoft Copilot Studio?

Yes. Microsoft Copilot Studio is supported. You can use the ERP Analytics MCP server in both Visual Studio Code with GitHub Copilot and Microsoft Copilot Studio.

### How often is the data refreshed?

Business performance analytics data currently refreshes twice daily (12-hour intervals). The complete pipeline including data sync, transforms, and refresh can take 4-5 hours or more depending on data volume. Hourly refresh is in development.

## Security and Permissions

### How does security work?

The MCP server enforces [row-level security (RLS)](/power-bi/enterprise/service-admin-rls) based on the authenticated user's roles. Users only see data they have permission to access in Business performance analytics. All security configurations from your Business performance analytics environment are respected.

### What authentication is required?

Currently, Microsoft authentication clients are required. You'll authenticate using your Power Platform environment credentials when connecting to the MCP server.

### Can I restrict which users can access the MCP server?

Yes. Access is controlled through Business performance analytics user roles and Dynamics 365 finance and operations security roles. Users must have appropriate permissions in both systems to access data through the MCP server.

## Usage Questions

### What types of questions can I ask?

You can ask any analytical question about your Business performance analytics data, including:
- Aggregations and summaries - What were total sales by region last quarter?
- Trend analysis - Show me revenue trends over the past 12 months.
- Comparative analysis - Compare vendor performance between Q1 and Q2.
- Top/bottom performers - Who are my top 10 customers by revenue?
- Anomaly detection - Identify invoices that deviate from normal patterns.
- Complex calculations - Calculate inventory turnover by product category.

See example queries in [Dynamics 365 ERP Analytics MCP for finance and operations apps](erp-analytics-mcp-overview.md).

### How do I write effective prompts?

Best practices for prompts:
1. Be specific about time periods. Use explicit dates like "Q4 2024" rather than "last quarter".
2. Specify the granularity you need. For example, daily, weekly, monthly.
3. Use structured prompts for complex multi-metric analyses.
4. Iterate - start with broad questions and refine based on results.

See [Using ERP Analytics MCP in Visual Studio Code](erp-analytics-mcp-vscode.md) for detailed guidance.

### Can I combine this with the Dynamics 365 ERP MCP server?

Yes, the ERP Analytics MCP server works alongside the [Dynamics 365 ERP MCP server](../../fin-ops-core/dev-itpro/copilot/copilot-mcp.md) to enable powerful workflows:
- **Insights to Action** - Analyze Business performance analytics data to identify issues, then trigger Dynamics 365 finance and operations actions.
- **Action Informed by Insights** - Start with a task in Dynamics 365 finance and operations, then use Business performance analytics data to optimize decisions.

### What are the query limits?

- Query timeout: 120 seconds maximum execution time.
- Data return limit: Approximately 10MB per query.
- For large datasets, use aggregations and summaries rather than requesting detailed transaction-level data.

## Troubleshooting

### The server shows as disconnected

Check the following:
- Verify your environment ID is correct in the URL.
- Ensure you're authenticated to your Power Platform environment.
- Confirm Business performance analytics v2.4.3224 or higher is installed.
- Try restarting the MCP server connection.

### I see 0 tools available in Copilot Studio

If you see 0 tools when connecting to the ERP Analytics MCP server in Microsoft Copilot Studio, this typically indicates one of the following issues:

**Business performance analytics not properly installed or configured:**
- Verify that Business performance analytics is installed in your environment.
- Check that Business performance analytics installation completed successfully, including all data sync and refresh steps.
- Confirm that you have Business performance analytics user role permissions assigned.
- Visit the Business performance analytics app in your environment to verify it's accessible and showing data.

**Version compatibility:**
- The ERP Analytics MCP server requires Business performance analytics version 2.4.3224 or higher.
- To check your Business performance analytics version, go to Settings > Solutions in Power Platform admin center.
- If you have an older version, upgrade Business performance analytics to the minimum required version.
- After upgrading, wait for the next Business performance analytics data refresh cycle (12-hour intervals) before reconnecting.

**What to do:**
1. Log into your Power Platform environment and navigate to the Business performance analytics app.
2. Verify you can access Business performance analytics reports and see data.
3. Check your Business performance analytics version in the Solutions area.
4. If issues persist, contact your Power Platform administrator to verify the environment configuration.

### Queries are timing out

To resolve timeout issues:
- Reduce the time range in your query
- Request aggregated data rather than detailed transactions
- Break complex analyses into multiple simpler queries
- Consider whether your data volume requires optimization

### Authentication keeps failing

Verify that you have:
- Basic User role in Dynamics 365 finance and operations
- Business performance analytics user role permissions
- Try re-authenticating through the authentication prompt
- Contact your administrator if issues persist

## Preview and Future

### Is this feature generally available?

The ERP Analytics MCP server is currently in public preview. It's subject to the [preview supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2105274). Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release, so that customers can get early access and provide feedback.

### What features are coming?

Future capabilities include:
- Natural language dashboard creation
- Report updates through natural language
- Custom measures creation with approval workflows
- Expanded Business performance analytics data coverage
- Integration with Dynamics 365 Analyst Agent

See the roadmap in [Dynamics 365 ERP Analytics MCP for finance and operations apps](erp-analytics-mcp-overview.md).

### How do I provide feedback?

During the public preview, you can provide feedback through the [Business performance analytics Viva Engage group](https://engage.cloud.microsoft/main/org/microsoft.com/groups/eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIyMzc3NDU0NTUxMDQifQ). You can also reach out through your Microsoft account team or support channels.

## See also

- [Dynamics 365 ERP Analytics MCP for finance and operations apps](erp-analytics-mcp-overview.md)
- [ERP Analytics MCP Technical Details](erp-analytics-mcp-technical-details.md)
- [Business performance analytics overview](business-performance-analytics-home-page.md)
- [Model Context Protocol specification](https://spec.modelcontextprotocol.io/)
