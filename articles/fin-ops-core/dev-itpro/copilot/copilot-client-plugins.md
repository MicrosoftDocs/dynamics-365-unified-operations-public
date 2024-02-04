---
title: Create client plugins for Copilot in finance and operations apps
description: This article provide guidance
author: jaredha
ms.author: jaredha
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 12/11/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Create client plugins for Copilot in finance and operations apps

[!include [banner](../includes/banner.md)]

**Client plugins** or client actions are Copilot plugins that invoke client code. Developers are able to define plugins that convert the functionality, operations, and business logic of the X++ code base into something the user can invoke and communicate with in natural language through the Copilot interface. For example, with client plugins, Copilot can be extended to let the user perform application actions, fill in form values, or ask questions requiring calculations and business logic from the application by entering prompts in natural language in Copilot.

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
| MenuItemName | string | The menu item associated with the action. User permissions to invoke the client action are defined by defining permissions to the menu item defined in this parameter. |
| MenuItemType | securingMenuItemType | The item type for the menu item defined in the MenuItemName parameter. |

#### Example

```x++
[SysCopilotChatActionDefinition(
    identifierStr(MS.ServerForm.CopilotExample.ConvertCurrency),
    'Currency converter',
    'Converts a defined currency value to a foreign currency based on today's exchange rate.',
    menuItemActionStr(SysCopilotChatConvertCurrencyAction), 
    MenuItemType::Action)]

```

### Define the action type
The action type is a mechanism for controlling the availability of the action to Copilot. This allows you to define the appropriate context in which should be available to be performed by the user with Copilot.

#### Global actions
Global actions have no specific application context and are available for the user to perform on any form in the application, any time the Copilot chat panel is open. Define a client action as global by decorating the method with the `SysCopilotChatGlobalAction` attribute.

#### Form actions
Form actons are only applicable in the context of a specific form. For example, the action may invoke a form action like approving an invoice record or performing a calculation on data that is available when on a specific form. 

Decorate the method with one or more `ExportMetadata` attributes to define the form or forms on which the action is available. The action is then only considered in the Copilot plugin orchestration if the user is on one of the forms defined for the action. The action will otherwise be ignored by the orchestration.

The following example defines the action as a form action available on the `Batch` and `BatchGroup` forms.

```x++
[ExportMetadata(formStr(SysCopilotTestActionForm), identifierStr(FormName))]
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
Input parameters can be defined for the action, and are received with the event payload sent from Copilot Studio to finance and operations apps to invoke the action. These are defined as data members of the data contract.

Use the `SysCopilotChatActionInputParameter` function to define the properties of the parameter:

| Parameter | Type | Description | 
| --- | --- | --- | 
| description | string | A natural language description of the parameter. This is not currently used by Copilot, but should be provided in the definition. In a future release it will be used to enhance intelligent orchestration of plugins by linking the parameter to the user's natural language prompt. |
| isRequired | boolean | Determines whether a value must be defined for the parameter |

You must also define an accessor method for each parameter to get and set the variables. The following example shows defining a `currencyAmount` input parameter for a client action.

```x++
    [DataMember('currencyAmount'),
    SysCopilotChatActionInputParameter('The currency value to be converted', true)]
    public Money parmCurrencyAmount(Money _currencyAmount = currencyAmount)
    {
        currencyAmount = _currencyAmount;
        return currencyAmount;
    }
```

### Define output parameters
Output parameters can be defined for the action, and are sent with the event payload from finance and operations apps to Copilot Studio as a response. Like input parameters, these are defined as data members of the data contract.

Use the `SysCopilotChatActionOutputParameter` function to define the properties of the parameter:

| Parameter | Type | Description | 
| --- | --- | --- | 
| description | string | A natural language description of the parameter. This is not currently used by Copilot, but should be provided in the definition. In a future release it will be used to enhance intelligent orchestration of plugins by linking the parameter to the user's natural language prompt. |

You must define an accessor method for each output parameter. The following example shows defining a `convertedValue` output parameter for a client action.

```x++
    [DataMember('convertedValue'),
    SysCopilotChatActionOutputParameter('The converted value after the exchange rate is applied')]
    public Money parmConvertedValue(Money _convertedValue = convertedValue)
    {
        convertedValue = _convertedValue;
        return convertedValue;
    }
```

### Defining the execution of the client action
Create an instance of the `SysCopilotChatActionDefinitionAttribute` class to define business logic that should execute for action and set any output parameter values. When calling `executeAction`, the output parameters will be resealized and returned in the event payload to Copilot Studio.

For example, if you have a `calculateForeignCurrency` class that you want to use to convert your input parameters to a foreign currency value as the Copilot action, you could do the following to call the class and set the `parmConvertedValue` output parameter to the resulting value.

```x++
public void executeAction(SysCopilotChatActionDefinitionAttribute _actionDefinition, object _context)
{
    date exchangeDate = systemDateGet();
    Money foreignCurrencyValue = CurrencyConverter::calculateForeignCurrency(currencyAmount, exchangeDate, currencyCode);
    this.parmConvertedValue(foreignCurrencyValue);
}

