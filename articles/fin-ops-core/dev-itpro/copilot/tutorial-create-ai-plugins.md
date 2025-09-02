---
title: Tutorial - Create AI tools for copilots with finance and operations business logic
description: This tutorial shows how to create an AI tool that that uses finance and operations business logic that can be used in agent experiences.
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
   - bap-template
ms.date: 10/01/2024

---

# Tutorial: Create AI tools with finance and operations business logic

[!include [banner](../includes/banner.md)]

Finance and operations apps let you create AI tools to extend the capabilities of copilot experiences in Microsoft Copilot Studio by using business logic in finance and operations code. These tools are headless operations that don't require specific application context in the finance and operations client. They can be added to Copilot for finance and operations apps to extend the in-app chat experience, or they can be added to other custom copilots. Learn more in [Create AI tools with finance and operations business logic](copilot-ai-plugins.md).

## Scenario

You're creating an AI tool that calculates the balance of a customer account in finance and operations apps. This tool lets users interact with the business logic in natural language, and it invokes X++ in response to user prompts in the copilot chat. You can then add the capability to the in-app chat for Copilot for finance and operations apps, or to any custom copilot. In this scenario, a customer's balance isn't a value stored in a database field, so it wouldn't be retrieved with a simple get operation or by using a knowledge source in Copilot Studio. The AI tool runs application code to perform the calculation and returns a response back to the agent.

Here's an overview of the steps in this tutorial:

1. In your unified developer environment, create a class in X++ to define the tool operation. Add security privileges for the new class.
1. In Dataverse, create a custom API to invoke the X++ class.
1. In Microsoft Copilot Studio, add the API as a tool in your agent.

## Prerequisites

This tutorial has the following prerequisites:

- You must have a unified developer environment. The development of AI tools that use finance and operations business logic is available only in the [unified developer experience](/power-platform/developer/unified-experience/finance-operations-dev-overview). Learn more about how to create a unified developer environment from the [unified admin experience for finance and operations apps](/power-platform/admin/unified-experience/finance-operations-apps-overview) in [Tutorial: Install the Finance and Operations Provisioning App](/power-platform/admin/unified-experience/tutorial-install-finance-operations-provisioning-app).
- The following solutions must be installed in the Power Platform environment. If they aren't already installed, see [Manage Dynamics 365 apps](/power-platform/admin/manage-apps) for information about how to install Dynamics 365 solution packages in Dataverse.

    - The Copilot for finance and operations package, which includes the following solutions:

        - Copilot for finance and operations apps
        - Copilot for finance and operations generation solution
        - Copilot for finance and operations anchor solution

    - Finance and Operations Virtual Entity

- The **(Preview) Custom API Generation** feature must be enabled in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md).

## Step 1: Define the tool operation in X++

In your unified developer environment, you must create a class in X++ that is called and can run code when Copilot Studio invokes the tool. This class encapsulates the code/business logic that defines the AI operation.

1. In Visual Studio, in your development project, create a model that references the following packages. Learn more about how to create models and work with unified developer environments in [Tutorial: Write, deploy, and debug X++ code](/power-platform/developer/unified-experience/finance-operations-debug).

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

## Step 2: Create the Dataverse custom API

