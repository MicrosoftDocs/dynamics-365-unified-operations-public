---
title: Create AI plugins for copilots with finance and operations business logic (preview)
description: Learn how to create AI plugins that are registered in the Dataverse plugin registry and that use finance and operations business logic that can be used in copilot experiences (preview).
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/03/2025

---

# Create AI plugins for copilots with finance and operations business logic (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Finance and operations apps let you create AI plugins to extend the capabilities of copilot experiences in Microsoft Copilot Studio. These plugins can be added to the in-app Copilot for finance and operations apps, other Microsoft copilots, or custom copilots.

The plugins that you create can use finance and operations business logic that you want to use in your copilots across Microsoft products. When the plugins are created and deployed in X++, they're automatically registered in the Dataverse plugin registry. In this way, they become available for use in copilots that are connected to the registry. Copilot users can then chat in natural language and receive copilot responses that are based on the business logic of the finance and operations code base.

These plugins are headless operations. They don't require specific context in the finance and operations client. (For a description of headless and client plugins, and an explanation of the differences between them, see [Plugin context](copilot-architecture.md#plugin-context).)

For example, a method in finance and operations apps has a calculation for customer balances, and input and output parameters are specified. Information about a customer's balance is useful even outside the context of finance and operations apps. It might also make sense in other natural language contexts, such as a Teams chat or an Outlook email message. By using the feature that this article describes, you can package the customer balance calculation as a copilot plugin and publish it to copilots across Microsoft products. Users can then easily perform the operation in natural language from the Copilot chat experience.

Finance and operations apps offer many scenarios and opportunities for copilot plugins. The following table provides some examples.

| Operation type | Example of a user prompt |
| -------------- | ------------------------ |
| Return calculated values | "What is the current balance for customer Fabrikam?" |
| Create, update, or delete a record in finance and operations apps | "Create a new task to follow up with Contoso with a due date of next Monday." |
| Perform an action | "Approve Paul Cannon's expense report." |

> [!IMPORTANT]
> This feature is a preview feature. It's subject to the [preview supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2105274). Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release, so that customers can get early access and provide feedback. For more information about preview releases, see [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).

## Prerequisites

Before you begin to develop AI plugins that use finance and operations business logic, your system must meet the following requirements:

- You must have a unified developer environment. The development of AI plugins that use finance and operations business logic is available only in the [unified developer experience](/power-platform/developer/unified-experience/finance-operations-dev-overview). For information about how to create a unified developer environment from the [unified admin experience for finance and operations apps](/power-platform/admin/unified-experience/finance-operations-apps-overview), see [Tutorial: Install the Finance and Operations Provisioning App](/power-platform/admin/unified-experience/tutorial-install-finance-operations-provisioning-app).
- Your environment must be on version 10.0.40 proactive quality update 1 (PQU-1) with platform version 7.0.7279.80 or later.
- The following solutions must be installed in the Power Platform environment. If they aren't already installed, see [Manage Dynamics 365 apps](/power-platform/admin/manage-apps) for information about how to install Dynamics 365 solution packages in Dataverse.

    - The Copilot for finance and operations package, which includes the following solutions:

        - Copilot for finance and operations apps
        - Copilot for finance and operations generation solution
        - Copilot for finance and operations anchor solution

    - Finance and Operations Virtual Entity

- The **(Preview) Custom API Generation** feature must be enabled in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md).

## Plugin granularity and operations

Copilot plugins that are registered in the Dataverse plugin registry can have one-to-many operations. Users who have access to a plugin must have security access to all the operations or functions in that plugin. For finance and operations apps, plugin operations are grouped into plugins based on security roles. This approach ensures appropriate access to the operations by role.

For example, you create the following plugin operations. Each operation is assigned to privileges that are associated with the appropriate security roles. The plugins are then created or updated in the Dataverse plugin registry with the defined operations.

| Plugin (security role) | Plugin operation |
| ---------------------- | ---------------- |
| Collections Manager | <ul><li>Get customer balance</li><li>Dispute invoice</li><li>Write off invoice</li></ul> |
| Collections Agent | <ul><li>Get customer balance</li><li>Dispute invoice</li></ul> |
| Sales Associate | <ul><li>Get customer balance</li><li>Increase credit limit</li><li>Check on-hand inventory</li></ul> |
| Inventory Manager | <ul><li>Check on-hand inventory</li><li>Adjust cycle count</li><li>Reorder stock</li></ul> |

A plugin operation can be added to multiple plugins, based on the security roles that have privileges to the action menu item for that operation.

## Architecture of AI plugins for finance and operations apps

The development of AI plugins for finance and operations apps has three key components:

