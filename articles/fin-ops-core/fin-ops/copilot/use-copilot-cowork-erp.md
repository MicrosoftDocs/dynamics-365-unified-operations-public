---
title: Use Copilot Cowork with Dynamics 365 ERP
description: Learn about how to use Microsoft Copilot Cowork with the Microsoft Dynamics 365 ERP apps plugin to orchestrate business workflows across ERP, email, and collaboration tools.
author: anupams
ms.author: anupams
ms.reviewer: johnmichalak
ms.topic: how-to
ms.date: 10/27/2026
ms.update-cycle: 180-days
ms.custom: bap-template
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Use Copilot Cowork with Dynamics 365 ERP

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to use Microsoft Copilot Cowork with the Microsoft Dynamics 365 ERP apps plugin to interact with finance and operations apps data and orchestrate business workflows.

Copilot Cowork is an agentic orchestrator that helps you accomplish complex business tasks by combining multiple data sources. When you use the Dynamics 365 ERP apps plugin, Copilot Cowork connects to your finance and operations apps environment through the [Dynamics 365 ERP MCP server](../../dev-itpro/copilot/copilot-mcp.md). You can work with ERP data alongside email, documents, and other Microsoft 365 services in a single conversational experience.

Learn more about how Copilot Cowork works in [Copilot Cowork overview](/microsoft-365/copilot/cowork/).

## Prerequisites

Before you can use Copilot Cowork with Dynamics 365 ERP, ensure that:

- You have Microsoft 365 Copilot and Copilot Cowork access.
- Usage-based billing and Copilot Credits are configured for you.
- You have a qualifying Dynamics 365 license for finance and operations apps.
- You have access to a supported cloud finance and operations apps environment and have the appropriate finance and operations apps security roles.
- The Dynamics 365 ERP apps plugin is installed and its **Finance & Operations** connector is configured.

Learn more about licensing, environment requirements, and plugin setup in [Enable the Dynamics 365 ERP apps plugin for Copilot Cowork](../../dev-itpro/copilot/enable-copilot-cowork-erp.md).

## Connect to your finance and operations apps environment

When you first use the Dynamics 365 ERP apps plugin in Copilot Cowork, you need to connect to your finance and operations apps environment.

To connect to your finance and operations apps environment, follow these steps:

