---
title: Use the LATAM extension in customer payments journals
description: Learn how to use payment methods in customer payments, including prerequisites and a process for adding LATAM information to customer payment journal lines.
author: Cpicon85
ms.author: v-cpicon
ms.date: 10/23/2023
ms.topic: article
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Use the LATAM extension in customer payments journals

This article explains how to use the customer collection process with the Latin American (LATAM) extension and the payment methods functionality in the customer payment journal. The LATAM localization adds fields that let you provide additional data to represent payment methods according to the legislation of each country or region.

## Prerequisites

Before you complete the procedures in this article, the following prerequisites must be met:

- Enable the **LATAM** globalization feature with a valid country/region.
- Create a document class for each payment method.

## Add LATAM information to customer payment journal lines

1. Go to **Accounts receivable** \> **Payments** \> **Customer payment journal**.
2. On the Action Pane, select **New**.
3. In the **Name** field, select a customer payment journal.
4. On the Action Pane, select **Lines**.
5. In the **Account** field, select a customer account.
6. On the **LATAM** tab, in the **Document class Id** field, select **REC** as the document class ID for a receipt document.
7. Select **Settle transactions**, and then select the invoices that you want to collect from the customer.

## Add information to the Payment method page

Use the **Payment method** page to select one or more payment methods for the same transaction. In the customer payment journal, after you select the invoices to collect and complete the information on the **LATAM** tab, complete the following procedures for each payment method that you must use.

### Use a bank transfer

Follow these steps to select a bank transfer payment.

1. Go to **Accounts receivable** \> **Payments** \> **Customer payment journal**.
2. On Action Pane, select **LATAM** \> **Payment methods**.
3. On the **Payment method** page, select **New**.
4. In the **Document class id.** field, select **TRB** as the document class ID for a bank transfer. For more information, see [Document classes for Latin America](ltm-core-document-class.md).
5. In the **Account number** field, select a bank account.
6. In the **Document number** field, enter a value.
7. Close the page, and review the information in the customer payment journal before you post.

### Use customer checks

Follow these steps to record customer checks. You can use the same steps for both current-date checks and deferred (post-dated) checks, because the entry of values is similar for both types and has the same impact on the customer account. Only the entry of additional data differs.

1. Go to **Accounts receivable** \> **Payments** \> **Customer payment journal**.
2. On the Action Pane, select **LATAM** \> **Payment methods**.
3. On the **Payment method** page, select **New**.
4. In the **Document class id.** field, select a document class ID that represents customer checks. For more information, see [Document classes for Latin America](ltm-core-document-class.md).
5. In the **Document Number** field, enter the customer's check number.
6. In the **Document Date** field, enter the date when the check was issued.
7. In the **Amount in Transaction Currency** field, enter the check amount.
8. In the **Exchange Rate** field, enter the exchange rate value. By default, if the currency isn't the base currency, the nearest exchange rate is assigned.
9. In the **Due Date** field, enter the expiration date of the post-dated check.
10. In the **Bank group** field, select the bank group of the received check.
11. In the **Check source** field, select a value to specify the source of the check that the customer uses for the payment:

    - If the check belongs to the customer, not to a third party, select **Own**.
    - If the check is an endorsed check, select **Third Party**.

12. Close the page, and review the information in the customer payment journal before you post.
