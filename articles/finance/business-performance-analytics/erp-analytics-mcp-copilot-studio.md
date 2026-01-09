---
title: Build an agent with ERP Analytics MCP in Copilot Studio (preview)
description: This article provides guidance and best practices for building an agent with the ERP Analytics MCP server in Microsoft Copilot Studio.
author: wei-msft
ms.author: zhuw
ms.topic: how-to
ms.date: 01/09/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.form: business-performance-analytics
---

# Build an agent with ERP Analytics MCP in Copilot Studio (preview)

The Dynamics 365 ERP Analytics MCP server enables AI agents to access and analyze [Business Performance Analytics (BPA)](business-performance-analytics-home-page.md) data through natural language. This article provides guidance and best practices for building an agent with the ERP Analytics MCP server in [Microsoft Copilot Studio](https://www.microsoft.com/en-us/microsoft-copilot/microsoft-copilot-studio).

> [!IMPORTANT]
> This feature is a preview feature. It's subject to the [preview supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2105274). Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release, so that customers can get early access and provide feedback.

## Prerequisites

Before building an agent, ensure you have:

- **Microsoft Copilot Studio access**: License and permissions to create agents

For complete environment and system prerequisites, see [ERP Analytics MCP Technical Details](erp-analytics-mcp-technical-details.md).

## Adding the MCP server to your agent

When you add the MCP server to your agent, you give the agent access to the analytical tools available on the server. This access includes BPA data that matches the user's security role and permissions. Follow these steps to add the MCP server to your agent in Microsoft Copilot Studio:

1. Go to [Microsoft Copilot Studio](https://copilotstudio.microsoft.com/) and create a new agent or open an existing agent.

2. On the **Tools** tab of the agent, select **Add a tool**.

3. Select the **Model Context Protocol** filter.

4. Search for and select the **Dynamics 365 ERP Analytics MCP** server.

5. Create a connection to the server using your Power Platform environment credentials.

6. Select **Add to agent**.

After you add the Dynamics 365 ERP Analytics MCP server, the agent can access the analytical tools on the server and use them to answer data questions and generate insights from your BPA data. 

Learn more about configuration options for MCP tools in [Add tools and resources from a Model Context Protocol (MCP) server to your agent](https://learn.microsoft.com/en-us/microsoft-copilot-studio/mcp-add-components-to-agent).

## Selecting a model

On the **Overview** tab, you can view and change the agent's model. This model is the primary model the agent uses for reasoning, orchestration, and responding to prompts and instructions. The model you select for your agent has a significant impact on the quality of analytical responses.

**The recommended model for agents using the Dynamics 365 ERP Analytics MCP server is Claude Sonnet 4.5.** If Claude Sonnet 4.5 isn't available in your environment, use GPT-5 (Chat) as an alternative.

> [!NOTE]
> Claude models are external models not hosted in Azure. Tenant administrators must approve them for use on the tenant. Learn more in [Choose an external model as the primary AI model](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-select-external-response-model).

## Providing agent instructions

The **Instructions** on the Overview tab of the agent are the core directives or guidance on how the agent should function. They tell the agent what to do and how to do it, in natural language statements. Instructions provide important context for improving the agent's orchestration in selecting the right tool, interpreting analytical requests, and generating responses.

Learn more about writing instructions for agents in Copilot Studio in [Write agent instructions](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-instructions).

### Principles for effective instructions

Providing instructions to an agent with the Dynamics 365 ERP Analytics MCP server helps the agent understand when and how to use the analytical tools. The following principles can help you write effective agent instructions:

1. **Define the purpose**:
   - Clearly state the agent's role (for example, "Provide analytical insights from Business Performance Analytics data")
   - Include tone and restrictions (for example, "Provide data-driven insights in plain language")

2. **Include skills and actions**:
   - List what the agent can do (for example, "Use ERP Analytics MCP tools to analyze financial, vendor, and customer data")

3. **Add workflow details**:
   - Provide step-by-step guidance for common analytical tasks

### Sample agent instructions

The following instructions provide context on using the tools in the Dynamics 365 ERP Analytics MCP server. You can copy and paste these instructions into your agent as a starting point:

```
# Role
Act as a business analyst assistant that provides data-driven insights from Business Performance Analytics (BPA) data.

# Objective
Your objective is to answer analytical questions about ERP data using natural language. Use the ERP Analytics MCP tools to retrieve and analyze data from the BPA environment.

# Available Tools
You have access to two analytical tools:
- get-bpa-dataset-schema: Retrieves the schema of analytical data models, including tables, columns, measures, and relationships
- execute-dax-query: Executes DAX queries against BPA data with automatic security enforcement

# Tool Usage Instructions
- Always start by using get-bpa-dataset-schema to understand the available data model before answering analytical questions
- Generate appropriate DAX queries based on the user's question and the data model schema
- Use the execute-dax-query tool to retrieve data and calculate insights
- Present results in a clear, business-friendly format

# Query Best Practices
- For time-based analyses, use explicit date ranges rather than relative terms
- When requesting aggregations, specify the grouping dimensions clearly
- For top/bottom analyses, include appropriate sorting and filtering
- Keep queries focused and avoid requesting excessive detail when aggregates suffice

# Response Guidelines
- Present insights in plain language without technical jargon
- Include relevant context about the data (time periods, filters applied, etc.)
- If data is limited by security permissions, explain what the user has access to
- When data is not available, explain what BPA coverage exists

# Reasoning Instructions
- Before generating DAX queries, plan what data and calculations are needed
- Check if the schema contains the required tables, columns, and measures
- Validate that the query addresses the user's question
- If a query fails or returns unexpected results, adjust and retry
```

## Tips for analytical agent design

### Focus on business questions

Design your agent to handle common business analytical scenarios:
- Financial performance analysis (P&L trends, budget variance)
- Vendor performance tracking (OTIF, payment cycles)
- Customer analytics (revenue by segment, DSO)
- Operational insights (inventory turnover, product profitability)

### Handle conversational context

Enable follow-up questions by maintaining context:
- "Show me top vendors by spend" → "Now show me their on-time delivery rates"
- "What's our revenue trend?" → "Break that down by region"

### Provide actionable insights

Structure responses to include:
- Clear answer to the question
- Supporting data and metrics
- Context about time periods and filters
- Recommendations or observations when appropriate

### Set expectations

In your agent instructions, clarify:
- Data refresh frequency (twice daily)
- Available data scope (Record-to-Report, Procure-to-Pay, Order-to-Cash)
- Security-based limitations on data access

## Testing your agent

When testing your agent:

1. **Start with simple queries**: Test basic aggregations and summaries first
2. **Progress to complex analyses**: Try multi-metric analyses with grouping and filtering
3. **Test different time periods**: Verify handling of various date ranges and granularities
4. **Validate security**: Test with users having different BPA permissions
5. **Check error handling**: Verify appropriate responses when data isn't available

## Example analytical queries

Use these example queries to test your agent:

**Financial Analysis:**
- "What is our profit and loss trend over the last 12 months?"
- "Show me budget variance for this fiscal year by department"
- "What are our top 5 expense categories this quarter?"

**Vendor Analysis:**
- "Which vendors have the best on-time delivery performance?"
- "Calculate average payment cycle time by vendor"
- "Show me vendor spend concentration risk"

**Customer Analysis:**
- "Who are our top 10 customers by revenue?"
- "Calculate average days sales outstanding"
- "Identify customers with declining purchase trends"

**Product Analysis:**
- "What are our most profitable product lines?"
- "Show me inventory turnover by category"
- "Identify products with declining sales"

## Troubleshooting

### Agent not finding the MCP server

- Verify BPA v2.4.3224 or higher is installed
- Ensure you have appropriate permissions in your Power Platform environment
- Check that the ERP Analytics MCP server is enabled

### Poor query results

- Review your agent instructions for clarity
- Ensure you're using Claude Sonnet 4.5 or GPT-5 (Chat)
- Add more specific guidance about your BPA data model in instructions

### Timeout issues

- Add instructions to focus queries on aggregated data
- Guide the agent to limit time ranges for large datasets
- Instruct the agent to break complex analyses into multiple steps

## Next steps

- [Back to overview](erp-analytics-mcp-overview.md)
- [Review technical details and limitations](erp-analytics-mcp-technical-details.md)
- [See frequently asked questions](erp-analytics-mcp-faq.md)

## See also

- [Write agent instructions](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-instructions)
- [Add tools from an MCP server](https://learn.microsoft.com/en-us/microsoft-copilot-studio/mcp-add-components-to-agent)
- [Choose an external model](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-select-external-response-model)
- [Business Performance Analytics overview](business-performance-analytics-home-page.md)
- [Model Context Protocol specification](https://spec.modelcontextprotocol.io/)
