---
title: Tutorial: Create AI plugins for copilots with finance and operations business logic
description: This article provides guidance on creating AI plugins registered in the Dataverse plugin registry using finance and operations business logic to be used in copilot experiences
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
   - bap-template
ms.date: 07/05/2024

---

# Tutorial: Create AI plugins for copilots with finance and operations business logic

[!include [banner](../includes/banner.md)]

Finance and operations apps enables the creation of AI plugins to extend the capabilities of copilot experiences in Microsoft Copilot Studio, using the business logic in finance and operations code. These are headless operations that don't require specific application context in the finance and operations client, and can be added to **Copilot for finance and operations apps** to extend in in-app chat experience, or in other custom copilots. For more information, see [Create AI plugins for copilots with finance and operations business logic](copilot-ai-plugins.md).

## Scenario
In this scenario, you create an AI plugin that calculates the balance of a customer account in finance and operations apps. This enables the user to interact with the business logic in natural language, invoking X++ to respond to the user prompt in the copilot chat. This becomes a capability that can be added to the **Copilot for finance and operations apps** in-app chat, or to any custom copilot.

Here's an overview of the steps in this tutorial:
1. In your unified developer environment, create a class in X++ to define the plugin operation, and add security privileges for the new class.
2. In the finance and operations environment, run the process to generate the AI plugin and related plugin operations in Dataverse.
3. Add the AI plugin as an action in your custom copilot.

## Prerequisites

This tutorial has the following prerequisites:
- You must have a unified developer environment. The development of AI plugins with finance and operations business logic is available only in the [unified developer experience](/power-platform/developer/unified-experience/finance-operations-dev-overview). For information about how to create a unified developer environment from the [unified admin experience for finance and operations apps](/power-platform/admin/unified-experience/finance-operations-apps-overview), see [Tutorial: Install the Finance and Operations Provisioning App](/power-platform/admin/unified-experience/tutorial-install-finance-operations-provisioning-app).
- Your environment must be on version 10.0.40 PQU-3 with platform version 7.0.7279.80 or later.
- The following solutions must be installed in the Power Platform environment. If not already installed, see [Manage Dynamics 365 apps](/power-platform/admin/manage-apps) for information on installing Dynamics 365 solution packages in Dataverse.
   - The Copilot for finance and operations package, which includes the following solutions:
      - Copilot for finance and operations apps
      - Copilot for finance and operations generation solution
      - Copilot for finance and operations anchor solution
   - Finance and Operations Virtual Entity
 - The **(Preview) Custom API Generation** feature must be enabled in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md).

## Step 1: Define the plugin operation in X++
In your unified developer environment, you must create a class in X++ that is called and can execute code when Copilot Studio invokes the plugin. This class encapsulates the code/business logic that defines the AI operation.
1. In your development project in Visual Studio, create a new model that references the following packages. For more information on creating models and working with unified developer environments, see [Tutorial: Write, deploy, and debug X++ code](/power-platform/developer/unified-experience/finance-operations-debug).
   - ApplicationCommon
   - ApplicationFoundation
   - ApplicationPlatform
   - ApplicationSuite
   - ContactPerson
   - Currency
   - Directory
2. Create a class named **CustomAPICalculateCustomerBalance**, and add the following code to the new class:
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

3. In your development project, add an **Action Menu Item**. Set the following property values:
   - **Name:** CustomAPICalculateCustomerBalance
   - **Object Type:** Class
   - **Object:** CustomAPICalculateCustomerBalance
4. Create a new **Security Privilege** item named **CopilotCalculateCustomerBalancePrivilege**. Add an **Entry Point** to the new privilege:
   - **Name:** CustomAPICalculateCustomerBalance
   - **Object Type:** MenuItemAction
   - **Object Name:** CustomAPICalculateCustomerBalance
5. Create a new **Security Role** item named **SalesTeamCopilotRole**. Add a privilege to the role, setting the properties to reference the **CopilotCalculateCustomerBalancePrivilege** privilege created in the previous step.
6. Save, build, and deploy the code to your finance and operations apps environment.

## Step 2: Generate the AI plugin in Dataverse
1. In finance and operations apps, navigate to the **Synchronize Dataverse Custom APIs** page (System administration >> Setup >> Synchronize Dataverse Custom APIs). If the menu navigation isn't available in your environment, you can navigate to menu item directly by adding the `&mi=CustomApiTable` parameters to the environment URL. For example: <p>
`https://<environment>.operations.dynamics.com/?cmp=usmf&mi-CustomApiTable`
2. In the list page, ensure you see the **CustomAPICalculateCustomerBalance** class in the list.
3. Select the **Synchronize** action.

You can then verify the custom API and AI plugins were created in your Dataverse environment. Open the **Dynamics 365 ERP Virtual Entities** solution in the [Power Apps portal](https://make.powerapps.com). Verify:
   - The **mserp_xppapi_SalesTeamCopilotRole** record was created in the **AIPlugin** list.
   - The **Calculate customer balance** record was created in the **AIPluginOperation** list.
   - The **Calculate customer balance** record was created in the **Custom API list**, with related **Custom API Request Parameter** record and **Custom API Response Property** records.

## Step 3: Add the plugin as an action in your copilot
1. Open [Copilot Studio](https://web.powerva.microsoft.com) and select your environment.
2. Select an existing custom copilot or create a new custom copilot.
3. In the copilot, select the **Actions** menu, and select **Add an action**.
4. In the **Choose an action** page search for and select the **Calculate customer balance** plugin operation.
5. On the **Review and Finish** page, select **Edit** in the **Review inputs and outputs** section.
6. Select **Add** under **Additional inputs**, and select the **mserp_CustomAPICalculateCustomerBalance_accountNumber** input.
7. Select **Save** and **Finish**.

> [!NOTE]
> This tutorial assumes you have enabled generative mode in your copilot for plugin orchestration. If you have selected to use the default classic mode in your copilot you have an additional step of creating a topic in the copilot to invoke the action. See [Configuring the copilot to invoke the action](copilot-ai-plugins.md#configuring-the-copilot-to-invoke-the-action) for more information.

## Step 4: Test the new plugin action
To test the plugin you can use the **Test your copilot** panel in Copilot Studio, or publish the copilot to a channel, such as Teams. In the chat pane, enter prompts to ask about customer balances from your finance and operations apps environment. For example: "What is the current balance for customer account US-001?"

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
