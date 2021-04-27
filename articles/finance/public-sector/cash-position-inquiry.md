---
# required metadata

title: Cash position inquiry
description: This topic provides information about how to determine the corresponding cash positions for financial dimension sets that contain self-balancing dimensions.
author: velofog
ms.date: 10/24/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
ms.search.industry: public sector
ms.author: roschlom
ms.search.validFrom: 2019-10-24
ms.dyn365.ops.version: 10.0.7

---

# Cash position inquiry
[!include [banner](../includes/banner.md)]

The **Cash position** inquiry allows you to determine the corresponding cash positions for financial dimension sets that contain self-balancing dimensions. The inquiry shows the beginning cash balance, and the effect of the addition of cash receipts, the subtraction of cash disbursements, and the subtraction of interfund transfers to arrive at an ending balance. Then, from the ending balance, general budget reservations, encumbrances, or pre-encumbrances are subtracted to arrive at an unencumbered balance.

This inquiry is unique in that it allows users to customize the terminology for column names and for the main accounts that are used to derive amounts for the columns. On the **Cash position parameters** page, the columns that appear in the inquiry are numbered starting with the left-most data column as column one.

## Cash position inquiry setup

1. Go to **General ledger** > **Ledger setup** > **Cash position parameters**.
2. In the **Cash position parameters** page, in the **Column one** section:

- In the **Column name** field, type a label to use as the header for the inquiry’s first column (for example, "Beginning balance").
- In the **Opening balance main accounts** field, select the account(s) that you want to reference for inquiring on the opening balance.

3. In the **Column two** section: 

- Specify a label for the second column in the inquiry (for example, "Cash receipts").
- In the **Debit and credit main accounts** list, select the main accounts from which to use only the sum of all debit and credit transaction amounts for the inquiry's data. 

> [!NOTE]
> The inquiry will add the net of the debit and credit accounts plus the debit amount and credit amounts from the main accounts in the other fields in the group.

- In the **Debit-only main accounts** list, select the main accounts from which to use only the sum of all debit transaction amounts for the inquiry's data.
- In the **Credit-only main accounts** list, select the main accounts from which to use only the sum of all credit transaction amounts for the inquiry's data.

4. In the **Column three** and **Column four** sections: 

- Specify a label for the third column (for example, "Cash disbursements") and fourth column (for example, "Interfund transfers").
- For both columns, specify account numbers for the debit and credit main accounts, debit-only main accounts, and credit-only main accounts.

5. In the **Column five** group section, specify a label for the fifth column (for example, ""Ending balance""). 

> [!NOTE]
> Dynamics 365 Finance automatically calculates a sum from the accounts you specified for the first four columns: Beginning balance plus cash receipts, minus cash disbursements, minus interfund transfers.

6. In the **Column six** and **Column seven** sections: 

- Specify a label for column six (for example, General budget reservations or Encumbrances") and column seven (for example, "Pre-encumbrances").
- For both columns, specify account numbers for the **Debit and credit main accounts**, **Debit-only main accounts**, and **Credit-only main accounts**.

7. In the **Column eight** section, specify a column label (for example, "Unencumbered balance"). 

> [!NOTE]
> Dynamics 365 Finance automatically calculates a result from the accounts you specified for columns five through seven: Ending balance minus Encumbrances, minus Pre-encumbrances.

8. Click **Save**.

## Running the inquiry

1. Go to **General ledger** > **Inquiries and reports** > **Cash position**.
2. In the **Parameters** section: 

- Select the **Date interval** code, or the **From date** and **To date**.
- Select the **Financial dimension set**.
- Select **Calculate balances** to run the inquiry.

Optional: 

- Set the **Suppress accounts with all zeroes** option to **Yes** to exclude accounts that have zero balances from the inquiry.
- Set the **Display segments in separate columns** option to **Yes** to show the account names for each dimension as separate columns in the grid.
- If you want to filter the values for a specific dimension selected, select the dimensions you want in the fields below the **Financial dimension set** field. The choices you have to select from depend on which financial dimension set you selected.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]