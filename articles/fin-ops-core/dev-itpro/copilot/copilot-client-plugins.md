---
title: Create client plugins for Copilot in finance and operations apps
description: This article provides guidance about how to create client plugins to extend the capabilities of Copilot in finance and operations apps.
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.search.form:
ms.topic: how-to
ms.date: 06/12/2024
audience: Developer
ms.search.region: Global
ms.custom: 
  - bap-template
---

# Create client plugins for Copilot in finance and operations apps

[!include [banner](../includes/banner.md)]

*Client plugins*, or client actions, are Microsoft Copilot plugins that invoke client code and are available for users in the context of client experiences for finance and operations apps. Developers can define plugins that convert the functionality, operations, and business logic of the X++ code base into actions that users can invoke and communicate with in natural language through the Copilot interface. For example, through client plugins, Copilot in finance and operations apps can be extended to let users enter natural language prompts in Copilot to perform application actions, fill in form values, or ask questions that require calculations and business logic from the application.

This article contains details about the components and options of client plugins. For a step-by-step tutorial that shows how to create a client plugin, see [Tutorial: Create client plugins for Copilot in finance and operations apps](tutorial-create-client-plugins.md).

> [!IMPORTANT]
> - The development of client plugins is available only in the [unified developer experience](/power-platform/developer/unified-experience/finance-operations-dev-overview). For information about how to create a unified developer environment from the [unified admin experience for finance and operations apps](/power-platform/admin/unified-experience/finance-operations-apps-overview), see [Tutorial: Install the Finance and Operations Provisioning App](/power-platform/admin/unified-experience/tutorial-install-finance-operations-provisioning-app).
> - The ability to extend Copilot in finance and operations apps with client plugins is available in finance and operations version 10.0.40 and later. For information about release schedules for finance and operations apps, see [Service update availability](../get-started/public-preview-releases.md).
> - This feature is a preview feature. It's subject to the [preview supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2105274). Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback. For more information about preview releases, see [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).

## Architecture of client plugins

The development of client plugins has two key components:

- The plugin must be created by using the **Copilot in Finance and Operation** chatbot in Copilot Studio. The plugin understands the user's natural language prompt, and the orchestration and execution of the plugin are managed based on the user's Copilot prompt. Upon execution, the plugin sends an event to the finance and operations client.
- A method must be created in X++. This method is invoked by Copilot Studio and runs the defined client code. When Copilot Studio sends the event to finance and operations apps, the class is called, and the client operations are run. 

For more information about the plugin architecture and execution, see [Architecture of Copilot in finance and operations](copilot-architecture.md).

## Defining the action in X++

In X++, you must create a class that's called and can run code when Copilot Studio invokes the method. The new class must be a subclass that extends the `SysCopilotChatAction` class.

### Data contract

The method must be defined as a data contract. In this way, complex data types can be passed as input and output parameters of the method. As a result, serialization and deserialization of the parameters aren't required for communication with Copilot Studio. To define the method as a data contract, decorate it with the `DataContract` attribute. For more information about how to implement data contracts in X++, see [Using Data Contracts in X++](/dynamicsax-2012/appuser-itpro/using-data-contracts-in-x).

### Provide the action definition

To define the action, decorate the class with the `SysCopilotChatActionDefinition` function.

#### Parameters

| Parameter | Type | Description | 
| --- | --- | --- | 
| IdentifierName | string | An identifier for the plugin action. It's the identifier that's defined for the event that's sent from Copilot Studio to finance and operations apps, and that returns output parameters from finance and operations apps to Copilot Studio. Use the [identifierStr](../dev-ref/xpp-compile-time-functions.md#identifierstr) compile-time function to convert the identifier to a string. <br><p><br> The identifier name must begin with the prefix `MS.PA` | 
| Name | string | A descriptive name for the action. | 
| Description | string | A natural language description of the action. Although Copilot doesn't currently use this parameter, it should be provided in the definition. In a future release, this parameter will be used to enhance intelligent orchestration of plugins by linking the action to user intent. | 
| MenuItemName | string | <p>The menu item that's associated with the action.</p><p>The permissions to this menu item determine the user permissions to invoke the client action. You can use an existing menu item, or you can create a new one to associate with the action.</p> |
| MenuItemType | securingMenuItemType | The [MenuItemType](/dotnet/api/dynamics.ax.application.menuitemtype) value for the menu item that's defined in the `MenuItemName` parameter. |

#### Example

```x++
[SysCopilotChatActionDefinition(
    identifierStr(MS.PA.CopilotExample.ClientNavigate),
    'Navigate',
    'Navigates to or opens a defined form in the application client',
    menuItemActionStr(SysCopilotChatCustomNavigateAction), MenuItemType::Action)]
```

### Define the action type

The action type is a mechanism for controlling the availability of the action to Copilot. It lets you define the context in which the action should be available for users to perform by using Copilot.

#### Global actions

Global actions have no specific application context and are available for users to perform in any form of the application, whenever the Copilot chat pane is open. To define a client action as global, decorate the method with the `SysCopilotChatGlobalAction` attribute.

#### Form actions

Form actions are applicable only in the context of a specific form. For example, the action might invoke a form action such as approving an invoice record or performing a calculation on data that's available in a specific form. 

To define the form or forms where the action is available, decorate the method with one or more `ExportMetadata` attributes. The action is then considered in the Copilot plugin orchestration only if the user is in one of the forms that are defined for the action. If the user isn't in one of those forms, the orchestration ignores the action.

