---
# required metadata

title: Configure the ledger
description: This topic provides information about configuring ledgers for each legal entity. It includes information about selecting currencies, fiscal calendars, the chart of accounts, and the account structures to be used with each legal entity.
author: kweekley
manager: 
ms.date: 09/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: Ledger
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2020-09
ms.dyn365.ops.version: 8.1

---

# Configure the ledger

[!include [banner](../includes/banner.md)]

This topic provides information about configuring ledgers for each legal entity. It includes information about selecting currencies, fiscal calendars, the chart of accounts, and the account structures to be used with each legal entity.

## Selecting the chart of accounts
Each legal entity in Dynamics 365 Finance must be configured with details about the Ledger. The **Ledger** page allows you to select which chart of accounts and account structures will be used for the selected legal entity. You can share your chart of accounts and the account structures by configuring the **Ledger** page in each legal entity to use the same chart of accounts and account structures. You can also share a portion of the configuration in each legal entity and have specific configurations in each legal entity. 

If your legal entities need different charts of accounts or account structures, the legal entity override feature might provide a useful option. Using the same chart of accounts and account structures for multiple legal entities, and managing the exceptions through the legal entity overrides, can simplify maintenance over time.

To configure the chart of accounts for a legal entity, open **General ledger > Ledger setup > Ledger** page. Click the **Chart of accounts** drop-down button and select the chart of accounts to use. It is important to note that the chart of accounts cannot be changed after you have selected a value and posted transactions in the legal entity. 

For more information on how to plan and configure the chart of accounts and main accounts, see [Plan the chart of accounts](plan-chart-of-accounts.md).

## Selecting account structures
Each legal entity in Dynamics 365 Finance can be configured to use one or more account structures. Each account structure defines the financial dimensions and combinations of main accounts and financial dimensions that will be allowed when posting transactions. You can use the same account structures in more than one legal entity. 

If you have multiple account structures it is important to note that you can only select account structures that don't have overlapping main account and financial dimension combinations. For example, you have one account structure is configured to add a Business unit for main accounts between 1000 and 1999. In another account structure, you have added a Department financial dimension for main accounts that begin with 1. In this example, only one of the account structures can be added into the same legal entity.

To configure **Account structures** for your ledger, use the **Add** button on the **Account structures** FastTab, select an account structure from the list, and then click **Select**. It may take a few minutes for the account structures to be added and saved. It is important to note that the account structures selected must be active in order for the details of the account structures to be effective in the legal entities where it is linked.

To remove an account structure, you can click **Remove** on the **Account structures** FastTab. It is important to note that removing an account structure from your ledger does not remove any transactions that were posted with the configuration of that account structures. 

For more information about setting up your account structures see [Configure account structures](configure-account-structures.md).

## Configuring calendars for the ledger
Another component of the ledger is the **Fiscal calendar**. Each legal entity must have a fiscal calendar selected. You can use the same fiscal calendar in more than one legal entity. When you select a calendar for the **Ledger**, a copy of the fiscal calendar is made and is referred to as the **Ledger calendar**. The **Ledger calendar** allows you to select the status of the periods and modules within each period. Click **Ledger calendar** in the Action Pane to access and make updates to the calendar for the selected legal entity.

To select the calendar, click the **Fiscal calendars** drop-down button and choose the calendar from the list. If you change the fiscal calendar after transactions have been posted in the legal entity, you'll need to click the **Recalculate ledger periods** button. This will open a dialog where you can update the ledger balances for the periods in your calendar. We recommend running the **Recalculate ledger periods** process in **Batch** mode when noncritical processes are occurring in your system. Depending on the number of transactions and financial dimension combinations, this process can take some time to complete. 

If a fiscal calendar isn't selected in a legal entity, an error message will display when you try to post a transaction in that legal entity. 

For more information, see [Fiscal calendars, fiscal years, and periods](../budgeting/fiscal-calendars-fiscal-years-periods.md).

## Use a balancing financial dimension
After you have selected the **Chart of accounts** and added one or more **Account structures**, you can optionally select a single financial dimension to be the **Balancing financial dimension**. However, the dimention you select must exist in all the account structures. The financial dimension that you select here must also be balanced in all accounting entries. In other words, the debits and credits must be equal for the main account and **Balancing financial dimension**. The system creates transactions automatically to balance the entries based on the main accounts that are identified in the **Accounts for automatic transaction** page in the **Interunit - credit** and **Interunit - debit** fields.

For more information about balancing entires, see the [Balanced journals for interunit accounting](example-balanced-journals-interunit-accounting.md) page. 

## Configure currencies for the ledger
The **Ledger** page is also used to control and define the currencies that will be used when posting transactions into the general ledger. You must specify the **Accounting currency**, which is the currency used in the **Accounting currency** column in the general ledger on all vouchers. You can optionally select a second currency in the **Reporting currency** column. If you select a currency, all transactions will be recorded in the selected currency in the general ledger on all vouchers in the **Reporting currency** column on vouchers. 

When transactions are posted in a different currency, the system will automatically convert the transaction amount from the transactions currency into the accounting currency and reporting currencies on the voucher. In the **Accounting currency exchange rate type** field select the exchange rate type that is configured with the exchange rates that should be used to convert values from the transaction currency to the accounting currency on the vouchers. If you selected a different reporting currency, you must also select the **Reporting currency exchange rate type** to indicate which exchange rate will be used when converting from the transaction currency to the reporting currency on a voucher. 

If you're using **Budgeting**, you can also specify the **Budget exchange rate type** to indicate which exchange rate should be used for converting budget transactions from one currency to another. 

When you use two currencies, or if you use a single currency and transactions are posted in a different currency, you will need to configure the **Accounts for currency revaluation**. This FastTab allows you to define default realized and unrealized gain and loss accounts to use when posting transactions. The accounts you specify here are used as the default accounts if an account is not specified on the **Currency revaluation accounts** page. This page is used to configure different accounts for realized and unrealized gains and losses for each currency. 

Realized gains and losses are profits and losses that are made from completed transactions, and are recorded in the profit and loss statement. Unrealized gains and losses are profits and losses that have materialized, but the transaction is not completed. In other words, you have posted an invoice, for example, but the invoice is not settled and paid yet. Unrealized gains and losses are recorded on the balance sheet. 

For more information about using two currencies, see [Dual currency](dual-currency.md)


