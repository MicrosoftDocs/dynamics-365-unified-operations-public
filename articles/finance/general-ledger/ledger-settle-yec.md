---
# required metadata

title: Awareness between ledger settlement feature before the year-end close
description: This article provides information about awareness between ledger settlements feature before the General ledger year-end close.
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

# Awareness between ledger settlement feature before year-end close

[!include [banner](../includes/banner.md)]
Preparing for ledger settlement Awareness feature, before year-end close

One primary change of the **Awareness between ledger settlement and year end close** feature (Awareness) is that ledger settlement can't be done across fiscal years. 
The cross-year limitation is only relevant to ledger settlement, not accounts receivable or accounts payable settlement. 


In preparation for enabling the feature, the fiscal year that will go through the year-end close must not have any ledger transactions that are settled across fiscal years. Specifically, any transactions posted in the fiscal year for which you're running the year-end close must be unsettled from transactions posted into a
different fiscal year. The transactions can then be resettled against transactions within the same fiscal year. 


This topic walks you through the steps required to identify, unsettle and resettle the ledger transactions that are settled across years. For exampe, fiscal year 2021 has been closed. You're preparing to run the year-end close for fiscal year 2022. 

A new inquiry has been introduced on release 10.0.29 that makes the identification and unsettling process easier. If on that release or later, use the steps can be found in scenarios 3 (preparing before year end close) or scenario 4 (preparing after year end close). 

## Example setup
The following transactions were posted for main account 110190. The ledger transactions in green are settled within the same fiscal year, and don’t need to change. Transactions in red are ledger settled but the transactions have transaction dates in different fiscal years. Those transactions must be identified and potentially have the ledger settlement reversed.  

![Ledger transactions.](./media/YEC1.png)

## Example 
The following steps should be used if your organization wants to use the feature before you run the year-end close for fiscal year 2022. 

>[!NOTE]
>	The year-end close for 2021 and earlier fiscal years must only be rerun if new transactions are posted into the fiscal year 2021 or earlier. When completing the following steps, no new transactions are posted into 2021 so the year-end close doesn’t have to be rerun.
>	Ledger transactions that are settled across fiscal years can remain ledger settled as long as they're not settled against a transaction posted into 2022 or later.  For example, if you have settled transactions across 2019 and 2020, they can remain settled.


1.	Optional: Temporarily enable the Awareness feature. 
 - If you choose to enable the feature, it must be disabled in later steps as noted. The benefit of enabling the feature now is to temporarily prevent users from settling ledger transactions that were posted in different fiscal years. 
 - If you choose to not enable the feature, it would be best to notify your team to not settle transactions across fiscal years. If cross-year settlement occurs after the following steps are completed, you will need to repeat the steps to identify and unsettle the ledger transactions.

2.	Next you need to identify the total of all the transactions that are settled across fiscal years 2021 and 2022. This is possible by going to the **Ledger settlement** page.
 - Enter a date range for the entire fiscal year 2021. For example, enter 1/1/2021 to 12/31/2021 if using a calendar year.
    - If the feature is enabled, you'll receive a warning that transactions can't be settled or unsettled for a closed fiscal year. The warning isn’t an issue because no settlement or unsettlement is occurring in this step.
 - Filter to show **Settled transactions**. 
 - Filter on one ledger account at a time. 
    - You'll need to repeat these steps for each ledger account for which ledger settlement occurs. If other ledger accounts are no longer setup for ledger settlement, you may need to temporarily add them back to the Ledger settlement setup, and perform these steps if they have transactions within 2022 that are settled to transactions in another fiscal year.
  
 - Right-click on the **Status** column and choose **Group** by this column. Right-click on the **Amount** in **Transaction currency** column and choose **Total** this column. 
      - If you only settled transactions within 2021, the total would be zero.  
      - If you have transactions that were settled across fiscal years, it won’t be zero. 
 - In screenshot below, there's a balance of $525.00. This is the total of the transactions that were settled against transactions in a different fiscal year. Your total may include transactions settled between 2021/2022 and transactions settled between 2022/2023.  
  
  ![Ledger transactions 2021-2022.](./media/YEC2.png)
  
 
 - Identify which transactions were settled between 2020 and 2021 by further filtering on the **Settlement date**. 
    - Enter a date range filter of 1/1/2021 to 12/31/2021. No transactions are shown because no 2020 transactions were settled to transactions posted in 2021.
 - Identify which transactions were settled between 2021 and 2022 by changing the date filter on the **Settlement date**. 
    - Enter a date range filter of 1/1/2022 to 12/31/2022. The transactions are shown again and the total is $525.00 because all the transactions were settled between 2021 and 2022.

