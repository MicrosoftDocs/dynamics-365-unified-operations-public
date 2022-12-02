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

[!include [banner](../includes/banner.md)]
Preparing for ledger settlement Awareness feature, after year-end close.

A major change of the **Awareness between ledger settlement and year end close** feature (Awareness) is that ledger settlement can't be done across fiscal years. 
The cross-year limitation is only relevant to ledger settlement, not Accounts receivable or Accounts payable settlements. 

Before the Awareness feature is enabled, the fiscal year that will go through the year-end close must not have any ledger transactions that are settled across fiscal 
years. Specifically, any transactions posted in the fiscal year for which you're running the year-end close must be unsettled from transactions posted into a different fiscal year. The transactions can then be resettled against transactions within the same fiscal year. 

This article describes the steps required to identify, unsettle and resettle the ledger transactions that are cross-year settled. For this scenario, fiscal year 2022 has been closed. The focus is preparing the ledger settlement transactions well before running the 2023 year-end close. 

## Example setup

The following transactions were posted for main account 110190. The ledger transactions in green are settled within the same fiscal year, and don’t need to change. 
Transactions in red are ledger settled but the transactions have transaction dates in different fiscal years. Those transactions must be identified and potentially have
the ledger settlement reversed.  

![Ledger transactions.](./media/afterYEC1.png)

## Example 

The following steps should be used if your organization wants to use the feature after the year-end close is ran for fiscal year 2022. 

A few notes:
 - The year-end close for 2022 and earlier fiscal years must only be rerun if new transactions are posted into the fiscal year 2022 or earlier. When completing the 
following steps, no new transactions should be posted into 2022 so the year-end close doesn’t have to be rerun.
 - Ledger transactions that are settled across fiscal years can remain ledger settled as long as they're not settled against a transaction posted into 2023 or later.  
For example, if you have settled transactions in 2019 and 2020, they can remain settled.

1.	Complete the YEC for 2022 without the Awareness feature enabled. 
2.	Optional: Enable the Awareness feature after the year-end is complete for 2022. The year-end is considered complete when all adjustments are posted and the year-end
close process will not be run again. 

> [!IMPORTANT] 
> The feature must not be enabled if the year-end close will be run again for 2022. The benefit of enabling the feature now is to prevent users from settling ledger  transactions that were posted in different fiscal years.
 
-   If the year-end close is not complete, the next steps can still be completed without the feature enabled. The feature will be enabled in a later step.

3.	Identify the total of all the transactions that are settled across fiscal years 2022 and 2023. This is possible by going to the **Ledger settlement** page. Note that 2021 transactions settled against 2022 transactions aren’t relevant because the year has already been closed for 2022. Those transactions can remain settled.
-   Enter a date range for the entire fiscal year 2022. For example, enter January 1, 2022 to December 31, 2022 is using a calendar year.
-   In the **Status** field, select **Settled**. 
-   Filter on one ledger account at a time. 
    -   You'll need to repeat these steps for each ledger account for which ledger settlement occurs. 
    -   If other ledger accounts are no longer set up for ledger settlement, you may need to temporarily add them back to the Ledger settlement setup and perform these 
steps if they have transactions within 2023 that are settled to transactions in 2022 or earlier.
-   Right-click on the **Status** column and choose **Group by** this column. Right-click on the **Amount in transaction currency** column and choose **Total** this column. 
    -   If you only settled transactions within 2022, the total would be zero.  
    -   If you have transactions that were settled across fiscal years, it won’t be zero. 
-   Identify which transactions were settled between 2022 and 2023 by filtering on the **Settlement date**. If I filter on a settlement date of January 1, 2023 to December 31, 2023, I get a total of $700, which is the total of transactions that were ledger settled across 2022 and 2023.  

![Total 2022 Ledger transactions.](./media/afterYEC2.png)
 
4.	Repeat the steps in #3 for fiscal year 2023. The total should match the $700 from 2022 because no 2023 transactions were settled to transactions in 2024.

![Total 2023 Ledger transactions.](./media/afterYEC3.png)

 
5.	If you enabled the feature in step 2, it must be disabled before continuing with the next step. The next steps are to reverse the ledger settlement that crossed 
fiscal years. With the feature enabled, ledger settlement can't be reversed for fiscal year 2022, so the feature must be disabled before continuing.
6.	Once the feature is disabled, use the same filters on the ledger settlement pages to reverse the ledger settlement of the detailed transactions.  
-   Return to the **Ledger settlement** page and filter on transaction dates for 2023. From here, find the detailed transactions that comprise the $700 total. This may not be easy to filter. You may need to send the data to Excel to evaluate.  
-   Once you have the list of transactions, select the ledger transactions on the **Ledger settlement** page and choose **Mark selected**. You don't need to see both sides of the ledger transactions that were settled. If you mark either the debit or credit, it will reverse everything with the same **Settlement ID**, even if the **Marked amount** is not zero.
-   Click **Reverse marked transactions** to unsettle the transactions. 
 
![Reverse transactions.](./media/afterYEC4.png)

7.	Post an adjusting general journal to split the opening balance for 2023 into two amounts: the portion settled to the 2022 fiscal year transaction and the 
portion not settled yet within 2023. This will allow you to settle the 2023 transactions against the $700 originally settled against 2022 transaction. This is required
because ledger settlement doesn’t allow partial settlement. 
-   The portion of the opening balance that was settled to the previous year.
    -   The first amount is $700 based on the totals found settled across 2022 and 2023.
-   The portion of the opening balance that was NOT settled to the previous year. 
    -   The second amount is the difference between the opening balance and the first amount of $525: the remaining amount is $1700 - $700 = $1000.  
-   Go to the general journal and post the adjustment. Your organization will have to decide what transaction date to use based on what periods are open in 2023. 
-   It may be necessary to temporarily turn off the **Do not allow manual entry** parameter on the **Main account** page. If the main account doesn’t allow manual entry, this adjustment won’t post.
 
![Adjust won't post.](./media/afterYEC5.png)

8.	The unsettled transactions can be resettled again. Return to the **Ledger settlement** page and restrict the date range to January 1, 2022 to December 31, 2022. The following unsettled transactions now exist:
 
![Unsettled transactions.](./media/afterYEC6.png)
 
-   The Opening balance of $1,700 can be settled against the adjustment for -$1,700. 
-   The detailed transactions that were unsettled for -$700 can be settled against the adjustment for $700.00.  
9.	Enable the feature again. 
10.	Now that the feature is enabled, ledger settlement can't be done across fiscal years. The remaining balance of $1,000 may have to be further divided into smaller 
amounts in order to settle against new transactions in 2023. Some customers choose to post that detail during step 12, where the $1,000 is further divided to represent
the unsettled transactions from 2022. This is essentially mimicking what the Awareness feature does for only this year. Next year, it will happen automatically by 
using the **Keep details** setting in the **Ledger settlement setup**. 


