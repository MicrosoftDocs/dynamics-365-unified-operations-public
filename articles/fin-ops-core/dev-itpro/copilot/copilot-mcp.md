---
title: Use Model Context Protocol for finance and operations apps
description: Learn how to use a Model Context Protocol (MCP) server to create and extend agents for Microsoft Dynamics 365 finance and operations apps.
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

# Use Model Context Protocol for finance and operations apps (preview)

[!include [banner](../includes/banner.md)]

The [Model Context Protocol (MCP)](https://www.anthropic.com/news/model-context-protocol) is an open standard that facilitates the connection of AI agents to various data systems to enhance the relevance of agent responses. MCP standardizes how applications provide context to large language models (LLMs). Because it enables seamless integration between LLM applications and external data sources, the protocol is useful for building AI-powered tools and workflows. MCP defines a common language for how agents and applications interact with enterprise data and business logic. Instead of relying on custom APIs or pont-to-point integrations, MCP provides a unified framework that standardizes access to ERP operations, ensuring consistency, context, and control. Standardization on the common protocol enables:

- Agent access to data and business logic in multiple apps
- Reuse of agents across enterprise resource planning (ERP) systems
- Access to tools in finance and operations apps from any compatible agent platform
- A simplified agent development experience
- Consistent data access, permissions, and auditability across all agent integrations

## Prerequisites

Before you can use the Dynamics 365 ERP MCP (Preview) server, the following prerequisites must be met:

- The product version of finance and operations apps must be at least **10.0.2428.15**.
- The **(Preview) Dynamics 365 ERP Model Context Protocol server** feature must be enabled in [Feature Management](../../fin-ops/get-started/feature-management/feature-management-overview.md)

> [!NOTE] An earlier version of the MCP server, known as the "static Dynamics 365 ERP MCP" server, is also available in public preview. This server, built on the Dataverse connector framework, has 13 tools enabling specific business functions for Dynamics 365 Finance and Supply Chain Management. This static server will be **retired in the 2026 calendar year**. The server is still available in finance and operations apps environments with version 10.0.2263.17 and greater. However, it is recommended that you use the new dynamic Dynamics 365 ERP MCP server that is the subject of this documentation to avoid disruption when the static server is retired.

## Use the Dynamics 365 ERP MCP server in Copilot Studio
You can use the Dynamics 365 ERP MCP server to create agents in Microsoft Copilot Studio. The server provides tools for actions in Dynamics 365 Finance and Dynamics 365 Supply Chain Management.

To add the tools to your agent, follow these steps.

1. In [Copilot Studio](https://copilotstudio.microsoft.com), open an existing agent, or create a new one.
1. In the agent, on the **Tools** tab, select **Add a tool**.
1. In the **Add tool** dialog, select the **Model Context Protocol** filter, and search for **Dynamics 365 ERP MCP**.
1. Create a connection to the server.
1. Select **Add to agent**.

After the Dynamics 365 ERP MCP server is added, the agent has access to the tools on it and can use them to perform actions for the related finance and operations apps. To view the list of available tools on the server, open the Dynamics 365 ERP MCP server in the agent.

## Dynamic MCP tools
The tools in the Dynamics 365 ERP MCP server provide a dynamic framework, enabling developers to build agents that can work with data and perform nearly any function that is available to users in the application interface, without the need of custom code, connectors, or APIs. The tools in the MCP server work by enabling the agent to navigate server forms to complete tasks. The agent works with the application data and business logic through server APIs the same way a human would perform the task in the application client. Rather than having static tools for specific actions, like Find Approved Vendors or Release Purchase Requisition Lines, the agent uses the tools to open forms, set field values, and click actions available on the form. This interaction pattern unlocks millions of ERP functions across the Dynamics 365 ERP applications, which become instantly accessible through MCP. 

### Dynamic context
The context provided to the agent through the MCP server is dynamically updated with each tool call based on the agent's security permissions and application configuration, extensions, and personalization. This ensures the agent is working with an accurate view of available actions and data for the given context, and ensures that any extensions or personalization in the environment is automatically available for agents to access through the MCP framework.

### Dynamics 365 ERP MCP tools
The following are the tools available in the Dynamics 365 ERP MCP (Preview) server. The agent orchestration uses these tools to translate natural language prompts into actions in the finance and operations apps environment.