- A method must be created in X++. Copilot Studio invokes this method. It runs the defined application code and returns the response to Copilot. Copilot then translates the response into natural language for the user.
- The plugin must be created in Dataverse with an associated custom API. In this way, it can be added to copilots in Copilot Studio.
- The plugin operation must be added as an action in your selected copilot.

For more information about the plugin architecture and execution, see [Architecture of Copilot in finance and operations](copilot-architecture.md).

## Define the plugin operation in X++

In X++, you must create a class that is called and can run code when Copilot Studio invokes the plugin.

### AI plugin

You must decorate the new class with the `AIPluginOperationAttribute` attribute to define it as an AI operation. Classes that are decorated with this attribute are registered in the Plugin Registration Service in Dataverse during synchronization of Dataverse custom APIs. As a result, a record for the plugin operation is created in the `AIPlugin` and `AIPluginOperation` tables in Dataverse.

### Data contract

You must decorate the method with the `DataContract` attribute to define it as a data contract. Complex data types can then be passed as input and output parameters of the method, so that serialization and deserialization of the parameters aren't required for communication with Copilot Studio. For more information about how to implement data contracts in X++, see [Using Data Contracts in X++](/dynamicsax-2012/appuser-itpro/using-data-contracts-in-x).

### Custom API

The new class creates the definition for a [Dataverse custom API](/power-apps/developer/data-platform/custom-api). This custom API is created in Dataverse and associated with your class during the synchronization process. When the plugin is invoked in Copilot Studio, the custom API is called, and the logic in your class is invoked.

The new class must implement the `ICustomAPI` class, and you must decorate it with the `CustomAPIAttribute` class. In this way, the class gets attributes that indicate that it's a Custom API that can be called from Dataverse.

#### Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| CustomAPIName | string | The natural language name of the action. |
| CustomAPIDescription | string | A natural language definition of what the action does. Copilot Studio uses this definition for plugin orchestration, to determine when the plugin should be invoked based on the user's prompt. |

#### Request parameters

