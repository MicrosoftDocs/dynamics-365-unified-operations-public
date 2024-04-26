---
title: Create client plugins for Copilot in finance and operations apps
description: This article provide guidance on creating client plugins to extend the capabilities of Copilot in finance and operations
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

# Create client plugins for Copilot in finance and operations apps

[!include [banner](../includes/banner.md)]

**Client plugins** or client actions are Copilot plugins that invoke client code, and are available for users within the context of client experiences of finance and operations apps. Developers are able to define plugins that convert the functionality, operations, and business logic of the X++ code base into actions the user can invoke and communicate with in natural language through the Copilot interface. For example, with client plugins Copilot in finance and operations can be extended to let the user perform application actions, fill in form values, or ask questions requiring calculations and business logic from the application by entering prompts in natural language in Copilot.

This topic contains detail on the components and options of client plugins. For a step-by-step tutorial for creating a client plugin, see [Tutorial: Create client plugins for Copilot in finance and operations apps](tutorial-create-client-plugins.md).

> [!IMPORTANT]
> - Developing client plugins is available only in the [unified developer experience](https://learn.microsoft.com/power-platform/developer/unified-experience/finance-operations-dev-overview). See [Tutorial: Install the Finance and Operations Provisioning App](https://learn.microsoft.com/power-platform/admin/unified-experience/tutorial-install-finance-operations-provisioning-app) for information on creating a unified developer environment from the [unified admin experience for finance and operations apps](https://learn.microsoft.com/power-platform/admin/unified-experience/finance-operations-apps-overview).
> - The ability to extend Copilot in finance and operations with client plugins is available on finance and operations version 10.0.40 and higher. See [Service update availability](../get-started/public-preview-releases.md) for more information on release schedules for finance and operations apps.
> - This is a preview feature. It is subject to the [preview supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2105274). Preview features aren't meant for production use and may have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback. For more information about preview releases, see [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).

## Architecture of client plugins
There are two key components in developing client plugins: 
1. The plugin must be created in the Copilot in Finance and Operation chatbot in Microsoft Copilot Studio. The plugin understand the user's natural language prompt and manages the orchestration and execution of the plugin based on the user's Copilot prompt. On execution the plugin sends an event to the finance and operations client.
2. A method must be created in X++ that is invoked by Copilot Studio, and executes the defined client code. When Copilot Studio sends the event to finance and operations apps, the class is called, running the client operations. 

See [Architecture of Copilot in finance and operations](copilot-architecture.md) for additional detail on the plugin architecture and execution.

## Defining the action in X++
In X++ you must create a class that is called and can execute code when Copilot Studio invokes the method. The new class must be a subclass extending the `SysCopilotChatAction` class.

### Data contract
The method must be defined as a data contract. This enables passing complex data types as input and output parameters of the method so serialization and deserialization of the parameters isn't required for the communication Copilot Studio. Define the method as a data contract by decorating it with the `DataContract` attribute. See [Using Data Contracts in X++](https://learn.microsoft.com/dynamicsax-2012/appuser-itpro/using-data-contracts-in-x) for more information in implementing data contracts in X++.

### Provide the action definition
Decorate the class with the `SysCopilotChatActionDefinition` function to define the action.

#### Parameters
| Parameter | Type | Description | 
| --- | --- | --- | 
| IdentifierName | string | An identifier for the plugin action. This is the identifier defined for the event that is sent from Copilot Studio to finance and operations apps, the event returning output parameters from finance and operations apps to Copilot Studio. Use the [identifierStr](../dev-ref/xpp-compile-time-functions#identifierstr) compile-time function to convert the identifier to a string. | 
| Name | string | A descriptive name provided for the action. | 
| Description | string | A natural language description of the action. This field is not currently used by Copilot, but should be provided in the definition. In a future release this property will be used to enhance intelligent orchestration of plugins by linking the action to user intent. | 
| MenuItemName | string | The menu item associated with the action.<br><br> User permissions to invoke the client action are determined by defining permissions to the menu item selected in this parameter. You can use an existing menu item or create a new one to associate with the action. |
| MenuItemType | securingMenuItemType | The [MenuItemType](https://learn.microsoft.com/dotnet/api/dynamics.ax.application.menuitemtype) value for the menu item defined in the MenuItemName parameter. |

#### Example

```x++
[SysCopilotChatActionDefinition(
    identifierStr(MS.ServerForm.CopilotExample.ClientNavigate),
    'Navigate',
    'Navigates to or opens a defined form in the application client',
    menuItemActionStr(SysCopilotChatCustomNavigateAction), MenuItemType::Action)]
```

### Define the action type
The action type is a mechanism for controlling the availability of the action to Copilot. This allows you to define the appropriate context in which the action should be available to be performed by the user with Copilot.

#### Global actions
Global actions have no specific application context and are available for the user to perform on any form in the application, any time the Copilot chat panel is open. Define a client action as global by decorating the method with the `SysCopilotChatGlobalAction` attribute.

#### Form actions
Form actons are only applicable in the context of a specific form. For example, the action may invoke a form action like approving an invoice record or performing a calculation on data that is available when on a specific form. 

Decorate the method with one or more `ExportMetadata` attributes to define the form or forms on which the action is available. The action is then only considered in the Copilot plugin orchestration if the user is on one of the forms defined for the action. The action will otherwise be ignored by the orchestration.

The following example defines the action as a form action available on the `Batch` and `BatchGroup` forms.

```x++
[ExportMetadata(formStr(BatchGroup), identifierStr(FormName))]
[ExportMetadata(formStr(Batch), identifierStr(FormName))]
[Export(identifierstr(Microsoft.Dynamics.AX.Application.SysCopilotChatAction))]
```

#### Runtime actions
Runtime actions are availabe at any point the developer defines they are available in code by adding the action to, or removing the action from, a list of available actions. 

Use `SysCopilotChatAction::addToCopilotRuntimeActions` to add the client action to the list of available actions.

| Parameter | Type | Description |
| --- | --- | --- |
| runtimeAction | ClassName | The class name of the runtime action to add to the list of runtime actions available to the user. |
| removeOnFormChange | boolean | True to unregister the action when the user navigates to a different form. Otherwise, false. |
| context | object | The context object instance to pass to the action with it executes. Optional |

Use `SysCopilotChatAction::removeFromCopilotRuntimeActions` to remove a runtime action from the list of actions available to Copilot for the user.

| Parameter | Type | Description |
| --- | --- | --- |
| runtimeAction | ClassName | The class name of the action to remove from the list of runtime actions available to Copilot for the user. |

### Define input parameters
Input and output parameters are used to pass values between the Copilot orchestration and finance and operations client. Input parameters can be defined for the action, and are received with the event payload sent from Copilot Studio to finance and operations apps to invoke the action. These are defined as data members of the data contract.

Use the `SysCopilotChatActionInputParameter` function to define the properties of the parameter:

| Parameter | Type | Description | 
| --- | --- | --- | 
| description | string | A natural language description of the parameter. This is not currently used by Copilot, but should be provided in the definition. In a future release it will be used to enhance intelligent orchestration of plugins by linking the parameter to the user's natural language prompt. |
| isRequired | boolean | Determines whether a value must be defined for the parameter |

You must also define an accessor method for each parameter to get and set the variables. The following example shows defining a `menuItemName` input parameter for a navigation action that will navigate the client to the form defined for this parameter.

```x++
    [DataMember('menuItemName'),
    SysCopilotChatActionInputParameter('The name of the menu for the form to launch', true)]
    internal MenuItemName parmMenuItemName(MenuItemName _menuItemName = menuItemName)
    {
        menuItemName = _menuItemName;
        return menuItemName;
    }
```

### Define output parameters
Output parameters can be defined for the action, and are sent with the event payload from finance and operations apps to Copilot Studio as a response. Like input parameters, these are defined as data members of the data contract. For example, if your client action performs a calculation based on the form data, your output parameter can be the result of the calculation that can then be sent to Copilot as a response.

Use the `SysCopilotChatActionOutputParameter` function to define the properties of the parameter:

| Parameter | Type | Description | 
| --- | --- | --- | 
| description | string | A natural language description of the parameter. This is not currently used by Copilot, but should be provided in the definition. In a future release it will be used to enhance intelligent orchestration of plugins by linking the parameter to the user's natural language prompt. |

You must define an accessor method for each output parameter. The following example shows defining a `navResponse` output parameter for a client action, which will the action response sent back to Copilot and can be displayed to the user in the chat session.

```x++
    [DataMember('navResponse'),
    SysCopilotChatActionOutputParameter('The response from the navigation, whether an error or successful navigation')]
    public str parmNavResponse(str _navResponse = navResponse)
    {
        navResponse = _navResponse;
        return navResponse;
    }
```

### Defining the execution of the client action
Create an instance of the `SysCopilotChatActionDefinitionAttribute` class to define business logic that should execute for action and set any output parameter values. When calling `executeAction`, the output parameters will be reserealized and returned in the event payload to Copilot Studio.

For example, if your Copilot action is to navigate to a form in the client, you can use the following to perform the navigation and define a message to be set as the output parameter to be sent to Copilot.

```x++
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
```

## Creating a plugin in Microsoft Copilot Studio

### Invoking the client action
When the user enters a prompt in the Copilot chat panel with the intent of invoking a client action, the prompt is sent to Copilot Studio to manage the orchestration and invocation of the action based on the user intent. When Copilot Studio determines which plugin to invoke for the prompt, for client actions the plugin must define which X++ action to invoke. Copilot Studio then sends an event to finance and operations to invoke the action. The event payload defines the values of the input parameters for the X++ class as a JSON object.

In your topic or plugin in Copilot Studio, create an **Event activity** node that defines the event to send to X++ and the event payload to be included as input parameters for the client action. The **Name** property for the event activity is the `IdentifierName` parameter defined in the `SysCopilotChatActionDefinition` attribute of your X++ class. The **Value** property of the event activity is a JSON string defining the values for the input parameters to be sent to the X++ class.

### Receiving output parameters of the client action
Your client action may have output parameters that you want to return as a natural language response to the user in Copilot or to continue with additional action. When the client action is executed in X++ the output parameters are sent as an event to Copilot Studio.

In Copilot Studio, you will need a separate topic created to receive the response from the X++ class. Create a topic with an **Event received** trigger. The **Event name** property of the trigger must be the value of the `IdentifierName` parameter defined in the `SysCopilotChatActionDefinition` attribute of your X++ class. The **System.Activity.Text** variable is set to the event payload as a JSON string. You can add a **Parse value** node to the topic to parse the **System.Activity.Text** value for the values of the client action output parameters.
