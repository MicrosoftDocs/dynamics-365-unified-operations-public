---
title: Create AI plugins for copilots with finance and operations business logic (preview)
description: Learn how to create AI plugins that are registered in the Dataverse plugin registry and that use finance and operations business logic that can be used in copilot experiences (preview).
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 01/26/2026

---

# Create AI tools with finance and operations business logic (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Finance and operations apps let you create AI tools to extend the capabilities of agents and copilots that invoke business logic in finance and operations apps. You can add these tools to the in-app Copilot for finance and operations apps, other Microsoft copilots or agents, or custom agents.

The tools you create can use the finance and operations business logic that you want to use in your agents across Microsoft products. These tools are headless operations. They don't require specific context in the finance and operations client. You enable them by creating an X++ class deployed in the environment, decorated with attributes identifying the class as one that an AI agent can invoke. The class has request and response parameters defining the inputs received from the agent, and the outputs returned after the business logic executes.

Agents can invoke these classes with business logic in two ways:

1. The **Dynamics 365 ERP MCP** server makes the classes available to find and invoke by using the `find_actions` and `invoke_action` tools. When you create and deploy the classes in the environment, and define appropriate security for the associated menu action item, the actions become automatically accessible through the MCP server. Learn more in [Use Model Context Protocol for finance and operations](copilot-mcp#using-actions-that-invoke-application-code).
1. You can also build a separate API and related tool in Dataverse to call the class. If you don't use the MCP server, you need to create Dataverse and Copilot Studio objects that make the operation available as a tool in your agent.

Users in copilot chat or autonomous agents can then invoke the business logic in natural language and receive copilot responses that are based on the business logic of the finance and operations code base.

Finance and operations apps offer many scenarios and opportunities for AI tools. The following table provides some examples.

| Operation type | Example of a user prompt |
| -------------- | ------------------------ |
| Return calculated values | "What is the current balance for customer Fabrikam?" |
| Create, update, or delete a record in finance and operations apps | "Create a new task to follow up with Contoso with a due date of next Monday." |
| Perform an action | "Approve Paul Cannon's expense report." |

> [!IMPORTANT]
> This feature is a preview feature. It's subject to the [preview supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2105274). Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release, so that customers can get early access and provide feedback. Learn more in [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).

## Prerequisites

Before you begin developing AI tools that use finance and operations business logic, your system must meet the following requirements:

- You must have a unified developer environment. You can develop AI tools that use finance and operations business logic only in the [unified developer experience](/power-platform/developer/unified-experience/finance-operations-dev-overview). Learn more about how to create a unified developer environment in [unified admin experience for finance and operations apps](/power-platform/admin/unified-experience/finance-operations-apps-overview) and in the [Tutorial: Install the Finance and Operations Provisioning App](/power-platform/admin/unified-experience/tutorial-install-finance-operations-provisioning-app).
- The following solutions must be installed in the Power Platform environment. If they're not already installed, learn more about how to install Dynamics 365 solution packages in Dataverse in [Manage Dynamics 365 apps](/power-platform/admin/manage-apps).

  - The Copilot for finance and operations package, which includes the following solutions:

    - Copilot for finance and operations apps
    - Copilot for finance and operations generation solution
    - Copilot for finance and operations anchor solution

  - Finance and Operations Virtual Entity

- The **(Preview) Custom API Generation** feature must be enabled in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md).

## Architecture of AI tools for finance and operations apps

The development of AI tools for finance and operations apps has three key components:

- A class that you create in X++ and deploy to the finance and operations environment. This class defines the business logic to run when the AI tool is called. Copilot Studio invokes this class. It runs the defined application code and returns the response to the agent. The agent then translates the response into natural language for the user.
- A Dataverse Custom API that you create in Dataverse.
- A tool that you add for the operation in your agent in Copilot Studio.

Learn more about the tool architecture and execution in [Architecture of Copilot in finance and operations](copilot-architecture.md).

## Define the operation in X++

In X++, you must create a class that Copilot Studio calls and runs code when it invokes the tool.

### AI tool

You must add the `AIPluginOperationAttribute` attribute to the new class to define it as an AI operation. This attribute enables the class to be associated with the related Custom API and AI tool that you must create in Dataverse for the class.

### Data contract

You must add the `DataContract` attribute to the method to define it as a data contract. You can then pass complex data types as input and output parameters of the method, so that serialization and deserialization of the parameters aren't required for communication with Copilot Studio. Learn more about how to implement data contracts in X++ in [Using Data Contracts in X++](/dynamicsax-2012/appuser-itpro/using-data-contracts-in-x).

### Custom API

The new class creates the definition for a [Dataverse custom API](/power-apps/developer/data-platform/custom-api). You must create this custom API in Dataverse and associate it with your class. When you invoke the tool in Copilot Studio, it calls the custom API and runs the logic in your class.

