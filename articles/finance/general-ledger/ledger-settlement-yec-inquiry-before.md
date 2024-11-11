---
title: Enable advanced awareness options parameter before year-end close using the inquiry page
description: Learn how to use the Enable advanced awareness options parameter by using the new inquiry page before the General ledger year-end close is run.
author: moaamer
ms.author: kweekley
ms.topic: article
ms.date: 11/08/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-01-31
ms.search.form:
ms.dyn365.ops.version: 10.0.25
---

# Enable advanced awareness options parameter before year-end close using the inquiry page

> [Note]
> Beginning in Dynamics 365 Finance version 10.0.40, the **Awareness between ledger settlement** feature, along with its associated features **Automate ledger settlement process** and **Post foreign currency realized gains/losses for ledger settlements**, can be found on the **General Ledger parameters**, specifically under the **Ledger settlements** tab. These features are managed through parameters titled **Enable advanced awareness options**, **Enable process automation for ledger settlement**, and **Enable post currency realized gains/losses for ledger settlements** respectively.

A major change of the **Enable advanced awareness options** parameter is that ledger settlement can't be done across fiscal years. This cross-year limitation is relevant only to ledger settlement, not to Accounts receivable or Accounts payable settlements.

Before you enable the **Enable advanced awareness options** parameter, the fiscal year that will undergo the year-end close must not have any ledger transactions that are settled across fiscal years. Specifically, any transactions that were posted into the fiscal year that you're running the year end close for must be unsettled from transactions that were posted into a different fiscal year. The transactions can then be resettled against transactions in the same fiscal year.

This article describes the steps that are required to identify, unsettle, and resettle ledger transactions that are settled across fiscal years. In the example that's provided, fiscal year 2021 has been closed, and you're preparing to run the year-end close for fiscal year 2022.

As of Microsoft Dynamics 365 Finance release 10.0.29, you can identify, unsettle, and resettle ledger transactions by using a new inquiry page that's available. If you aren't currently on Finance release 10.0.29 or later, you can find the steps for identifying, unsettling, and resettling the ledger transactions in the following articles:

- [Awareness between ledger settlement feature before year-end close](ledger-settle-yec.md)
- [Awareness between ledger settlement feature after year-end close](ledger-settle-yec-after.md)

For more information about the new inquiry window, see [Ledger settlement inquiry](ledger-settlement-inquiry.md). 

## Example setup

The following illustration shows the transactions that were posted for main account 110200. The transactions in green were ledger settled in the same fiscal year and don't have to change. The transactions in red were ledger-settled, but they have transaction dates in different fiscal years. Those transactions must be identified, and the ledger settlement might have to be reversed.

![Posted ledger transactions.](./media/ledgersettlement.png)

## Example

Follow these steps if your organization wants to use the **Enable advanced awareness options** parameter before you run the year-end close for fiscal year 2022.

> [!NOTE]
> The year-end close for 2021 and earlier fiscal years must be rerun only if new transactions are posted into fiscal year 2021 or earlier. When you complete the following procedure, no new transactions are posted into 2021. Therefore, the year-end close doesn't have to be rerun.
>
> Ledger transactions that are settled across fiscal years can remain ledger-settled if they aren't settled against a transaction that was posted into 2022 (the year that's being closed) or later. For example, if you've settled transactions in 2019 and 2020, they can remain settled.

1. Do not enable the **Enable advanced awareness options** parameter.
2. On the **Ledger settlements** page, select **Review cross-year settlement**.
3. Identify all the transactions that were posted into other fiscal years but settled against transactions that were posted into 2022.

    1. Select fiscal year 2022, the fiscal year that you want to run the year-end close process for.
    2. Select a value in the **Financial dimension set** field to show the financial dimensions that you want to view for the ledger account. The main account is always shown, even if the dimension set that's selected doesn't contain a main account.
    3. Select **Show transactions**.

    The inquiry page will show all transactions, for all ledger accounts (even if they are no longer in the ledger settlement setup), from all other fiscal years that are settled against transactions that were posted into 2022. Three different ledger accounts are shown.

    ![2022 cross-year settlements.](./media/review-cross-year.png)

3. Select and hold (or right-click) in the grid, and then select **Export all rows**. These rows are all the transactions that must be unsettled from the transactions in 2022 before the year-end close can be run. You want the detailed transaction list so that you can correctly resettle the transactions later.
4. Note the fiscal years that the transactions were posted for. In this example, there are transactions in 2021 and 2023.
5. On the inquiry page, change the fiscal year to 2021, the first fiscal year that contains transactions that were settled against 2022 transactions.
6. Filter on the **Transaction date** column, so that only transactions that were posted into 2022 are included. These transactions are the detailed transactions from 2022 that were settled against transactions in 2021.
7. Select and hold (or right-click) in the grid, and then select **Export all rows**.

    > [!IMPORTANT]
    > In the following steps, these transactions will be unsettled and then resettled against transactions in 2022. It's essential that you maintain this detail in Excel.

    ![2021 cross-year settlements.](./media/review-cross-year.png)

