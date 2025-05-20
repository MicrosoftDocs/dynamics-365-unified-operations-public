---
title: Use Model Context Protocol for finance and operations apps
description: Learn how to use a Model Context Protocol (MCP) server to create and extend agents for Microsoft Dynamics 365 finance and operations apps.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 05/18/2024
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
audience: Application User
ms.search.region: Global
ms.search.form:
---

# Use Model Context Protocol for finance and operations apps

[!include [banner](../includes/banner.md)]

The [Model Context Protocol (MCP)](https://www.anthropic.com/news/model-context-protocol) is an open standard that facilitates the connection of AI agents to various data systems to enhance the relevance of agent responses. MCP standardizes how applications provide context to large language models (LLMs). Because it enables seamless integration between LLM applications and external data sources, the protocol is useful for building AI-powered tools and workflows.

The **Microsoft Dynamics 365 ERP MCP server** is now available. This server exposes tools for Dynamics 365 finance and operations apps to agent platforms that support MCP. Standardization on the common protocol enables the following capabilities:

- Agent access to data and business logic in multiple apps
- Reuse of agents across enterprise resource planning (ERP) systems
- Access to tools in finance and operations apps from any compatible agent platform
- A simplified agent development experience

## Prerequisites

Before you can use the Dynamics 365 ERP MCP server, the following prerequisites must be met:

- The product version of finance and operations apps must be at least **10.0.2263.17**.
- The version of the **Copilot in Microsoft Dynamics 365 Finance** solution must be at least **1.0.3049.1**.
- The version of the **Copilot in Microsoft Dynamics 365 Supply Chain Management** solution must be at least **1.1.03046.2**.

## Use the Dynamics 365 ERP MCP server in Copilot Studio

You can use the Dynamics 365 ERP MCP server to create agents in Microsoft Copilot Studio. The server provides tools for actions in Dynamics 365 Finance and Dynamics 365 Supply Chain Management.

To add the tools to your agent, follow these steps.

1. In [Copilot Studio](https://copilotstudio.microsoft.com), open an existing agent, or create a new one.
1. In the agent, on the **Tools** tab, select **Add a tool**.
1. In the **Add tool** dialog, select the **Model Context Protocol** filter, and search for **Dynamics 365 ERP MCP**.
1. Create a connection to the server.
1. Select **Add to agent**.

After the Dynamics 365 ERP MCP server is added, the agent has access to the tools on it and can use them to perform actions for the related finance and operations apps. To view the list of available tools on the server, open the Dynamics 365 ERP MCP server in the agent.
