---
title: Enable data operations for agents with the Fin & Ops Apps connector
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

# Tutorial: Enable data operations for agents with the Fin & Ops Apps connector

[!include [banner](../includes/banner.md)]

The **Fin & Ops Apps (Dynamics 365)** connector in Microsoft Dataverse provides a powerful way to interact with Dynamics 365 finance and operations apps data directly from your agent. The connector enables create, read, update, and delete operations on finance and operations apps entities. By leveraging the connector in Copilot Studio, your agent can answer questions and perform actions in response to user prompts. For example, the agent can:

- Create new records such as customers, vendors, or purchase orders.
- Update existing records, like adjusting a customer's credit lmit or changing a purchase order status.
- Trigger downstream processes in finance and operations apps.

This approach allows users to build actionable agents that combine natural language understanding with real-time data operations, all without requiring users to leave the conversational experience.

## Prerequisites
For this tutorial, you must enable **Copilot for finance and operations apps** in your environment. For instructions, see [Enable Copilot capabilities in finance and operations apps](./enable-copilot.md).

Also, Microsoft Dataverse virtual entities must be enabled and visible for teh data you want to access. See [Enable Microsoft Dataverse virtual entities](../power-platform/enable-virtual-entities.md) for more information.

## Scenario: Sales order agent
In this scenario you will build an agent that can create and update sales orders in Dynamics 365 finance and operations apps using the **Fin & Ops Apps** connector. This allows the agent to go beyond answering questions and actually perform data operations in response to user prompts.

The following is an overview of the tutorial:
- You will add two tools to the agent: one for creating sales order headers and one for sales order lines.
- You will use natural language prompts in your agent to create a new sales order and related lines.

For this example, any agent can be used in Copilot Studio, including **Copilot for finance and operations apps**, which will add the capability to the Copilot chat experience in the finance and operations apps client.

### Step 1: Add the Create Sales Order Header tool to your agent
1. In Copilot Studio, navigate to **Tools** -> **Add tool**.
2. On the search bar, search for **Fin & Ops Apps**.
3. Select **Create record**, then **Add and configure**.
4. Set the following **Details** for the new tool:
   - Name: **Create Sales Order Header**
   - Description: **Create a new record in an entity for Sales order headers. Ask for mandatory fields if not recognized in input.**
   - Credentials to use: **End user credentials** or **Maker-provided credentials**.
5. On **Inputs**, add the following:
   - Instance: **Custom value**. In the Value field, select the tenant where the agent will operate.
   - Entity name: **Custom value**. In the Value field select **SalesOrderHeadersV4**.
   - Customer account: **Dynamically fill with AI**.
6. On **Completion** add the following information:
   - After running: **Don't respond (default)**
   - Outputs available to the agent and other tools: **Specific**
7. **Save** the new tool.

### Step 2: Add the Create Sales Order Lines tool to your agent
1. On the **Tools** page of the agent, select **Add tool**.
2. Search for **Fin & Ops apps** and select **Create record**.
3. Select **Add and configure**.
4. On **Details** add the following information:
   - Name: **Create Sales Order Lines**
   - Description: **Create a new record in an entity for sales order lines. Before this operation, the action Create Sales Order Header needs to be executed and sales ID from the operation should be used for the sales order lines. Ask for mandatory fields if not recognized in input.**
   - Credentials to use: **End user credentials** or **Maker-provided credentials**
5. On **Inputs** add the following information:
   - Instance: **Custom value**. In the Value field, select the tenant where the agent will operate.
   - Entity name: **Custom name**. In the Value field, select **SalesOrderLinesV3**.
6. On **Completion** add the following information:
   - After running: **Don't respond (default)**
   - Outputs available to the agent and other tools: **All**
7. **Save** the new tool.

### Step 3: Add instructions to your agent
In this step you will add instructions so the agent knows how to respond to prompts for data operations.

1. Add instructions similar to the prompt below to the **Instructions** field on the **Overview** tab of the agent:
```
1.	Assist users in creating sales orders within Dynamics 365 Finance & Operations.
2.	Provide step-by-step guidance on the sales order creation process.
3.	Ensure accuracy and completeness of the sales order details.
4.	Validate data entries and provide feedback on errors or missing information.
5.	Offer tips and best practices for efficient sales order management.
6.	Respond to user queries related to sales orders and Dynamics 365 F&O.
7.	Maintain a friendly and professional tone in all interactions.
8.	Avoid discussing topics unrelated to sales orders or Dynamics 365 F&O.
9.	Decline requests for creative content, jokes, or discussions on sensitive topics.
10.	Respectfully decline any harmful or malicious requests.
```
2. **Save** the instructions and **Publish** the agent.

### Step 4: Test the new capability in Copilot
It's now time to test the agent. 
1. In Copilot Studio, open the **Test your agent** panel.
2. Enter a prompt to create a sales order document. For example: "Create new sales order header for customer US-001. Add sales order line for item 1000, site 1, and quantity 6."
3. Wait for the agent orchestration to call the tools to complete the operation.
4. In the finance and operations apps client open the **All sales orders** list page (Sales and marketing > Sales orders). Verify that the sales order record was created as expected.