8. On the inquiry page, change the fiscal year to 2023, the next fiscal year that contains transactions that were settled against 2022 transactions. 
9. Filter on the **Transaction date** column, so that only transactions that were posted into 2022 are included. These transactions are the detailed transactions from 2023 that were settled against transactions in 2022. 
10. Select and hold (or right-click) in the grid, and then select **Export all rows**.

    > [!IMPORTANT]
    > In the following steps, these transactions will be unsettled and then resettled against transactions in 2022. It's essential that you maintain this detail in Excel.

    ![2023 cross-year settlements.](./media/filter-transactions.png)

11. Repeat the previous steps for each fiscal year that has transactions that were settled against transactions in 2022. Always export the detailed transactions to Excel.

    After all the detailed transactions from 2021 and 2023 are exported to Excel, you're ready to unsettle the transactions by using the new inquiry page.

12. Change the fiscal year to 2022.
13. Select all the records in the grid, and then select **Unsettle marked records**. All the selected transactions in the grid will be unsettled.

    Two warning messages are shown to ensure that the transaction details are exported to Excel before the transactions are unsettled. If you accidentally unsettle ledger transactions before you send the details to Excel, there's no way to reverse the unsettlement.

    ![Unsettling cross-settlement transactions.](./media/revert-unsettle.png)

14. Use the Excel data to find the total amount of transactions in 2021 and 2023 that were settled against transactions in 2022. In this example, the transactions for 2021 total $525, and the transactions for 2023 total $700.
15. Post an adjusting general journal to split the opening balance for 2022 into two amounts: the portion that was settled to the 2021 fiscal year and the portion that hasn't yet been settled to 2022.

    - **Portion of the opening balance that was settled to the previous year:** The first amount is $525, based on the totals that were found that were settled across 2021 and 2022.
    - **Portion of the opening balance that wasn't settled to the previous year:** The second amount is the difference between the opening balance and the settled amount of $525. The remaining amount is $1,025 – $525 = $500.

    In this way, you can settle the 2022 transactions against the $525 that was originally settled against the 2021 transaction. This step is required because ledger settlement doesn't allow for partial settlement.

    1. Go to the general journal, and post the adjustment. Your organization will have to decide what transaction date to use, based on the periods that are open. These transactions might have been settled by using a settlement date of January or February 2022, but the adjustment might have to be posted into December if that's the only open period.
    2. You might have to temporarily turn off the **Do not allow manual entry** parameter for account 110200 on the **Main account** page. This adjustment won't be posted if the main account doesn't allow for manual entry.

    ![Posting an adjusting general journal.](./media/not-post.png)

16. You can now resettle the unsettled transactions. Return to the **Ledger settlements** page, specify a date range of January 1 through December 31, 2022, and filter on main account 110200. Then use the detailed transactions that you exported to Excel to find the specific transactions that must be resettled. The following illustration shows the unsettled transactions that now exist.

    ![Unsettled transations.](./media/updated-unsettled.png)

    - The opening balance of $1,025 can be settled against the adjustment for -$1,025.
    - The detailed transactions that were unsettled for -$400, -$50, and -$75 can be settled against the adjustment for $25.

17. Enable the **Enable Advanced Awareness Options** parameter. You're now ready to run the year-end close.

    - Before you run the year-end close, consider selecting the **Keep details** option for all balance sheet accounts in the ledger settlement setup. For more information, see [Awareness between ledger settlement and year-end close](awareness-between-ledger-settlement-year-end-close.md).
    - When you begin the year-end close for 2022, if transactions are still found that were settled across fiscal years, the year-end close process will immediately notify you. This situation might occur if users settled transactions across fiscal years after you completed the previous steps.
    - If 2021 and 2022 transactions are still settled, you'll have to disable the **Enable advanced awareness options** parameter again and then repeat the previous steps to unsettle those transactions. This approach is required because 2021 is closed, and transactions can't be unsettled in a closed fiscal year.
    - If 2022 and 2023 transactions are still settled, you don't have to disable the **Enable advanced awareness options** parameter. Because neither 2022 nor 2023 is closed, you can use the previous steps to unsettle the transactions.

18. You can settle the $700 transaction from 2023 against the detailed transactions that were brought over as opening balances in 2023. This transaction won't be settled against the original transaction in 2022.

After the year-end close for 2022 is successfully run, you can leave the **Enable advanced awareness options** parameter enabled.