3.	Identify the total of all the transactions that are settled across fiscal years 2021 and 2022. 
   - Go to the **Ledger settlement** page.
   - Enter a date range for the entire fiscal year 2022. For example, enter 1/1/2022 to 12/31/2022 if using a calendar year.
   - Filter to only the **Settled transactions**. 
   - Filter on one ledger account at a time.
   - Right-click on the **Status** column and choose **Group** by this column. Right-click on the **Amount** in the **Transaction currency** column and choose **Total** this column.
  
  ![Ledger transactions total amounts.](./media/YEC3.png)
  
   - Add an additional filter on the **Settlement date** as 1/1/2022 to 12/31/2022. The same total of $525.00 is shown. This validates that the total amount of transactions settled across 2021 and 2022 is $525.00. 
  
  ![Ledger transactions settlement date 2022 and 2023.](./media/YEC4.png)
 
   - Change the additional filter on the **Settlement date** as 1/1/2023 to 12/31/2023. A new total of $700 is shown. This is the total amount of the transactions that were settled across 2022 and 2023. 
 
4.	Repeat the steps in #3 for fiscal year 2023. The total should match the $700 from 2022 because no 2023 transactions were settled to transactions in 2024.
5.	If you enabled the feature in step 1, it must be disabled before continuing with the next step. The next steps are to reverse the ledger settlement that crossed fiscal years. With the feature enabled, ledger settlement can't be reversed for fiscal year 2021, so the feature must be disabled before continuing.
6.	Once the feature is disabled, use the same filters on the ledger settlement pages to reverse the ledger settlement of the detailed transactions. 
 - Return to the **Ledger settlement** page and filter on transaction dates for 2021. Add an additional filter on the **Settlement date** between 1/1/2022 and 12/31/2022. Find the detailed transactions that comprise the $525 total. This may not be easy to filter. You may need to send the data to Excel to evaluate.  
 - Once you have the list of transactions, select the ledger transactions on the **Ledger settlement** page and choose **Mark selected**. You don't need to see both sides of the ledger transactions that were settled. If you mark either the debit or credit, it will reverse everything with the same **Settlement ID**, even if the **Marked amount** isn't zero.
 - Click **Reverse marked transactions** to unsettle the transactions. 
  
  ![Reverse marked transactions.](./media/YEC5.png)
  

7.	Repeat step 6 to reverse the settlement for the transactions that were settled across 2022 and 2023. 

![Reverse ledger transactions.](./media/YEC6.png)
 

8.	Post an adjusting general journal to split the opening balance for 2022 into two amounts: the portion settled to the 2021 fiscal year transaction and the portion not settled yet within 2022. This will allow you to settle the 2022 transactions against the $525 originally settled against 2021 transaction. This is required because ledger settlement doesn’t allow partial settlement. 
 - The portion of the opening balance that was settled to the previous year.
    - The first amount is $525 based on the totals found settled across 2021 and 2022.
  - The portion of the opening balance that was NOT settled to the previous year. 
    - The second amount is the difference between the opening balance and amount settled of $525. The remaining amount is $1025 - $525 = $500.  
 - Go to the general journal and post the adjustment. Your organization will have to decide what transaction date to use based on what periods are open. These transactions may have been settled with a settlement date of January or February 2022, but the adjustment may have to be posted in December if that is the only open period. 
 - It may be necessary to temporarily turn off the parameter on the Main account setup **Do not allow manual entry**. If the main account doesn’t allow manual entry, this adjustment won’t post. 
  
  ![Adjustment not posting.](./media/YEC7.png)
 
9.	The unsettled transactions can be resettled again. Go to the **Ledger settlement** page and restrict the date range to 1/1/2022 to 12/31/2022. The following unsettled transactions now exist:

![Unsettled transactions.](./media/YEC8.png)

  - The **Opening balance** of $1,025 can be settled against the adjustment for -$1,025. 
  - The detailed transactions that were unsettled for -$400, -$50, and -$75 can be settled against the adjustment for $525.00. 
  
  ![Detailed transactions.](./media/YEC9.png)
 
10.	Enable the **Awareness** feature. You're now ready to run the year-end close. 
 - Before running the YEC, consider marking the option **Keep details in the Ledger settlement** setup for all balance sheet accounts. For more information, see Awareness document for the benefits of doing this.   
 - When beginning the year-end close for 2022, if transactions are still found that were settled across fiscal years, the year-end close process will immediately notify you.
 - If 2021 and 2022 transactions are still settled, you'll need to disable the feature again, and repeat the previous steps to unsettle the transactions. This is because transactions can't be unsettled in a closed fiscal year, and 2021 is closed. 
 - If 2022 and 2023 transactions are still settled, you do NOT need to disable the feature. The previous steps can be used to unsettle the transactions because neither 2022 or 2023 are closed. 
 
11.	After successfully running the year end close for 2022, the feature can remain enabled moving forward. 


