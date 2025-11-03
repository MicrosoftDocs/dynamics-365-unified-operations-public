---
title: Build an agent with Dynamics 365 ERP MCP (Preview)
description: Learn how to build an agent in Microsoft Copilot Studio with the Model Context Protocol (MCP) server.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 06/03/2025
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Build an agent with Dynamics 365 ERP MCP (Preview)

[!include [banner](../includes/banner.md)]

The **Dynamics 365 ERP MCP (Preview)** server provides a dynamic framework for agents to perform data operations and access the business logic of finance and operations apps. Developers can build agents that work with data and perform nearly any function that is available to a user through the application interface, without the need of custom code, connectors, or APIs. In this article we provide guidance and best practices for building an agent with the MCP server in Microsoft Copilot Studio.

> [!IMPORTANT]
> This feature is a preview feature. It's subject to the [preview supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2105274). Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release, so that customers can get eary access and provide feedback. Learn more about preview releases in [One version service updates FAQ](../../dev-itpro/get-started/one-version.md).

## Prerequisites
Before building an agent, the **Dynamics 365 ERP MCP (Preview)** server must be enabled in your environment. See [Use Model Context Protocol for finance and operations apps](copilot-mcp.md) for more information.

## Adding the MCP server to your agent
Adding the MCP server to your agent provides the agent with all the tools available in the server. This gives the agent access to the data and business logic available to the agent's security role and environment context. Follow the steps below to add the MCP server to your agent in Microsoft Copilot Studio.

1. Navigate to Microsoft Copilot Studio and either create a new agent or open an existing agent.
2. On the **Tools** tab of the agent, select **Add a tool**.
3. Select the **Model Context Protocol** filter.
4. Search for and select the **Dynamics 365 ERP MCP (Preview)** server.
5. Create a connection to the server.
6. Select **Add to agent**.

After the **Dynamics 365 ERP MCP (Preview)** server is added, the agent has access to the tools on it and can use them to perform action for the related finance and operations apps. To view the list of tools on the server, open the tool in the agent, or see [Use Model Context Protocol for finance and operations apps](copilot-mcp.md) for more information.

> [!NOTE]
> The **Dynamics 365 ERP MCP** server is also available to select in Microsoft Copilot Studio. This server contains 13 static tools for specific actions in Dynamics 365 Finance and Supply Chain Management. Due to limitations in the server's scale and extensibility, this version of the server will be retired. We will continue to enhance the **Dynamics 365 ERP MCP (Preview)** server.

## Selecting a model
On the **Overview** tab you can view and change the agent's model. This is the primary model th agent uses for reasoning, orchestration, and responding to prompts and instructions. The model you select for your agent has a signficant impact on the quality of responses in your agent.

The recommended model for agents using the Dynamics 365 ERP MCP (Preview) server is **Claude Sonnet 4.5**. This model is observed to provide a significantly better success rate in Copilot Studio over other default models like GPT-4.1. 

> [!NOTE]
> Claude models are external models not hosted in Azure. Tenant administrators must approve them for use on the tenant. For more information see [Choose an external model as the primary AI model](https://learn.microsoft.com/microsoft-copilot-studio/authoring-select-external-response-model) in Microsoft Copilot Studio documentation.

## Providing agent instructions
The **Instructions** on the **Overview** tab of the agent are the core directives or guidance on how the agent should function. They tell the agent what to do and how to do it (tools, workflows, tone), in natural language statements. They can give the agent important context to improve the agentic orchestration in selecting the right tool or knowledge source, filling inputs for tools based on context, or generating responses to the user. See [Write agent instructions](https://learn.microsoft.com/microsoft-copilot-studio/authoring-instructions) for more information on writing instructions for agents in Microsoft Copilot Studio.

Providing instructions to an agent with the Dynamics 365 ERP MCP (Preview) server helps the agent understand when and how to use the tools in the MCP server. The following are some principles for writing effective agent instructions:
1. **Define the purpose:**
   - Clearly state the agent's role (e.g., "Assist with ERP queries and inventory checks").
   - Include tone and restrictions (e.g., "Respond professionally, avoid technical jargon for end users").
2. **Include skills and actions:** List what the agent can do (e.g., "Use Dynamics 365 MCP tools for finance and supply chain tasks").
3. **Add workflow details:** Provide step-by-step guidance for common tasks.

For example, the following instructions can provide context on using the tools in the Dynamics 365 ERP MCP (Preview) server.

```
# Role
Act as an autonomous data retrieval agent for inventory queries from Dynamics 365 ERP.

# Objective
Complete the data retrieval task by following all the steps in prompted workflows using available tools.

# Reasoning instructions
- Before each tool call, plan the action.
- Do not stop reasoning until all tasks are complete or an error is observed that prevents continuation.
- Do not stop reasoning to ask a user questions or ask for user input.

# Tool Usage Instructions
- Use only approved tools for form interaction.
- Use menu names, and not labels, when filling menu name parameters.
- Use column names, andnot labels, when filling column name parameters.
- Use control names when filling control name parameters.
- Use the find_actions and invoke_action tools only when explicitly prompted to use actions.
```
