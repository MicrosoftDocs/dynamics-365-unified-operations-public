---
# required metadata

title: Waive, reinstate, or reverse interest fees
description: This article explains how to waive, reinstate, and reverse charges for interest and fees.
author: ShivamPandey-msft
ms.date: 03/28/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustInterestJourList 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 25ec29f3-e3ea-4abb-bf6b-f6240873b315
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Waive, reinstate, or reverse interest fees

[!include [banner](../includes/banner.md)]

This article explains how to waive, reinstate, and reverse charges for interest and fees.

You can use the buttons on the **Collect** tab of the **All customers** list page to waive, reverse, or reinstate charges:

-   Waived charges are forgiven. You might waive a charge if, for example, a customer disputes the charge, and you want to maintain a good business relationship with that customer.
-   Reinstated charges become due again. You can reinstate charges that were previously waived. You might have to reinstate charges if you determine that they should not have been waived.
-   Reversed charges are removed from a customer’s account and are no longer due. You might reverse charges if, for example, the wrong interest rate was selected to calculate the amount that a customer owes. You can use a separate process to recalculate interest and create an interest note that contains new charges for the customer.

All these actions change an interest note. An interest note is a business document that informs customers when interest or fees have been charged to their account. When you waive or reverse interest or fees, a credit note or adjustment invoice is automatically created to settle the charges. If you reinstate waived charges, an invoice that has a debit amount is automatically created to reinstate the charges that the customer owes. The following table describes the results of each action.

| Action           | Result for the customer                     | Process                       |
|------------------|--------------------------------------------|--------------------------|
| Waive whole interest notes together with all the interest and fees that they include. –or– Select and waive fees or interest transactions that are part of interest notes.   | The charges are forgiven.   | A credit note, or adjustment invoice, is created for the customer. The credit is not used to automatically settle the interest note, or the interest transactions or fees that you selected. The settled amount equals the total amount of the charges, minus any previous payments that the customer made, and minus any amounts that were previously waived or written off. If the amount of the credit note exceeds the amount that the customer owes, you can convert the credit note to a vendor invoice. You can then give the customer a refund.                                                       |
| Reinstate whole interest notes together with all the interest and fees that they include. –or– Select and reinstate fees or interest transactions that are part of interest notes.   | The waived amount is due again.  | An invoice that has a debit amount is created, and the amount is automatically settled against the charges that were previously waived. The actual interest notes aren't reinstated. Instead, an invoice is created that shows the amount that is due from the customer. The credit notes, or adjustment invoices, that were created to settle waived interest notes can still exist if they weren't used to settle the interest notes. In this case, the outstanding credit notes are canceled. Outstanding credit notes are usually automatically settled when interest notes are waived. However, an outstanding credit note might exist if a customer paid an interest note, even though the customer disputed the charges. |
| Reverse whole interest notes. –or– Reverse selected interest transactions that are part of interest notes. **Note:** You can't reverse a fee. However, you can reverse a whole interest note that includes a fee. | The charges are no longer due from the customer. However, the charges become due again if you recalculate interest. | The process is the same as the process for waiving interest notes or selected interest transactions. A credit note, or adjustment invoice, is created for the customer. This credit note is used to automatically settle the interest note. You can use a separate process to recalculate interest and create a new interest note.             |

> [!NOTE] 
> You can also use a separate process to write off bad debts. This process marks all customer transactions for settlement instead of waiving only the charges that are part of interest notes.

## Adjust interest for invoices
In addition to adjusting interest notes, you can remove the interest charges on invoices by using one of the following processes. Both processes make adjustments to the related interest notes.

### Correct an invoice that has associated interest

You can correct a posted invoice that is included in an interest note. This process copies the details from the existing invoice to a new invoice to make only the corrections that you want. The invoice is canceled, and a new invoice is created. Interest on the transaction is also reversed on the interest note, if the interest note was posted. 

You can make the correction by clicking **Correct invoice** on the Action Pane of the free text invoice. This button is available only if the **Free text invoice correction** configuration key is selected.

### Reverse a customer transaction that has associated interest

You can reverse a customer transaction on an invoice if an invoice was created incorrectly. If the reversed customer transaction has interest that is included on an interest note, and if the interest note was posted, interest on the transaction is also reversed on the interest note. The interest note is canceled if it hasn't been posted. 

You can reverse customer transactions by using **Reverse** on the **Customer transactions** page.

## Waive or reinstate interest notes
You can waive or reinstate all the charges on interest notes that you select. When you waive charges, the total amount to waive can't exceed any amount limits that have been set. You can reinstate an interest note only if it was previously waived. 

You can waive or reinstate interest notes by using the **Interest note** button on the **Collect** tab of the **Customer** page.

## Waive or reinstate interest transactions
You can waive or reinstate specific interest transactions on an interest note, instead of adjusting all the charges on that interest note. When you waive charges, the total amount to waive can't exceed any amount limits that have been set. You can reinstate an interest transaction only if it was previously waived. 

You can waive or reinstate interest notes by using **Transaction interest** on the **Collect** tab of the **Customer** page.

## Waive or reinstate fees
You can waive or reinstate specific fees on an interest note, instead of adjusting all the charges on that interest note. When you waive charges, the total amount to waive can't exceed any amount limits that have been set. You can reinstate a fee only if it was previously waived. 

You can waive or reinstate interest notes by using **Fee** on the **Collect** tab of the **Customer** page.

## Reverse interest notes
You can reverse all the charges on interest notes that you select. Reversed charges are removed from a customer’s account and are no longer due. After the interest note is reversed, you can recalculate interest and create a new interest note. 

You can reverse interest notes by using **Interest note** on the **Collect** tab of the **Customer** page.

## Reverse interest transactions
You can reverse all the interest transactions that you select. Reversed charges are removed from a customer’s account and are no longer due. After the transactions are reversed, you can recalculate interest and create a new interest note.

You can reverse interest transactions by using the **Transaction interest** button on the **Collect** tab of the **Customer** page.

## View the history of adjustments for charges that were waived, reinstated, or reversed
You can view the detailed history of adjustments that were made for interest notes, such as the user who entered the adjustment, the type of adjustment, the amount, and when the adjustment was entered. For example, you might want to view the previous adjustments that were entered for an interest note before you create a new interest note. 

You can reverse interest transactions by using **History** on the **Collect** tab of the **Customer** page.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
