---
title: Create AI plugins for copilots with finance and operations business logic
description: This article provides guidance on creating AI plugins registered in the Dataverse plugin registry using finance and operations business logic to be used in copilot experiences
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.search.form:
ms.topic: how-to
ms.date: 4/5/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Create AI plugins for copilots with finance and operations business logic (preview)

[!include [banner](../includes/banner.md)]

Finance and operations apps enables the creation of AI plugins to extend the capabilities of copilot experiences in Microsoft Copilot Studio. These plugins can added to the in-app **Copilot for finance and operations apps**, other Microsoft copilots, or custom copilots. With finance and operations apps, you can create plugins using finance and operations business logic to use in your copilots across Microsoft products. The plugins, when created and deployed in X++, are automatically registered in the Dataverse plugin registry, making them available for use in copilots connected to the registry. This enables copilot users to chat in natural language, receiving copilot responses based in the business logic of the finance and operations code base. 

These plugins are headless operations. They don't require specific context in the finance and operations client. See [Plugin context](copilot-architecture.md#plugin-context) for a description and differentiation between headless and client plugins. For example, a method in finance and operations apps may have a calculation for a customer balance, with specified input and output parameters. A customer's balance doesn't require finance and operations application context to be useful, and may make sense in other natural language contexts, like a Teams chat or Outlook email message. With this capability, the customer balance calculation can be packaged as a copilot plugin and published to copilots across Microsoft products, enabling users to perform the oeprations headlessly in natural language from the Copilot chat experience.

There are many finance and operations scenarios and opportunities for copilot plugins. For example:

| Operation type | Example |
| -------------- | ------- |
| Return calculated values | "What is the current balance for customer Fabrikam?" | 
| Create, update, or delete a record in finance and operations apps | "Create a new task to follow up with Contoso with a due date of next Monday." | 
| Perform an action | "Approve Paul Cannon's expense report." | 

> [!IMPORTANT]
> This feature is a preview feature. It's subject to the [preview supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2105274). Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback. For more information about preview releases, see [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).

## Prerequisites

Before you begin developing AI plugins with finance and operations business logic, your system must meet the following requirements:
- You must have a unified developer environment. The development of AI plugins with finance and operations business logic is available only in the [unified developer experience](/power-platform/developer/unified-experience/finance-operations-dev-overview). For information about how to create a unified developer environment from the [unified admin experience for finance and operations apps](/power-platform/admin/unified-experience/finance-operations-apps-overview), see [Tutorial: Install the Finance and Operations Provisioning App](/power-platform/admin/unified-experience/tutorial-install-finance-operations-provisioning-app).
- Your environment must be on version 10.0.40 PQU-3 with platform version 7.0.7279.80 or later.
- The following solutions must be installed in the Power Platform environment. If not already installed, see [Manage Dynamics 365 apps](https://learn.microsoft.com/power-platform/admin/manage-apps) for information on installing Dynamics 365 solution packages in Dataverse.
   - The Copilot for finance and operations package, which includes the following solutions:
      - Copilot for finance and operations apps
      - Copilot for finance and operations generation solution
      - Copilot for finance and operations anchor solution
   - Finance and Operations Virtual Entity
 - The **(Preview) Custom API Generation** feature must be enabled in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview).

## Plugin granularity and operations
Copilot plugins registered in the Dataverse plugin registry can have one-to-many operations. Users who have access to the plugin must have security access to all operations or functions in the plugin. For finance and operations apps, plugin operations are grouped into plugins by security role to ensure appropriate access to the operations by role.

For example, you may create the following plugin operations that are assigned to privileges associated with the respective security roles. The plugins are then created or updated in the Dataverse plugin registry with the defined operations.

| Plugin (security role) | Plugin operation |
| ---------------------- | ---------------- |
| Collections Manager | Get customer balance <br> Dispute invoice <br> Write off invoice |
| Collections Agent | Get customer balance <br> Dispute invoice |
| Sales Associate | Get customer balance <br> Increase credit limit <br> Check on-hand inventory <br> | 
| Inventory Manager | Check on-hand inventory <br> Adjust cycle count <br> Reorder stock |

A plugin operation can be added to multiple plugins, based on the security roles that have privileges to the action menu item for the operation.

## Architecture of AI plugins for finance and operations apps

The development of AI plugins with finance and operations apps has three key components:
- A method must be created in X++. This method is invoked by Copilot Studio and runs the defined application code and returns the response to copilot, which then translates the response into natural language for the user.
- The plugin must be created in the Dataverse, with an associated custom API, making it available to add to copilots in Copilot Studio. 
- The plugin operation must be added as an action in your selected copilot(s).

