---
title: Create AI plugins for copilots with finance and operations business logic (preview)
description: Learn how to create AI plugins that are registered in the Dataverse plugin registry and that use finance and operations business logic that can be used in copilot experiences (preview).
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/24/2024

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

Use the `run` method of the `ICustomAPI` interface to define the code that runs when the operation is invoked. This code is the business logic that defines the action that is run for the AI operation. In this method, set the values of any response properties that should be returned to Copilot Studio when the operation is completed.

## Define plugin security

You must assign each plugin operation to a security role that grants user access to perform the operation from Copilot. When finance and operations apps synchronize the `AIPlugin` and `AIPluginOperation` records in Dataverse, the records are grouped based on the security role that the operation is assigned to. The operation is generated in Dataverse only if it's assigned to a security role.

For each class, follow these steps.

1. In Visual Studio, in your development project, create an action menu item. Give it a name that is similar to the name of your class.
1. Set the following properties for the new action menu item:

    - Set the **ObjectType** value to **Class**.
    - Set the **Object** value to the name of your class.

1. Add the menu item to a [security role](../sysadmin/role-based-security.md) as a privileged item.

> [!NOTE]
> The menu item for the class must be assigned to a security role. Otherwise, the custom API, AI plugin, and AI plugin operation records aren't created in Dataverse. <br><p>
> After deploying the new classes to your environment, you need to ensure the extension cache is flushed before the new classes can be invoked. This is done as part of database synchronization, or by running the `SysFlushAOD` class in your environment. You can do this by adding the class runner to your environment URL:<br><p>
> `https://<environment>.operations.dynamics.com/?cmp=usmf&mi=SysClassRunner&cls=SysFlushAOD`

## Generate the Copilot plugin

After the operation is defined in X++ and deployed in your finance and operations environment, you must generate the custom API and AI plugin in Dataverse. The AI plugin is added to the Dataverse plugin registry and can then be added to copilots as an action. The plugin is configured to invoke the custom API, which runs the code that is defined in X++.

To generate the custom API and AI plugin, follow these steps.

1. Open the finance and operations apps client for the environment where you deployed your new X++ class.
1. Open the **Synchronize Dataverse Custom APIs** page (**System administration** \> **Setup** \> **Synchronize Dataverse Custom APIs**). If the menu navigation isn't available in your environment, you can go directly to the menu item by adding the `mi=CustomApiTable` parameter to the environment URL. Here's an example:

    `https://<environment>.operations.dynamics.com/?cmp=USMF&mi=CustomApiTable`

1. On the list page, ensure that your class is included in the grid. The grid includes every class that meets the following criteria:

    - It implements the `ICustomApi` interface.
    - It contains the `[CustomApi]` attribute.
    - It has an associated action menu item that is included in a security privilege that is assigned to a duty/role.

1. Select the **Synchronize** action.

The synchronization process synchronizes all listed classes with Dataverse and adds them to the **Dynamics 365 ERP Virtual Entities** solution. You can confirm that the classes were created and added to the solution in the **Custom API** list, together with the associated request parameters and response properties.

For each class that also contains the `[AIPluginOperationAttribute]` attribute, a record for the AI plugin is created in the same solution. An `AIPlugin` record is created for each security role that is configured in finance and operations apps. This record contains an assigned class that has the `[AIPluginOperationAttribute]` attribute. The associated `AIPluginOperaton` records are linked to the plugin.

## Add the action to your copilot

For each operation that is listed in the plugin registry, you can add the action to any copilot that is connected to the registry in Copilot Studio. For example, you can add the action to Copilot for finance and operations apps or custom copilots.

> [!NOTE]
> You can't currently add the plugins to some Microsoft copilots, such as Copilot for Microsoft 365.

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