1. Open [Copilot Cowork](https://m365.cloud.microsoft).
1. Open the **Sources & Skills** panel, and ensure that the **Dynamics 365 ERP apps** plugin is enabled. Learn more about managing plugins in [Use plugins with Copilot Cowork](/microsoft-365/copilot/cowork/cowork-plugins).
1. Find the **Finance & Operations** connector, and then select **Configure**.
1. Select your compatible finance and operations apps environment.
1. Complete the sign-in or consent flow.

After you connect, Copilot Cowork communicates with the MCP server on your finance and operations apps environment and makes the available tools accessible.

> [!NOTE]
> You only need to connect once. After the initial connection, Copilot Cowork remembers your authorization unless you or your administrator revoke it. The connector provides **Connect**, **Retry**, and **Disconnect** options as appropriate for its current state.

## How to use Copilot Cowork with Dynamics 365 ERP

The Dynamics 365 ERP apps plugin uses the dynamic [Dynamics 365 ERP MCP server](../../dev-itpro/copilot/copilot-mcp.md). The server discovers available tools at runtime based on the product version, environment configuration, extensions, personalization, and your finance and operations apps security permissions. It provides three categories of tools:

- **Data tools** &ndash; Read, create, update, and delete records in finance and operations apps data entities.
- **Form tools** &ndash; Navigate application pages, set field values, select actions, and perform operations just as you would in the application.
- **Action tools** &ndash; Invoke secured business logic that developers explicitly expose through the MCP server.

In addition, Copilot Cowork combines these ERP capabilities with its built-in **Work IQ** features (email, calendar, documents, spreadsheets) to orchestrate workflows that span multiple systems.

Data tools are the most efficient option for standard create, read, update, and delete operations. Form tools are used for business operations that aren't available through data entities. Action tools invoke business logic that developers expose through the finance and operations apps AI tool framework.

## Example scenarios

The following examples illustrate how Copilot Cowork can help with common finance and operations apps tasks.

### Look up ERP data

Ask Copilot Cowork natural language questions about your finance and operations apps data.

**Example prompts:**

- *"What is the credit limit for customer US-001 in USMF?"*
- *"Show me all open purchase orders for vendor 1001."*
- *"What are the depreciation profiles available in the system?"*

Copilot Cowork uses the data tools to find the relevant entities, retrieve the data, and present it in a structured format.

### Perform operations on forms

Ask Copilot Cowork to perform operations that you normally do through the application interface.

**Example prompts:**

- *"Open the All customers list in USMF and find the phone number for customer US-003."*
- *"Create a new vendor invoice journal entry for 500 USD."*

Copilot Cowork uses the form tools to go to the right page, interact with controls, and complete the requested operation.

### Orchestrate cross-application workflows

Copilot Cowork can combine ERP data with email and document capabilities to enable end-to-end business workflows.

**Example: Bid evaluation for an RFQ**

A sourcing manager can give Copilot Cowork a single prompt such as:

> *"Evaluate bids for RFQ 000012. Use the latest vendor emails and PDF attachments to extract bid details, update the RFQ replies in finance and operations apps, score the bids using the configured scoring criteria, and recommend the supplier to award. Provide the recommendation in an interactive document. After my approval, create the purchase order and draft the bid award email."*

In this scenario, Copilot Cowork:

1. Retrieves the RFQ data (lines, vendors, scoring criteria) from Dynamics 365 through the MCP server.
1. Reads vendor bid emails and PDF attachments from Outlook (Work IQ).
1. Extracts and cross-references bid details, flagging discrepancies.
1. Scores responses against the configured ERP criteria.
1. Generates a recommendation document with ranked vendors, strengths, and risks.
1. On approval, creates the purchase order in Dynamics 365 and drafts an award email in Outlook.

> [!IMPORTANT]
> Copilot Cowork asks for approval before it takes actions on your behalf. ERP changes, such as updating bid records or creating purchase orders, are performed through the Finance & Operations connector. Email and document operations are performed through Cowork and Work IQ. Review the proposed action before you approve it. In a conversation, you can select **Always allow** to skip subsequent approval prompts for similar actions in that conversation.

## Tips for effective prompts

To get the best results from Copilot Cowork with the Dynamics 365 ERP apps plugin, consider the following tips:

- **Be specific about the company.** If your environment has multiple legal entities, specify the company in your prompt (for example, *"in USMF"* or *"in company DEMF"*).
- **Use business terms.** Copilot Cowork understands finance and operations apps terminology. Use terms like *"purchase order,"* *"vendor invoice,"* *"customer credit limit,"* and *"sales order"* as you would in the application.
- **Break complex tasks into steps.** For multistep workflows, you can either give Copilot Cowork a comprehensive prompt or guide it step by step. Copilot Cowork asks for clarification when needed.
- **Review before approving write operations.** Copilot Cowork shows you what it plans to do before taking an action. Review the details carefully before you approve, or cancel the action if the details aren't correct.

## Data security and privacy

- **User-level permissions.** The MCP server dynamically filters entities, menu items, forms, fields, actions, and business data based on the authenticated user's finance and operations apps security roles. Users can't access data or operations through Copilot Cowork that they can't access through the application.
- **Action approval.** Copilot Cowork requests approval before it performs an action on your behalf. You can approve, cancel, or pause the work. An **Always allow** selection applies only to similar actions in the current conversation.

## Licensing and billing

Each user needs an active Microsoft 365 Copilot license and a qualifying Dynamics 365 license for finance and operations apps. Configure usage-based billing and Copilot Credits. Calls to the Dynamics 365 ERP MCP server can consume Copilot Credits according to the current MCP licensing rules, with applicable exemptions for qualifying premium licenses. Learn more in [Licensing](../../dev-itpro/copilot/copilot-mcp.md#licensing).

## Limitations

- The Dynamics 365 ERP apps plugin requires the dynamic Dynamics 365 ERP MCP server and finance and operations apps version 10.0.47, 10.0.46 PQU-2, or 10.0.45 PQU-7 or later.
- The environment must be Tier 2 or above or a Unified Developer Environment. Cloud-hosted environments and on-premises environments aren't supported.
- Some complex form interactions might require multiple tool calls and can take longer than simple data lookups.
- Form tabs are closed by default, and some lookups require a separate interaction.
- Some controls and system administration forms aren't available through the MCP server.
- MCP guidance is provided in US English. Dates, times, and numeric values use ISO formats and don't consider the user's locale.
- The plugin is currently available in regions where Copilot Cowork is deployed. Learn more about the latest availability in [Explore Copilot products by geography and languages](https://releaseplans.microsoft.com/availability-reports/?report=copilotproductreport).

For the complete list, see [Known limitations for the Dynamics 365 ERP MCP server](../../dev-itpro/copilot/copilot-mcp.md#known-limitations).

## Related information

- [Enable the Dynamics 365 ERP apps plugin for Copilot Cowork](../../dev-itpro/copilot/enable-copilot-cowork-erp.md)
- [Use Model Context Protocol for finance and operations apps](../../dev-itpro/copilot/copilot-mcp.md)
- [Create AI tools with finance and operations business logic](../../dev-itpro/copilot/copilot-ai-plugins.md)
- [Overview of Copilot capabilities in finance and operations apps](copilot-for-finance-operations.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