For more information about the plugin architecture and execution, see [Architecture of Copilot in finance and operations](copilot-architecture.md).

## Defining the plugin operation in X++
In X++ you must create a class that is called and can execute code when Copilot Studio invokes the plugin.

### AI Plugin
The class must be decorated with the `AIPluginOperationAttribute` attribute defining the new class as an AI operation. Classes decorated with this attribute will be registered in the Plugin Registration Service in Dataverse during the process to synchronize Dataverse custom APIs, creating a record for the plugin operation in the `AIPlugin` and `AIPluginOperation` tables in Dataverse.

### Data contract
The method must be defined as a data contract. This enables passing complex data types as input and output parameters of the method so serialization and deserialization of the parameters isn't required for communication with Copilot Studio. Define the method as a data contract by decorating it with the `DataContract` attribute. See [Using Data Contracts in X++](https://learn.microsoft.com/dynamicsax-2012/appuser-itpro/using-data-contracts-in-x) for more information on implmenting data contracts in X++.

### Custom API
Your new class is creating definition for a [Dataverse custom API](https://learn.microsoft.com/power-apps/developer/data-platform/custom-api). The custom API is created in Dataverse and associated with your class during the synchronization process. When the plugin is invoked in Copilot Studio, the custom API is called, invoking the logic in your class.

The new class must implement the `ICustomAPI` class and be decorated with the `CustomAPIAttribute` class. This provides attributes to your new class indicating that it is a Custom API that is callable from Microsoft Dataverse.

**Parameters**

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| CustomAPIName | string | The natural language name for the action. |
| CustomAPIDescription | string | A natural language definition of what the action does. This definition will be used by Copilot Studio for plugin orchestration, determining when to invoke this plugin based on the user's prompt. |

#### Request parameters
Request parameters are used to define the action inputs for the API, which are used to pass values from the Copilot orchestration and finance and operations runtime. In the class you must define any custom API request parameters for the API using `CustomAPIRequestParameter`:

| Parameter | Type | Description | 
| --------- | ---- | ----------- |
| description | string | The natural language description of the parameter. This description is used by Copilot Studio to match text from the user's prompt to the parameter. | 
| isOptional | boolean | Determines whether a value must be defined for the parameter when making a request to the custom API. Set to true if the parameter is optional when invoking the action. Otherwise set to false. | 

You must also define an accessor method for each parameter to get and set the variables. The following examples shows defining an `accountNumber` request parameter. The parameter name is defined as a data member of the data contract.

```x++
[CustomAPIRequestParameter('The customer account number', true),
  DataMember('accountNumber')]
  public CustAccount parmAccountNum(CustAccount _accountNum = accountNum)
  {
    accountNum = _accountNum;
    return accountNum;
  }
```

#### Response properties
Define response properties for the custom API using `CustomAPIResponseProperty`.

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| description | string | The natural language description of the response property. | 

As with request parameters, you must also define an accessor method for the properties to get and set the variables. The following example shows defining a `balance` response property, which is the output of the action.

```x++
[CustomAPIResponseProperty('The current customer account balance'),
  DataMember('balance')]
  public AmountCur parmBalance(AmountCur _balance = balance)
  {
    balance = _balance;
    return balance;
  }
```

#### Define the operation
Use the `run` method of the `ICustomAPI` interface to define the code that runs when the operation is invoked. This is the business logic that defines that action that is run for the AI operation. Within this method set the value(s) of any response properties that should be returned to Copilot Studio when the operation is complete.

## Defining plugin security
Each plugin operation must be assigned to a security role to grant user access to perform the operation from Copilot. When finance and operations synchronizes the `AIPlugin` and `AIPluginOperation` records in Dataverse, they are grouped based on the security role to which the operation is assigned. The operation is only generated in Dataverse if it is assigned to a security role.

For each class:
1. In your development project in Visual Studio, create a new **Action Menu Item** with a name similar to your class.
   - Set the **ObjectType** value to **Class**.
   - Set the **Object** value to the name of your class.
2. Add the menu item as a privileged item to a [security role](../sysadmin/role-based-security).

> [!NOTE]
> The custom API, AI plugin, and AI plugin operation records will not be created in Dataverse if the menu item for the class has not been assigned to a security role.

## Generating the Copilot plugin
With the operation defined in X++ and deployed in your finance and operation environment, you then need to generate the custom API and AI plugin in Dataverse. The AI plugin is added to the Dataverse plugin registry, making it available to add as an action to copilots. Then plugin is configured to invoke the custom API, which runs the code defined in X++.

To generate the custom API and AI plugin:
1. Open the finance and operations apps client for the environment where you deployed your new X++ class.
2. Navigate to **Synchronize Dataverse Custom APIs** page (System administration > Setup > Synchronize Dataverse Custom APIs). If the menu navigation isn't available in your environment you can navigate to the **CustomApiTable** menu item directly by adding the `mi=CustomApiTable` parameter to the environment URL. For example:<br>
   `https://<environment>.operations.dynamics.com/?cmp=USMF&mi=CustomApiTable`
3. In the list page, ensure your class is included in the table as expected. This list will include all classes that meet the following criteria:
   - Implement the `ICustomApi` interface.
   - Contain the `[CustomApi]` attribute.
   - Have an associated ActionMenuItem that is included in a security privilege assigned to a duty/role.
4. Select the **Synchronize** action.

The synchronization process will synchronize all listed classes with Microsoft Dataverse, adding them to the **Dynamics 365 ERP Virtual Entities** solution. You can verify that the classes were created and added to teh solution in the **Custom API** list, with the associated request parameters and response properties.

Each class that also includes the `[AIPluginOperationAttribute]` attribute will have a record created for the AI plugin in the same solution. An `AIPlugin` record is created for each security role configured in finance and operations apps that contains an assigned class with the `[AIPluginOperationAttribute]` attribute, with the associated `AIPluginOperaton` records linked to the plugin.

## Add the action to your copilot

For each operation listed in the plugin registry, you can add teh action to any copilot connected to the registry in Copilot Studio, such as Copilot for finance and operations apps or custom copilots.

> [!NOTE]
> The option is not yet available to add the plugins to some Microsoft copilots, such as Copilot for Microsoft 365.

You can add your AI operation to the in-app sidecar chat experiences in finance and operations apps, or a custom copilot, with the following steps:
1. Open the copilot in Copilot Studio in which you want to add the plugin capability.
2. On the **Actions** page, select **Add an action**.
3. In the **Search** box, search for teh name of your AI plugin operation, and select your plugin.
4. Follow the steps in the wizard, selecting the inputs and outputs from your custom API.
5. Click **Finish**.

See [Use actions with custom copilots in Copilot Studio (preview)](https://learn.microsoft.com/microsoft-copilot-studio/advanced-plugin-actions) for more information on adding actions the actions to your copilot.

### Configuring the copilot to invoke the action
The copilot where you added the new action needs to know when to invoke the action as part of the copilot orchestration. The copilot needs a way to match a user's prompt in the chat panel to your action, or sequence of actions. There are a couple of options for enabling the copilot to include the action in the copilot orchestration:
1. Add a topic to the copilot that calls the action, or
2. Enable the copilot to let generative AI orchestrate copilot topics and actions.

#### Create a topic in the copilot
By default, a copilot responds to users by triggering the topic whose trigger phrases most closely match the user's prompt, and fills the topic inputs from the conversation context. You can verify your copilot is in classic mode by selecting the **Classic** option in the **How should your copilot decide how to respond?** section of the **Generative AI** tab in the copilot settings. When in classic mode, you will need to create a topic to invoke the action added to the copilot.
1. Open the copilot in Copilot Studio.
2. Select the **Topics** tab and select **Add a topic >> From blank**.
3. On the **Trigger** node, edit the trigger phrases to provide the types of user prompts that should trigger the action.
4. Add a **Plugin action** node to the topic for your action:
   - Select **Add node (+)**.
   - Select **Class an action >> Plugin (preview)**.
   - Select your action from the list.
   - **Save** the topic and **Publish** the change to the copilot.
  
See [Call an action from within a topic](https://learn.microsoft.com/microsoft-copilot-studio/advanced-plugin-actions#call-action-from-within-a-topic) for more information.

#### Let generative AI orchestrate copilot topics and actions
When enabling generative mode for the copilot, Copilot Studio uses generative AI to identify the most appropriate action, topic, or combination of actions and topics to respond to a user prompt. Generative AI is used to determine the user's intent and determines the appropriate sequence of actions and topics to invoke to respond to the prompt. When generative mode is enabled for the copilot, you don't need to create a separate topic to invoke the action. See [Orchestrate copilot topics and actions with generative AI (preview)](https://learn.microsoft.com/microsoft-copilot-studio/advanced-generative-actions) for more information on generative mode.

> [!IMPORTANT]
> Generative mode is currently in preview. You may consider testing this mode for your custom copilots that include AI actions with finance and operations business logic. However, enabling generative mode is not yet supported for Copilot for finance and operations apps. Generative mode will be supported and enabled by default in Copilot for finance and operations apps in a future release as feature and quality benchmarks are validated.


