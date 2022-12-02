---
# required metadata

title: Awareness between ledger settlement feature before the year-end close using the inquiry window.
description: This article provides information about awareness between ledger settlements feature before the General ledger year-end close using the inquiry window.
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
# Awareness between ledger settlement feature before year-end close using inquiry window

One primary change of the **Awareness between ledger settlement and year end close** feature (Awareness) is that ledger settlement can't be done across fiscal years. 
The cross-year limitation is only relevant to ledger settlement, not Accounts receivable or Accounts payable settlement. 

In preparation for enabling the feature, the fiscal year that will go through the year-end close must also not have any ledger transactions that are settled across fiscal years. Specifically, any transactions posted in the fiscal year for which you're running the year end close must be unsettled from transactions posted into a different fiscal year. The transactions can then be resettled against transactions within the same fiscal year. 

This articles describes the steps required to identify, unsettle and resettle the ledger transactions that are cross-year settled. For this scenario, fiscal year 2021 has been closed. You're preparing to run the year-end close for fiscal year 2022. 

If you're not currently on Microsoft Dynamics 365 Finance release 10.0.29 or above, the steps for identifying, unsettling and resettling the ledger transactions can be found using scenario 1 (preparing before year-end close) and scenario 2 (preparing after year-end close). 

## Scenario setup
The following transactions were posted for main account 110200. The transactions in green are ledger settled within the same fiscal year, and don’t need to change. Transactions in red were ledger settled but the transactions have transaction dates in different fiscal years. Those transactions must be identified and potentially have the ledger settlement reversed.  

## Scenario steps
The following steps should be used if your organization wants to use the feature before you run the year-end close for fiscal year 2022. 
A few notes:
 - The year-end close for 2021 and earlier fiscal years must only be rerun if new transactions are posted into the fiscal year 2021 or earlier. When completing the following steps, no new transactions are posted into 2021 so the year-end close doesn’t have to be rerun.
 - Ledger transactions that are settled across fiscal years can remain ledger settled as long as they are not settled against a transaction posted into 2022 (the year being closed) or later. For example, if you have settled transactions in 2019 and 2020, they can remain settled.

1.	Do NOT enable the Awareness feature. 
2.	Identify all the transactions posted in other fiscal years but settled against transactions posted in 2022. This is possible by going to the **Ledger settlement** page, then directly select the **Review cross-year settlement** button. 
 - Select fiscal year 2022, the fiscal year we want to run the year end close process for.
 - Select the Financial dimension set to display the financial dimensions you want to see for the ledger account. The main account is always shown, even if a dimension set is selected that doesn’t contain a main account. 
 - Click **Show transactions**. The inquiry page will show all transactions, for all ledger accounts (even if they're not in ledger settlement setup anymore), from all other fiscal years that are settled against transactions posted within 2022. There are three different ledger accounts shown. 


3.	Right click on the grid and choose **Export all rows**. These are all the transactions that must be unsettled from the transactions in 2022 to run the year-end close. You want the detailed transaction list to correctly resettle the transactions later. 
4.	Note the fiscal years for which the transactions were posted. In this scenario, there are transactions in 2021 and 2023. 
5.	Still in the inquiry page, change the fiscal year to 2021, the first fiscal year that contains transactions settled against 2022 transactions. 
 - Filter on the transaction date column to only include transactions posted within 2022. These are the detailed transactions from 2022 that were settled against transactions in 2021. These transactions are unsettled and resettled to transactions within 2022, in the following steps. It’s essential to maintain this detail in Excel.

>[!IMPORTANT] 
>Right click on the grid and choose **Export all rows**. 

6.	Still in the inquiry page, change the fiscal year to 2023, the next fiscal year that contains transactions settled against 2022 transactions. 
 - Filter on the transaction date column to only include transactions posted within 2022. These are the detailed transactions from 2023 that were settled against transactions in 2022. These transactions are unsettled and resettled to transactions within 2022, in the following steps. It’s essential to maintain this detail in Excel.

>[!IMPORTANT] 
>Right click on the grid and choose **Export all rows**.

 - Repeat the previous steps for each fiscal year that has transactions settled against transactions in 2022. Always export the detailed transactions to Excel. 
7.	Once all the detailed transactions from 2021 and 2023 are exported to Excel, you're ready to unsettle the transactions using the new inquiry page. 
 - Change the fiscal year to 2022.
 - Select all the records in the grid and choose the **Unsettle marked records** button. All the selected transactions in the grid will be unsettled.
 - Two warning messages are given to ensure that the transaction details were exported to Excel before they're unsettled. If you accidentally unsettle before sending the detail to Excel, there's no way to revert the unsettlement of the ledger transactions. 
8.	Using the Excel data, find the total amount of transactions in 2021 and 2023 that were settled to transactions within 2022. For 2021, the transactions total $525 and for 2023, the transactions total $700. 
9.	Post an adjusting general journal to split the opening balance for 2022 into two amounts: the portion settled to the 2021 fiscal year transaction and the portion not settled yet within 2022. This will allow you to settle the 2022 transactions against the $525 originally settled against 2021 transaction. This is required because ledger settlement doesn’t allow partial settlement. 
 - The portion of the opening balance that was settled to the previous year.
    - The first amount is $525 based on the totals found settled across 2021 and 2022.
 - The portion of the opening balance that was NOT settled to the previous year. 
    - The second amount is the difference between the opening balance and amount settled of $525. The remaining amount is $1025 - $525 = $500.  
 - Go to the general journal and post the adjustment. Your organization will have to decide what transaction date to use based on what periods are open. These transactions may have been settled with a settlement date of January or February 2022, but the adjustment may have to be posted in December if that is the only open period. 
 - It may be necessary to temporarily turn off the parameter on the 110200 main account setup **Do not allow manual entry**. If the main account doesn’t allow manual entry, this adjustment won’t post. 
 
10.	The unsettled transactions can be resettled again. Return to the **Ledger settlement** page, enter the date range 1/1/2022 to 12/31/2022 and filter on the main account 110200. Use the detailed transactions sent to Excel to find the specific transactions that need to be resettled. The following unsettled transactions now exist:
 
 - The Opening balance of $1,025 can be settled against the adjustment for -$1,025. 
 - The detailed transactions that were unsettled for -$400, -$50, and -$75 can be settled against the adjustment for $25.00.  
11.	Enable the **Awareness** feature. You are now ready to run the year end close. 
 - Before running the YEC, consider marking the option **Keep details in the Ledger settlement** setup for all balance sheet accounts. For more information, see Awareness document.   
 - When beginning the year-end close for 2022, if transactions are still found that were settled across fiscal years, the year-end close process will notify you. This may happen if users settled transactions across fiscal years after you completed the previous steps.
 - If 2021 and 2022 transactions are still settled, you'll need to disable the feature again and repeat the previous steps to unsettle the transactions. This is because transactions can't be unsettled in a closed fiscal year, and 2021 is closed. 
 - If 2022 and 2023 transactions are still settled, you don't need to disable the feature. The previous steps can be used to unsettle the transactions because neither 2022 or 2023 are closed. 
12.	The $700 transaction from 2023 can be settled against the detailed transactions brought over as opening balances in 2023. It won't be settled against the original transaction in 2022. 

After successfully running the year end close for 2022, the feature can remain enabled moving forward. 




