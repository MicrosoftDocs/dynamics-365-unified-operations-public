---
# required metadata

title: Cash flow forecasting
description:his topic provides an overview for the cash flow forecasting process – configuration, calculation, and reporting. It will also discuss how cash flow forecasting is integrated with other modules in the system.
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

[!include[banner](../includes/banner.md)]---

---

This topic provides an overview for the cash flow forecasting process – configuration, calculation, and reporting. It will also discuss how cash flow forecasting is integrated with other modules in the system.

You can use the cash flow forecasting tools to analyze upcoming cash flow and currency requirements to estimate the company's future need for cash. To obtain a forecast of the cash flow, you must do the following:

-   Identify and list all the liquidity accounts. Liquidity accounts are the company's accounts for cash or cash equivalents.

-   Configure behavior for forecasts of transactions that affect the company's liquidity accounts.

You can then calculate and analyze forecasts of the cash flow and upcoming currency requirements.

## Cash flow forecasting integration

Cash flow forecasting can be integrated with General ledger, Accounts payable, Accounts receivable, Budgeting and Inventory management modules. The forecasting process will use transaction information entered in the system, and the calculation process will forecast the expected cash impact for each transaction. The following information explains what types of transactions are considered when calculating the cash flow.

-   Sales orders – Sales orders that are not yet invoiced and that result in physical or financial sales.

-   Purchase orders – Purchase orders that are not yet invoiced and that result in physical or financial purchases.

-   Accounts receivable – Open customer transactions (invoices that are not yet paid).

-   Accounts payable – Open vendor transactions (invoices that are not yet paid).

-   Ledger transactions – Transactions where it is specified that a future posting will occur.

-   Budget register entries – Budget register entries that are selected for cash flow forecasts.

-   Demand forecasts – Inventory forecast model lines that are selected for cash flow forecasts.

-   Supply forecasts – Inventory forecast model lines that are selected for cash flow forecasts.

Although there is no direct integration with the Project management and accounting module, there are a number of ways to include Project transactions in the cash flow forecast. Posted project invoices will be included in the forecast as part of open customer transactions. Project-initiated sales orders and purchase orders are included in the forecast as open orders once they are entered in the system. You can also transfer project forecasts to a ledger budget model, which will be included in the cash flow forecast as part of the budget register entries.

## Configuration

Configuration of the cash flow forecasting process is completed using the Cash flow forecast setup page. On this page, you will tell the system what liquidity accounts you want to track and the default forecasting behaviors for each area.

### General ledger 

First you must define the liquidity accounts to track with cash flow forecasting. These liquidity accounts are typically main accounts associated with the bank accounts which will receive and disburse cash. On the **General ledger** tab, select the main accounts to be included for forecasting. The **Bank account** field will show you a bank account if one has been associated with that main account on the **Bank account** page.

You can set up a dependent cash flow forecast for a main account that contains transactions which are directly related to transactions in another main account. Each line that you add **In the Dependent accounts** section creates a cash flow forecast amount in a dependent main account that is a percentage of cash flow amounts to the primary main account that you selected. 

First, set the **Main account** to the primary main account where transactions are expected to initially occur. Set the **Dependent main account** to the account that will be impacted by the initial transaction against the defined Main account. Set the appropriate values for the other fields on the line. You can change the value displayed in the **Percent** text box to reflect the effect of primary main account on the dependent main account. For a sales or purchase forecast, select a Terms of payment value that is typical for most customers or vendors. The Posting type is the expected posting type, related to the cash flow forecast.

### Accounts payable

You can calculate the forecast for purchases using the setup options on the **Accounts payable** tab of the **Cash flow forecast setup** page. You must have configured Terms of payment, Vendor groups, and Vendor posting profiles before configuring cash flow forecasting for the area.

The Purchasing forecast defaults section allows you to select the most common purchasing behaviors to be used as a default for cash flow forecasting. There are three fields to determine time of the cash impact: **Time between delivery date and invoice date, Terms of payment, and Time between invoice due date and payment date**. The forecast will only use the default setting for the Terms of
payment setting if it is not available on the transaction. 

Use a term of payment to describe the most typical number of days for each part of the process. The Liquidity accounts for payments field is the most commonly used liquidity account for payments. Use the Percentage of amount to allocate to cash flow forecast field to describe if a percentage of amounts should be used in forecasting. Leave this field blank if the full transaction amounts should be used in forecasting.

You can override the default setting for **Time between invoice due date** and payment date for specific vendor groups. The forecast will use the default value from the Purchasing forecast defaults section unless a different value is specified for the vendor group related to the vendor on the transaction. To override the default value, select a vendor group and set the new value for the purchasing time field.

You can override the default setting for Liquidity account for specific vendor posting profiles. The forecast will use the default value from the Purchasing forecast defaults section unless a different liquidity account is specified for posting profile related to the vendor on the transaction. To override the default value, select a posting profile and set the liquidity account expected to be impacted.

### Accounts receivable

You can calculate the forecast for sales using the setup options on the **Accounts receivable** tab of the **Cash flow forecast setup** page. You must have configured Terms of payment, Customer groups, and Customer posting profiles before configuring cash flow forecasting for the area.

