---
title: Create client plugins for Copilot in finance and operations apps tutorial
description: This article provides a step-by-step tutorial of an example creating client plugins to extend the capabilities of Copilot in finance and operations.
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.search.form:
ms.topic: how-to
ms.date: 4/26/2024
audience: Developer
ms.search.region: Global
ms.custom: bap-template
---

# Tutorial: Create client plugins for Copilot in finance and operations apps tutorial

[!include [banner](../includes/banner.md)]

**Client plugins** or client actions are Copilot plugins that invoke client code, and are available for users within the context of client experiences of finance and operations apps. Developers can extend the Copilot chat capabilities in finance and operations apps by defining plugins that convert the functionality, operations, and business logic of the X++ code base into actions that can be invoked using natural language. For more information on client plugins and syntax, see [Create client plugins for Copilot in finance and operations apps](create-client-plugins.md).

## Scenario
There are many possible use cases for client plugins, exposing business logic contained in X++ to Copilot, making the logic something Copilot "knows how to do" and enabling the user to interact with the logic in natural language. In this scenario, you add the Copilot capability of a simplified client navigation action, enabling users to navigate to specific forms in the application through natural language in the Copilot chat panel.

Here's an overview of the steps in this tutorial:
1. Create a client-side action in X++ that defines the logic to be invoked for the action.
2. In Copilot Studio, create a topic that's triggered by a Copilot prompt to navigate to a defined form, and invokes the client action created in step 1.
3. Create a topic that is triggered by the completed client action and returns a response to the user in the Copilot chat.

