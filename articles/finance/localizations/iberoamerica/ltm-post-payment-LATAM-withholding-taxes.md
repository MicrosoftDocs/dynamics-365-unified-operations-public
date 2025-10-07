---
title: Post vendor payment transactions with LATAM Withholding taxes
description: Learn how to post vendor payment journals with LATAM Withholding taxes.
author: Fhernandez0088
ms.date: 10/07/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Post vendor payment transactions with LATAM withholding taxes

[!INCLUDE[banner](../../includes/banner.md)]

This process consists of two parts: first the vendor invoice posting, and then the vendor payment journal posting.

## How to post a vendor invoice with a withholding tax group

1. Go to **Accounts payable > Invoices > Invoice journal**.
1. Select **New**.
1. In the **Name** field, enter or select a value (choose a vendor invoice journal).
1. Select **Lines**.
1. Add a new line.
1. In the **Account** field, specify the desired values (choose a vendor).
1. In the **Credit** field, enter a value.
1. Select the **LATAM** tab.
1. Select a document class (invoice).
1. Enter a value in the prefix field.
1. Enter a value in the document number field.
1. Verify that the **Withholding tax group** field shows the group assigned in the vendor configuration. If it doesn't, select one from the list.
1. Go to lines, in the **Account type** field, select ledger, and choose a ledger account to register the expense as offset account or in a new line.
1. In the debit field, enter a value.
1. Select a sales tax group and item tax group according to the expense.

> [!NOTE]
> You can post the vendor invoice from any journal configured for that purpose and from purchase orders. Just be sure that in the LATAM section the **Withholding tax group** field contains a value.

## How to register a vendor payment journal with withholding tax

1. Go to **Accounts payable > Payments > Vendor payment journal**.
1. Select **New**.
1. In the list, select the row.
1. In the **Name** field, enter or select a value (choose a vendor payment journal).
1. Select **Lines**.
1. In the list, select the row.
1. In the **Account field**, specify the desired values (choose a vendor).
1. Select or verify that the vendor line has a payment order as document class in the LATAM section before settling a transaction (the document class can be predefined in the LATAM section from the vendor payment journal name configuration).
1. Go to settle transaction and choose the invoice to pay.
1. In the settlement form, check that in the **LATAM** tab the vendor withholding group is selected (select one if it's empty, and it can also be changed for another one).
1. Return to journal lines and go to the **LATAM** tab.
1. Complete or verify the document number.
1. After you settle a transaction, a bank type line with the calculated withholding tax appears.
1. Then you can select the payment method for the remaining invoice amount and post the journal. Here's an example:
    1. On the Action Pane, select **LATAM > Payment methods**.
    1. On the **Payment method** page, select **New**.
    1. In the **Document class ID.** field, select a document class for a wire transfer. For more information, see [Document classes for Latin America](ltm-core-document-class.md).
    1. In the **Account number** field, select a bank account.
    1. In the **Document number** field, enter the wire transfer number that's assigned by the bank. If the document class ID is configured as automatic, the number is automatically filled in.
    1. Complete the rest of the LATAM fields configured for the document class.
    1. Post the journal.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]