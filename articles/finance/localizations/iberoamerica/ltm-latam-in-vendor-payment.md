---
title: Use latam extension in vendor payments journals
description: This article explains how use payment method in vendor payments
author: Cpicon85 
ms.date: 10/18/2023 
ms.topic: Article
ms.reviewer: kfend
ms.author: v-cpicon 
ms.custom: bap-template
---

# Use latam extension in vendor payments journals.
## In this article
1. [Prerequisites]()
2. [Complete Latam information in vendor line]()
3. [Complete payment method form]()

This article explains how to use the vendor payment process with the LATAM extension and the Payment Methods button in the vendor payment journal. The fields added by the LATAM Localization allow you to fill in additional data to represent the payment methods according to the legislation of each country.

## Prerequisites
-	Enable the **LATAM** globalization feature with a valid country/region
-	Create a document class for each payment method.

## Complete Latam information in vendor line

1.	Go to accounts payable>>Payments>> Vendor payment journal.
2.	On the Action pane, Click **New**.
3.	In **Name** field, select a vendor payment journal.
4.	On the Action pane, select **Lines**.
5.	In the **Account** field, select a vendor account.
6.	On the **LATAM** tab, in the Document class Id field, select **OP** as payment order document.
7.	Go to Settle transactions and select the invoice(s) you wish to pay to the vendor.

## Complete payment method form

The payment method form allows you to select one or multiple payment methods for the same transaction. After completing the **LATAM** tab on the vendor line, for each payment method to be used, follow the detailed steps in each of the following sections.

### Use Bank transfer
Follow these steps to select bank transfer payment.

1. On the Action Pane, select **LATAM**, and then select Payment methods form.
2. On the **payment method** page, select New.
3. In **document class id.** select a document class id **TRB** as Document class Id for bank transfer. (See [Document classes for Latin America](../ltm-core-document-class.md) article).
4. In the **Account number** field select a bank account.
5. In the **Document number** field enter manually with the bank transfer number assigned by the bank. If the document class id is configured as automatic, the number will be filled in automatically.
6. Close the page, and check the information in vendor payment journal before post.

### Use own checks
Follow the steps to register your own current-date and deferred checks. You can use them for both, because the entry of these values is similar for both and has the same impact on the vendor account. The only difference is the entry of additional data.

1. On the Action Pane, select **LATAM**, and then select Payment methods form.
2. On the **payment method** page, select New.
3. In **document class id.** field, select a document class id that represents own checks. (See [Document classes for Latin America](../ltm-core-document-class.md) article).
4. In **Action** field, default action will be **entry** and cannot be modified.
5. In **Document Number** field, Fill with the check number. If numbering is configured as automatic, the check number will be assigned automatically.
6. In **Document Date** field, enter the date of the day the check was issued.
7. In **Amount in Transaction Currency** field, enter manually the check amount.
8. In **Exchange Rate** field, you can enter exchange rate value. By default, if the currency is not the base currency, the nearest exchange rate will be assigned.
9. In **Due Date** field, enter the post-date check expiration date.
10. Close the page, and check the information in customer payment journal before post.
### Use checks received from customers
1. On the Action Pane, select **LATAM**, and then select Payment methods form.
2. On the **payment method** page, use **Select payment media** button.
3. On the **select payment media** page:
   - In **Action** field, select **exit action**.
   - In the Document class Id field, select a document class id for the type of customer check.
   - Select one or more checks.
   - Close the page.
> [!NOTE]
>After closing the page, you could confirm the selection in the verification message.

Once the checks have been selected, on the payment method page, as many lines will be automatically created as checks have been selected.
