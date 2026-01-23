---
title: Build an agent with Dynamics 365 ERP MCP
description: Learn how to build an agent in Microsoft Copilot Studio with the Model Context Protocol (MCP) server.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 11/05/2025
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Build an agent with Dynamics 365 ERP MCP

[!include [banner](../includes/banner.md)]

The **Dynamics 365 ERP MCP** server provides a dynamic framework for agents to perform data operations and access the business logic of finance and operations apps. Developers can build agents that work with data and perform nearly any function that's available to a user through the application interface, without the need for custom code, connectors, or APIs. This article provides guidance and best practices for building an agent with the MCP server in Microsoft Copilot Studio.

## Prerequisites

Before building an agent, you must enable the **Dynamics 365 ERP MCP** server in your environment. Learn more about enabling the server in [Use Model Context Protocol for finance and operations apps](copilot-mcp.md).

## Adding the MCP server to your agent

When you add the MCP server to your agent, you give the agent access to all the tools available on the server. This access includes data and business logic that matches the agent's security role and environment context. Follow these steps to add the MCP server to your agent in Microsoft Copilot Studio:

1. Go to Microsoft Copilot Studio and create a new agent or open an existing agent.
1. On the **Tools** tab of the agent, select **Add a tool**.
1. Select the **Model Context Protocol** filter.
1. Search for and select the **Dynamics 365 ERP MCP** server.
1. Create a connection to the server.
1. Select **Add to agent**.

After you add the **Dynamics 365 ERP MCP** server, the agent can access the tools on the server and use them to perform actions for related finance and operations apps. To view the list of tools on the server, open the tool in the agent, or learn more in [Use Model Context Protocol for finance and operations apps](copilot-mcp.md).

Learn more about configuration options for the MCP tools in [Add tools and resources from a Model Context Protocol (MCP) server to your agent](/microsoft-copilot-studio/mcp-add-components-to-agent).

> [!NOTE]
> You can also select the **Dynamics 365 ERP MCP** server in Microsoft Copilot Studio. This server contains 13 static tools for specific actions in Dynamics 365 Finance and Supply Chain Management. However, this version of the server will be retired due to limitations in the server's scale and extensibility. We continue to enhance the **Dynamics 365 ERP MCP** server.

## Selecting a model

On the **Overview** tab, you can view and change the agent's model. This model is the primary model the agent uses for reasoning, orchestration, and responding to prompts and instructions. The model you select for your agent has a significant impact on the quality of responses in your agent.

While GPT-4.1 can be used in other clients like Microsoft Visual Studio Code with GitHub Copilot and achieve good results, don't use it as the orchestration model for agents in Copilot Studio. The recommended model for agents using the Dynamics 365 ERP MCP server is **Claude Sonnet 4.5**. This model provides a better success rate in Copilot Studio over other default models like GPT-4.1. If Claude Sonnet 4.5 isn't available in your environment, use **GPT-5 (Chat)**.

> [!NOTE]
> Claude models are external models not hosted in Azure. Tenant administrators must approve them for use on the tenant. Learn more in [Choose an external model as the primary AI model](/microsoft-copilot-studio/authoring-select-external-response-model).

## Providing agent instructions

The **Instructions** on the **Overview** tab of the agent are the core directives or guidance on how the agent should function. They tell the agent what to do and how to do it (tools, workflows, tone), in natural language statements. They can give the agent important context for improving the agentic orchestration in selecting the right tool or knowledge source, filling inputs for tools based on context, or generating responses to the user. Learn more about writing instructions for agents in Copilot Studio in [Write agent instructions](/microsoft-copilot-studio/authoring-instructions).

Providing instructions to an agent with the Dynamics 365 ERP MCP server helps the agent understand when and how to use the tools in the MCP server. The following principles can help you write effective agent instructions:

1. **Define the purpose:**
   - Clearly state the agent's role (for example, "Assist with ERP queries and inventory checks").
   - Include tone and restrictions (for example, "Respond professionally, avoid technical jargon for end users").
1. **Include skills and actions:** List what the agent can do (for example, "Use Dynamics 365 MCP tools for finance and supply chain tasks").
1. **Add workflow details:** Provide step-by-step guidance for common tasks.

For example, the following instructions can provide context on using the tools in the Dynamics 365 ERP MCP server. You can copy and paste these instructions into your agent's instructions as a starting point for guiding the agent in how to use the available tools to perform the agentic tasks. Then update the instructions as you test your agent to provide guidance on how you expect the agent to orchestrate in performing assigned tasks.

``` txt
# Role
Act as an autonomous data entry agent responsible for interacting with the Dynamics 365 Finance and Operations app. 

There are 3 types of tools for interacting with Dynamics 365 Finance and Operations applications: form tools, API tools, and data tools.
- Form tools enable interaction with F&O forms in the same way a user would through the UI. 
- API tools allow calling custom X++ logic.
- Data tools allow interacting with F&O using OData.

# Tool selection guidance
- For create/read/update/delete operations - you MUST prefer using data tools before using form tools.
- When explicitly instructed, or if proved impossible to complete the task using data tools, use the form or API tools.

# Objective
Your objective is to respond to tasks provided by the user. First execute each step of the provided task workflow using your MCP tools. Check if you have achieved your objective after each tool call. If you have not achieved your objective then continue to execute the next step in the task workflow.

# Form tool Usage Instructions
- Typical flow for record creation operations is to find a menu item, open a form, click the new button, find and set values for relevant controls, save the form.
- You can use grid filtering to find relevant records for update, delete or inquiry scenarios.
- DO NOT EVER EVER ask for menu item types. The find_menu tool groups menu items by their type.

# Data Tool Parameter Filling Instructions
- Get the entity types and their schema metadata using data_find_entity_type tool before using CRUD data tools, unless instructed otherwise in the task instructions.
- You MUST use plural entity name in the OData path for data operations. For V2+ entities, use plural before V. E.g. SalesOrderHeadersV2.
- DO NOT use deep insert (nested entity creation in one call), it is not supported.
- For filtering by enums (or setting enum values), use the following format: `$filter=Style has Namespace.Pattern'Yellow'`.

# Form Tool Parameter Filling Instructions
- Omit optional parameters if no value is provided as input.
- Use menu item names (and not labels) when filling menu name parameters in tool calls.
- Use grid column names (and not labels) when filling grid column name parameters in tool calls.
- Use control names (and not labels) when filling control name parameters in tool calls.
- Use tab names (and not labels) when filling tab name parameters in tool calls.
- `(lessThanDate(x:int))`  is a valid value for a grid date column filter.

# Extraction Instructions
- A tool call response can include up to 25 rows of data as form state. Generate a warning if the form state contains 25 rows of data.

# Reasoning Instructions
- Think out loud and reason step by step.
- Before each tool call, plan the action.
- After each tool call, reflect on the result and determine the next step.
- When answering questions about data DO NOT rely on your general knowledge. Use tools to find accurate and precise data
- When instructed to create new data, and the creation fails, DO NOT retrieve existing data instead.
- DO NOT stop reasoning until all tasks are complete or an error is observed prevents continuation.
- DO NOT stop reasoning to ask a user questions or ask for user input.
- Only ask questions if the task is not clear
```
