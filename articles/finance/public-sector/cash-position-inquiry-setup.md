---
# required metadata

title: Cash Position Inquiry Setup
description: This topic describes the Cash position inquiry, which lets you determine the corresponding cash positions for financial dimension sets that contain self-balancing dimensions.
author: velofog
manager: AnnBe
ms.date: 10/07/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Operations, Core 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
ms.search.industry: public sector
ms.author: v-alpavk
ms.search.validFrom: 2019-10-07
ms.dyn365.ops.version: 10.0.7

---
# Cash Position Inquiry Setup

This topic describes the Cash position inquiry, which lets you determine the corresponding cash positions for financial dimension sets that contain self-balancing dimensions. The inquiry shows the following items: 

•	The beginning cash balance
•	The effect of the addition of cash receipts
•	The subtraction of cash disbursements
•	The subtraction of interfund transfers to arrive at an ending balance. 
•	From the ending balance, general budget reservations, encumbrances, or pre-encumbrances are subtracted to arrive at an unencumbered balance
This inquiry differs from other inquiries in that it lets you customize the terminology for column names and for the main accounts that are used to derive amounts displayed in the columns. On the **Cash position parameters** page, the columns that appear in the inquiry are numbered starting, with the left-most data column as Column one.
Cash position inquiry setup
1.	Go to **General ledger > Ledger setup > Cash position parameters.**
2.	In the **Cash position parameters** page, in the Column one group:
•	In the **Column name** field, type a label for the heading on the inquiry’s first column, for example, "Beginning balance."
•	In the **Opening balance main accounts** field, select the account(s) that you want to reference for inquiring on the opening balance.
3.	In the Column two group:
•	Specify a label for the second column in the inquiry for example, “Cash receipts.”
> [!Note]
> In the **Debit and credit main accounts** list, select the main accounts to use only the sum of all debit and credit transaction amounts in the data included in the inquiry. 
•	The inquiry will add the net of the debit and credit accounts plus the debit amount and credit amounts from the main accounts in the other fields in the group.
•	In the **Debit-only main accounts** list, select the main accounts from which to use only the sum of all debit transaction amounts for the inquiry's data.
•	In the **Credit-only main accounts** list, select the main accounts from which to use only the sum of all credit transaction amounts for the inquiry's data.
4.	In the Column three and Column four groups:
•	Specify a label for the third column (for example, "Cash disbursements") and fourth column (for example, "Interfund transfers").
•	For both columns, specify the main account numbers to distribute debit and credit entries, as well as debit-only main accounts, and credit-only main accounts.
5.	In the Column five group, specify a label for the fifth column (for example, Ending balance).
> [Note!] 
> A sum will be calculated from the accounts you specified in the first four columns, which in the examples will include Beginning balance plus Cash receipts, minus Cash disbursements, minus Interfund transfers.
6.	In the Column six and Column seven groups:
•	Specify a label for column six, for example, "General budget reservations" or "Encumbrances" and column seven, for example, "Pre-encumbrances.
•	For both columns, specify account numbers for the **Debit and credit main accounts**, **Debit-only main accounts**, and **Credit-only main accounts**.
7.	In the Column eight group:
•	Specify a column label, for example, "Unencumbered balance."
> [Note!] 
> Microsoft Dynamics 365 for Finance and Operations automatically calculates a result from the accounts you specified for columns five through seven will be calculated. In the examples, the accounts include Ending balance minus Encumbrances, minus Pre-encumbrances.
8.	Click **Save**.
## Running the inquiry
1.	Go to **General ledger > Inquiries and reports > Cash position**.
2.	In the **Parameters** section:
•	Select the **Date interval** code, or the **From date** and **To date**.
•	Select the **Financial dimension set**.
•	Click **Calculate balances** to run the inquiry.
### Optional:
•	Set the **Suppress accounts with all zeroes option** to Yes to exclude accounts that have all zero balances from the inquiry.
•	Set the **Display segments in separate columns option** to Yes to show the account names for each dimension as separate columns in the grid.
•	To filter the values for a specific dimension, select the dimensions to include in the fields below the **Financial dimension set** field. The options that are available depend on which financial dimension set you selected.
