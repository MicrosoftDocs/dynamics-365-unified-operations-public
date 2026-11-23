---
title: Dynamics 365 ERP in Work IQ (preview)
description: Learn how Dynamics 365 ERP in Work IQ brings finance and operations apps data, business logic, and business skills to Copilot and agents, and how to enable it.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 11/17/2026
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: twheeloc
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Dynamics 365 ERP in Work IQ (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Dynamics 365 ERP in Work IQ brings the data, business logic, and business skills of Dynamics 365 finance and operations apps into Work IQ, the intelligence layer for Microsoft Copilot and agents. Work IQ connects how people work, across their email, meetings, chats, and documents, with how the business operates. With Dynamics 365 ERP in Work IQ, finance and operations apps data sits alongside Microsoft 365 productivity data and other business applications in Work IQ. Copilot and agents can answer questions from ERP data and complete governed ERP tasks, so users can get work done without leaving the flow of work.

Dynamics 365 ERP in Work IQ extends [Business Applications in Work IQ](/power-apps/maker/data-platform/business-applications-work-iq) to finance and operations apps.

> [!IMPORTANT]
> This is a preview feature. Preview features aren't meant for production use and might have restricted functionality. These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2216214), and are available before an official release so customers can get early access and provide feedback.

## Capabilities

Dynamics 365 ERP in Work IQ includes two capabilities.

| Capability | Description |
| --- | --- |
| **ERP data in Ask** | Users and agents can ask questions about finance and operations apps data in natural language. A semantic model covers the most commonly used finance and operations data entities, and semantic indexing helps Work IQ find relevant data quickly and return accurate answers. Because ERP data is available in Work IQ alongside Microsoft 365 data and data from other business applications, a single question can draw on ERP records, email, meetings, and documents at the same time. ERP data in Ask is read-only. |
| **Dynamics 365 ERP MCP in Work IQ** | The [Dynamics 365 ERP MCP server](copilot-mcp.md) is available through the Work IQ MCP server. Agents can work with nearly all the data and business logic in finance and operations apps that's available to the signed-in user. Agents can do more than report on ERP data. They can update records and complete business processes in finance and operations apps, and run workflows that span finance and operations apps and Microsoft 365 apps such as Outlook and Teams. |

### Business skills

Both capabilities work with business skills. A business skill is a reusable set of instructions that tells an agent how your organization completes a specific task, such as which steps to follow, which policies and approvals apply, and which ERP data and actions to use. Business skills help agents complete tasks consistently and in line with your organization's processes, policies, and procedures.

Business skills are available in any agent experience that connects to Work IQ or to the Dynamics 365 ERP MCP server, so users get the same guidance and consistent results wherever they work. For more information, see [Business skills for Dynamics 365 ERP](mcp/erp-business-skills.md).

### Example scenario

A buyer needs to know which purchase orders recent supplier updates affect. Without Work IQ, the buyer reads supplier emails in Outlook, looks up each purchase order in Dynamics 365 finance and operations apps, updates the delivery dates, and then notifies the planners who depend on those orders.

With Dynamics 365 ERP in Work IQ, the buyer asks an agent which purchase orders changed. The agent reads the supplier emails, identifies the affected purchase orders, and updates the delivery dates after the buyer approves the changes. The agent then lets the affected planners know about the new dates. A business skill tells the agent how your organization handles supplier delays, including who approves a change and who needs to be notified.

#### Security and governance

Dynamics 365 ERP in Work IQ uses the security controls that already protect your finance and operations apps data:

- **User context:** Work IQ and finance and operations apps share the same Microsoft Entra ID identity foundation. Copilot and agents access finance and operations apps on behalf of the signed-in user. The user's security roles, duties, privileges, and data security policies apply to every request, and the agent can't do more than the user can do in the finance and operations apps client. For more information, see [Security for Dynamics 365 ERP MCP](mcp/mcp-security.md).
- **Client control:** Administrators decide whether Work IQ can connect to the Dynamics 365 ERP MCP server in each environment. For more information, see [Step 2: Allow the Work IQ client to access the Dynamics 365 ERP MCP server](#step-2-allow-the-work-iq-client-to-access-the-dynamics-365-erp-mcp-server).
- **Business skill governance:** Administrators control who can create and modify business skills, which security roles can use a custom skill, and which legal entities it applies to. For more information, see [Share a business skill](mcp/erp-business-skills.md#share-a-business-skill).

Availability and use of Dynamics 365 ERP in Work IQ are subject to administrator configuration, licensing, and organizational policies.

## Enable Dynamics 365 ERP in Work IQ

### Prerequisites

Before you enable Dynamics 365 ERP in Work IQ, make sure that you meet the following prerequisites:

- Your finance and operations apps environment meets the [prerequisites for the Dynamics 365 ERP MCP server](copilot-mcp.md#prerequisites).
- Users have the security roles in finance and operations apps that they need for the data and tasks that they work with.
- To use business skills, the **Business skills (preview)** feature is enabled. For more information, see [Business skills prerequisites](mcp/erp-business-skills.md#prerequisites).

### Step 1: Set up Business Applications in Work IQ

Complete all the setup steps in [Quickstart: Set up Business Applications in Work IQ](/power-platform/admin/business-applications-work-iq/quickstart?toc=/power-platform/business-applications-work-iq). These steps make Business Applications in Work IQ available to your users in Microsoft Copilot and turn on Work IQ for your environment.

### Step 2: Allow the Work IQ client to access the Dynamics 365 ERP MCP server

The **Allowed MCP clients** page controls which client applications can connect to the Dynamics 365 ERP MCP server in your environment.

Work IQ connects to your environment through the **DORS Work IQ (preview)** client. When you set **Allowed** to `true` for this client, Work IQ can connect to the Dynamics 365 ERP MCP server on behalf of signed-in users. This connection makes the data, business logic, and business skills of finance and operations apps available to Copilot and agents through Work IQ. Allowing the client doesn't give users additional permissions. Every request runs in the context of the signed-in user and their security roles in finance and operations apps.

To allow the Work IQ client, follow these steps.

1. In finance and operations apps, use the search bar to find and open the **Allowed MCP clients** page.
1. Select the row where **Name** is **DORS Work IQ (preview)** and **ClientId** is `300e430c-5476-4a1d-b223-35194efd4e57`. If the client isn't in the list, select **New**, and then enter the name and client ID.
1. Select **Edit**, and then set **Allowed** to `true`.
1. Select **Save**.

> [!NOTE]
> Changes to the allowed MCP clients can take up to one minute to take effect.

For more information, see [Allowed MCP clients](mcp/mcp-security.md#allowed-mcp-clients).

## Where you can use Dynamics 365 ERP in Work IQ

The following table describes which capabilities are available in each client surface and how to configure each one.

| Client surface | ERP data in Ask | Dynamics 365 ERP MCP in Work IQ | Configuration |
| --- | --- | --- | --- |
| Microsoft Copilot Studio | Supported | Supported | Add the Work IQ MCP server as a tool in the agent. Learn more in [Work IQ in Copilot Studio](/microsoft-copilot-studio/agents-experience/add-work-iq). |
| GitHub Copilot in Visual Studio Code | Supported | Supported | Configure a remote connection to the Work IQ MCP server. Learn more in [Work IQ MCP overview](/microsoft-365/copilot/extensibility/work-iq/mcp/overview). |
| Third-party MCP clients, such as Claude | Supported | Supported | Configure a remote connection to the Work IQ MCP server. Learn more in [Work IQ MCP overview](/microsoft-365/copilot/extensibility/work-iq/mcp/overview). |
| Microsoft Copilot Chat | Supported | Not supported | Enable Work IQ in Copilot Chat. Learn more in [Set up Business Applications in Work IQ](/power-platform/admin/business-applications-work-iq/quickstart). |
| Copilot Cowork | Supported | Supported | Enable Work IQ in Copilot Cowork. Learn more in [Use the Business Applications in Work IQ plugin in Cowork](/microsoft-365/copilot/cowork/cowork-work-iq). |

> [!TIP]
> To update records and complete business processes in finance and operations apps from Copilot Cowork, use the Dynamics 365 ERP apps plugin for Copilot Cowork. For more information, see [Enable the Dynamics 365 ERP apps plugin for Copilot Cowork](enable-copilot-cowork-erp.md).

## Related information

- [Business Applications in Work IQ](/power-apps/maker/data-platform/business-applications-work-iq)
- [Work IQ MCP overview](/microsoft-365/copilot/extensibility/work-iq/mcp/overview)
- [Use Model Context Protocol for finance and operations apps](copilot-mcp.md)
- [Business skills for Dynamics 365 ERP](mcp/erp-business-skills.md)
- [Enable the Dynamics 365 ERP apps plugin for Copilot Cowork](enable-copilot-cowork-erp.md)
