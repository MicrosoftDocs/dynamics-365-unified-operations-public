---
title: Add knowledge to agents for finance and operations apps
description: Learn how to use finance and operations virtual entities as knowledge sources for your ERP agents through a tutorial.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 10/05/2025
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Tutorial: Add knowledge to agents for finance and operations apps

[!include [banner](../includes/banner.md)]

Virtual entities for Dynamics 365 finance and operations apps expose live operational data in Microsoft Dataverse. They appear as Dataverse tables that point back to data in finance and operations apps, enabling create, read, update, and delete (CRUD) operations where supported. This allows your apps, flows, and agents to use current data directly accessed in the finance and operations database.

By connecting the virtual entities as knowledge sources in Copilot Studio, your agent can interact in natural language with the data available in finance and operations apps, returning explanations, aggregations, and citations for records. Copilot Studio includes a Dataverse knowledge experience enabling this functionality.

## Prerequisites
For this tutorial, you must enable **Copilot for finance and operations apps** in your environment. For instructions, see [Enable Copilot capabilities in finance and operations apps](./enable-copilot.md).

Also, Microsoft Dataverse virtual entities must be enabled and visible for teh data you want to access. See [Enable Microsoft Dataverse virtual entities](../power-platform/enable-virtual-entities.md) for more information.

## Scenario 1: On-hand inventory
In this scenario, you will add virtual entities to an agent enabling the agent to reply to questions about on-hand inventory. 

- You will add a knowledge source to the agent in Copilot Studio.
- You will query the agent in natural language about on-hand inventory, recenving responses back based on the provided knowledge.

For this example, any agent can be used in Copilot Studio, including **Copilot for finance and operations apps**, which will add the capability to the Copilot chat experience in the finance and operations apps client.

### Step 1: Add the virtual entities to your agent
1. In Copilot Studio, go to **Knowledge** -> **Add knowledge**.
2. Select **Dynamics 365**.
3. On table selection, select **mserp_inventoryonhandaientity**. All vitual entities for finance and operations apps that have been generated in the environment are available in the list, identified with the "mserp_" prefix.
4. Select **Add to agent**.
5. **Publish** the changes to the agent.

The knowledge source is then added to the agent. Once they are ready to use, the status of the knowledge source will show as **Ready**.

### Step 2: Test the new capability in Copilot
You can now test the knowledge source in your agent. 
1. In Copilot Studio, navigate to the **Knowledge** tab and open the **Inventory onhand for AI (mserp)** knowledge source.
2. Select **Preview** to view some of the data available in the virtual entity.
3. In the chat experience for your agent, ask questions related to the knowledge source. For example:
   - "How available stock do we have for item number M0001?"
   - "What is the available inventory for this item per each company?"
  
## Scenario 2: Validate customer credit risk
In this scenario you will add virtual entities enabling you to ask the agent questions about customer information.

- You will add one knowledge source to your agent.
- You will query the agent for information about customers, provided by the added knowledge source.

For this example, any agent can be used in Copilot Studio, including **Copilot for finance and operations apps**, which will add the capability to the sidecar chat experience in the finance and operations apps client.

### Step 1: Add the virtual entity to your agent
1. In Copilot Studio, go to **Knowledge** -> **Add knowledge**.
2. Select **Dynamics 365**.
3. On table selection, select **mserp_custtablebientity**.
4. Select **Add to agent**.

The knowledge source is now added to your agent. Once the source is ready to use, the status of the knowledge source will show as **Ready**.

### Step 2: Test the new capability in Copilot
You can now query the agent to retrieve customer information in natural language.
1. In Copilot Studio, go to **Knowledge** -> **Customers**.
2. Select **Preview** to view some of the data available in the virtual entity.
3. In the chat experience for your agent, ask questions related to the knowledge source. For example:
   - "What is the credit limit for customer DE-001?"
   - "Show me all customers have a credit limit higher than $50,000. Return the list in tabular format with the following columns: Customer account, Customer name, Credit limit, Credit rating."
