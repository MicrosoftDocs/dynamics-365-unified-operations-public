---
# required metadata

title: Ledger settlements
description: This article explains how to use the Ledger settlements page to settle ledger transactions and reverse settlements.
author: kweekley
ms.date: 07/14/2023
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
Select **Unmark for selected users** to unmark ledger settled transactions for all legal entities by user ID. For instance, this allows an accounting manager to unmark transactions for a user that left on vacation before finishing the settlement or for a user who has left the organization. The action allows those transactions to be marked for settlement by another user.


## Unmark all transactions
Select **Unmark all transactions** to unmark all ledger settled transactions for all users and all legal entities. This action is available for the Administrator role.

## Review cross-year settlements
Beginning in Microsoft Dynamics 365 Finance release 10.0.29, you can identify vouchers that were ledger settled across fiscal years. The **Review cross-year settlements** page allows you to view and unsettle ledger transactions. On the **Ledger settlements** page, select **Review cross-year settlement**. The **Inquiry** page displays all transactions from other fiscal years that are settled against transactions that were posted in the fiscal year that are specified in the **Fiscal year** drop list field.

It's important to export the data to Excel, prior to unsettling records. Upon selecting the **Unsettle marked records** action, two warning messages are shown to ensure that the transaction details are exported to Excel before the transactions are unsettled. If you accidentally unsettle ledger transactions before you send the details to Excel, there's no way to reverse the unsettlement.

For more information about how to use the **Review cross-year settlements** page to assist in year-end close processes, see [Awareness between ledger settlement feature before year-end close using the inquiry page](ledger-settlement-yec-inquiry-before.md) and [Awareness between ledger settlement feature after year-end close using the inquiry page](ledger-settlement-yec-inquiry-after.md).

## Post foreign currency realized gains/losses for ledger settlements
In Microsoft Dynamics 365 Finance version 10.0.36, the **Post foreign currency realized gains/losses for ledger settlements** feature is available in the **Feature management** workspace.    
This feature calculates and posts foreign currency realized gains and losses for settlements from the **Ledger settlements** page when the reporting currency values of the debits and credits differ. To enable the **Post foreign currency realized gains/losses for ledger settlements** feature, the **Awareness between ledger settlement and year-end close** feature must be enabled.

The feature also includes usability improvements to the Ledger settlement process. The process of marking has been simplified. You no longer must select and mark vouchers for ledger settlement in two steps. Now, you can mark the voucher in the grid on the **Ledger settlements** page. The **Marked debits**, **Marked credits** and **Difference** fields are displayed to provide clear indication of your work in progress totals. You must complete your work by settling the marked vouchers prior to closing the **Ledger settlements** page.

### Set up realized gain and realized loss account information
After you enable the feature, you must determine which ledger settlement accounts will process realized gains and losses during settlement. 
The **Calculate realized gains and losses** option is set for each main account that is ledger settled.

1.	Go to **General ledger > Ledger setup > General ledger parameters**.
2.	On the **Ledger settlements** tab, select **Ledger settlement accounts**.
-or-
1.	Go to **General ledger > Periodic tasks > Ledger settlements**.
2.	Select **Ledger settlement accounts**.
   
By default, the option is set to **No**. When the option is set to **Yes**, the foreign currency exchange rate realized gains and losses are posted during the ledger settlement process. Foreign currency exchange rate realized gains and losses are generated when the debit and credit amounts in the reporting currency don't equal. When the option is set to **No**, realized gains and losses won't be generated by the ledger settlement process. We recommend setting this option to **No** for your Accounts receivable and Accounts payable summary accounts, since foreign currency exchange rate gains and losses are typically realized in the subledgers. Additional consideration should be given to your **Cash** accounts that may be revalued in the **Cash and bank management** module.

The posting accounts for the realized gains and realized losses can be set up in the **Currency revaluation posting profile** page on the **General ledger** tab. If these accounts aren't defined on the currency revaluation posting profile, the accounts that are selected on the **Account for currency revaluation** FastTab of the **Ledger** page are used.

In order to post a realized gain or loss, the number sequence information for the type **Ledger settlements** on the **General ledger parameters** page must be specified. (**General ledger > Ledger setup > General ledger parameters > Number sequences**)

### Post a realized gain or realized loss
During the ledger settlement process, realized gain and realized losses are posted when the reporting currency amounts of the marked debits and marked credits differ. To determine if there's a gain or a loss, the account type and the direction of the change are taken into account. The adjustment amount is calculated using the formula: Adjustment Amount = 0 - (Debits - Credits). This calculated amount represents the adjustment required to balance the debits and credits to zero. A gain or loss is determined based on the **Main account type** of the account that is being settled. For accounts of type **Balance sheet**, **Asset**, **Liability**, **Equity** or **CA Common**, a gain is posted when the adjustment value is greater than zero and a loss is posted when the adjustment value is less than or equal to zero. For accounts of type **Profit and loss**, **Revenue** or **Expense**, a loss will be posted when the adjustment value is greater than zero and a gain will be posted when the adjustment value is less than or equal to zero. 

A voucher that contains the accounting for the realized gain or realized loss information is created as of the settlement date. The financial dimensions for the accounting entries is based on the voucher that is being settled. The **Settlement typical balance** setting is used to determine which voucher to retrieve the default dimensions from. If multiple vouchers are being settled, the calculated realized gain or realized loss amount will be prorated to the financial dimensions of the voucher, based on the transaction currency values. The transaction type for the posted voucher will be **Ledger settlement**.

### Reverse a settlement that contains a realized gain or realized loss
When a ledger settlement is reversed, any realized gain or realized loss vouchers that were recognized at the time of settlement will be fully reversed. The transaction type for the posted reversal voucher will be **Ledger settlement reversal**. You can't reverse a reversed ledger settlement. Instead, you can resettle the vouchers. 

### Unrealized gains and losses
The foreign currency revaluation process in general ledger creates unrealized gains and losses transactions. If unrealized gain and losses exist for transactions that are ledger settled, they'll be resolved the next time the foreign currency process is run. We recommend that unrealized gains and loss transactions from prior foreign currency revaluation runs aren't marked for ledger settlement and that you perform foreign currency revaluations in general ledger, after ledger settlement. The foreign currency revaluation routine resolves the unrealized gain or unrealized loss. 



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
