---
title: ERP Analytics MCP technical details
description: This article covers the technical prerequisites, limitations, and best practices for implementing the Dynamics 365 ERP Analytics MCP server.
author: wei-msft
ms.author: zhuw
ms.topic: concept-article
ms.date: 01/09/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.form: business-performance-analytics
---

# ERP Analytics MCP technical details

This article covers the technical prerequisites, limitations, and best practices for implementing the Dynamics 365 ERP Analytics MCP server.

## Prerequisites

Before you can use the Dynamics 365 ERP Analytics MCP server, you must meet the following prerequisites:

- Dynamics 365 finance and operations - Version 10.0.38 or higher required.
- Business performance analytics - Version 2.4.3224 or higher required. To install Business performance analytics, see [Business performance analytics installation guide](install-bpa.md).
- User roles and permissions:
  - Basic user role in Dynamics 365 finance and operations environment.
  - Business performance analytics user role for accessing analytical data.
- Agent platform - The agent platform on which you're building your agent must support MCP connections.

## Service Limits

The current implementation of the Dynamics 365 ERP Analytics MCP server has the following limitations:

### Data refresh frequency

Business performance analytics data refreshes twice daily (12-hour intervals). The full pipeline (data sync, transforms, and refresh) can take 4-5 hours or more, depending on your data volume.

### Performance limitations

- Query timeout - 120 seconds maximum execution time.
- Data return limit - Approximately 10MB per query.
- Schema size - The complete data model schema is extensive. 24,000+ tokens for tables/columns/relationships, 48,000+ tokens including measures.

### Row-level security

Row-level security (RLS) is enforced based on user roles. Ensure users have appropriate permissions in Business performance analytics to access the data they need for analysis. The MCP server respects all security configurations defined in your Business performance analytics environment.

### Business performance analytics coverage

The MCP server exposes what's available in your Business performance analytics environment. If certain data areas aren't covered by Business performance analytics, they won't be accessible through the MCP server. 
Current coverage includes:
- Record-to-Report - Financial data, P&L, budgets.
- Procure-to-Pay - Purchase orders, vendor management.  
- Order-to-Cash - Sales orders, invoicing, receivables.

For more information, see [Business performance analytics data model and capabilities](reports-in-bpa.md).

### Query complexity

Complex multi-step analytical scenarios may require multiple tool calls. DAX query generation quality varies by model. Claude Sonnet 4+ is recommended for optimal performance.

### Authentication

Currently requires Microsoft authentication clients only. Direct access from non-Microsoft clients might not work during the preview period.

### Best practices
Prompt design
 - Be specific about time periods - Use explicit date ranges like "Q4 2024" or "October through December 2024" rather than relative terms like "last quarter".
 - Specify granularity when needed - Clarify whether you need daily, weekly, monthly, or annual aggregations.
 - Use structured prompts for complex analysis - For multi-metric analyses, provide a structured format with clear sections for metrics, grouping, filtering, and sorting.
 - Iterate based on results - Start with broad exploratory questions, then refine based on initial insights.

### Model selection
- Claude Sonnet 4+ - Recommended for optimal DAX query generation and reasoning.
- GPT models - Supported but may require more iterations for complex analytical queries.

### Configuration
- Use workspace-level configuration - When setting up the MCP server in Visual Studio Code, use workspace-level configuration to isolate server connections per project.
- Disable built-in tools - For focused analytical sessions, disable VS Code's built-in tools to ensure the agent only uses ERP Analytics MCP tools.

### Performance optimization

- Limit data return sizes - When possible, use aggregations and summaries rather than requesting detailed transaction-level data.
- Break complex analyses into steps - For multi-part analyses, structure your prompts to build up insights incrementally.
- Use appropriate time windows - Balance data freshness needs with query performance by selecting appropriate time ranges.

### Security considerations
- Verify user permissions - Before onboarding users, ensure they have appropriate Business performance analytics roles and Dynamics 365 finance and operations permissions.
- Test with role-based access - Validate that row-level security is working as expected for different user roles.
- Monitor data access patterns - Track which data sources and measures are being accessed through the MCP server.

## Next steps

- [Using ERP Analytics MCP in Visual Studio Code](erp-analytics-mcp-vscode.md)
- [Build an agent with ERP Analytics MCP in Copilot Studio](erp-analytics-mcp-copilot-studio.md)
- [See frequently asked questions](erp-analytics-mcp-faq.md)

## See also

- [Business performance analytics overview](business-performance-analytics-home-page.md)
- [Business performance analytics installation guide](install-bpa.md)
- [Business performance analytics reports and data model](reports-in-bpa.md)
- [Row-level security in Power BI](https://learn.microsoft.com/en-us/power-bi/enterprise/service-admin-rls)
- [DAX queries reference](https://learn.microsoft.com/en-us/dax/dax-queries)
