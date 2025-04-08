---
title: Tutorial - Create client plugins for Copilot in finance and operations apps
description: This article provides a step-by-step tutorial that shows how to create client plugins to extend the capabilities of Copilot in finance and operations apps.
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.search.form:
ms.topic: how-to
ms.date: 06/12/2024
audience: Developer
ms.search.region: Global
ms.custom: bap-template
---

# Tutorial: Create client plugins for Copilot in finance and operations apps

[!include [banner](../includes/banner.md)]

*Client plugins*, or client actions, are Microsoft Copilot plugins that invoke client code and are available for users in the context of client experiences for finance and operations apps. Developers can extend the Copilot chat capabilities in finance and operations apps by defining plugins that convert the functionality, operations, and business logic of the X++ code base into actions that users can invoke through natural language. For more information about client plugins and syntax, see [Create client plugins for Copilot in finance and operations apps](copilot-client-plugins.md).

## Scenario

There are many possible use cases for client plugins, and for exposing business logic in X++ to Copilot, making the logic something that Copilot "knows" how to do, and enabling the user to interact with the logic in natural language. In this scenario, you're adding a simplified client navigation action as a Copilot capability. Users can then go to specific forms in the application through natural language in the Copilot chat pane.

Here's an overview of the steps in this tutorial.

1. Create a client-side action in X++ that defines the logic to invoke for the action.
2. In Copilot Studio, create a topic that's triggered by a Copilot prompt to go to a defined form, and that invokes the client action that you created in step 1.
3. Create a topic that's triggered by the completed client action and returns a response to the user in the Copilot chat pane.

### Prerequisites

This tutorial has the following prerequisites:

- You must have a unified developer environment. The development of client plugins is available only in the [unified developer experience](/power-platform/developer/unified-experience/finance-operations-dev-overview). For information about how to create a unified developer environment from the [unified admin experience for finance and operations apps](/power-platform/admin/unified-experience/finance-operations-apps-overview), see [Tutorial: Install the Finance and Operations Provisioning App](/power-platform/admin/unified-experience/tutorial-install-finance-operations-provisioning-app).
- You must have version 10.0.40 or later of finance and operations apps. For information about release schedules for finance and operations apps, see [Service update availability](../get-started/public-preview-releases.md).
- Copilot in finance and operations apps must be enabled in your environment. For instructions, see [Enable Copilot capabilities in finance and operations apps](enable-copilot.md).

## Step 1: Create a client-side action

In your unified developer environment, create an X++ class that defines the navigation action. The action includes input and output parameters that pass properties between the client and Copilot.

1. In Visual Studio, in your development project, create a class that's named **SysCopilotChatCustomNavigateAction**.
2. Add the following code to the new class.

    ```x++
    /// <summary>
    /// Provides a client-side action for copilot that navigates to a defined form in the application.
    /// </summary>
    [DataContract]
    [SysCopilotChatGlobalAction]
    [SysCopilotChatActionDefinition(
        identifierStr(MS.PA.CopilotExample.ClientNavigate),
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

3. In your development project, add an action menu item. Set the following property values for it:

    - **Name:** SysCopilotChatCustomNavigateAction
    - **Object Type:** Class
    - **Object:** SysCopilotChatCustomNavigateAction

4. Save and deploy the code to your environment.

## Step 2: Create a topic to invoke the action

For this example, you create two topics in the **Copilot in Finance and Operation** chatbot in Copilot Studio. The first topic initiates the plugin when the prompt that a user enters in Copilot indicates intent to go to a form. When this topic is triggered, it determines the input parameters for the action and sends them as an event to X++ to call the action.

1. In Copilot Studio, open the **Copilot in Finance and Operation** chatbot.
2. Create a topic that's named **CustomClientNavigation** and has the following trigger phrases:

    - "Navigate to form"
    - "Open page"
    - "Take me to form"

3. In the new topic, create **Question** nodes to ask the user to define the form that the client should go to.

    - In the message field, enter **What form do you want to navigate to?**
    - In the **Identify** field, select **Options from a list variable**.
    - In the **List variable** field, specify **Global.PA_Copilot_ServerForm_NavigationContext**.
    - In the **Save user response as** field, create a local topic variable, `Topic.SelectedTarget`.

4. Create an **Event activity** node that invokes the X++ class.

    - In the **Name** field, enter **MS.PA.CopilotExample.ClientNavigate**.
    - In the **Value** field, enter the following Power Fx formula.

        ```powerapps-dot
        Concatenate("{""menuItemName"": """,Topic.SelectedTarget.MenuItem, """}")
        ```

5. Create an **End current topic** node to end the topic.
6. Save the new topic.

## Step 3: Create a topic for returned output parameters

The second topic receives the output parameters that are returned from the X++ class. It then returns the response to the user in the Copilot chat pane.

1. In the **Copilot in finance and operations** chatbot, create a topic.

    - Set the trigger type to **Event received**. For more information, see [Changing the trigger for a topic](/microsoft-copilot-studio/authoring-triggers#changing-the-trigger-for-a-topic).
    - In the **On Event Activity properties** pane, set the **Event name** property to **MS.PA.CopilotExample.ClientNavigate**.

2. In the new topic, create a **Parse value** node to parse the JavaScript Object Notation (JSON) string from the event payload.

    - In the **Parse value** field, enter **System.Activity.Text**.
    - In the **Data type** field, specify **From sample data**.
    - Select **Get schema from sample JSON**, and enter the following JSON string to define the schema of the returned parameters.

        ```json
        {
            "isResponse":true,
            "menuItemName":"EInvoiceExtCodeWeightUnit_MX",
            "navResponse":"You successfully navigated to the EInvoiceExtCodeWeightUnit_MX form."
        }
        ```

    - In the **Save as** field, create a `Topic.NavigationResponse` variable as the record type for the parsed response.

3. Create a **Message** node. Set the message value to the `Topic.NavigationResponse` variable.
4. Save the topic.
5. Publish the changes to the chatbot.

## Step 4: Test the plugin

After you create the action and the topics to manage the execution and response, and after you publish and deploy the code, the Copilot chat has a new capability. Users can now go to specific forms in the application as part of a Copilot natural language chat in finance and operations apps. For example, the user can enter the following prompts in the Copilot chat pane:

- **"Open form: Default dashboard"** – This prompt has the client go to the **DefaultDashboard** form.
- **"Navigate to page"** – This prompt provides a list of menu items that are available to the user, based on their permissions. The user can then select a menu item. 

    > [!NOTE]
    > Depending on a user's permissions, the list can be long. However, it's limited to 500 menu items.