The following example defines the action as a form action that's available in the `Batch` and `BatchGroup` forms.

```x++
[ExportMetadata(formStr(BatchGroup), identifierStr(FormName))]
[ExportMetadata(formStr(Batch), identifierStr(FormName))]
[Export(identifierstr(Microsoft.Dynamics.AX.Application.SysCopilotChatAction))]
```

#### Runtime actions

Runtime actions are available wherever the developer defines them as available in code by adding them to a list of available actions. 

To add a client action to the list of available actions, use `SysCopilotChatAction::addToCopilotRuntimeActions`.

| Parameter | Type | Description |
| --- | --- | --- |
| runtimeAction | ClassName | The class name of the runtime action to add to the list of runtime actions that are available to the user. |
| removeOnFormChange | boolean | If the value is **true**, the action is unregistered when the user goes to a different form. If it's **false**, the action remains registered. |
| context | object | (Optional) The context object instance to pass to the action when it runs. |

To remove a runtime action from the list of actions that are available to Copilot for the user, use `SysCopilotChatAction::removeFromCopilotRuntimeActions`.

| Parameter | Type | Description |
| --- | --- | --- |
| runtimeAction | ClassName | The class name of the action to remove from the list of runtime actions that are available to Copilot for the user. |

### Define input parameters

Input and output parameters are used to pass values between the Copilot orchestration and the finance and operations client.

Input parameters that are defined for the action are received with the event payload that's sent from Copilot Studio to finance and operations apps to invoke the action. They're defined as data members of the data contract.

To define the properties of an input parameter, use the `SysCopilotChatActionInputParameter` function.

| Parameter | Type | Description | 
| --- | --- | --- | 
| description | string | A natural language description of the parameter. Although Copilot doesn't currently use this parameter, it should be provided in the definition. In a future release, this parameter will be used to enhance intelligent orchestration of plugins by linking the parameter to the user's natural language prompt. |
| isRequired | boolean | A value that determines whether a value must be defined for the parameter. |

For each parameter, you must also define an accessor method to get and set the variables. The following example shows the definition of a `menuItemName` input parameter for a navigation action that has the client go to the form that's defined for this parameter.

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

Output parameters that are defined for the action are sent with the event payload from finance and operations apps to Copilot Studio as a response. Like input parameters, output parameters are defined as data members of the data contract. For example, if your client action performs a calculation that's based on the form data, your output parameter can be the result of the calculation. That result can then be sent to Copilot as a response.

To define the properties of an output parameter, use the `SysCopilotChatActionOutputParameter` function.

| Parameter | Type | Description | 
| --- | --- | --- | 
| description | string | A natural language description of the parameter. Although Copilot doesn't currently use this parameter, it should be provided in the definition. In a future release, this parameter will be used to enhance intelligent orchestration of plugins by linking the parameter to the user's natural language prompt. |

For each output parameter, you must define an accessor method. The following example shows the definition of a `navResponse` output parameter for a client action. This parameter is the action response that's sent back to Copilot and can be shown to the user in the chat session.

```x++
[DataMember('navResponse'),
SysCopilotChatActionOutputParameter('The response from the navigation, whether an error or successful navigation')]
public str parmNavResponse(str _navResponse = navResponse)
{
    navResponse = _navResponse;
    return navResponse;
}
```

### Define the execution of the client action

To define business logic that should run for the action and set any output parameter values, create an instance of the `SysCopilotChatActionDefinitionAttribute` class. When you call `executeAction`, the output parameters are reserialized and returned to Copilot Studio in the event payload.

For example, if your Copilot action is used to go to a form in the client, you can use the following code to perform the navigation and define a message that's set as the output parameter that's sent to Copilot.

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

## Creating topics in Copilot Studio

### Invoke the client action

When the user enters a prompt in the Copilot chat pane with the intent to invoke a client action, the prompt is sent to Copilot Studio so that it can manage the orchestration and invocation of the action, based on the user intent. Copilot Studio determines which plugin to invoke for the prompt. For client actions, the plugin must define which X++ action should be invoked. Copilot Studio then sends an event to finance and operations apps to invoke the action. The event payload defines the values of the input parameters for the X++ class as a JavaScript Object Notation (JSON) object.

In your topic or plugin in Copilot Studio, create an **Event activity** node that defines the event to send to X++ and the event payload to include as input parameters for the client action. The value of the **Name** property of the event activity is the value of the `IdentifierName` parameter that's defined in the `SysCopilotChatActionDefinition` attribute of your X++ class. The value of the **Value** property of the event activity is a JSON string that defines the values for the input parameters that should be sent to the X++ class.

### Receive output parameters of the client action

Your client action might have output parameters that you want to return either as a natural language response to the user in Copilot or to continue with another action. When the client action is run in X++, the output parameters are sent to Copilot Studio as an event.

In Copilot Studio, you must create a separate topic to receive the response from the X++ class. Create a topic that has an **Event received** trigger. The value of the **Event name** property of the trigger must be the value of the `IdentifierName` parameter that's defined in the `SysCopilotChatActionDefinition` attribute of your X++ class. The `System.Activity.Text` variable is set to the event payload as a JSON string. You can add a **Parse value** node to the topic to parse the `System.Activity.Text` value for the values of the output parameters of the client action.

> [!NOTE]
> In a coming release, client plugins will be invoked by generative AI, removing the requirement to create topics to invoke the actions and receive the output parameters.
