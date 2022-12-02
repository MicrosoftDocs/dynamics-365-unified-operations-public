---
# required metadata

title: Awareness between ledger settlement feature after the year-end close
description: This article provides information about awareness between ledger settlements feature after the General ledger year-end close.
author: kweekley
ms.date: 12/02/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom:
# ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2022-01-31
ms.dyn365.ops.version: 10.0.25

---
# Awareness between ledger settlement feature after year-end close

One primary change of the “Awareness between ledger settlement and year end close” feature (Awareness) is that ledger settlement cannot be done across fiscal years. The cross-year limitation is only relevant to ledger settlement, not Accounts receivable or Accounts payable settlement. 

In preparation for enabling the feature, the fiscal year that will go through the year-end close must also not have any ledger transactions that are settled across fiscal years. Specifically, any transactions posted in the fiscal year for which you are running the year end close must be unsettled from transactions posted into a different fiscal year. The transactions can then be resettled against transactions within the same fiscal year. 

This article walks through the steps required to identify, unsettle and resettle the ledger transactions that are cross-year settled. For this scenario, fiscal year 2022 has been closed. The focus is preparing the ledger settlement transactions well before running the 2023 year-end close. 

If you're not currently on Microsoft Dynamics 365 Finance release 10.0.29 or above, the steps for identifying, unsettling and resettling the ledger transactions can be found using scenario 1 (preparing before year-end close) and scenario 2 (preparing after year-end close). 

## Scenario setup
The following transactions were posted for main account 110200. The transactions in green are ledger settled within the same fiscal year, and don’t need to change. Transactions in red were ledger settled but the transactions have transaction dates in different fiscal years. Those transactions must be identified and potentially have the ledger settlement reversed. 

![Total main account](./media/excel.png)

## Scenario steps
The following steps should be used if your organization wants to use the feature after you run the year-end close for fiscal year 2022. 

A few notes:
•	The year-end close for 2022 and earlier fiscal years must only be rerun if new transactions are posted into the fiscal year 2022 or earlier. When completing the following steps, no new transactions are posted into 2022 so the year-end close doesn’t have to be rerun.
•	Ledger transactions that are settled across fiscal years can remain ledger settled as long as they are not settled against a transaction posted into 2022 or later.  For example, if you have settled transactions in 2019 and 2020, they can remain settled.

1.	Complete the YEC for 2022 without the Awareness feature enabled. 
2.	Identify all the transactions posted in other fiscal years but settled against transactions posted in 2023, which is the next fiscal year that will be closed. 

>[!Note] 
> 2021 transactions settled against 2022 transactions aren’t relevant because the year has already been closed for 2022. Those transactions can remain settled. 

To identify the transactions in 2023, go to the **Ledger settlement** page, then directly select the **Review cross-year settlement** button. 
-   Select fiscal year 2023, the next fiscal year we want to run the year end close process for.
-   Select the Financial dimension set to display the financial dimensions you want to see for the ledger account. The main account is always shown, even if a dimension set is selected that doesn’t contain a main account. 
-   Click **Show transactions**. The inquiry page will show all transactions from other fiscal years that are settled against transactions posted within 2023.  

![2023 cross-year settlements](./media/2023-cross-settlement.png)

-   Right click on the grid and choose **Export all** rows. These are all the transactions that must be unsettled from the transactions in 2022 in order to run the year-end close next year for 2023. You want a record of these transactions.  
-   Once all the detailed transactions from 2022 are exported to Excel, you are ready to unsettle the transactions using the new inquiry page. 
    -   Select all the records in the grid and choose the **Unsettle marked records** button. All the selected transactions in the grid will be unsettled.
    -   Two warning messages are given to ensure that the transaction details were exported to Excel before they are unsettled. If you accidentally unsettle before sending the detail to Excel, there is no way to revert the unsettlement of the ledger transactions. 

![Revert cross-year settlements](./media/revert-settlement.png)

5.	Using the Excel data, find the total amount of transactions in 2022 that were settled to transactions within 2023. For 2023, the transactions total $700. 
6.	Next, post an adjusting general journal to split the opening balance for 2022 into two amounts: the portion settled to the 2022 fiscal year transaction and the portion not settled yet within 2023. This will allow you to settle the 2023 transactions against the $700 originally settled against 2022 transaction. This is required because ledger settlement doesn’t allow partial settlement. 
-   The portion of the opening balance that was settled to the previous year.
    -   The first amount is $700 based on the totals found settled across 2021 and 2022.
-   The portion of the opening balance that was NOT settled to the previous year. 
    -   The second amount is the difference between the opening balance and amount settled of $700. The remaining amount is $1700 - $700 = $1000.  
-   Go to the general journal and post the adjustment. Your organization will have to decide what transaction date to use based on what periods are open in 2023.
-   It may be necessary to temporarily turn off the parameter on the **Main account** setup **Do not allow manual entry**.  If the main account doesn’t allow manual entry, this adjustment won’t post. 

![Do not allow manual entry](./media/no-manual4.png)

7.	The unsettled transactions can be resettled again. Return to the **Ledger settlement** page and restrict the date range to 1/1/2023 to 12/31/2023. Use the detailed transactions sent to Excel to find the specific transactions that need to be resettled. The following unsettled transactions now exist:

![2023 Unsettled transactions](./media/2023-unsettled5.png)

-   The Opening balance of $1,700 can be settled against the adjustment for -$1,700. 
-   The detailed transactions that were unsettled for -$700 can be settled against the adjustment for 700.00.  
8.	Enable the **Awareness** feature. You're now ready to run the year end close. 
-   Before running the year-end close for 2023, consider marking the option **Keep details** on the **Ledger settlement setup** for all balance sheet accounts. For more information, see Awareness.   
-   When beginning the year-end close for 2023, if transactions are still found that were settled across fiscal years, the year-end close process will immediately notify you. This may happen if users settled transactions across fiscal years before the feature was enabled.
-   If 2022 and 2023 transactions are still settled, you'll need to disable the feature again and repeat the previous steps to unsettle the transactions. This is because transactions can't be unsettled in a closed fiscal year, and 2022 is closed. 
9.	After successfully running the year end close for 2022, the feature can remain enabled moving forward. 






