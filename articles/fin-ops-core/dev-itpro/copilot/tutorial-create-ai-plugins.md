---
title: Tutorial - Create AI plugins for copilots with finance and operations business logic
description: This tutorial shows how to create an AI plugin that is registered in the Dataverse plugin registry and that uses finance and operations business logic that can be used in copilot experiences.
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
   - bap-template
ms.date: 10/01/2024

---

# Tutorial: Create AI plugins for copilots with finance and operations business logic

[!include [banner](../includes/banner.md)]

Finance and operations apps let you create AI plugins to extend the capabilities of copilot experiences in Microsoft Copilot Studio by using business logic in finance and operations code. These plugins are headless operations that don't require specific application context in the finance and operations client. They can be added to Copilot for finance and operations apps to extend the in-app chat experience, or they can be added to other custom copilots. For more information, see [Create AI plugins for copilots with finance and operations business logic](copilot-ai-plugins.md).

## Scenario

You're creating an AI plugin that calculates the balance of a customer account in finance and operations apps. This plugin lets users interact with the business logic in natural language, and it invokes X++ in response to user prompts in the copilot chat. You can then add the capability to the in-app chat for Copilot for finance and operations apps, or to any custom copilot.

Here's an overview of the steps in this tutorial:

1. In your unified developer environment, create a class in X++ to define the plugin operation. Add security privileges for the new class.
2. In Dataverse, create a Custom API to invoke the X++ class.
3. In Dataverse, create the AI plugin and related plugin operations.
4. Add the AI plugin as an action in your custom copilot.

## Prerequisites

This tutorial has the following prerequisites:

- You must have a unified developer environment. The development of AI plugins that use finance and operations business logic is available only in the [unified developer experience](/power-platform/developer/unified-experience/finance-operations-dev-overview). For information about how to create a unified developer environment from the [unified admin experience for finance and operations apps](/power-platform/admin/unified-experience/finance-operations-apps-overview), see [Tutorial: Install the Finance and Operations Provisioning App](/power-platform/admin/unified-experience/tutorial-install-finance-operations-provisioning-app).
- Your environment must be on version 10.0.40 proactive quality update 1 (PQU-1) with platform version 7.0.7279.80 or later.
- The following solutions must be installed in the Power Platform environment. If they aren't already installed, see [Manage Dynamics 365 apps](/power-platform/admin/manage-apps) for information about how to install Dynamics 365 solution packages in Dataverse.

    - The Copilot for finance and operations package, which includes the following solutions:

        - Copilot for finance and operations apps
        - Copilot for finance and operations generation solution
        - Copilot for finance and operations anchor solution

    - Finance and Operations Virtual Entity

- The **(Preview) Custom API Generation** feature must be enabled in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md).

## Step 1: Define the plugin operation in X++

In your unified developer environment, you must create a class in X++ that is called and can run code when Copilot Studio invokes the plugin. This class encapsulates the code/business logic that defines the AI operation.

1. In Visual Studio, in your development project, create a model that references the following packages. For more information about how to create models and work with unified developer environments, see [Tutorial: Write, deploy, and debug X++ code](/power-platform/developer/unified-experience/finance-operations-debug).

    - ApplicationCommon
    - ApplicationFoundation
    - ApplicationPlatform
    - ApplicationSuite
    - ContactPerson
    - Currency
    - Directory

1. Create a class that is named **CustomAPICalculateCustomerBalance**. Add the following code to it.

    ```X++
    [CustomAPI('Calculate customer balance', 'Calculates the current balance for a customer in the local currency defined for the customer')]
    [AIPluginOperationAttribute]
    [DataContract]
    public final class CustomAPICalculateCustomerBalance implements ICustomAPI
    {
        private CustAccount accountNum;
        private CurrencyCode currencyCode;
        private boolean customerFound;
        private AmountCur balance;
        CustTable custTable;
    
        [CustomAPIRequestParameter('The customer account number', true),
            DataMember('accountNumber')]
            public CustAccount parmAccountNum(CustAccount _accountNum = accountNum)
        {
            accountNum = _accountNum;
            return accountNum;
        }
    
        [CustomAPIResponseProperty('The currency code for the customer balance'),
            DataMember('currencyCode')]
            public CurrencyCode parmCurrencyCode(CurrencyCode _currencyCode = currencyCode)
        {
            currencyCode = _currencyCode;
            return currencyCode;
        }
    
        [CustomAPIResponseProperty('Indicator whether the customer record exists'),
            DataMember('customerFound')]
            public boolean parmCustomerFound(boolean _customerFound = customerFound)
        {
            customerFound = _customerFound;
            return customerFound;
        }
    
        [CustomAPIResponseProperty('The current customer account balance'),
            DataMember('balance')]
            public AmountCur parmBalance(AmountCur _balance = balance)
        {
            balance = _balance;
            return balance;
        }
    
        public void run(Args _args)
        {
            changecompany('usmf') //Can add company as input to allow switching
            {
                custTable = CustTable::find(this.parmAccountNum());
                if (this.parmAccountNum())
                {
                    if (custTable)
                    {
                        this.parmCustomerFound(true);
                        this.parmCurrencyCode(custTable.Currency);
                        this.parmBalance(custTable.balanceAllCurrency());
                    }
                }
            }
        }
    }
    ```

