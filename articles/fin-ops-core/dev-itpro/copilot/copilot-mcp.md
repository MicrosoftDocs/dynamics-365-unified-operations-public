---
title: Model Context Protocol for finance and operations apps
description: Use a Model Context Protocol server to create and extend agents for Dynamics 365 finance and operations apps
author: jaredha
ms.author: jaredha
ms.topic: overview
ms.date: 05/18/2024
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
audience: Application User
ms.search.region: Global
ms.search.form:
---

# Model Context Protocol for finance and operations apps

[!include [banner](../includes/banner.md)]

The [Model Context Protocol (MCP)](https://www.anthropic.com/news/model-context-protocol) is an open standard that facilitates the connection of AI agents to various data systems, enhanceing the relevance of their responses. It standardizes how applications provide context to lage language models (LLMs). MCP enables seamless integration between LLM applications and external data sources, making it useful for building AI-powered tools and workflows.

The **Dynamics 365 ERP MCP** server is now available, exposing tools for finance and operations apps to agent platforms that support the protocol. Standardizing on the common protocol enables:
- Agents accessing data and business logic in multiple apps
- Reuse of agents across ERP systems
- Access to tools in finance and operations apps from any compatible agent platform
- Simplified agent development experience

## Prerequisites
The following prerequisites must be configured to use the **Dynamics 365 ERP MCP** server.
- The product version of finance and operations apps must be a minimum of **10.0.2263.17**.
- The **Copilot in Microsoft Dynamics 365 Finance** solution must be a minimum version of **1.0.3049.1**.
- The **Copilot in Microsoft Dynamics 365 Supply Chain Management** solution must be a minimum version of **1.1.03046.2**.

## Dynamics 365 ERP MCP in Copilot Studio
You can create agents in Microsoft Copilot Studio using the **Dynamics 365 ERP MCP** server. The server provides tools for actions in Dynamics 365 Finance and Dynamics 365 Supply Chain Management. To add the tools to your agent:

1. Open your agent or create a new agent in [Copilot Studio](https://copilotstudio.microsoft.com).
2. On the **Tools** tab of the agent, select **Add a tool**.
3. On the **Add tool** dialog, select the **Model Context Protocol** filter and search for **Dynamics 365 ERP MCP**.
4. Create a connection to the server.
5. Select **Add to agent**.

With the **Dynamics 365 ERP MCP** server added, the agent then has access to the tools on the server, performing actions for the related Dynamics 365 finance and operations apps. You can view the list of available tools on the server by opening the **Dynamics 365 ERP MCP** server in the agent. 