The Sales forecast defaults section allows you to select the most common sales behaviors to be used as a default for cash flow forecasting. There are three fields to determine time of the cash impact: Time between shipping date and invoice date, Terms of payment, and Time between invoice due date and payment date. The forecast will only use the default setting for the Terms of payment setting if it is not available on the transaction. Use a term of payment to describe the most typical number of days for each part of the process. 

The Liquidity accounts for payments field is the most commonly used liquidity account for payments. Use the Percentage of amount to allocate to cash flow forecast field to describe if a percentage of amounts should be used in forecasting. Leave this field blank if the full transaction amounts should be used in forecasting.

You can override the default setting for **Time between invoice due date** and payment date for specific customer groups. The forecast will use the default value from the **Sales forecast defaults** section unless a different value is specified for the customer group related to the customer on the transaction. To override the default value, select a customer group and set the new value for the sales time field.

You can override the default setting for Liquidity account for specific customer posting profiles. The forecast will use the default value from the **Sales forecast defaults** section unless a different liquidity account is specified for posting profile related to the customer on the transaction. To override the default value, select a posting profile and set the liquidity account expected to be impacted.

### Budgeting

Budgets that are created from budget models can be included in cash flow forecasts. Select the budget models to include in the forecast on the **Budgeting** tab of the **Cash flow forecast setup** page. New budget register entries will be included in forecasts by default once the budget model has been enabled for cash flow forecasting. Inclusion in cash flow forecasting can be overwritten on individual budget register entries.

### Inventory management

Inventory supply and demand forecasts can be included in cash flow forecasts. Select the forecast model to include in the cash flow forecast on the **Inventory management** tab of the **Cash flow forecast setup** page. Inclusion in cash flow forecasting can be overwritten on individual supply and demand forecast lines.

### Calculation

You must run the cash flow calculation process before viewing cash flow forecasting analytics. The calculation process will project the future cash impacts of transactions that have been entered.

Calculate the cash flow forecast using the **Calculate cash flow forecasts** page. You have the option to calculate the full cash flow forecast or an incremental cash flow forecast. 

 - Set the **Cash flow forecast calculation method** field to **Total** to clear all cash flow forecast transactions and recalculate. This option is preferred if you have not updated the cash flow forecasts for a long time. 
  - Set the **Cash flow forecast calculation method** field to **New** to update the existing cash flow information for only new transactions. The page will give you the date your cash flow calculation was last run.

You also have the ability to use batch processing for your cash flow forecasting. Set up a recurring batch process for cash flow forecast calculation to ensure your forecasting analytics are updated on a regular basis.

### Reporting
=========

Once the cash flow forecast is calculated, you must refresh the associated entity information for analytical reporting. Using the **Entity store** page, select the **LedgerCovLiquidityMeasurement aggregate** measurement and click **Refresh**.

There are two workspaces with cash flow forecasting data, one with data for all companies and a second with data only for the current company. Access to the all companies workspace is controlled using the View cash flow all companies workspace duty. By default, the **Cash overview – all companies** workspace is available to the following roles:

-   Chief executive officer

-   Chief financial officer

-   Financial controller

Access to the current company workspace is controlled using the **View cash flow current company** workspace duty. By default, the Cash overview – current company workspace is available for the following roles:

-   Accountant

-   Accounting manager

-   Accounting supervisor

-   Accounts payable manager

-   Accounts receivable manager

The **Cash overview – all companies** workspace shows cash flow forecasting analytics using the System currency. The **System currency** and **System exchange** rate type used for the analytics are defined on the **System parameters** page. On this workspace, you will see an overview of cash flow forecasting as well as bank account balances for all companies. A cash inflows and outflows chart gives an overview of cash movements and balances in the future in system currency, along with detailed information on the forecasted transactions. You will also see the forecasted currency balances.

The **Cash overview – current company** workspace shows cash flow forecasting analytics using the company’s defined Accounting currency. The **Accounting currency** used for the analytics are defined on the **Ledger** page. On this workspace, you will see an overview of cash flow forecasting as well as bank account balances for the current company. A cash inflows and outflows chart gives an overview of cash movements and balances in the future in accounting currency, along with detailed information on the forecasted transactions. You
will also see the forecasted currency balances.

See Cash overview Power BI content article for additional details on the cash flow forecasting analytics.

There are also pages in the system where you can see cash flow forecasting data for specific accounts, orders, and items.

-   **Trial balance** page: Select **Cash flow forecasts** to view the future cash flows for the selected main account.

-   **All sales orders** page: On the **Invoice** tab, select **Cash flow forecasts** to view the forecasted cash impact of the selected sales order.

-   **All purchase orders** page: On the **Invoice** tab, select **Cash flow forecasts** to view the forecasted cash impact of the selected purchase order.

-   **Supply forecast** page: Select **Cash flow forecasts** to view the future cash flows associated with the selected item supply forecast.

-   **Demand forecast** page: Select **Cash flow forecasts** to view the future cash flows associated with the selected item demand forecast.
