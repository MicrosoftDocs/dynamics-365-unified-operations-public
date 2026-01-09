---
title: Dynamics 365 ERP Analytics MCP for finance and operations apps (preview)
description: Learn about the Dynamics 365 ERP Analytics Model Context Protocol server that enables AI agents to access and analyze Business performance analytics data through natural language.
author: wei-msft
ms.author: zhuw
ms.topic: overview
ms.date: 01/09/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.form: business-performance-analytics
---

# Dynamics 365 ERP Analytics MCP for finance and operations apps (preview)

> [!IMPORTANT]
> This feature is a preview feature. It's subject to the [preview supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2105274). Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release, so that customers can get early access and provide feedback.

The [Model Context Protocol (MCP)](https://www.anthropic.com/news/model-context-protocol) is an open standard that connects AI agents to various data systems to enhance the relevance of agent responses. The Dynamics 365 ERP Analytics MCP server enables AI agents to access and analyze [Business performance analytics](business-performance-analytics-home-page.md) data through natural language, unlocking powerful analytical capabilities for finance and operations insights.

Business performance analytics transforms raw transactional data from Dynamics 365 finance and operations into optimized analytical datasets across [three key value chains](reports-in-bpa.md): 

- **Record-to-Report** - financial data, P&L, budgets
- **Procure-to-Pay** - purchase orders, vendor management
- **Order-to-Cash** - sales orders, invoicing, receivables

The ERP Analytics MCP server exposes this analytical layer to AI agents through the Model Context Protocol, enabling agents to generate insights, perform analyses, and answer complex business questions using natural language.

## Prerequisites

Before using the ERP Analytics MCP server, ensure your environment meets the technical requirements:

- Dynamics 365 finance and operations - Version 10.0.38 or higher required
- Business performance analytics - Version 2.4.3224 or higher required. To install Business performance analytics, see [Business performance analytics installation guide](install-bpa.md).
- User roles and permissions:
  - Basic User role in Dynamics 365 finance and operations environment
  - Business performance analytics user role for accessing analytical data
- Agent platform - The agent platform on which you're building your agent must support MCP connections

## Use case: Natural language to analytics and insights

The ERP Analytics MCP server enables users to ask analytical questions in plain natural language and receive data-driven insights without writing DAX queries or navigating complex reporting interfaces. Simply describe what you want to know, and the AI agent generates the appropriate analysis by:

1. Understanding your analytical intent from natural language.
2. Retrieving the relevant Business performance analytics data model schema.
3. Generating and executing optimized DAX queries.
4. Returning structured insights you can act on.

For example, you can ask "Which vendors have the best on-time delivery performance this quarter?" and immediately receive a ranked analysis with supporting metrics.
This approach eliminates the technical barrier between business questions and analytical insights, making ERP data accessible to all users regardless of their technical expertise.

## How ERP Analytics MCP works

Unlike traditional API approaches that require custom engineering for each analytical operation, the ERP Analytics MCP server provides a small set of powerful tools that enable agents to dynamically query your Business performance analytics data.

### Dynamic analytical context

The MCP server dynamically exposes your Business performance analytics data model to agents, including dimensional models, measures, and relationships. The security role of the authenticated user determines which data the agent can access. The system enforces [row-level security (RLS)](/power-bi/enterprise/service-admin-rls) based on user roles, ensuring that agents only work with data the user has permission to access.

When the agent calls tools from the MCP server, it receives the analytical data model schema. This includes fact tables, dimension tables, measures, and relationships - the same analytical layer that powers [Business performance analytics reports](reports-in-bpa.md). Because the schema is dynamically retrieved, any updates to your Business performance analytics environment are automatically available to agents through the MCP framework.

### ERP Analytics MCP tools

The following tools are available in the Dynamics 365 ERP Analytics MCP server. The agent orchestration uses these tools to translate natural language prompts into analytical operations.

| Tool | Description |
|------|-------------|
| get-bpa-dataset-schema | Retrieves the schema of dimensional models, including tables, columns, measures, and relationships from your Business performance analytics environment |
| execute-dax-query | Executes [DAX (Data Analysis Expressions)](https://learn.microsoft.com/en-us/dax/dax-overview) queries against your Business performance analytics data with automatic row-level security enforcement |

The agent uses these tools to understand your data model and generate appropriate [DAX queries](/dax/dax-queries) to answer analytical questions. Data is returned as JSON that agents can analyze and present.

### Two-tier analytical architecture

The ERP Analytics MCP server leverages a two-tier calculation system:

1. Business performance analytics pre-transforms - Business performance analytics aggregates Dynamics 365 finance and operations transactional data into optimized [dimensional models](/power-bi/guidance/star-schema). These transforms currently run twice daily (12-hour intervals).

2. On-demand DAX queries - Agents generate custom calculations based on user questions by analyzing the facts, measures, and dimensional models to construct appropriate [DAX queries](dax/dax-queries).

This architecture enables agents to answer complex analytical questions without requiring custom API development for each scenario. The agent can dynamically construct queries for aggregations, trend analysis, comparative analysis, top/bottom performers, anomaly detection, and complex calculations.

## Example queries

The MCP server supports natural language queries for analytical operations on yourBusiness performance analytics data:

**Financial Analysis:**
- What is our profit and loss trend over the last 12 months?
- Show me our budget variance for this fiscal year.
- What are our top expense categories this quarter?

**Vendor Analysis:**
- Which vendors have the best on-time delivery performance?
- Calculate average payment cycle time by vendor.
- Identify vendors with the highest return rates.

**Customer Analysis:**
- Who are our top 10 customers by revenue?
- Show me customer concentration risk analysis.
- Calculate average days sales outstanding.

**Product Analysis:**
- What are our most profitable product lines?
- Identify products with declining sales trends.
- Calculate inventory turnover by product category.

## Combining with Dynamics 365 ERP MCP

The ERP Analytics MCP server works alongside the [Dynamics 365 ERP MCP server](../../fin-ops-core/dev-itpro/copilot/copilot-mcp.md) to enable powerful agent workflows that combine analytical insights with transactional actions:

1. Insights to action - Explore Business performance analytics data to identify issues, then trigger Dynamics 365 finance and operations actions through the Dynamics 365 ERP MCP server
2. Action informed by insights - Start with a task in Dynamics 365 finance and operations, then use Business performance analytics data to optimize decisions. For example, requisition management with vendor performance analysis. 

Agents can use both servers together to create comprehensive workflows that span from data analysis to business process execution.


## Next steps

- [Technical details and prerequisites](erp-analytics-mcp-technical-details.md)
- [Using ERP Analytics MCP in Visual Studio Code](erp-analytics-mcp-vscode.md)
- [Build an agent with ERP Analytics MCP in Copilot Studio](erp-analytics-mcp-copilot-studio.md)
- [See frequently asked questions](erp-analytics-mcp-faq.md)

## See also

- [Business performance analytics overview](business-performance-analytics-home-page.md)
- [Business performance analytics reports and data model](reports-in-bpa.md)
- [Use Model Context Protocol for finance and operations apps](../../fin-ops-core/dev-itpro/copilot/copilot-mcp.md)
- [Model Context Protocol specification](https://spec.modelcontextprotocol.io/)
