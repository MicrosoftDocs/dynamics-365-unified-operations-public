---
title: Use Model Context Protocol for finance and operations apps
description: Learn how to use a Model Context Protocol (MCP) server to create and extend agents for Microsoft Dynamics 365 finance and operations apps.
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

# Use Model Context Protocol for finance and operations apps

[!include [banner](../includes/banner.md)]

The [Model Context Protocol (MCP)](https://www.anthropic.com/news/model-context-protocol) is an open standard that connects AI agents to various data systems to enhance the relevance of agent responses. MCP standardizes how applications provide context to large language models (LLMs). Because it enables seamless integration between LLM applications and external data sources, the protocol is useful for building AI-powered tools and workflows. MCP defines a common language for how agents and applications interact with enterprise data and business logic. Instead of relying on custom APIs or point-to-point integrations, MCP provides a unified framework that standardizes access to ERP operations, ensuring consistency, context, and control. Standardization on the common protocol enables:

- Agent access to data and business logic in multiple apps
- Reuse of agents across enterprise resource planning (ERP) systems
- Access to tools in finance and operations apps from any compatible agent platform
- A simplified agent development experience
- Consistent data access, permissions, and auditability across all agent integrations

The **Dynamics 365 ERP MCP** server provides a dynamic framework for agents to perform data operations and access the business logic of finance and operations apps. Developers can build agents that work with data and perform nearly any function that's available to a user through the application interface, without the need for custom code, connectors, or APIs.

## Prerequisites

Before you can use the Dynamics 365 ERP MCP server, you must meet the following prerequisites:

- The product version of finance and operations apps must be at least:
  - 10.0.45 PQU-6
  - 10.0.46 PQU-1
  - 10.0.47
- The **Dynamics 365 ERP Model Context Protocol server** feature must be enabled in [Feature Management](../../fin-ops/get-started/feature-management/feature-management-overview.md).
- The agent platform on which you're building your agent must be allowed in the **Allowed MCP Clients** form. Learn more in [Allowed MCP clients](copilot-mcp.md#allowed-mcp-clients).
- Your environment is Tier 2 or above, or a Unified Developer Environment. The MCP server isn't supported on Cloud Hosted Environments (CHE).

> [!NOTE]
> An earlier version of the MCP server, known as the "static Dynamics 365 ERP MCP" server, built on the Dataverse connector framework, has 13 tools enabling specific business functions for Dynamics 365 Finance and Supply Chain Management. This static server will be **retired in the 2026 calendar year**. The server is still available in finance and operations apps environments with version 10.0.2263.17 and greater. However, to avoid disruption when the static server is retired, use the new dynamic Dynamics 365 ERP MCP server that is the subject of this documentation.

## Dynamic MCP tools
The Dynamics 365 ERP MCP server has three categories of tools for working with the data and business logic of finance and operations apps: 
- **Data tools:** These tools enable the agent to perform standard data operations to create, read, update, and delete data in your finance and operations apps environment.
- **Form tools:** Enable the agent to work perform operations that are available on forms in the application. 
- **Action tools:** Enable the agent to find and directly invoke classes in finance and operations apps code.

### Data tools
Data tools in the MCP server enable the agent to work with application data through data entities. The agent can use these tools to perform Create, Read, Update, Delete (CRUD) operations with the application data in your environment.

Working with data through data entities is more efficient for standard CRUD operations, providing better performance and fewer tool calls to perform the operations than using the form tools described below. If you find that your agent is using form tools for operations that could be performed more optimally through data tools, you may improve performance for the agent by adding guidance in your agent instructions on which tools the agent should use for your scenarios. The agent orchestration should then use these tools to translate the natural language prompts in the agent into data operations performed in the finance and operations apps environment.

The following data tools are available in the Dynamics 365 ERP MCP server.

| Tool name | Description |
| --------- | ----------- |
| `data_find_entity_type` | Find OData entity types. This is needed for calling the data_get_entity_metadata tool. The tool returns multiple top hits that may be related to your query. You decide which one matches your search. |
| `data_get_entity_metadata` | Get metadata for an entity. This metadata is needed for calling the `data_find_entities`, `data_create_entities`, `data_update_entities`, `data_delete_entities` tools. |
| `data_create_entities` | Create data records using OData. Deep inserts are not supported for create. |
| `data_delete_entities` | Delete data records using OData. | 
| `data_update_entities` | Update data records using OData. | 
| `data_find_entities` | Find or read data records using OData. |


### Form tools
The form tools in the MCP server enable the agent to navigate server forms to complete tasks. The agent works with the application data and business logic through server APIs the same way a human would perform the task in the application client. Rather than having static tools for specific actions, like Find Approved Vendors or Release Purchase Requisition Lines, the agent uses the tools to open forms, set field values, and select actions available on the form. 

Although form tools are conceptually similar to Computer Use Agents (CUA), the tools do not work directly with the application client. Rather than opening a client session for the agent interaction, the tools work through server APIs that provide the agent with the application view model as context, enabling more optimized agent interactions.

Form tools are optimal for enabling agents to perform operations that are available in the application that are not standard Create, Read, Update, Delete (CRUD) operations. For example, actions in the application performed by clicking buttons that execute business logic through code are available to agents through these tools, or retrieving record values that are calculated at runtime in the application. With these tools the agent works with the application like a human with the same security access would perform the actions.

The following form tools are available in the Dynamics 365 ERP MCP server.

| Tool name | Description |
| --------- | ----------- |
| `form_click_control` | Select a control or a subelement of a control on the form. Clicking on a subelement of a control is done through the actionId parameter. |
| `form_close_form` | Close form |
| `form_filter_form` | Applies a filter on the form |
| `form_filter_grid` | Filter on a grid |
| `form_find_controls` | Find controls on the form. Use this tool if you do not see the required controls in the form state after opening it, suspect that the control must be on one of the closed tabs, but not sure which one. This tool accepts only one search term per call - to find multiple different controls, call this multiple times with different search terms. |
| `form_find_menu_item` | Find a menu item |
| `form_open_lookup` | Open a lookup control on the form |
| `form_open_menu_item` | Opens menu item |
| `form_open_or_close_tab` | Open or close a tab on the form |
| `form_save_form` | Saves form |
| `form_select_grid_row` | Select a row in a grid |
| `form_set_control_values` | Set values on one or more form controls. Note that this should not be used to set values for form controls that require lookup. Use the form_open_lookup for those controls. |
| `form_sort_grid_column` | Sort a grid by a grid column |

### Action tools
Action tools enable the agent to find and directly invoke classes in finance and operations apps code that are enabled for use by agents. While working through data entities and form interactions makes millions of actions available to agents, there might be scenarios where the action or business logic isn't available through the entities or application client, or the agent needs direct access to the logic through code.

In these situations, a developer can write a class in finance and operations apps code to make the business logic available through the MCP server. The developer creates the class by using the AI tool framework. Any classes created as AI tools that implement the `ICustomAPI` interface and have appropriate security defined for the associated menu action item are available to find in the MCP server with the `api_find_actions` tool and invoke with the `api_invoke_action` tool. Classes that are configured correctly to use the `ICustomAPI` interface as AI tools are displayed in the list on the **Synchronize Dataverse Custom APIs** (CustomApiTable) form.

For more information on creating AI tools that expose business logic and actions in the Dynamics 365 ERP MCP server, see [Create AI tools with finance and operations business logic](copilot-ai-plugins.md).

The following action tools are available in the Dynamics 365 ERP MCP server.

| Tool name | Description |
| --------- | ----------- |
| `api_find_actions` | Finds actions available to invoke |
| `api_invoke_action` | Invokes an action |

## Dynamic context

The MCP server dynamically updates the context it provides to the agent with each tool call based on the agent's security permissions and application configuration, extensions, and personalization. This approach ensures the agent works with an accurate view of available actions and data for the given context, and ensures that any extensions or personalization in the environment are automatically available for agents to access through the MCP framework.

When the tools respond to the agent, they return the application view model to the agent orchestration. This view model is the same one presented to the application to be rendered for a user in the client. The security role of the authenticated user for the agent determines which objects are returned in the view model. For example, if the agent is assigned to a Purchasing Agent security role in finance and operations apps, then it only has access to the objects assigned to the duties and privileges for that security role.

For example, when the agent calls the `form_find_menu_item` tool, it returns only menu items to which that security role has access. When the view model for a form is returned to the agent, it includes only data, fields, and actions to which the user role has access. The system rejects any explicit calls to actions or objects to which the user role doesn't have access.

Similarly, the entities returned in the response to the `data_find_entity_type` tool and APIs returned in the response to the `api_find_actions` tool will only include objects to which the security role for the user context has access.

Limiting the menu items, entities, and APIs with roles is important for limiting the scope of the agent. It's also a way to improve agent orchestration by limiting the context the agent needs to orchestrate over to find the right form, data, or actions.

## Allowed MCP clients
When you enable the Dynamics 365 ERP MCP server in your environment, you decide which agent platforms can access the server. By default, only the following two platforms can access the MCP server:

| Platform | Client ID |
| -------- | --------- |
| Microsoft Copilot Studio | 7ab7862c-4c57-491e-8a45-d52a7e023983 |
| Visual Studio Code | aebc6443-996d-45c2-90f0-388ff96faa56 |

You must grant access to any other agent platforms that need to access the MCP server. To add new agent platforms, you need to:

1. Register the application in Microsoft Entra ID. For more information, see [Register an application in Microsoft Entra ID](/entra/identity-platform/quickstart-register-app).
1. Add the registered client ID value in the **Allowed MCP clients** form, setting the **Allowed** property to `true`.

## Known limitations

The current implementation of the Dynamics 365 ERP MCP server has the following limitations:

1. **Language:** The MCP server supports only US English (en-us). If the authenticated user of the agent specifies a different locale, the form labels and values returned in the tool context appear in that locale. However, the MCP responses always provide metadata and guidance in English.
1. **Dates:** Dates, times, and numerics use ISO format. They don't consider user locale. 
1. **Control limitations:** Agents can't interact with some controls, such as calendar controls, organization chart controls, list view, availability view, HTML editor, image, radio button, and time edit. Custom controls aren't supported.
1. **Available menu items:** The `find_menu_item` tool returns display and action menu items filtered by items in the left-side navigation pane and items that a user role can access.
1. **Form tabs:** Form tabs are closed by default. Agents must open form tabs to interact with the data and controls under the form tab.
1. **Output menu items:** The MCP server doesn't support output menu items that generate and display reports or print results.
1. **Attachments:** The MCP server doesn't support attachments, including the document viewer DocuUpload, and FileUpload controls.
1. **System admin forms:** The MCP server doesn't provide access to some forms related to system admin tasks, like feature management, user management, and managing security. The following forms are excluded:
   
   | Category | Form label | Form name |
   | -------- | --------- | ---------- |
   | Security | Security configuration | SysSecConfiguration |
   | Security | User role assignment | SysSecUserAddRoles | 
   | Security | Separation of duties config | SysSecSegrationOfDuties |
   | Security | Temporary roles | <ul><li>UserSecGovTemporaryRole</li><li>UserSecGovTemporaryRoleAddRoles</li><li>UserSecGovTemporaryRoleAssignOrg</li><li>UserSecGovTemporaryRoleUser</li></ul> |
   | Security | Privileged access control | <ul><li>UserSecGovPrivilegedUserManagement</li><li>UserSec</li></ul> |
   | User setup | Users | SysUserInfoPage |
   | User setup | User groups | SysUserGroupInfo |
   | Integrations | Microsoft Entra ID applications | SysAADClientTable |
   | Features | Feature Management | FeatureManagementWorkspace |

1. **Advanced filters:** The MCP server doesn't support advanced filters on grids. For example, it doesn't support the "before," "after," and "between" operators for date columns. It supports only the "matches" operator for filtering.
2. **Environment downtime:** The MCP server will be unavailable during environment downtime, such as servicing windows. Any MCP requests made by agents during these servicing windows will fail.
