---
title: Configure ledgers
description: Learn about how to configure ledgers for each legal entity, including outlines on how to select currencies and the account structures that should be used.
author: kweekley
ms.author: kweekley
ms.topic: article
ms.date: 09/24/2020
ms.custom:
ms.reviewer: kfend
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-09
ms.search.form: Ledger
ms.dyn365.ops.version: 8.1
---

# Configure ledgers

[!include [banner](../includes/banner.md)]

This article provides information about how to configure ledgers for each legal entity. It includes information about how to select currencies, fiscal calendars, the chart of accounts, and the account structures that should be used with each legal entity.

## Selecting the chart of accounts

For each legal entity in Microsoft Dynamics 365 Finance, details about the ledger must be configured. The **Ledger** page lets you select the chart of accounts and the account structures that will be used for the selected legal entity. You can share your chart of accounts and the account structures by configuring the **Ledger** page in each legal entity to use the same chart of accounts and account structures. You can also share part of the configuration in each legal entity and have specific configurations in each legal entity.

If your legal entities must have different charts of accounts or different account structures, the legal entity override feature might be useful. By using the same chart of accounts and account structures for multiple legal entities, and then managing any exceptions through legal entity overrides, you can simplify maintenance over time.

To configure the chart of accounts for a legal entity, go to **General ledger \> Ledger setup \> Ledger**. On the **Ledger** page, select **Chart of accounts**, and then, in the list, select the chart of accounts to use. Note that the chart of accounts can't be changed after you select a value and post transactions in the legal entity.

For more information about how to plan and configure the chart of accounts and main accounts, see [Plan the chart of accounts](plan-chart-of-accounts.md).

## Selecting account structures

Each legal entity in Dynamics 365 Finance can be configured to use one or more account structures. Each account structure defines the financial dimensions, and the combinations of main accounts and financial dimensions, that will be allowed when transactions are posted. You can use the same account structures in more than one legal entity.

Note that, if you have multiple account structures, you can select only account structures that don't have overlapping combinations of main accounts and financial dimensions. For example, one of your account structures is configured to add a business unit for main accounts between 1000 and 1999. In another account structure, you've added a Department financial dimension for main accounts that begin with 1. In this case, only one of the account structures can be added in the same legal entity.

To configure account structures for your ledger, on the **Ledger** page, on the **Account structures** FastTab, select **Add**, select an account structure in the list, and then select **Select**. It will take a few minutes for the account structures to be added and saved. When the changed account structure is saved to the ledger, the process to synchronize all the unposted transactions will begin. You must wait until the change is completed for the current ledger in the legal entity where the change is being made before you can make an account structure change for a ledger in another legal entity. Note that the account structures that you select must be active. Otherwise, the details of the account structures won't be effective in the legal entities where they are linked.

To remove an account structure, on the **Ledger** page, on the **Account structures** FastTab, select **Remove**. Note that, if you remove an account structure from your ledger, you don't remove any transactions that were posted by using the configuration of that account structure.

For more information about how to set up your account structures, see [Configure account structures](configure-account-structures.md).

## Configuring calendars for the ledger

Another component of the ledger is the fiscal calendar. A fiscal calendar must be selected for each legal entity. You can use the same fiscal calendar in more than one legal entity. When you select a fiscal calendar for the ledger, a copy is made. This copy is referred to as the ledger calendar. The ledger calendar lets you select the status of the periods and the modules in each period.

To access and update the calendar for the selected legal entity, on the **Ledger** page, on the Action Pane, select **Ledger calendar**.

To select the calendar, select **Fiscal calendars**, and then select the calendar in the list. If you change the fiscal calendar after transactions have been posted in the legal entity, you must select **Recalculate ledger periods**. Then, in the dialog that appears, you can update the ledger balances for the periods in your calendar. We recommend that you run the **Recalculate ledger periods** process in **Batch** mode, and that you run it when non-critical processes are occurring in your system. Depending on the number of transactions and financial dimension combinations, this process can take some time.

If no fiscal calendar is selected for a legal entity, you will receive an error message when you try to post a transaction in that legal entity.

For more information, see [Fiscal calendars, fiscal years, and periods](../budgeting/fiscal-calendars-fiscal-years-periods.md).

## Using a balancing financial dimension

After you've selected the chart of accounts, and added one or more account structures, you can optionally select a single financial dimension to use as the balancing financial dimension. The dimension that you select must exist in all the account structures. It must also be balanced in all accounting entries. In other words, the debits and credits must be equal for the main account and the balancing financial dimension. The system automatically creates transactions to balance the entries, based on the main accounts that are specified in the **Interunit - credit** and **Interunit - debit** fields on the **Accounts for automatic transaction** page.

For more information about balancing entries, see [Balanced journals for interunit accounting](example-balanced-journals-interunit-accounting.md).

## Configuring currencies for the ledger

The **Ledger** page is also used to control and define the currencies that will be used when transactions are posted to the general ledger. You must specify the accounting currency, which is the currency that is used in the **Accounting currency** column in the general ledger on all vouchers. Additionally, in the **Reporting currency** column, you can optionally select a second currency. If you select a reporting currency, all transactions will be recorded in that currency in the **Reporting currency** column in the general ledger on all vouchers.

If transactions are posted in a different currency, the system automatically converts the transaction amount from the transaction currency into the accounting currency and reporting currency on the voucher. On the **Ledger** page, in the **Accounting currency exchange rate type** field, select the type of exchange rate that is configured for the exchange rates that should be used to convert values from the transaction currency to the accounting currency on a voucher. If you selected a reporting currency, you must also set the **Reporting currency exchange rate type** field to indicate the exchange rate that should be used to convert values from the transaction currency to the reporting currency on a voucher.

If you're using budgeting functionality, you can also set the **Budget exchange rate type** field to indicate the exchange rate that should be used to convert budget transactions from one currency to another.

If you use two currencies, or if you use a single currency but transactions are posted in a different currency, you must configure the **Accounts for currency revaluation** FastTab on the **Ledger** page. On this FastTab, you define the default realized and unrealized gain and loss accounts that will be used by default when transactions are posted, if no account is specified on the **Currency revaluation accounts** page. (The **Currency revaluation accounts** page is used to configure different accounts for realized and unrealized gains and losses for each currency.)

Realized gains and losses are profits and losses that are made from completed transactions. They are recorded on the profit and loss statement. Unrealized gains and losses are profits and losses that have materialized, but the transaction isn't completed. In other words, you've posted an invoice, for example, but the invoice isn't yet settled and paid. Unrealized gains and losses are recorded on the balance sheet.

For more information about how to use two currencies, see [Dual currency](dual-currency.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
