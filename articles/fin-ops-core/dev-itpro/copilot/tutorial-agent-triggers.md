---
title: Trigger autonomous agents with business events
description: Learn how to trigger autonomous agents with business events.
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

# Tutorial: Trigger autonomous agents with business events

[!include [banner](../includes/banner.md)]

Business events in Dynamics 365 finance and operations apps provide a powerful mechanism for integrating external systems and automating workflows. These events are emitted when specific business actions occur, such as confirming a purchase order or approving a requisition. Use these events to notify external systems or trigger downstream processes. For more information about the business events framework in finance and operations apps, see [Business events overview](../business-events/home-page.md).

By connecting these business events to agents, you can unlock intelligent, event-driven automation. When a business event is raised, it can serve as a trigger for an agent to perform tasks such as:
- Initiating reconciliation processes
- Sending notifications or approvals
- Updating external systems or databases
- Launching low-code workflows via Power Platform

This approach enables seamless orchestration between finance and opeations apps and Copilot Studio agents, allowing you to extend business logic beyond the boundaries of the Dynamics 365 application. Whether the event is workflow-based (for example, approvals) or nonworkflow (for example, confirmations), you can harness it to drive real-time, contextual automation. By using low-code plugins, developers and solution architects can configure these triggers with minimal effort, ensuring scalability and maintainability across business scenarios. 

## Prerequisites
For this tutorial, you must first enable Copilot for finance and operations apps in your environment. For instructions, see [Copilot capabilities in finance and operations apps](./enable-copilot.md).

## Scenario: Notify a manager when a purchase order is confirmed
In this scenario, you add a trigger capability to an agent. Once the business event conditions are reached (a purchase order is confirmed), the agent is triggered and sends an email or Teams message to the manager of that company referring the purchase order has been created, sending all relevant data via email. 

You can achieve this scenario in two different ways:
- Create a specific agent for purchase orders
- Integrate the trigger on an existing agent (it can be the Copilot for Dynamics 365 finance and operations or any agent already created in Copilot Studio)

Here's an overview of the steps in this tutorial:
- A trigger action for the business event. This action calls the agent once a purchase order is confirmed in Dynamics 365 finance and operations.
- Add two tools (Send an Email and Send a Teams Message), so that a specific user is notified regarding this action on Dynamics 365 finance and operations.
- Clear instructions so that the right tools are called based on the triggered event.

### Step 1: Create a new trigger that monitors purchase orders confirmed
1.	In Copilot Studio, go to **Overview** -> **Triggers** -> **Add trigger**.
1.	Select **All** and, on the search bar, search for **When a Business Event occurs Fin & Ops Apps (Dynamics 365)**. 
1.	Select **Next**. A connection from Microsoft Copilot Studio to Dynamics 365 Finance and Operations is created. For this example, rename the trigger to “Notify a Manager When a Purchase Order Is Confirmed”.
1.	After selecting **Next**, define:
   - The instance (environment) where the agent looks for the business event trigger.
   - Category - select **Purchase orders**.
   - Business event - select **Purchase order confirmed**.
   - Legal entity - keep it blank. If you don't select a legal entity, the event triggers when the operation is performed in _any_ legal entity.
   - Other instructions to the agent when it's invoked by this trigger - **Use content from @{triggerBody()}**.
1. Select **Create Trigger** once all the options above are defined. The trigger is created for this specific purpose.
1. The trigger appears in the **Triggers** section of the **Overview** page for the agent.

The agent is now called when a purchase order is confirmed on Dynamics 365 finance and operations.

### Step 2: Add tools for email and Teams communication
In this step, you add tools so that the agent can communicate via email and Teams with a specific, predefined person.

1. In Copilot Studio, go to **Overview** -> **Tools** -> **Add tool**.
1. Select **All** and, on the search bar, search for **Mail**. Select the option **Send an email (V2)** with the Outlook connector.
1. When you select **Next**, select **Add to agent** for this specific tool. The option for our agent to send emails is available on its toolkit. You now configure this specific tool.
1. On **Overview** -> **Tools**, select **...** and then **Edit**. Here you can edit each field for customizing what this tool does if triggered by the agent.
1. For this example, keep the inputs **To**, **Subject**, and **Body** to **Dynamically fill with AI** so the agent understands what information to add for each field. You can customize it by changing the dropdown to **Custom Value**.
1. On **Additional details**, use the **Maker-provided credentials**, as this is an autonomous agent.
1. After defining the email tool, go to **Tools** -> **Add tool**.
1. Select **All**, and search for **Post a message in a chat or channel**.
1. When you select **Next**, select **Add and configure**. It creates the connection for Teams and you're redirected to the settings option.
1. On **Inputs**, change the parameters to directly define how the tool interacts with the incoming message from Dynamics 365 finance and operations apps and delivers it to Teams.
    - Post as - **Custom Value - Flow bot**
    - Post in - **Custom value - Chat with Flow bot**
    - Recipient - **Dynamically fill with AI**
    - Message - **Dynamically fill with AI**
1. On **Additional details**, select **Maker-provided credentials**, as this is an autonomous agent.
1. Leave the default values for the remaining options, and **Save**.

### Step 3: Define the instructions for the agent
In this step, you define clear instructions for the agent to understand what to do when the purchase order is marked as confirmed in the application.

1. In Copilot Studio, go to **Overview** -> **Instructions** -> **Edit**.
1. Enter a prompt similar to the following text into the **Instructions**, replacing the email with the email address of the account where you want the notifications sent.
   ```
   Send the triggered message to **yourexample@email.com** via Teams and Email. When a Payment Journal is Posted - Be polite, send a good natural language phrase with all the relevant details from the journal that was posted. Also include some sort of follow-up that might be relevant. Add also relevant information around the currency code if detected (e.g. if it's EUR = EURO, define that on the payment amount). The end of the message should not include the name of the agent. Format the email as HTML.
   ```
1. **Save** and **Publish** the agent.

### Step 4: Test the agent
You can now test the agent, starting in your Dynamics 365 finance and operations apps client, with your Microsoft Teams and email inbox open.

1. In Dynamics 365 finance and operations apps, in company USMF, open **Accounts Receivable** -> **Payments** -> **Customer payment journal**.
1. Select **New**.
1. Define the **Name** parameter with any entry already prepopulated, such as **CustPay**.
1. Once added, select **Lines** from the action ribbon.
1. Add the following values to the line:
   - Account - **DE-001** (Contoso Europe)
   - Description - **Check**
   - Credit - **1000**
   - Method of payment - **CHECK**
1. **Save** the line with the defined inputs and return to the previous screen.
1. **Validate** the journal entry. If successful, **Post** the journal by selecting **Post** -> **Post**.

Once you post the journal, open Microsoft Teams and your email account to verify that the agent automatically sent the messages on the triggered event.
