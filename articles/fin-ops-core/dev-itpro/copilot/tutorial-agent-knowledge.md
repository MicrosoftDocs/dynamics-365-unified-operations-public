---
title: Add knowledge to agents for finance and operations apps
description: Learn how to add knowledge to agents for finance and operations apps.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 10/08/2025
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Tutorial: Add knowledge to agents for finance and operations apps

[!include [banner](../includes/banner.md)]

Virtual entities for Dynamics 365 finance and operations apps expose live operational data in Microsoft Dataverse. They appear as Dataverse tables that point back to data in finance and operations apps, enabling create, read, update, and delete (CRUD) operations where supported. This feature lets your apps, flows, and agents use current data directly accessed in the finance and operations database.

When you connect the virtual entities as knowledge sources in Copilot Studio, your agent can interact in natural language with the data available in finance and operations apps, returning explanations, aggregations, and citations for records. Copilot Studio includes a Dataverse knowledge experience that lets you use this functionality.

## Prerequisites

For this tutorial, enable **Copilot for finance and operations apps** in your environment. For instructions, see [Enable Copilot capabilities in finance and operations apps](./enable-copilot.md).

Also, enable Microsoft Dataverse virtual entities and make them visible for the data you want to access. See [Enable Microsoft Dataverse virtual entities](../power-platform/enable-virtual-entities.md) for more information.

## Scenario 1: On-hand inventory

In this scenario, you add virtual entities to an agent that enable the agent to reply to questions about on-hand inventory. 

- You add a knowledge source to the agent in Copilot Studio.
- You query the agent in natural language about on-hand inventory, receiving responses based on the provided knowledge.

For this example, you can use any agent in Copilot Studio, including **Copilot for finance and operations apps**, which adds the capability to the Copilot chat experience in the finance and operations apps client.

### Step 1: Add the virtual entities to your agent

1. In Copilot Studio, go to **Knowledge** > **Add knowledge**.
1. Select **Dynamics 365**.
1. On table selection, select **mserp_inventoryonhandaientity**. The list shows all virtual entities for finance and operations apps that are generated in the environment, identified with the "mserp_" prefix.
1. Select **Add to agent**.
1. **Publish** the changes to the agent.

The knowledge source is then added to the agent. Once they're ready to use, the status of the knowledge source shows as **Ready**.

### Step 2: Test the new capability in Copilot

You can now test the knowledge source in your agent. 
1. In Copilot Studio, go to the **Knowledge** tab and open the **Inventory on hand for AI (mserp)** knowledge source.
1. Select **Preview** to view some of the data available in the virtual entity.
1. In the chat experience for your agent, ask questions related to the knowledge source. For example:
   - "How much available stock do we have for item number M0001?"
   - "What is the available inventory for this item per each company?"
  
## Scenario 2: Validate customer credit risk

In this scenario, you add virtual entities that let you ask the agent questions about customer information.

- You add one knowledge source to your agent.
- You query the agent for information about customers, provided by the added knowledge source.

For this example, you can use any agent in Copilot Studio, including **Copilot for finance and operations apps**, which adds the capability to the sidecar chat experience in the finance and operations apps client.

### Step 1: Add the virtual entity to your agent

1. In Copilot Studio, go to **Knowledge** -> **Add knowledge**.
1. Select **Dynamics 365**.
1. On table selection, select **mserp_custtablebientity**.
1. Select **Add to agent**.

The knowledge source is now added to your agent. When the source is ready to use, the status of the knowledge source shows as **Ready**.

### Step 2: Test the new capability in Copilot

Query the agent to retrieve customer information in natural language.
1. In Copilot Studio, go to **Knowledge** > **Customers**.
1. Select **Preview** to view some of the data available in the virtual entity.
1. In the chat experience for your agent, ask questions related to the knowledge source. For example:
   - "What is the credit limit for customer DE-001?"
   - "Show me all customers who have a credit limit higher than $50,000. Return the list in tabular format with the following columns: Customer account, Customer name, Credit limit, Credit rating."

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
