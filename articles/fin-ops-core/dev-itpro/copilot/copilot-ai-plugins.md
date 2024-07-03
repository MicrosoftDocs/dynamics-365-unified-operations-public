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

# Create AI plugins for copilots with finance and operations business logic

[!include [banner](../includes/banner.md)]

Microsoft Copilot Studio enables the creation of AI plugins to extend the capabilities of copilot experiences. These plugins can added to the in-app **Copilot for finance and operations apps**, other Microsoft copilots, or custom copilots. With finance and operations apps, you can create plugins using finance and operations business logic to use in your copilots across Microsoft products. The plugins, when created and deployed in X++, are automatically registered in the Dataverse plugin registry, making them available for use in copilots connected to the registry. This enables copilot users to chat in natural language, receiving copilot responses based in the business logic of the finance and operations code base. 

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