### Prerequisites
This tutorial has the following prerequisites:
1. You must have a unified developer environment. Developing client plugins is available only in the [unified developer experience](https://learn.microsoft.com/power-platform/developer/unified-experience/finance-operations-dev-overview). For information on creating a unified developer environment from the [unified admin experience for finance and operations apps](https://learn.microsoft.com/power-platform/admin/unified-experience/finance-operations-apps-overview), see [Tutorial: Install the Finance and Operations Provisioning App](https://learn.microsoft.com/power-platform/admin/unified-experience/tutorial-install-finance-operations-provisioning-app).
2. You must have version 10.0.40 or higher of finance and operations apps. for more information on release schedules for finance and operations apps, see [Service update availability](../get-started/public-preview-releases.md).
3. Copilot in finance and operations apps must be enabled in your environment. For instructions, see [Enable Copilot capabilities in finance and operations apps](enable-copilot.md).

## Step 1: Create a client-side action
In your unified developer environment, create an X++ class that defines the navigation action. The action includes input and output parameters to pass properties between the client and Copilot.

1. In your development project in Visual Studio, create a new class. Name the class **SysCopilotChatCustomNavigateAction**.
2. Add the following code to the class.
   ```x++
    /// <summary>
    /// Provides a client-side action for copilot that navigates to a defined form in the application.
    /// </summary>
    [DataContract]
    [SysCopilotChatGlobalAction]
    [SysCopilotChatActionDefinition(
        identifierStr(MS.ServerForm.CopilotExample.ClientNavigate),
        'Navigate',
        'Navigates to or opens a defined form in the application client',
        menuItemActionStr(SysCopilotChatCustomNavigateAction), MenuItemType::Action)]
    public final class SysCopilotChatCustomNavigateAction extends SysCopilotChatAction
    {
        private MenuItemName menuItemName;
        private str navResponse;
    
        [DataMember('menuItemName'),
        SysCopilotChatActionInputParameter('The name of the menu for the form to launch', true)]
        internal MenuItemName parmMenuItemName(MenuItemName _menuItemName = menuItemName)
        {
            menuItemName = _menuItemName;
            return menuItemName;
        }
    
        [DataMember('navResponse'),
        SysCopilotChatActionOutputParameter('The response from the navigation, whether an error or successful navigation')]
        public str parmNavResponse(str _navResponse = navResponse)
        {
            navResponse = _navResponse;
            return navResponse;
        }
        public void executeAction(SysCopilotChatActionDefinitionAttribute _actionDefinition, Object _context)
        {
            super(_actionDefinition, _context);
    
            if (this.parmMenuItemName())
            {
                // Navigate
                MenuFunction::runClient(this.parmMenuItemName(), MenuItemType::Display, false, new Args());
                this.parmNavResponse("You were successfully navigated to the " + menuItemName + " form.");
            }
            else
            {
                throw Error(Error::wrongUseOfFunction(funcName()));
                this.parmNavResponse("There was an error navigating you to the " + menuItemName + " form. See the action menu for more information.");
            }
        }
    }
   ```
3. In your development project in Visual Studio, add a new **Action Menu Item**.
   - **Name:** SysCopilotChatCustomNavigateAction
   - **Object Type**: Class
   - **Object**: SysCopilotChatCustomNavigateAction
4. Save and deploy the code to your environment.

## Step 2: Create a topic to invoke the action
For this example you create two topics in the **Copilot in finance and operations** chatbot in  Copilot Studio. The first topic initiates the plugin when the user enters a prompt in Copilot indicating intent to navigate to a form. When the topic is triggered, it determines the input parameters for the action and send them as an event to X++ to call the action.

1. Open the **Copilot in finance and operations** chatbot in Copilot Studio.
2. Create a new topic named "CustomClientNavigation" with the following trigger phrases:
   - "Navigate to form"
   - "Open page"
   - "Take me to form"
3. Create **Question** nodes in the topic to ask the user to define the form to the client should navigate to.
   - **Message**: What form do you want to navigate to?
   - **Identify**: Options from a list variable
   - **List variable**: `Global.PA_Copilot_ServerForm_NavigationContext`
   - **Save user response as**: Create a new local topic variable: `Topic.SelectedTarget`
4. Create an **Event activity** node that invokes the X++ class.
    - **Name**: MS.ServerForm.CopilotExample.ClientNavigate
    - **Value**: Set the value to the following Power Fx formula:
    ```powerapps-dot
    Concatenate("{""menuItemName"": """,Topic.SelectedTarget.MenuItem, """}")        
    ```
5. Create an **End current topic** node to end the topic.
6. **Save** the new topic.

## Step 3: Create a topic for returned output parameters
The second topic receives the output parameters returned from the X++ class, and returns the response to the user in the Copilot chat panel.

1. In the **Copilot in finance and operations** chatbot, create a new topic.
  - Set the trigger type to **Event received**. For more information, see [Changing the trigger for a topic](https://learn.microsoft.com/microsoft-copilot-studio/authoring-triggers#changing-the-trigger-for-a-topic).
  - In the **On Event Activity properties** pane, set the **Event name** to "MS.ServerForm.CopilotExample.ClientNavigate".
3. Create a **Parse value** node to parse the JSON string from the event payload.
    - **Parse value**: `System.Activity.Text`
    - **Data type**: "From sample data"
    - Select **Get schema from sample JSON**, and enter the following JSON string to define the schema of the returned parameters:
      ```json
      {
	      "isResponse":true,
	      "menuItemName":"EInvoiceExtCodeWeightUnit_MX",
	      "navResponse":"You successfully navigated to the EInvoiceExtCodeWeightUnit_MX form."
      }
      ```
    - **Save as**: Create a `Topic.NavigationResponse` variable as a record type for the parsed response.
4. Create a **Message** node in the topic. Set message value to the `Topic.NavigationResponse` variable.
5. **Save** the topic.
6. **Publish** the changes to the chatbot.

## Step 4: Test the plugin
Once you've created your action in X++ and the topics to manage the execution and response, and published and deployed the code, the Copilot chat then has a new capability enabling users to navigate to forms in the application as part of a Copilot natural language chat in finance and operations apps. For example, the user can enter prompts in the Copilot chat panel like:
- "Open form: Default dashboard" - This prompt navigates the client to the DefaultDashboard form.
- "Navigate to page" - This prompt provides the user with a list of menu items that are available to the user, based on permissions, from which they can select. Note the list can be fairly large depending on permissions, and is capped at 500 menu items.
