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

The [Model Context Protocol (MCP)](https://www.anthropic.com/news/model-context-protocol) is an open standard that facilitates the connection of AI agents to various data systems to enhance the relevance of agent responses. MCP standardizes how applications provide context to large language models (LLMs). Because it enables seamless integration between LLM applications and external data sources, the protocol is useful for building AI-powered tools and workflows. MCP defines a common language for how agents and applications interact with enterprise data and business logic. Instead of relying on custom APIs or point-to-point integrations, MCP provides a unified framework that standardizes access to ERP operations, ensuring consistency, context, and control. Standardization on the common protocol enables:

- Agent access to data and business logic in multiple apps
- Reuse of agents across enterprise resource planning (ERP) systems
- Access to tools in finance and operations apps from any compatible agent platform
- A simplified agent development experience
- Consistent data access, permissions, and auditability across all agent integrations

The **Dynamics 365 ERP MCP (Preview)** server provides a dynamic framework for agents to perform data operations and access the business logic of finance and operations apps. Developers can build agents that work with data and perform nearly any function that is available to a user through the application interface, without the need of custom code, connectors, or APIs. 

> [!IMPORTANT] This feature is a preview feature. It's subject to the [preview supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2105274). Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release, so that customers can get eary access and provide feedback. Learn more about preview releases in [One version service updates FAQ](../../dev-itpro/get-started/one-version.md).

## Prerequisites

Before you can use the Dynamics 365 ERP MCP (Preview) server, the following prerequisites must be met:

- The product version of finance and operations apps must be at least **10.0.2428.15**.
- The **(Preview) Dynamics 365 ERP Model Context Protocol server** feature must be enabled in [Feature Management](../../fin-ops/get-started/feature-management/feature-management-overview.md)

> [!NOTE] An earlier version of the MCP server, known as the "static Dynamics 365 ERP MCP" server, is also available in public preview. This server, built on the Dataverse connector framework, has 13 tools enabling specific business functions for Dynamics 365 Finance and Supply Chain Management. This static server will be **retired in the 2026 calendar year**. The server is still available in finance and operations apps environments with version 10.0.2263.17 and greater. However, it is recommended that you use the new dynamic Dynamics 365 ERP MCP server that is the subject of this documentation to avoid disruption when the static server is retired.

## Dynamic MCP tools
The tools in the MCP server work by enabling the agent to navigate server forms to complete tasks. The agent works with the application data and business logic through server APIs the same way a human would perform the task in the application client. Rather than having static tools for specific actions, like Find Approved Vendors or Release Purchase Requisition Lines, the agent uses the tools to open forms, set field values, and click actions available on the form. This interaction pattern unlocks millions of ERP functions across the Dynamics 365 ERP applications, which become instantly accessible through MCP. The agent works with the application like a human with the same security access would perform the actions.

### Dynamic context
The context provided to the agent through the MCP server is dynamically updated with each tool call based on the agent's security permissions and application configuration, extensions, and personalization. This ensures the agent is working with an accurate view of available actions and data for the given context, and ensures that any extensions or personalization in the environment is automatically available for agents to access through the MCP framework.

### Dynamics 365 ERP MCP tools
The following are the tools available in the Dynamics 365 ERP MCP (Preview) server. The agent orchestration uses these tools to translate natural language prompts into actions in the finance and operations apps environment.

| Tool name | Description | 
| --------- | ----------- |
| `click_control` | Click a control or a sub-element of a control on the form. Clicking on a sub-element of a control is done via the actionId parameter. |
| `close_form` | Close form |
| `filter_form` | Applies a filter on the form |
| `filter_grid` | Filter on a grid |
| `find_menu_item` | Find a menu item |
| `find_actions` | Finds actions available to invoke |
| `invoke_action` | Invokes an action |
| `open_lookup` | Open a lookup control on the form |
| `open_menu_item` | Opens menu item |
| `open_or_close_tab` | Open or close a tab on the form |
| `save_form` | Saves form |
| `select_grid_row` | Select a row in a grid |
| `set_control_value` | Set the value of a field |
| `sort_grid_column` | Sort a grid by a grid column |

### Using actions that invoke application code
While most of the tools in the MCP server work through server form interactions, the `find_actions` and `invoke_action` tools are exceptions to this pattern. These tools enable the agent to find and directly invoke classes in finance and operations apps code that have been enabled for use by agents. While working through form interactions makes millions of actions available to agents, there may be scenarios where the action or business logic isn't available through the application client or the agent needs direct access to the logic through code.

In these situations a developer can write a class in finance and operations apps code to make the business logic available through the MCP server. The class is created using the AI tool framework. Any classes created as AI tools that implement the `ICustomAPI` interface and have appropriate security defined for the associated menu action item will be available to find in the MCP server with the `find_actions` tool and invoke with the `invoke_action` tool. Classes that have been configured correctly to use the `ICustomAPI` interface as AI tools are displayed in the list on the **Synchronize Dataverse Custom APIs** (CustomApiTable) form.

See [Create AI tools with finance and operations business logic](copilot-ai-plugins.md) for more information on creating AI tools that expose business logic and actions in the Dynamics 365 ERP MCP server.