1. In your development project, add an action menu item. Set the following property values for it:

    - **Name:** CustomAPICalculateCustomerBalance
    - **Object Type:** Class
    - **Object:** CustomAPICalculateCustomerBalance

1. Create a **Security Privilege** item that is named **CopilotCalculateCustomerBalancePrivilege**.
1. Add an entry point to the new privilege. Set the following property values for it:

    - **Name:** CustomAPICalculateCustomerBalance
    - **Object Type:** MenuItemAction
    - **Object Name:** CustomAPICalculateCustomerBalance
    - **Access Level:** Create

1. Create a **Security Role** item that is named **SalesTeamCopilotRole**.
1. Add a privilege to the new role. Set the properties for it so that they reference the **CopilotCalculateCustomerBalancePrivilege** privilege that you created.
1. Save, build, and deploy the code to your finance and operations environment.

## Step 2: Create the Dataverse Custom API

1. Open the [Power Apps maker portal](https://make.powerapps.com).
2. Create a new solution with the **Display name** of **Demo Sales Copilot**. Select the **Publisher** for the copilot, and note the **Prefix** of the selected publisher. For example, `cr689` if you use the CDS Default Publisher. Use the prefix for your selected solution when creating the objects in the solution, replacing `cr689` where needed.
3. On the action ribbon in the solution, select **New \> More \> Other \> Custom API**.
4. Enter the following detail for the Custom API, and save:
   - **Unique Name:** cr689_CustomAPICalculateCustomerBalance
   - **Name:** Calculate customer balance
   - **Display Name:** Calculate customer balance
   - **Description:** Calculates the current balance for a customer in the local currency defined for the customer
   - **Binding Type:** Global
   - **Plugin Type:** Microsoft.Dynamics.Fno.Copilot.Plugins.InvokeFnoCustomAPI
5. On the action ribbon in the solution, select **New \> More \> Other \> Custom API Request Parameter**.
6. Enter the following detail for the Custom API Request Parameter, and save:
   - **Custom API:** Calculate customer balance
   - **Unique Name:** cr689_CustomAPICalculateCustomerBalance_accountNumber
   - **Name:** accountNumber
   - **Display Name:** accountNumber
   - **Description:** The customer account number
   - **Type:** String
   - **Is Optional:** No
7. On the action action ribbon in the solution, select **New \> More \> Other \> Custom API Response Property**.
8. Enter the following detail for the Custom API Response Property, and save:
   - **Custom API:** Calculate customer balance
   - **Unique Name:** cr689_CustomAPICalculateCustomerBalance_balance
   - **Name:** balance
   - **Display Name:** balance
   - **Description:** The current customer account balance
   - **Type:** Decimal
9. Repeat steps 7 and 8 to create the Custom API Response Properties for each of the two remaining output parameters, **currencyCode** and **customerFound**, using the names, descriptions, and data types from the X++ class above.

## Step 3: Create the AI plugin in Dataverse

1. On the action ribbon in your solution, select **New \> More \> Other \> AI Plugin**.
2. Enter the following detail for the AI Plugin record, and save:
   - **Name:** cr689_SalesTeamCopilotRole
   - **PluginType:** Dataverse
   - **HumanName:** Sales Team Copilot
   - **HumanDescription:** This plugin provides actions for the sales team
   - **ModelName:** Sales Team Copilot
   - **ModelDescription:** This plugin provides actions for the sales team
3. On the action ribbon in your solution, select **New \> More \> Other \> AI Plugin Operation**.
4. Enter the following detail for the AI Plugin Operation record, and save:
   - **Name:** cr689_CustomAPICalculateCustomerBalance
   - **AIPlugin:** cr689_SalesTeamCopilotRole
   - **OperationId:** cr689_CustomAPICalculateCustomerBalance
   - **AI Plugin Operation Export Key:** aiplugin.name=cr689_SalesTeamCopilotRole,operationid=cr689_CustomAPICalculateCustomerBalance
   - **Custom API:** Calculate customer balance
   - **Description:** Calculates the current balance for a customer in the local currency defined for the customer

## Step 4: Add the plugin as an action in your copilot

1. Open [Copilot Studio](https://web.powerva.microsoft.com), and select your environment.
1. Select an existing custom copilot, or create a new custom copilot.
1. In the copilot, on the **Actions** menu, select **Add an action**.
1. On the **Choose an action** page, search for and select the **Calculate customer balance** plugin operation.
1. On the **Review and Finish** page, in the **Review inputs and outputs** section, select **Edit**.
1. Under **Additional inputs**, select **Add**, and then select the **cr689_CustomAPICalculateCustomerBalance_accountNumber** input.
1. Select **Save** and then **Finish**.

> [!NOTE]
> This tutorial assumes that you enabled generative mode in your copilot for plugin orchestration. If you use the default classic mode in your copilot, you must complete the extra step of creating a topic in the copilot to invoke the action. For more information, see [Configure the copilot to invoke the action](copilot-ai-plugins.md#configure-the-copilot-to-invoke-the-action).

## Step 5: Test the new plugin action

To test the plugin, you can use the **Test your copilot** pane in Copilot Studio. Alternatively, you can publish the copilot to a channel, such as Teams. In the chat pane, enter prompts to ask about customer balances from your finance and operations environment. For example, ask, "What is the current balance for customer account US-001?"

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
