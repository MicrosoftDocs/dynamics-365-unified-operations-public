---
# required metadata

title: Ledger settlements
description: This article explains how to use the Ledger settlements page to settle ledger transactions and reverse settlements.
author: kweekley
ms.date: 01/30/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  LedgerTransSettlement
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom:
# ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2018-11-30
ms.dyn365.ops.version: 8.1.1

---

# Ledger settlements

[!include [banner](../includes/banner.md)]

Ledger settlement is the process of matching debit and credit transactions in the general ledger. The settlement of the debit and credit amounts is used to reconcile the balance of the ledger account with the detailed transactions that make up that balance.

Settled transactions can be excluded from inquiries and reports. In this way, it's easier to analyze the open ledger transactions that make up the balance of the ledger account.

> [!IMPORTANT] 
> The Accounts payable (AP) and Accounts receivable (AR) modules also have settlement of invoices and payments. When settlement occurs in the AR and AP subledgers, the corresponding ledger entries aren't automatically settled.

## Ledger settlement features
In Microsoft Dynamics 365 Finance version 10.0.21, the **Enable advanced ledger settlement** option was removed from the **General ledger parameters** page. Advanced ledger settlement is now always enabled.
In Finance version 10.0.25, the **Awareness between ledger settlement and year-end close** feature was introduced. This feature changes the fundamental functionality in both ledger settlement and General ledger year-end close. Before you enable this feature in the **Feature management** workspace, see [Awareness between ledger settlement and year-end close](awareness-between-ledger-settlement-year-end-close.md).

## Set up ledger settlement
You must select the main accounts that you want to do ledger settlement for. There are two ways to select these main accounts.

1. Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
2. On the **Ledger settlements** tab, select the charts of accounts that you want to select the main accounts from.
3. Select the main accounts to do ledger settlement for. Because charts of accounts are global, all companies that the selected charts of accounts are assigned to will have the same main accounts selected for ledger settlement.

  -or-

1. Go to **General ledger** > **Periodic tasks** > **Ledger settlements**.
2. Select **Ledger settlement accounts**.
3. In the dialog box, select the charts of accounts and main accounts to do ledger settlement for. This dialog box is a shortcut. Any main accounts that you add here will also be reflected on the **General ledger parameters** page.

You can use the same basic procedures to remove main accounts from ledger settlement at any time. Removal of a main account has no effect on previous ledger settlements. However, the main account and transactions will no longer appear on the **Ledger settlement** page.

## <a name="settle-transactions"></a>Settle transactions
To settle ledger transactions, follow these steps.

1. Go to **General ledger** > **Periodic tasks** > **Ledger settlements**.
2. Set the filters at the top of the page:

    - Select a date range. Alternatively, select a date interval code to automatically fill in the date range. We don't recommend that you do ledger settlement for transactions that cross fiscal years.
    - Change the posting layer as required. You can't settle transactions that are in different posting layers.
    - To show the main account and dimensions separately, select a financial dimension set.

3. Select **Display transactions** to show all the transactions that match the filters that you set and the list of accounts that you specified when you set up the chart of accounts list in the previous section.

    - If you change any of the filters or the dimension sets, you must select **Display transactions** again.
    - To filter the transactions to an individual main account, use the filter on the **Ledger account** field. We don't recommend that you do ledger settlement for transactions that are posted to different main accounts.

4. Select lines for settlement. The value in the **Selected amount** field at the top of the page increases or decreases to reflect the total amount on the selected lines.
5. When you've finished selecting transactions, select **Mark selected**. For each selected transaction, a check mark appears in the **Marked** column. Additionally, the value in the **Marked amount** field above the grid increases or decreases to reflect the total amount on the marked lines.
6. When the value in the **Marked amount** field is **0** (zero), select **Settle marked transactions**. The status of the marked transactions is updated to **Settled**.

    > [!IMPORTANT]
    > All transactions that you've marked for settlement for the active legal entity will be settled, even if they aren't currently shown on the Ledger settlement page because you applied a filter.

## Make transactions easier to find
The **Ledger settlements** page includes capabilities that make it easier to view the transactions that you require for settlement.

- Use the **Marked** filter to filter transactions based on whether the **Marked** checkbox is selected for them.
- Use the **Status** filter to filter transactions based on their status.
- Select **Sort by absolute amount** to sort the amounts by absolute value. In this way, you can group debits and credits that have the same amount.

## Reverse a settlement
You can reverse a settlement that was made by mistake.

1. Follow steps 1 through 3 in the [Settle transactions](#settle-transactions) section to show the transactions that you're interested in.
2. In the **Status** filter, select **Settled**.
3. Select lines for reversal.
4. Select **Reverse marked transactions**. The status of all transactions that have the same settlement ID is updated to **Not settled**.

    > [!IMPORTANT]
    > All transactions that have the same settlement ID will be reversed, even if they aren't marked. For example, four lines were marked and settled. All four lines have the same settlement ID. If you mark one of those four lines and then select **Reverse marked transactions**, all four lines will be reversed.

## Unmark for selected users
Select **Unmark for selected users** to unmark ledger settled transactions for all legal entities by user ID. For instance, this will allow an accounting manager to unmark transactions for a user that left on vacation before finishing the settlement or for a user who has left the organization. The action will allow those transactions to be marked for settlement by another user.


## Unmark all transactions
Select **Unmark all transactions** to unmark all ledger settled transactions for all users and all legal entities. This action is available for the Administrator role.

## Review cross-year settlements
Beginning in Microsoft Dynamics 365 Finance release 10.0.29, you can identify vouchers that were ledger settled across fiscal years. The **Review cross-year settlements** page allows you to view and unsettle ledger transactions. On the **Ledger settlements** page, select **Review cross-year settlement**. The **Inquiry** page will show all transactions from other fiscal years that are settled against transactions that were posted in the fiscal year that are specified in the **Fiscal year** drop list field.

It is important to export the data to Excel, prior to unsettling records. Upon selecting the **Unsettle marked records** action, two warning messages are shown to ensure that the transaction details are exported to Excel before the transactions are unsettled. If you accidentally unsettle ledger transactions before you send the details to Excel, there's no way to reverse the unsettlement.

For more information about the how to use the **Review cross-year settlements** form to assist in year-end close processes, see [Awareness between ledger settlement feature before year-end close using the inquiry page](ledger-settlement-yec-inquiry-before.md) and [Awareness between ledger settlement feature after year-end close using the inquiry page](ledger-settlement-yec-inquiry-after.md).



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