1. Open [Power Apps](https://make.powerapps.com).
1. Create a new solution where the **Display name** field is set to **Demo Sales Copilot**. In the **Publisher** field, select the publisher for the copilot. Make a note of the **Prefix** value for the selected publisher. For example, if you select **CDS Default Publisher**, the prefix is **cr689**.

    > [!IMPORTANT]
    > In later steps in this article, where you create the objects in your solution, some of the values that you're instructed to enter use the prefix **cr689** as an example. You must replace this example prefix with the prefix of the publisher that you selected for your solution.

1. On the toolbar in the solution, select **New** \> **More** \> **Other** \> **Custom API**.
1. Enter the following details, and then save the new custom API:

    - **Unique Name:** cr689_CustomAPICalculateCustomerBalance
    - **Name:** Calculate customer balance
    - **Display Name:** Calculate customer balance
    - **Description:** Calculates the current balance for a customer in the local currency defined for the customer
    - **Binding Type:** Global
    - **Plugin Type:** Microsoft.Dynamics.Fno.Copilot.Plugins.InvokeFnoCustomAPI

1. On the toolbar in the solution, select **New** \> **More** \> **Other** \> **Custom API Request Parameter**.
1. Enter the following details, and then save the new custom API request parameter:

    - **Custom API:** Calculate customer balance
    - **Unique Name:** cr689_CustomAPICalculateCustomerBalance_accountNumber
    - **Name:** accountNumber
    - **Display Name:** accountNumber
    - **Description:** The customer account number
    - **Type:** String
    - **Is Optional:** No

1. On the toolbar in the solution, select **New** \> **More** \> **Other** \> **Custom API Response Property**.
1. Enter the following details, and then save the new custom API response property:

    - **Custom API:** Calculate customer balance
    - **Unique Name:** cr689_CustomAPICalculateCustomerBalance_balance
    - **Name:** balance
    - **Display Name:** balance
    - **Description:** The current customer account balance
    - **Type:** Decimal

1. Repeat steps 7 and 8 to create the custom API response property for each of the two remaining output parameters, `currencyCode` and `customerFound`. Use the names, descriptions, and data types from the X++ class earlier in this article.

## Step 3: Add the action as a tool in your agent

1. Open [Copilot Studio](https://web.powerva.microsoft.com), and select your environment.
1. Select an existing agent, or create a new custom agent.
3. In the agent, on the **Tools** menu, select **Add a tool**.
1. Search for and select the **Microsoft Dataverse** connector.
1. Select the **Perform an unbound action in selected environment** connector action.
1. Select a **Connection**, and select **Add and configure**.
1. In the **Details** section, enter the following values:

   1. **Name:** "Calculate customer balance."
   1. **Description:** "Calculates the current balance for a customer in the local currency defined for the customer"

1. In the **Inputs** section, enter the following values:

   1. **Environment:** Set the **Fill using** value to **Custom value**, and select a **Value** of **(Current)**.
   2. **Action Name:** Set the **Fill using** value to **Custom value**, and set the **Value** to `cr689_CustomAPICalculateCustomerBalance`.
   3. Select the **Add input** action, and select `cr689_CustomAPICalculateCustomerBalance_accountNumber`.
   4. Set the **Fill using** value to **Dynamically fill with AI**.
   5. In the **Value** field, select **Customize**.
   6. In the **Description** field for the parameter: "The customer account number."

1. In the **Completion** section:
   
   1. Open the **Advanced** section.
   1. Open the settings for the `cr689_CustomAPICalculateCustomerBalance_balance` output, and enter the following for the **Description**: "The current customer account balance."
   1. Open the settings for the `cr689_CustomAPICalculateCustomerBalance_currencyCode` output, and enter the following for the **Description**: "The currency code for the customer balance."
   1. Open the settings for the `cr689_CustomAPICalculateCustomerBalance_customerFound` output, and enter the following for the **Description**: "Indicator whether the customer record exists."

1. **Save** and close the new tool.


> [!NOTE]
> This tutorial assumes that you enabled generative AI orchestration in your agent. If you use the default classic orchestration in your copilot, you must complete the extra step of creating a topic in the copilot to invoke the action. Learn more in [Configure the copilot to invoke the action](copilot-ai-plugins.md#configure-the-copilot-to-invoke-the-action).

## Step 4: Test the new tool action

To test the tool, you can use the **Test your agent** pane in Copilot Studio. Alternatively, you can publish the agent to a channel, such as Teams. In the chat pane, enter prompts to ask about customer balances from your finance and operations environment. For example, ask, "What is the current balance for customer account US-001?"

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