The new class must implement the `ICustomAPI` class, and you must decorate it with the `CustomAPIAttribute` class. These attributes indicate that the class is a Custom API that Dataverse can call.

#### Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| CustomAPIName | string | The natural language name of the action. |
| CustomAPIDescription | string | A natural language definition of what the action does. Copilot Studio uses this definition for plugin orchestration, to determine when the plugin should be invoked based on the user's prompt. |

#### Request parameters

Request parameters define the action inputs for the API. The action inputs pass values from the Copilot orchestration and the finance and operations runtime. In the class, use `CustomAPIRequestParameter` to define any custom API request parameters for the API.

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

To define the code that runs when the operation is invoked, use the `run` method of the `ICustomAPI` interface. This code is the business logic that defines the action that runs for the AI operation. In this method, set the values of any response properties that you want to return to Copilot Studio when the operation is completed.

## Define tool security

You must assign each tool operation to a security role that grants user access to perform the operation from an agent. For each class, follow these steps.

1. In Visual Studio, in your development project, create an action menu item. Give it a name that's similar to the name of your class.
1. Set the following properties for the new action menu item:

    - Set the **ObjectType** value to **Class**.
    - Set the **Object** value to the name of your class.

1. Add the menu item to a [security role](../sysadmin/role-based-security.md) as a privileged item.

After you create and deploy the classes and security objects, you can verify the configuration by viewing the custom API on the **Dataverse Custom APIs** page in finance and operations apps (**System administration** \> **Setup** \> **Synchronize Dataverse Custom APIs**). On this page, ensure that your class is included in the grid. If your class is listed on the page with the appropriate security role, this is an indicator that it's configured correctly to be invoked by an AI tool. The grid includes every class that meets the following criteria:

- It implements the `ICustomApi` interface.
- It contains the `[CustomApi]` attribute.
- It has an associated action menu item that is included in a security privilege that is assigned to a duty/role.

> [!NOTE]
> After deploying the new classes to your environment, you need to ensure the extension cache is flushed before the new classes can be invoked. Flushing the cache is done as part of database synchronization, or by running the `SysFlushAOD` class in your environment. Run `SysFlushAOD` by adding the class runner to your environment URL:
>
> `https://<environment>.operations.dynamics.com/?cmp=usmf&mi=SysClassRunner&cls=SysFlushAOD`

## Create the AI tool

After you define the operation in X++ and deploy it in your finance and operations environment, you must create the custom API in Dataverse. You can then use the Dataverse connector to add the Custom API as a tool in your agent. Create a Dataverse Custom API and add the API as an unbound action to your agent using the Dataverse connector. Create the object in your Power Apps solution that you deploy with your agent or extension.

### Create the Dataverse custom API

The [Dataverse custom API](/power-apps/developer/data-platform/custom-api) is the API object that has the request and response parameters used to invoke the X++ class in finance and operations apps. Follow the steps in this section to create the custom API.

#### Create the API