Request parameters define the action inputs for the API. The action inputs are used to pass values from the Copilot orchestration and the finance and operations runtime. In the class, you must use `CustomAPIRequestParameter` to define any custom API request parameters for the API.

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| description | string | The natural language description of the parameter. Copilot Studio uses this description to match text from the user's prompt to the parameter. |
| isOptional | boolean | A *true*/*false* value that indicates whether a value must be defined for the parameter when a request is made to the custom API. If the parameter is optional when the action is invoked, set this parameter to *true*. Otherwise, set it to *false*. |

You must also define an accessor method for each parameter to get and set the variables. The following example shows the definition of an `accountNumber` request parameter. The parameter name is defined as a data member of the data contract.

```X++
[CustomAPIRequestParameter('The customer account number', true),
    DataMember('accountNumber')]
    public CustAccount parmAccountNum(CustAccount _accountNum = accountNum)
    {
        accountNum = _accountNum;
        return accountNum;
    }
```

#### Response properties

Use `CustomAPIResponseProperty` to define response properties for the custom API.

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| description | string | The natural language description of the response property. |

You must also define an accessor method for the properties to get and set the variables. The following example shows the definition of a `balance` response property, which is the output of the action.

```X++
[CustomAPIResponseProperty('The current customer account balance'),
    DataMember('balance')]
    public AmountCur parmBalance(AmountCur _balance = balance)
    {
        balance = _balance;
        return balance;
    }
```

#### Define the operation

To define the code that runs when the operation is invoked, use the `run` method of the `ICustomAPI` interface. This code is the business logic that defines the action that is run for the AI operation. In this method, set the values of any response properties that should be returned to Copilot Studio when the operation is completed.

## Define plugin security

You must assign each plugin operation to a security role that grants user access to perform the operation from Copilot. When finance and operations apps synchronize the `AIPlugin` and `AIPluginOperation` records in Dataverse, the records are grouped based on the security role that the operation is assigned to. The operation is generated in Dataverse only if it's assigned to a security role.

For each class, follow these steps.

1. In Visual Studio, in your development project, create an action menu item. Give it a name that is similar to the name of your class.
1. Set the following properties for the new action menu item:

    - Set the **ObjectType** value to **Class**.
    - Set the **Object** value to the name of your class.

1. Add the menu item to a [security role](../sysadmin/role-based-security.md) as a privileged item.

After you create and deploy the classes and security objects, you can verify the configuration by viewing the custom API on the **Dataverse Custom APIs** page in finance and operations apps (**System administration** \> **Setup** \> **Synchronize Dataverse Custom APIs**). On this page, ensure that your class is included in the grid. The grid includes every class that meets the following criteria:

- It implements the `ICustomApi` interface.
- It contains the `[CustomApi]` attribute.
- It has an associated action menu item that is included in a security privilege that is assigned to a duty/role.

> [!NOTE]
> The menu item for the class must be assigned to a security role. Otherwise, the custom API, AI plugin, and AI plugin operation records aren't created in Dataverse.
>
> After deploying the new classes to your environment, you need to ensure the extension cache is flushed before the new classes can be invoked. This is done as part of database synchronization, or by running the `SysFlushAOD` class in your environment. You can do this by adding the class runner to your environment URL:
>
> `https://<environment>.operations.dynamics.com/?cmp=usmf&mi=SysClassRunner&cls=SysFlushAOD`

## Create the Copilot plugin

After the operation is defined in X++ and deployed in your finance and operations environment, you must create the custom API and AI plugin in Dataverse. The AI plugin must be added to the Dataverse plugin registry to make it available so that it can be added to agents as an action. The plugin is configured to invoke the custom API, which runs the code that is defined in X++.

Three objects must be created in Dataverse to call the code in finance and operations apps: a Dataverse custom API, an AI plugin, and an AI plugin operation. These objects should be created in the Power Apps solution that is deployed with your agent or extension.

### Create the Dataverse custom API

The [Dataverse custom API](/power-apps/developer/data-platform/custom-api) is the API object that has the request and response parameters that are used to invoke the X++ class in finance and operations apps. Complete the procedures in this section to create the custom API.

#### Create the API

1. In [Power Apps](https://make.powerapps.com), open your solution.
1. Select **New** \> **More** \> **Other** \> **Custom API**.
1. On the **New Custom API** page, enter the following details for the API:

    - **Unique Name**: The unique name must be in the following format:

        \<*Your solution's prefix*\>\_\<*Name of the X++ class for the action*\>

        For example, enter **jch_CustomAPICalculateCustomerBalance**.

    - **Name** and **Display Name**: Enter a friendly name to identify the custom API.
    - **Description**: Enter a description of the business operation that the API performs. This description should match the description that is provided in the X++ class.
    - **Plugin Type**: Select **Microsoft.Dynamics.Fno.Copilot.Plugins.InvokeFnoCustomAPI**.

1. Save and close the new custom API.

#### Add request parameters to the API

After you create the API, you must add parameters to it. To create request parameters, follow these steps for each `CustomAPIRequestParameter` property in your X++ class.

1. In your solution, select **New** \> **More** \> **Other** \> **Custom API Request Parameter**.
1. On the **New Custom API Request Parameter** page, enter the following details for the parameter:

    - **Custom API**: Select the custom API that you created.
    - **Unique Name**: Use the following format:

        \<*Your solution's prefix*\>\_\<*Name of the X++ class for the action*\>\_\<*Name of the data member for the CustomAPIRequestParameter property in your class*\>

        For example, enter **jch_CustomAPICalculateCustomerBalance_accountNumber**.

    - **Name** and **Display Name**: You should enter the name of the data member for the property in your X++ class.
    - **Description**: Enter a description of the property that is defined in your class.
    - **Type**: Select the data type of the property.
    - **Is Optional**: Select whether the property is a required or optional input for the action.

1. Save and close the custom API request parameter.

#### Add response properties to the API

Response properties are the outputs of the action. To create response properties, follow these steps for each `CustomAPIResponseProperty` property in your X++ class.

1. In your solution, select **New** \> **More** \> **Other** \> **Custom API Response Property**.
1. On the **New Custom API Response Property** page, enter the following details for the parameter:

    - **Custom API**: Select the custom API that you created.
    - **Unique Name**: Use the following format:

        \<*Your solution's prefix*\>\_\<*Name of the X++ class for the action*\>\_\<*Name of the data member for the CustomAPIResponseProperty property in your class*\>

        For example, enter **jch_CustomAPICalculateCustomerBalance_balance**.

    - **Name** and **Display Name**: You should enter the name of the data member for the property in your X++ class.
    - **Description**: Enter a description of the property that is defined in your class.
    - **Type**: Select the data type of the property.

1. Save and close the custom API response property.

### Create the AI plugin

The AI plugin is the grouping of AI operations that are associated with the security role. The AI plugin record is the registration for the plugin in the Dataverse plugin registry. The plugin should be based on a specific security role. Users who have access to the plugin should have permissions to perform all operations in it.

1. In your solution, select **New** \> **More** \> **Other** \> **AIPlugin**.
1. On the **New AIPlugin** page, enter the following details for the AI plugin record:

    - **Name**: Use the following format:

        \<*Your solution's prefix*\>\_\<*Name of the security role*\>

        For example, enter **jch_SalesTeamCopilotRole**.

    - **PluginType**: Select **Dataverse**.
    - **ModelName**: Use the label for the security role in finance and operations apps. This label is shown for the plugin in Copilot Studio.
    - **ModelDescription** and **HumanDescription**: Provide a description of the plugin and related operations.

1. Save and close the AI plugin record.

### Create the AI plugin operation

The AI plugin operation is the registration in the Dataverse plugin registry for the business operation that is defined in your X++ class. The operation is assigned to an AI plugin in the registry. It then becomes available so that it can be added as an action in an agent. The operation is associated with the custom API to ensure that the correct logic is invoked when the action is included in an agent.

1. In your solution, select **New** \> **More** \> **Other** \> **AIPluginOperation**.
1. On the **New AIPluginOperation** page, enter the following details for the AI plugin operation record:

    - **Name**: Use the following format:

        \<*Your solution's prefix*\>\_\<*Name of the X++ class for the operation*\>

        For example, enter **jch_CustomAPICalculateCustomerBalance**.

    - **AIPlugin**: Select the `AIPlugin` record that you created.
    - **OperationId**: Use the following format:

        \<*Your solution's prefix*\>\_\<*Name of the X++ class for the operation*\>

    - **AI Plugin Operation Export Key**: Use the following format:

        aiplugin.name=\<*Name of the AI plugin*\>,operationid=\<*Name of the AI plugin operation*\>

        For example, enter **aiplugin.name=jch_SalesTeamCopilotRole,operationid=jch_CustomAPICalculateCustomerBalance**.

    - **Description**: Enter a description of the operation from your X++ class.

1. Save and close the AI plugin operation record.

## Add the action to your copilot

For each operation that is listed in the plugin registry, you can add the action to any copilot that is connected to the registry in Copilot Studio. For example, you can add the action to Copilot for finance and operations apps or custom copilots.

To add your AI operation to the in-app sidecar chat experiences in finance and operations apps, or to a custom copilot, follow these steps.

1. In Copilot Studio, open the copilot where you want to add the plugin capability.
1. On the **Actions** page, select **Add an action**.
1. In the **Search** field, search for the name of your AI plugin operation. Select your plugin.
1. Follow the steps in the wizard. Select the inputs and outputs from your custom API.
1. Select **Finish**.

For more information about how to add actions to your copilot, see [Use actions with custom copilots in Copilot Studio (preview)](/microsoft-copilot-studio/advanced-plugin-actions).

### Configure the copilot to invoke the action

The copilot where you added the new action must be able to determine when it should invoke the action as part of the copilot orchestration. The copilot needs a way to match a user's prompt in the chat pane to your action or sequence of actions. There are two ways to enable the copilot to include the action in the copilot orchestration:

- In the copilot, create a topic that calls the action.
- Enable the copilot to let generative AI orchestrate copilot topics and actions.

#### Create a topic in the copilot

If the default classic mode is used in a copilot, the copilot responds to users by triggering the topic that has trigger phrases that most closely match the user's prompt. It then fills in the topic inputs from the conversation context. To confirm that your copilot is in classic mode, select the **Classic** option in the **How should your copilot decide how to respond** section of the **Generative AI** tab in the copilot settings.

When classic mode is enabled in a copilot, you must create a separate topic to invoke the action that is added to the copilot.

1. In Copilot Studio, open the copilot.
1. On the **Topics** tab, select **Add a topic** \> **From blank**.
1. On the **Trigger** node, edit the trigger phrases to provide the types of user prompts that should trigger the action.
1. Add a **Plugin action** node to the topic for your action:

    1. Select **Add node (+)**.
    1. Select **Class an action** \> **Plugin (preview)**.
    1. Select your action in the list.
    1. Save the topic, and publish the change to the copilot.

For more information, see [Call an action from within a topic](/microsoft-copilot-studio/advanced-plugin-actions#call-action-from-within-a-topic).

#### Let generative AI orchestrate copilot topics and actions

When you enable generative mode in a copilot, Copilot Studio uses generative AI to determine the user's intent. It then uses generative AI to identify the most appropriate action, topic, or combination of actions and topics that should be invoked to respond to the user prompt.

When generative mode is enabled in a copilot, you don't have to create a separate topic to invoke the action. For more information about generative mode, see [Orchestrate copilot topics and actions with generative AI (preview)](/microsoft-copilot-studio/advanced-generative-actions).

> [!IMPORTANT]
> Generative mode is currently in preview. You might consider testing this mode for your custom copilots that include AI actions that use finance and operations business logic. Generative mode isn't currently supported in Copilot for finance and operations apps. However, it should become supported and enabled by default in Copilot for finance and operations apps in a future release, as feature and quality benchmarks are validated.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
