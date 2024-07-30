---
title: Set up and run the Cash position inquiry
description: Learn about the Cash position inquiry, which lets you determine the cash positions for financial dimension sets that contain self-balancing dimensions.
author: velofog
ms.author: twheeloc
ms.topic: article
ms.date: 10/07/2019
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.industry: public sector
ms.search.validFrom: 2019-10-07
ms.search.form:
ms.dyn365.ops.version: 10.0.7
---

# Set up and run the Cash position inquiry
[!include [banner](../includes/banner.md)]


This article provides information about the **Cash position** inquiry. This inquiry lets you determine the corresponding cash positions for financial dimension sets that contain self-balancing dimensions. It shows the following items:

- The beginning cash balance
- The effect of the addition of cash receipts
- The subtraction of cash disbursements
- The subtraction of interfund transfers to arrive at an ending balance
- The subtraction of general budget reservations, encumbrances, or pre-encumbrances from the ending balance to arrive at an unencumbered balance

This inquiry differs from other inquiries because you can customize the terminology for column names and for the main accounts that are used to derive the amounts that appear in the columns. On the **Cash position parameters** page, the columns that appear in the inquiry are numbered sequentially from left to right. The left-most column is **Column one**.

## Set up the Cash position inquiry

1. Go to **General ledger \> Ledger setup \> Cash position parameters**.
2. On the **Cash position parameters** page, in the **Column one** group, follow these steps:

    - In the **Column name** field, enter a label for the heading of the first column in the inquiry (for example, **Beginning balance**).
    - In the **Opening balance main accounts** field, select the accounts that you want to reference for inquiries about the opening balance.

3. In the **Column two** group, follow these steps:

    - Enter a label for the heading of the second column (for example, **Cash receipts**).
    - To use only the sum of all debit and credit transaction amounts for the data that is included in the inquiry, select the main accounts in the **Debit and credit main accounts** list.
    
        The inquiry will add the net amount of the debit and credit accounts, plus the debit and credit amounts from the main accounts that are specified in the other fields in the group.

    - To use only the sum of all debit transaction amounts for the inquiry's data, select the main accounts in the **Debit-only main accounts** list.
    - To use only the sum of all credit transaction amounts for the inquiry's data, select the main accounts in the **Credit-only main accounts** list.

4. In the **Column three** and **Column four** groups, follow these steps:

    - Enter a label for the heading of the third column (for example, **Cash disbursements**) and the fourth column (for example, **Interfund transfers**).
    - For both columns, specify the main accounts to distribute debit and credit entries. Also specify the debit-only main accounts and credit-only main accounts.

5. In the **Column five** group, enter a label for the heading of the fifth column (for example, **Ending balance**).

    A result is automatically calculated from the accounts that you specified in the first four columns. For this example, the calculation is Beginning balance + Cash receipts – Cash disbursements – Interfund transfers.

6. In the **Column six** and **Column seven** groups, follow these steps:

    - Enter a label for the heading of the sixth column (for example, **General budget reservations** or **Encumbrances**) and the seventh column (for example, **Pre-encumbrances**).
    - For both columns, specify account numbers for the debit and credit main accounts, and for the debit-only main accounts and credit-only main accounts.

7. In the **Column eight** group, enter a label for the heading of the eighth column (for example, **Unencumbered balance**).

    A result is automatically calculated from the accounts that you specified in the fifth through seventh columns. For this example, the calculation is Ending balance – Encumbrances – Pre-encumbrances.

8. Select **Save**.

## Run the Cash position inquiry

1. Go to **General ledger \> Inquiries and reports \> Cash position**.
2. In the **Parameters** section, follow these steps:

    - In the **Date interval** field, select the code for the date interval. Alternatively, in the **From date** and **To date** fields, define the date interval.
    - In the **Financial dimension set** field, select the financial dimension set.
    - Optional: Set the **Suppress accounts with all zeroes** option to **Yes** to exclude accounts from the inquiry if they have all 0 (zero) balances.
    - Optional: Set the **Display segments in separate columns** option to **Yes** to show the account names for each dimension as separate columns in the grid.
    - Optional: To filter the values for a specific dimension, in the fields below the **Financial dimension set** field, select the dimensions to include. The options that are available vary, depending on the financial dimension set that you selected.

3. Select **Calculate balances** to run the inquiry.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