1. In [Power Apps](https://make.powerapps.com), open your solution.
1. Select **New** \> **More** \> **Other** \> **Custom API**.
1. On **New Custom API**, enter the following details for the API:

    - **Unique Name**: Enter the unique name in the following format:

        \<*Your solution's prefix*\>\_\<*Name of the X++ class for the action*\>

        For example, enter **jch_CustomAPICalculateCustomerBalance**.

    - **Name** and **Display Name**: Enter a friendly name to identify the custom API.
    - **Description**: Enter a description of the business operation that the API performs. This description should match the description that is provided in the X++ class.
    - **Plugin Type**: Select **Microsoft.Dynamics.Fno.Copilot.Plugins.InvokeFnoCustomAPI**.

1. Save and close the new custom API.

#### Add request parameters to the API

After you create the API, you must add parameters to it. To create request parameters, follow these steps for each `CustomAPIRequestParameter` property in your X++ class.

1. In your solution, select **New** \> **More** \> **Other** \> **Custom API Request Parameter**.
1. On **New Custom API Request Parameter**, enter the following details for the parameter:

    - **Custom API**: Select the custom API that you created.
    - **Unique Name**: Use the following format:

        \<*Your solution's prefix*\>\_\<*Name of the X++ class for the action*\>\_\<*Name of the data member for the CustomAPIRequestParameter property in your class*\>

        For example, enter **jch_CustomAPICalculateCustomerBalance_accountNumber**.

    - **Name** and **Display Name**: Enter the name of the data member for the property in your X++ class.
    - **Description**: Enter a description of the property that is defined in your class.
    - **Type**: Select the data type of the property.
    - **Is Optional**: Select whether the property is a required or optional input for the action.

1. Save and close the custom API request parameter.

#### Add response properties to the API

Response properties are the outputs of the action. To create response properties, follow these steps for each `CustomAPIResponseProperty` property in your X++ class.

1. In your solution, select **New** \> **More** \> **Other** \> **Custom API Response Property**.
1. On **New Custom API Response Property**, enter the following details for the parameter:

    - **Custom API**: Select the custom API that you created.
    - **Unique Name**: Use the following format:

        \<*Your solution's prefix*\>\_\<*Name of the X++ class for the action*\>\_\<*Name of the data member for the CustomAPIResponseProperty property in your class*\>

        For example, enter **jch_CustomAPICalculateCustomerBalance_balance**.

    - **Name** and **Display Name**: Enter the name of the data member for the property in your X++ class.
    - **Description**: Enter a description of the property that is defined in your class.
    - **Type**: Select the data type of the property.

1. Save and close the custom API response property.

## Add the action as a tool in your agent

For each operation with a Custom API, you can add the action to any agent in Copilot Studio with access to the object. For example, you can add the action to Copilot for finance and operations apps or custom agents. 

To add your AI operation to the in-app sidecar chat experiences in finance and operations apps, or to a custom copilot, follow these steps.

1. In Copilot Studio, open the agent where you want to add the new capability.
1. On the **Tools** page, select **Add a tool**.
1. Search for and select the **Microsoft Dataverse** connector.
1. Select the **Perform an unbound action in selected environment** connector action.
1. Select a **Connection**, and select **Add and configure**.
1. In the **Details** section:
   
   1. Provide a **Name** value that's specific to the operation. This value could be the same name as the Custom API.
   1. Provide a **Description** that describes the operation to be performed. This description is the field the agent orchestrator uses to understand when generative orchestration needs to call the operation.
   1. Select the appropriate **Authentication** option for your agent.

1. In the **Inputs** section:

   1. For the **Environment**, set the **Fill using** value to **Custom value**. You can select a specific environment or select the **(Current)** environment if you deploy the agent solution in other environments.
   1. For the **Action Name**, set the **Fill using** value to **Customer value**. In the **Choose an action** drop-down list, select the unique name of your Custom API created earlier.
   1. Select the **Add input** action to add each request parameter from your Custom API. For each parameter, provide a **Description** for the input to help generative AI fill the properties from the prompt.

1. In the **Completion** section, open the settings for each of the outputs from the Custom API, and provide a **Description** for each.
1. **Save** and close the new tool.

Learn more about how to add actions to your agent in [Add tools to custom agents](/microsoft-copilot-studio/advanced-plugin-actions).

### Configure the copilot to invoke the action

The agent where you add the new tool must be able to determine when it should invoke the action as part of the agent orchestration. The copilot needs a way to match a user's prompt in the chat pane or autonomous trigger to your action or sequence of actions. There are two ways to enable the copilot to include the action in the copilot orchestration:

- If your agent uses classic orchestration, create a topic that calls the action.
- Enable the copilot to let generative AI orchestrate copilot topics and actions.

#### Create a topic in the copilot

If your agent uses classic orchestration, it responds to users by triggering the topic that has trigger phrases that most closely match the user's prompt. It then fills in the topic inputs from the conversation context. To confirm whether your copilot is in classic mode, select **No** in the **Use generative AI orchestration for your agent's response?** section of the **Generative AI** tab in the agent settings.

When you enable classic orchestration in an agent, you must create a separate topic to invoke the action that you add to the agent.

1. In Copilot Studio, open the agent.
1. On the **Topics** tab, select **Add a topic** \> **From blank**.
1. On the **Trigger** node, edit the trigger phrases to provide the types of user prompts that should trigger the action.
1. Add a **Plugin action** node to the topic for your action:

    1. Select **Add node (+)**.
    1. Select **Add a tool** \> **Tool**.
    1. Select your action in the list.
    1. If you don't define a response for the tool in the **Completion** section of the tool definition, you might want to add a **Message** node to provide a response to the user or agent after the action runs.
    1. Save the topic, and publish the change to the agent.

Learn more in [Call an existing tool from within a topic](/microsoft-copilot-studio/advanced-plugin-actions#call-an-existing-tool-from-within-a-topic).

#### Let generative AI orchestrate copilot topics and actions

When you enable generative AI orchestration in an agent, Copilot Studio uses generative AI to determine the user's intent. It then uses generative AI to identify the most appropriate action, topic, or combination of actions and topics that it should invoke to respond to the user prompt or autonomous trigger. In this case, you don't have to create a separate topic to invoke the tool. Learn more about generative mode in [Orchestrate agent behavior with generative AI](/microsoft-copilot-studio/advanced-generative-actions).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
