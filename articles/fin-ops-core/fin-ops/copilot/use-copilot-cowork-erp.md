---
title: Use Copilot Cowork with Dynamics 365 ERP
description: Learn about how to use Microsoft 365 Copilot Cowork with the Microsoft Dynamics 365 ERP apps plugin to orchestrate business workflows across ERP, email, and collaboration tools.
author: anupams
ms.author: anupams
ms.reviewer: johnmichalak
ms.topic: how-to
ms.date: 05/07/2026
ms.update-cycle: 180-days
ms.custom: bap-template
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Use Copilot Cowork with Dynamics 365 ERP

[!include [banner](../includes/banner.md)]

This article explains how to use Microsoft 365 Copilot Cowork with the Microsoft Dynamics 365 ERP apps plugin to interact with finance and operations data and orchestrate business workflows.

Copilot Cowork is an agentic orchestrator that helps you accomplish complex business tasks by combining multiple data sources. When you use the Dynamics 365 ERP apps plugin, Copilot Cowork connects to your finance and operations environment through the [Dynamics 365 ERP MCP server](../../dev-itpro/copilot/copilot-mcp.md). You can work with ERP data alongside email, documents, and other Microsoft 365 services in a single conversational experience.

Learn more about how Copilot Cowork works in [Copilot Cowork overview](/microsoft-365/copilot/cowork/).

## Prerequisites

Before you can use Copilot Cowork with Dynamics 365 ERP, an administrator must enable the plugin for your organization. Learn more about how to set up the plugin in [Enable the Dynamics 365 ERP apps plugin for Copilot Cowork](../../dev-itpro/copilot/enable-copilot-cowork-erp.md).

## Connect to your finance and operations environment

When you first use the Dynamics 365 ERP apps plugin in Copilot Cowork, you need to connect to your finance and operations environment.

To connect to your finance and operations environment, follow these steps:

1. Open [Copilot Cowork](https://m365.cloud.microsoft).
1. Ensure the **Dynamics 365 ERP Apps** plugin is enabled. Learn more about managing plugins in [Use plugins with Copilot Cowork](/microsoft-365/copilot/cowork/cowork-plugins).
1. If a connection isn't established, when you start a conversation that involves ERP data, Copilot Cowork prompts you to connect to your finance and operations environment. Follow the sign-in or consent flow to authorize access.

After you connect, Copilot Cowork communicates with the MCP server on your finance and operations environment and makes the available tools accessible.

> [!NOTE]
> You only need to connect once. After the initial connection, Copilot Cowork remembers your authorization unless you or your administrator revoke it.

## How to use Copilot Cowork with Dynamics 365 ERP

The Dynamics 365 ERP apps plugin gives Copilot Cowork access to three categories of tools from the [Dynamics 365 ERP MCP server](../../dev-itpro/copilot/copilot-mcp.md):

- **Data tools** &ndash; Read, create, update, and delete records in finance and operations data entities.
- **Form tools** &ndash; Navigate application pages, set field values, select actions, and perform operations just as you would in the application.
- **Action tools** &ndash; Invoke custom business logic that developers expose through the MCP server.

In addition, Copilot Cowork combines these ERP capabilities with its built-in **Work IQ** features (email, calendar, documents, spreadsheets) to orchestrate workflows that span multiple systems.

## Example scenarios

The following examples illustrate how Copilot Cowork can help with common finance and operations tasks.

### Look up ERP data

Ask Copilot Cowork natural language questions about your finance and operations data.

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

> *"Evaluate bids for RFQ 000012. Use the latest vendor emails and PDF attachments to extract bid details, update the RFQ replies in finance and operations, score the bids using the configured scoring criteria, and recommend the supplier to award. Provide the recommendation in an interactive document. After my approval, create the purchase order and draft the bid award email."*

In this scenario, Copilot Cowork:

1. Retrieves the RFQ data (lines, vendors, scoring criteria) from Dynamics 365 through the MCP server.
1. Reads vendor bid emails and PDF attachments from Outlook (Work IQ).
1. Extracts and cross-references bid details, flagging discrepancies.
1. Scores responses against the configured ERP criteria.
1. Generates a recommendation document with ranked vendors, strengths, and risks.
1. On approval, creates the purchase order in Dynamics 365 and drafts an award email in Outlook.

> [!IMPORTANT]
> Copilot Cowork asks for your approval before performing write operations in Dynamics 365, such as updating bid records, creating purchase orders, or sending emails. You remain in control of every consequential decision.

## Tips for effective prompts

To get the best results from Copilot Cowork with the Dynamics 365 ERP apps plugin, consider the following tips:

- **Be specific about the company.** If your environment has multiple legal entities, specify the company in your prompt (for example, *"in USMF"* or *"in company DEMF"*).
- **Use business terms.** Copilot Cowork understands finance and operations terminology. Use terms like *"purchase order,"* *"vendor invoice,"* *"customer credit limit,"* and *"sales order"* as you would in the application.
- **Break complex tasks into steps.** For multistep workflows, you can either give Copilot Cowork a comprehensive prompt or guide it step by step. Copilot Cowork asks for clarification when needed.
- **Review before approving write operations.** Copilot Cowork shows you a summary of what it plans to write before making changes. Review the details carefully before approving.

## Data security and privacy

- **User-level permissions.** All data access through Copilot Cowork respects the security roles and privileges assigned to the user in the finance and operations environment. Users can't access data through Copilot Cowork that they can't access through the application.
- **Human in the loop.** Copilot Cowork asks for explicit user approval before performing write operations (creating records, updating data, or taking actions that modify the system state).
- **Audit trail.** Operations performed through Copilot Cowork are logged in the standard finance and operations audit infrastructure, just like operations performed through the application client.

## Limitations

- The Dynamics 365 ERP apps plugin requires version 10.0.47 or later of finance and operations apps.
- The MCP server isn't supported on Cloud Hosted Environments (CHE).
- Some complex form interactions might require multiple tool calls and can take longer than simple data lookups.
- The plugin is currently available in regions where Copilot Cowork is deployed. Learn more about the latest availability in [Explore Copilot products by geography and languages](https://releaseplans.microsoft.com/availability-reports/?report=copilotproductreport).

## Related information

- [Enable the Dynamics 365 ERP apps plugin for Copilot Cowork](../../dev-itpro/copilot/enable-copilot-cowork-erp.md)
- [Use Model Context Protocol for finance and operations apps](../../dev-itpro/copilot/copilot-mcp.md)
- [Create AI tools with finance and operations business logic](../../dev-itpro/copilot/copilot-ai-plugins.md)
- [Overview of Copilot capabilities in finance and operations apps](copilot-for-finance-operations.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
