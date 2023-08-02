---
# required metadata

title: Cash flow forecasting
description: This article provides an overview of the cash flow forecasting process. It also explains how cash flow forecasting is integrated with other modules in the system.
author: angelad116
ms.date: 07/31/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  LedgerCovParameters
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update

---

# Cash flow forecasting

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

You can use the cash flow forecasting tools to analyze upcoming cash flow and currency requirements, so that you can estimate the company's future need for cash. To obtain a forecast of the cash flow, you must complete the following tasks:

- Identify and list all the liquidity accounts. Liquidity accounts are the company's accounts for cash or cash equivalents.
- Configure the behavior for forecasts of transactions that affect the company's liquidity accounts.

After you've completed these tasks, you can calculate and analyze forecasts of the cash flow and upcoming currency requirements.

## Cash flow forecasting integration

Cash flow forecasting can be integrated with General ledger, Accounts payable, Accounts receivable, Budgeting and inventory management. The forecasting process uses transaction information that is entered in the system, and the calculation process forecasts the expected cash impact of each transaction. The following types of transactions are considered when the cash flow is calculated:

- **Sales orders** – Sales orders that aren't yet invoiced, and that result in physical or financial sales.
- **Free text invoices** – Free text invoices that aren’t posted yet, and that result in financial sales. 
- **Purchase orders** – Purchase orders that aren't yet invoiced, and that result in physical or financial purchases.
- **Accounts receivable** – Open customer transactions (invoices that aren't yet paid).
- **Accounts payable** – Open vendor transactions (invoices that aren't yet paid).
- **Ledger transactions** – Transactions where it's specified that a future posting will occur.
- **Budget register entries** – Budget register entries that are selected for cash flow forecasts.
- **Demand forecasts** – Inventory forecast model lines that are selected for cash flow forecasts.
- **Supply forecasts** – Inventory forecast model lines that are selected for cash flow forecasts.
- **External data source** - External data that's entered or imported into the cash flow forecasts using spreadsheet templates.
- **Project forecasts** - Project management and accounting forecasts using forecast model.
- **Cash flow sales tax authority payments** – Predicted sales tax authority payment amounts and timing that result in financial payments. Enable the feature Cash flow sales tax authority payments.

## Configuration

To configure the cash flow forecasting process, use the **Cash flow forecast setup** page. On this page, you specify the liquidity accounts to track and the default forecasting behaviors for each area.

### General ledger

You must first define the liquidity accounts to track through cash flow forecasting. Typically, these liquidity accounts are main accounts that are associated with the bank accounts that will receive and disburse cash. On the **Cash flow forecast setup** page, on the **General ledger** tab, select the main accounts to include for forecasting. If a bank account has been associated with the main account on the **Bank account** page, it's shown in the **Bank account** field.

You can set up a dependent cash flow forecast for a main account that contains transactions that are directly related to transactions in another main account. Each line that you add in the **In the Dependent accounts** section creates a cash flow forecast amount in a dependent main account. This amount is a percentage of the cash flow amounts to the primary main account that you selected.

First, set the **Main account** field to the primary main account where transactions are expected to initially occur. Set the **Dependent main account** field to the account that will be affected by the initial transaction against the primary main account. Set appropriate values for the other fields on the line. You can change the value in the **Percent** field to reflect the effect of the primary main account on the dependent main account. For a sales or purchase forecast, select a **Terms of payment** value that is typical for most customers or vendors. Set the **Posting type** field to the expected posting type that is related to the cash flow forecast.

### Accounts payable

You can calculate the forecast for purchases by using the setup options on the **Accounts payable** tab of the **Cash flow forecast setup** page. Before you can configure cash flow forecasting for Accounts payable, you must configure terms of payment, vendor groups, and vendor posting profiles.

In the **Purchasing forecast defaults** section, you can select default purchasing behaviors for cash flow forecasting. Three fields determine the time of the cash impact: **Time between delivery date and invoice date**, **Terms of payment**, and **Time between invoice due date and payment date**. The forecast will  use the default setting for the **Terms of payment** field only if a value isn't specified on the transaction. Use a term of payment to describe the most typical number of days for each part of the process.

The **Liquidity accounts for payments** field specifies the liquidity account that is most often used for payments. Use the **Percentage of amount to allocate to cash flow forecast** field to specify whether a percentage of amounts should be used during forecasting. Leave this field blank if the full transaction amounts should be used during forecasting.

You can override the default setting for the **Time between invoice due date and payment date** field for specific vendor groups. The forecast will use the default value from the **Purchasing forecast defaults** section unless a different value is specified for the vendor group that is related to the vendor on the transaction. To override the default value, select a vendor group, and then set the new value for the **Purchasing time** field.

You can override the default setting for the **Liquidity account** field for specific vendor posting profiles. The forecast will use the default value from the **Purchasing forecast defaults** section unless a different liquidity account is specified for the posting profile that is related to the vendor on the transaction. To override the default value, select a posting profile, and then specify the liquidity account that is expected to be affected.

### Accounts receivable

You can calculate the forecast for sales by using the setup options on the **Accounts receivable** tab of the **Cash flow forecast setup** page. Before you can configure cash flow forecasting for the Accounts receivable, you must configure terms of payment, customer groups, and customer posting profiles.

In the **Sales forecast defaults** section, you can select default sales behaviors for cash flow forecasting. Three fields determine the time of the cash impact: **Time between shipping date and invoice date**, **Terms of payment**, and **Time between invoice due date and payment date**. The forecast will use the default setting for the **Terms of payment** field only if a value isn't specified on the transaction. Use a term of payment to describe the most typical number of days for each part of the process. 

The **Liquidity accounts for payments** field specifies the liquidity account that is most often used for payments. Use the **Percentage of amount to allocate to cash flow forecast** field to specify whether a percentage of amounts should be used during forecasting. Leave this field blank if the full transaction amounts should be used during forecasting.

You can override the default setting for the **Time between invoice due date and payment date** field for specific customer groups. The forecast will use the default value from the **Sales forecast defaults** section unless a different value is specified for the customer group that is related to the customer on the transaction. To override the default value, select a customer group, and then set the new value for the **Sales time** field.

You can override the default setting for the **Liquidity account** field for specific customer posting profiles. The forecast will use the default value from the **Sales forecast defaults** section unless a different liquidity account is specified for the posting profile that is related to the customer on the transaction. To override the default value, select a posting profile, and then set the liquidity account that is expected to be affected.

### Budgeting

Budgets that are created from budget models can be included in cash flow forecasts. On the **Cash flow forecast setup** page on the **Budgeting** tab, select the budget models to include in the forecast. By default, new budget register entries are included in forecasts after the budget model has been enabled for cash flow forecasting.

Budget register entries can be included in the cash flow forecast on an individual basis through personalization. When you add the "Include in cash flow forecasts" column to the **Budget register entry** page, the system will overwrite the settings on the **Cash flow forecast setup** page to include an individual budget register entry in the forecast.


### Inventory management

Inventory supply and demand forecasts can be included in cash flow forecasts. On the **Inventory management** tab of the **Cash flow forecast setup** page, select the forecast model to include in the cash flow forecast. Inclusion in cash flow forecasting can be overwritten on individual supply and demand forecast lines.

### Setting up Dimensions for Cash flow forecasting
A new tab on the **Cash flow forecasting setup** page lets you control which financial dimensions will be used for filtering in the **Cash flow forecasting** workspace. This tab will appear only when the Cash flow forecasts feature is enabled.

On the **Dimensions** tab, choose from the list of dimensions to use for filtering, and use the arrow keys to move them to the right-hand column. Only two dimensions can be selected for filtering cash flow forecast data. 

### Setting up External source
External data can be entered or imported into cash flow forecasts when Finance Insights has been configured. Before external data is entered or imported, external sources must be set up. On the **External source** tab, set up external cash flow categories. A category can be **Outgoing** or **Incoming**. **Liquidity** should be selected as the posting type. In the **Legal entity settings** grid, select the legal entities and the corresponding main accounts that the external cash flow categories apply to.

For more information, see [External data in cash flow forecasts](../../finance/finance-insights/external-data-in-cash-flow.md). 

### Project management and accounting

In version 10.0.17, a new feature enables integration with Project management and accounting and Cash flow forecasting. In the **Feature management** workspace, turn on the **Cash flow Project forecast** feature to include the forecasted costs and revenues in the cash flow forecast. On the **Project management and accounting** tab of the **Cash flow forecast setup** page, select the project types and transaction types that should be included in the cash flow forecast. Then select the project forecast model. A reduction type submodel works best. The liquidity accounts that were entered in the Accounts receivable setup are used as the default liquidity accounts. Therefore, you don't have to enter default liquidity accounts when you set up the cash flow forecast. A budget model can also be used, but only one type can be selected on the **Cash flow forecast setup** page for Project management and accounting. A forecast model provides the most flexibility when Project management and accounting or Project Operations is used.

After Cash flow project forecast feature is turned on, the cash flow forecast can be viewed for each project on the **All projects** page. On the Action Pane, on the **Plan** tab, in the **Forecast** group, select **Cash flow forecast**. In the **Cash overview** workspaces (see the [Reporting](#reporting) section later in this article), the Project forecast transaction type shows the inflows (project forecast revenue) and the outflows (project forecast costs). The amounts can be included only if the **Project stage** field in the **Cash overview** workspaces is set to **In process**.

Project transactions are still included in the cash flow forecast in several ways, regardless of whether the **Cash flow project forecast** feature is turned on. Posted project invoices are included in the forecast as part of open customer transactions. Project-initiated sales orders and purchase orders are included in the forecast as open orders after they are entered in the system. You can also transfer project forecasts to a ledger budget model. This ledger budget model is then included in the cash flow forecast as part of the budget register entries. If you've turned on the **Cash flow project forecast** feature, don't transfer project forecasts to a ledger budget model, because this action will cause the project forecasts to be counted two times.

### Sales tax authority payments 

The Cash flow sales tax authority payments feature predicts the cash flow impact of sales tax payments. It uses unpaid sales tax transactions, tax settlement periods, and the tax period payment term to predict the date and amount of cash flow payments. 

### Calculation

Before you can view cash flow forecasting analytics, you must run the cash flow calculation process. The calculation process will project the future cash impacts of transactions that have been entered.

Calculate the cash flow forecast by using the **Calculate cash flow forecasts** page. You can calculate either the full cash flow forecast or an incremental cash flow forecast. 

- To clear all cash flow forecast transactions and recalculate, set the **Cash flow forecast calculation method** field to **Total**. We recommend that you use this approach if you haven't updated the cash flow forecasts for a long time. 
- To update the existing cash flow information for new transactions only, set the **Cash flow forecast calculation method** field to **New**. The page will show the date when your cash flow calculation was last run.

You can also use batch processing for your cash flow forecasting. To help ensure that your forecasting analytics are regularly updated, set up a recurring batch process for cash flow forecast calculation.

In version 10.0.13, an enhancement to the calculation process was released that uses the process automation framework to schedule the cash flow calculation job. This is enabled using the **Cash flow forecast automation** feature in the **Feature Management** workspace. Once enabled, select the **Cash flow forecast automation** link to display the new automation page where you can schedule the cash flow calculation process. To create a new cash flow forecast schedule, select **Create new process automation** and then select **Cash flow forecast automation** in the **Schedule type** drop-down menu. You must set a schedule for each company that you're updating the cash flow forecast data for.  This page also shows which cash flow forecast automation jobs are pending, and when the last job was completed.  

> [!NOTE] 
> If existing batch jobs are already scheduled for cash flow forecasts, you will receive an error message and you won't be able to enable this feature. Existing batch jobs will need to be cleared before you can enable this feature. 

For more information, see [Process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

### Reporting

After the cash flow forecast is calculated, you must refresh the associated entity information for analytical reporting. On the **Entity store** page, select the **LedgerCovLiquidityMeasurementV2 aggregate** measurement, and then click **Refresh**.

There are two workspaces that contain cash flow forecasting data. One workspace has data for all companies, and the other workspace has data only for the current company.

Access to the workspace for all companies is controlled through the **View cash flow all companies workspace** duty. By default, the **Cash overview – all companies** workspace is available to the following roles:

- Chief executive officer
- Chief financial officer
- Financial controller

Access to the workspace for the current company is controlled through the **View cash flow current company** workspace duty. By default, the **Cash overview – current company** workspace is available to the following roles:

- Accountant
- Accounting manager
- Accounting supervisor
- Accounts payable manager
- Accounts receivable manager

The **Cash overview – all companies** workspace shows cash flow forecasting analytics in the system currency. The system currency and the system exchange rate type that are used for the analytics are defined on the **System parameters** page. This workspace shows an overview of cash flow forecasting and bank account balances for all companies. A chart of cash inflows and outflows gives an overview of future cash movements and balances in the system currency, together with detailed information about the forecasted transactions. You can also see the forecasted currency balances.

The **Cash overview – current company** workspace shows cash flow forecasting analytics in the company's defined accounting currency. The accounting currency that is used for the analytics is defined on the **Ledger** page. This workspace shows an overview of cash flow forecasting and bank account balances for the current company. A chart of cash inflows and outflows gives an overview of future cash movements and balances in the accounting currency, together with detailed information about the forecasted transactions. You can also see the forecasted currency balances.

For more information about the cash flow forecasting analytics, see [Cash overview Power BI content](Cash-Overview-Power-BI-content.md).

Additionally, you can view cash flow forecasting data for specific accounts, orders, and items on the following pages:

- **Trial balance**: Select **Cash flow forecasts** to view the future cash flows for the selected main account.
- **All sales orders**: On the **Invoice** tab, select **Cash flow forecasts** to view the forecasted cash impact of the selected sales order.
- **All purchase orders**: On the **Invoice** tab, select **Cash flow forecasts** to view the forecasted cash impact of the selected purchase order.
- **Supply forecast**: Select **Cash flow forecasts** to view the future cash flows that are associated with the selected item supply forecast.
- **Demand forecast**: Select **Cash flow forecasts** to view the future cash flows that are associated with the selected item demand forecast.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