```

## Creating a plugin in Microsoft Copilot Studio

### Invoking the client action
When the user enters a prompt in the Copilot chat panel with the intent of invoking a client action, the prompt is sent to Copilot Studio to manage the orchestration and invocation of the action based on the user intent. When Copilot Studio determines which plugin to invoke for the prompt, for client actions the plugin must define which X++ action to invoke. Copilot Studio then sends an event to finance and operations to invoke the action. The event payload defines the values of the input parameters for the X++ class as a JSON object.

In your topic or plugin in Copilot Studio, create an **Event activity** node that defines the event to send to X++ and the event payload to be included as input parameters for the client action. The **Name** property for the event activity is the `IdentifierName` parameter defined in the `SysCopilotChatActionDefinition` attribute of your X++ class. The **Value** property of the event activity is a JSON string defining the values for the input parameters to be sent to the X++ class.

### Receiving output parameters of the client action
Your client action may have output parameters that you want to return as a natural language response to the user in Copilot or to continue with additional action. When the client action is executed in X++ the output parameters are sent as an event to Copilot Studio.

In Copilot Studio, you will need a separate topic created to receive the response from the X++ class. Create a topic with an **Event received** trigger. The **Event name** property of the trigger must be the value of the `IdentifierName` parameter defined in the `SysCopilotChatActionDefinition` attribute of your X++ class. The **System.Activity.Text** variable is set to the event payload as a JSON string. You can add a **Parse value** node to the topic to parse the **System.Activity.Text** value for the values of the client action output parameters.

## Example client plugin
One of the possible use cases for client plugins is to expose business logic contained in X++ to Copilot, making the logic something Copilot "knows" and enabling the user to interact with the logic in natural language. In this example, assume you have an X++ class called `CurrencyConverter` that converts a currency value from the accounting currency to another currency. This example adds `SysCopilotChatConvertCurrencyAction` as a global Copilot action available to the user in Copilot in finance and operations.

### Define the action in X++
This example shows the `SysCopilotChatConvertCurrencyAction` class, which executes the `CurrencyConverter` class with defined input parameters, and returns the `convertedValue` parameter as an output parameter.

```X++
/// <summary>
/// Copilot action to converts a currency value from functional currency to a foreign currency
/// </summary>
using System.ComponentModel.Composition;

[DataContract]
[SysCopilotChatGlobalAction]
[SysCopilotChatActionDefinition(
    identifierStr(MS.ServerForm.CopilotExample.ConvertCurrency),
    'Convert a currency value',
    'Converts a defined currency value to a foreign currency based on the exchange rate for today',
    menuItemActionStr(SysCopilotChatConvertCurrencyAction), 
    MenuItemType::Action)]
public final class SysCopilotChatConvertCurrencyAction extends SysCopilotChatAction
{
    private Money currencyAmount;
    private str currencyCode;
    private Money convertedValue;

    [DataMember('currencyAmount'),
    SysCopilotChatActionInputParameter('The currency value to be converted', true)]
    public Money parmCurrencyAmount(Money _currencyAmount = currencyAmount)
    {
        currencyAmount = _currencyAmount;
        return currencyAmount;
    }

    [DataMember('currencyCode'),
    SysCopilotChatActionInputParameter('The foreign currency into which the currency value will be converted', true)]
    public str parmCurrencyCode(str _currencyCode = currencyCode)
    {
        currencyCode = _currencyCode;
        return currencyCode;
    }

    [DataMember('convertedValue'),
    SysCopilotChatActionOutputParameter('The converted value after the exchange rate is applied')]
    public Money parmConvertedValue(Money _convertedValue = convertedValue)
    {
        convertedValue = _convertedValue;
        return convertedValue;
    }

    public void executeAction(SysCopilotChatActionDefinitionAttribute _actionDefinition, object _context)
    {
        date exchangeDate = systemDateGet();
        Money foreignCurrencyValue = CurrencyConverter::calculateForeignCurrency(currencyAmount, exchangeDate, currencyCode);

        this.parmConvertedValue(foreignCurrencyValue);
    }
}
```

### Create a topic in Copilot Studio to invoke the action
For this example you will need to create two topics in the Copilot in Finance and Operation chatbot in Microsoft Copilot Studio. The first topic initiates the plugin when the user enters a prompt in Copilot indicating intent to convert a currency value. The the topic is triggered, it will determine the input parameters for the action and send them as an event to X++ to call the action.

1. Create a new topic with trigger phrases similar to "Convert a currency value to a foreign currency".
2. Create **Question** nodes in the topic to ask the user to define the currency amount and currency code to which the amount should be converted. Use the user responses to set local variables.
3. With the variables defined, create a new `eventString` variable that will be the JSON payload sent with the event defining the input parameters for the Copilot action in X++.
    - Create a **Set variable value** node.
    - Set the **Set variable** property to `Topic.eventString`.
    - set the **To value** property to the following formula:
    ```powerapps-dot
    Concatenate("{""currencyAmount"": ",
        Topic.currencyAmount,
        ", ""currencyCode"": """,
         Topic.currencyCode,
         """}"
    )        
    ```
4. Create an **Event activity** node that invokes the X++ class.
    - **Name**: MS.ServerForm.CopilotExample.ConvertCurrency
    - **Value**: `Topic.eventString`

### Create a topic for returned output parameters
The second topic receives the output parameters returned from the X++ class, and returns the response to the user in the Copilot chat panel.

1. Create a new topic with a trigger type of **Event received**. In the **On Event Activity properties** pane, set the **Event name** to "MS.ServerForm.CopilotExample.ConvertCurrency".
2. Create a **Parse value** node to parse the JSON string from the event payload.
    - **Parse value**: `System.Activity.Text`
    - **Data type**: "From sample data"
    - Select **Get schema from sample JSON**, and enter the following JSON string to define the schema of the returned parameters:
      ```json
      {
	      "convertedValue":790.00,
	      "currencyAmount":1000.00,
	      "currencyCode":"GBP",
	      "isResponse":true
      } 
      ```
    - **Save as**: Create a `Topic.CurrencyResponse` variable as a record type for the parsed response.
3. Create a **Message** node in the topic with the message "The converted currency value is: `CurrencyResponse.convertedValue`."'

Once you've created your action in X++ and the topics to manage the execution and response, and published and deployed the code, the Copilot chat then has a new capability enabling users to convert currency values as part of a Copilot natural language chat.
