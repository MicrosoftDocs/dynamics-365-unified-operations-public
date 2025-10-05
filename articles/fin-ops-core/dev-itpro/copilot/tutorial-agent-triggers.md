---
title: Trigger autonomous agents with business events
description: Learn how to use finance and operations business events to trigger autonomous agents through a tutorial.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 09/02/2025
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Tutorial: Trigger autonomous agents with business events

[!include [banner](../includes/banner.md)]

Business events in Dynamics 365 finance and operations apps offer a powerful mechanism for integrating external systems and automating workflows. These events are emitted when specific business actions occur, such as confirming a purchase order or approving a requisition. They can be used to notify external systems or trigger downstream processes. See [Business events overview](../business-events/home-page.md) for more information on the business events framework in finance and operations apps.

By connecting these business events to agents, organizations can unlock intelligent, event-driven automation. When a business event is raised, it can serve as a trigger for an agent to perform tasks such as:
- Initiating reconciliation processes
- Sending notifications or approvals
- Updating external systems or databases
- Launching low-code workflows via Power Platform

This approach enables seamless orchestration between F&O and Copilot Studio agents, allowing business logic to be extended beyond the boundaries of the Dynamics 365 application. Whether the event is workflow-based (e.g. approvals) or non-workflow (e.g. confirmations), it can be harnessed to drive real-time, contextual automation. By leveraging low-code plugins, developers and solution architects can configure these triggers with minimal effort, ensuring scalability and maintainability across business scenarios. 

## Prequisites
For this tutorial, you must first enable Copilot for finance and operations apps in your environment. For instructions, see [Copilot capabilities in finance and operations apps](./enable-copilot.md).

## Scenario: Notify a manager when a purchase order is confirmed
In this scenario, you add a trigger capability to an agent. Once the business event conditions are reached (a purchase order is confirmed), the agent will be triggered and an email/teams message will be sent to the manager of that company referring the purchase order has been created, sending all relevant data via email. 

This can be achieved in two different ways:
- Create a specific agent for purchase orders
- Integrate the trigger on an existing agent (it can be the Copilot for Dynamics 365 finance and operations or any agent already created in Copilot Studio)

Here's an overview of the steps in this tutorial:
- A trigger action for the business event. This will call the agent once a purchase order has been confirmed in Dynamics 365 finance and operations.
- Add two tools (Send an Email and Send a Teams Message), so that a specific user will be notified regarding this action on Dynamics 365 finance and operations.
- Have clear instructions so that the right tools will be called based on the triggered event.

### Step 1: Create a new trigger that monitors Purchase Orders confirmed
1.	In Copilot Studio, go to **Overview** -> **Triggers** -> **Add trigger**.
2.	Select **All** and, on the search bar, search for **When a Business Event occurs Fin & Ops Apps (Dynamics 365)**. 
3.	Once you select **Next**, a connection from Microsoft Copilot Studio to Dynamics 365 Finance and Operations will be created. For this example, rename the trigger to “Notify a Manager When a Purchase Order Is Confirmed”.
4.	After selecting **Next**, define:
   - The instance (environment) to which the agent will be looking for the business event trigger.
   - Category - select **Purchase orders**.
   - Business event - select **Purchase order confirmed**.
   - Legal entity - for this example, keep it as blank. If nothing is selected in this option, the event is triggered when the operation is performed in _any_ legal entity.
   - Additional instructions to the agent when it's invoked by this trigger - **Use content from @{triggerBody()}**.
5. Select **Create Trigger** once all the options above have been defined. The trigger will be created for this specific purpose.
6. The trigger should appear in the **Triggers** section of the **Overview** page for the agent.

The agent will now be called once a purchase order has been confirmed on Dynamics 365 finance and operations.

### Step 2: Add tools for email and Teams communication
In this step, you will add tools so that the agent can communicate via email and Teams with a specific, predefined person.

1. In Copilot Studio, go to **Overview** -> **Tools** -> **Add tool**.
2. Select **All** and, on the search bar, search for **Mail**. Select the option **Send an email (V2)** with the Outlook connector.
3. One you select **Next**, select **Add to agent** for this specific tool. The option for our agent to send emails will be available on its toolkit. We will now configure this specific tool.
4. On **Overview** -> **Tools**, select **...** and then **Edit**. Here you will have the possibility of editing each field for customizing what this tool will do if triggered by the agent.
5. For this example, we will keep the inputs **To**, **Subject**, and **Body** to **Dynamically fill with AI** so the agent will understand what should be added as information for each field. You can customize it by changing the dropdown to **Custom Value**.
6. On **Additional details**, we will be using the **Maker-provided credentials**, as this is an autonomous agent.
7. After defining the email tool, go to **Tools** -> **Add tool**.
8. Select **All**, and search for **Post a message in a chat or channel**.
9. Once you select **Next**, select **Add and configure**. It will create teh connection for Teams and you will be redirected to the settings option.
10. On **Inputs**, change the parametes to directly define how the tool will interact with the incoming message from Dynamics 365 finance and operations apps and deliver it to Teams.
    - Post as - **Custom Value - Flow bot**
    - Post in - **Custom value - Chat with Flow bot**
    - Recipient - **Dynamically fill with AI**
    - Message - **Dynamically fill with AI**
11. On **Additional details**, select **Maker-provided credentials**, as this is an autonomous agent.
12. Leave the default values for the remaining options, and **Save**.

### Step 3: Define the instructions for the agent
In this step we will define clear instructions for the agent to understand what to do when the Purchase Order is marked as confirmed in the application.

1. In Copilot Studio, go to **Overview** -> **Instructions** -> **Edit**.
2. Enter a prompt similar to the following into the **Instructions**, replacing the email with the email address of the account where you want the notifications sent.
   ```
   Send the triggered message to **yourexample@email.com** via Teams and Email. When a Payment Journal is Posted - Be polite, send a good natural language phrase with all the relevant details from the journal that was posted. Also include some sort of follow-up that might be relevant. Add also relevant information around the currency code if detected (e.g. if it's EUR = EURO, define that on the payment amount). The end of the message should not include the name of the agent. Format the email as HTML.
   ```
3. **Save** and **Publish** the agent.

### Step 4: Test the agent
You can now test the agent, starting in your Dynamics 365 finance and operations apps client, with your Microsoft Teams and email inbox open.

1. In Dynamics 365 finance and operations apps, in company USMF, open **Accounts Receivable** -> **Payments** -> **Customer payment journal**.
2. Select **New**.
3. Define the **Name** parameter with any entry already pre-populated, such as **CustPay**.
4. Once added, select **Lines** from the action ribbon.
5. Add the following values to the line:
   - Account - **DE-001** (Contoso Europe)
   - Description - **Check**
   - Credit - **1000**
   - Method of payment - **CHECK**
6. **Save** the line with the defined inputs and return to the previous screen.
7. **Validate** the journal entry. If successful, **Post** the journal by clicking **Post** -> **Post**.

Once the journal is posted, you can open Microsoft Teams and your email account to verify that the agent automatically sent to the messages on the triggered event.
