---
title: Post vendor payment transactions with LATAM Withholding taxes
description: Learn how to post vendor payment journals with LATAM Withholding taxes.
author: Fhernandez0088
ms.date: 10/03/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Post vendor payment transactions with LATAM Withholding taxes

This process consists of two parts, first the vendor invoice posting and then the vendor payment journal posting.

## How to post a vendor invoice with a withholding tax group

1. Go to **Accounts payable > Invoices > Invoice journal**.
2. Click **New**.
4. In the **Name** field, enter or select a value (choose a vendor invoice journal).
5. Click **Lines**.
6. Add a new line.
7.In the **Account** field, specify the desired values (choose a vendor).
8. In the **Credit** field, enter a value.
9. Click the **LATAM** tab.
10. Select a document class (invoice).
11. Complete prefix field with a value.
12. Complete document number field with a value.
13. Verify that **Withholding tax group** field must show the group assigned in the vendor configuration. If it doesn’t, select one from the list.
14. Go to lines, in the **Account type** field select ledger and choose a ledger account to register the expense as offset account or in a new line.
16. In the debit field, enter a value.
16. Select a sales tax group and item tax group according to the expense.

> [!NOTE]
> The vendor invoice can be posted from any journal configured for that purpose and from purchase orders. Just be sure that in the LATAM section the **Withholding tax group** field contains a value.

## How to register a vendor payment journal with a withholding tax.

1. Go to **Accounts payable > Payments > Vendor payment journal**.
2. Click **New**.
3. In the list, mark the selected row.
4. In the **Name** field, enter or select a value (choose a vendor payment journal).
5. Click **Lines**.
6. In the list, mark the selected row.
7. In the **Account field**, specify the desired values (choose a vendor).
10. Select or verify that the vendor line has a payment order as document class in the LATAM section before settling a transaction (the document class can be predefined in the LATAM section from the vendor payment journal name configuration).
8. Go to settle transaction and choose the invoice to pay.
1. In the settlement form check that in the **LATAM** tab the vendor withholding group is selected (select one if it is empty, it also can be changed for another one).
9. Return to journal lines and go to the **LATAM** tab.
11. Complete or verify the document number.
12. After settling a transaction, a bank type line with the calculated withholding tax should appear.
13. Then you can select the payment method for the remaining invoice amount and post the journal. Here is an example: 
    1. On the Action Pane, select **LATAM > Payment methods**.
    1. On the **Payment method** page, select **New**.
    1. In the **Document class id.** field, select a document class for a wire transfer. For more information, see [Document classes for Latin America](ltm-core-document-class.md).
    1. In the **Account number** field, select a bank account.
    1. In the **Document number** field, enter the wire transfer number that's assigned by the bank. If the document class ID is configured as automatic, the number is automatically filled in.
    1. Complete the rest of the LATAM fields configured for the document class.
    1. Post the journal.


