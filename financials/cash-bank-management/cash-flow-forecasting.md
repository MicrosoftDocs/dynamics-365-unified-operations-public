---
# required metadata

title: Cash flow forecasting
description: This topic provides an overview of the cash flow forecasting process. It also explains how cash flow forecasting is integrated with other modules in the system.
author: saraschi
manager: AnnBe
ms.date: 05/15/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
# ms.reviewer: twheeloc
# ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sarasch 
ms.search.validFrom: 2017/06/01
ms.dyn365.ops.version: 
---

# Cash flow forecasting

[!include[banner](../includes/banner.md)]

You can use the cash flow forecasting tools to analyze upcoming cash flow and currency requirements, so that you can estimate the company's future need for cash. To obtain a forecast of the cash flow, you must complete the following tasks:

- Identify and list all the liquidity accounts. Liquidity accounts are the company's accounts for cash or cash equivalents.
- Configure the behavior for forecasts of transactions that affect the company's liquidity accounts.

After you've completed these tasks, you can calculate and analyze forecasts of the cash flow and upcoming currency requirements.

## Cash flow forecasting integration

Cash flow forecasting can be integrated with General ledger, Accounts payable, Accounts receivable, Budgeting and inventory management. The forecasting process uses transaction information that is entered in the system, and the calculation process forecasts the expected cash impact of each transaction. The following types of transactions are considered when the cash flow is calculated:

- **Sales orders** – Sales orders that aren't yet invoiced, and that result in physical or financial sales.
- **Purchase orders** – Purchase orders that aren't yet invoiced, and that result in physical or financial purchases.
- **Accounts receivable** – Open customer transactions (invoices that aren't yet paid).
- **Accounts payable** – Open vendor transactions (invoices that aren't yet paid).
- **Ledger transactions** – Transactions where it's specified that a future posting will occur.
- **Budget register entries** – Budget register entries that are selected for cash flow forecasts.
- **Demand forecasts** – Inventory forecast model lines that are selected for cash flow forecasts.
- **Supply forecasts** – Inventory forecast model lines that are selected for cash flow forecasts.

Although there is no direct integration with Project management and accounting, there are several ways to include project transactions in the cash flow forecast. Posted project invoices are included in the forecast as part of open customer transactions. Project-initiated sales orders and purchase orders are included in the forecast as open orders after they are entered in the system. You can also transfer project forecasts to a ledger budget model. This ledger budget model is then included in the cash flow forecast as part of the budget register entries.

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

Budgets that are created from budget models can be included in cash flow forecasts. On the **Budgeting** tab of the **Cash flow forecast setup** page, select the budget models to include in the forecast. By default, new budget register entries are included in forecasts after the budget model has been enabled for cash flow forecasting. Inclusion in cash flow forecasting can be overwritten on individual budget register entries.

### Inventory management

Inventory supply and demand forecasts can be included in cash flow forecasts. On the **Inventory management** tab of the **Cash flow forecast setup** page, select the forecast model to include in the cash flow forecast. Inclusion in cash flow forecasting can be overwritten on individual supply and demand forecast lines.

### Calculation

Before you can view cash flow forecasting analytics, you must run the cash flow calculation process. The calculation process will project the future cash impacts of transactions that have been entered.

Calculate the cash flow forecast by using the **Calculate cash flow forecasts** page. You can calculate either the full cash flow forecast or an incremental cash flow forecast. 

- To clear all cash flow forecast transactions and recalculate, set the **Cash flow forecast calculation method** field to **Total**. We recommend that you use this approach if you haven't updated the cash flow forecasts for a long time. 
- To update the existing cash flow information for new transactions only, set the **Cash flow forecast calculation method** field to **New**. The page will show the date when your cash flow calculation was last run.

You can also use batch processing for your cash flow forecasting. To help guarantee that your forecasting analytics are regularly updated, set up a recurring batch process for cash flow forecast calculation.

### Reporting

After the cash flow forecast is calculated, you must refresh the associated entity information for analytical reporting. On the **Entity store** page, select the **LedgerCovLiquidityMeasurement aggregate** measurement, and then click **Refresh**.

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

The **Cash overview – current company** workspace shows cash flow forecasting analytics in the company’s defined accounting currency. The accounting currency that is used for the analytics is defined on the **Ledger** page. This workspace shows an overview of cash flow forecasting and bank account balances for the current company. A chart of cash inflows and outflows gives an overview of future cash movements and balances in the accounting currency, together with detailed information about the forecasted transactions. You can also see the forecasted currency balances.

For more information about the cash flow forecasting analytics, see the Cash overview Power BI content topic.

Additionally, you can view cash flow forecasting data for specific accounts, orders, and items on the following pages:

- **Trial balance**: Select **Cash flow forecasts** to view the future cash flows for the selected main account.
- **All sales orders**: On the **Invoice** tab, select **Cash flow forecasts** to view the forecasted cash impact of the selected sales order.
- **All purchase orders**: On the **Invoice** tab, select **Cash flow forecasts** to view the forecasted cash impact of the selected purchase order.
- **Supply forecast**: Select **Cash flow forecasts** to view the future cash flows that are associated with the selected item supply forecast.
- **Demand forecast**: Select **Cash flow forecasts** to view the future cash flows that are associated with the selected item demand forecast.
