---
title: Use latam extension in customer payments journals
description: This article explains how use payment method in customer payments
author: Cpicon85 
ms.date: 10/18/2023 
ms.topic: Article
ms.reviewer: kfend
ms.author: v-cpicon 
ms.custom: bap-template
---

# Use latam extension in customer payments journals.
## In this article
1. [Prerequisites]()
2. [Complete Latam information in customer line]()
3. [Complete payment method form]()

This article explains how to use the customer collection process with the LATAM extension and the Payment Methods button in the customer payment journal. The fields added by the LATAM Localization allow you to fill in additional data to represent the payment methods according to the legislation of each country.

## Prerequisites
-	Enable the **LATAM** globalization feature with a valid country/region
-	Create a document class for each payment method.

## Complete Latam information in customer line

1. Go to Accounts receivable > Payments > Customer payment journal.
2. On the Action pane, Click **New**.
3. In **Name** field, select a customer payment journal.
4. On the Action pane, select **Lines**.
5. In the **Account** field, select a customer account.
6. On the **LATAM** tab, in the Document class Id field, select **REC** as receipt documen.
7. Go to Settle transactions and select the invoice(s) you wish to collect from the customer

## Complete payment method form

The payment method form allows you to select one or multiple payment methods for the same transaction. After completing the **LATAM** tab on the customer line, for each payment method to be used, follow the detailed steps in each of the following sections.

### Use Bank transfer
Follow these steps to select bank transfer payment.

1. On the Action Pane, select **LATAM**, and then select Payment methods form.
2. On the **payment method** page, select New.
3. In **document class id.** select a document class id **TRB** as Document class Id for bank transfer. (See [Document classes for Latin America](../ltm-core-document-class.md) article).
4. In the **Account number** field select a bank account.
5. In the **Document number** field type a value.
6. Close the page, and check the information in customer payment journal before post.

### Use customer checks
Follow these steps to record customer checks. You can use them for both, current date checks and post-dated checks. The entry of these values is similar for both and has the same impact on the customer account. The only difference is the entry of additional data.

1. On the Action Pane, select **LATAM**, and then select Payment methods form.
2. On the **payment method** page, select New.
3. In **document class id.** field, select a document class id that represents customer checks. (See [Document classes for Latin America](../ltm-core-document-class.md) article).
4. In **Action** field, default action will be **entry** and cannot be modified.
5. In **Document Number** field, enter manually the customer's check number.
6. In **Document Date** field, enter the date of the day the check was issued.
7. In **Amount in Transaction Currency** field, enter manually the check amount.
8. In **Exchange Rate** field, you can enter exchange rate value. By default, if the currency is not the base currency, the nearest exchange rate will be assigned.
9. In **Due Date** field, enter the post-date check expiration date.
10. In **Bank group** field, select the bank group of the received check.
11. In **check source** field, select an option.
    > [!NOTE]
    > The Own option is used when the check with which the customer is making the payment belongs to them and not to third parties. If it is an endorsed check, you should select 'Third Party.
12. Close the page, and check the information in customer payment journal before post.
