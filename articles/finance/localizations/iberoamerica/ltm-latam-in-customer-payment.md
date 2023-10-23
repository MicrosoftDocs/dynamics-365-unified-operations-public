---
title: Use latam extension in customer payments journals
description: This article explains how use payment methods in customer payments.
author: Cpicon85 
ms.date: 10/23/2023 
ms.topic: Article
ms.reviewer: kfend
ms.author: v-cpicon 
ms.custom: bap-template
---

# Use latam extension in customer payments journals.

This article explains how to use the customer collection process with the LATAM extension and Payment Methods n the customer payment journal. The fields added by the LATAM Localization allow you to provide additional data to represent the payment methods according to the legislation of each country.

## Prerequisites
Before you complete the tasks in this article, the following prerequisites must be met:

- Enable the **LATAM** globalization feature with a valid country/region.
- Create a document class for each payment method.

## Add LATAM information in the customer payment journal line

1. Go to **Accounts receivable** > **Payments** > **Customer payment journal**.
2. On the Action Pane, select **New**.
3. In **Name** field, select a customer payment journal.
4. On the Action Pane, select **Lines**.
5. In the **Account** field, select a customer account.
6. On the **LATAM** tab, in the **Document class Id** field, select the receipt document, **REC**.
7. Select **Settle transactions** and then select the invoices to collect from the customer.

## Add information to the Payment method page

Use the **Payment method** page to select one or more payment methods for the same transaction. In the customer payment journal, after you select the invoices to be collected and complete the information on the **LATAM** tab, for each payment method you need to use, follow the steps in the sections below.

### Use Bank transfer
Follow these steps to select a bank transfer payment.

1. Go to **Accounts receivable** > **Payments** > **Customer payment journal**, and on Action Pane, select **LATAM** > **Payment methods**.
2. On the **Payment method** page, select **New**.
3. In the **Document class id.** field, select **TRB** as the Document class Id for a bank transfer. To learn more, see [Document classes for Latin America](ltm-core-document-class.md).
4. In the **Account number** field, select a bank account.
5. In the **Document number** field, enter a value.
6. Close the page, and check the information in the **Customer payment journal** before posting.

### Use customer checks
Follow these steps to record customer checks. You can use them for current date checks and post-dated checks. Entering these values is similar for both and has the same impact on the customer account. The only difference is the entry of more data.

1. Go to **Accounts receivable** > **Payments** > **Customer payment journal** and on the Action Pane, select **LATAM** > **Payment methods**.
2. On the **Payment method** page, select **New**.
3. In the **Document class id.** field, select a document class ID that represents customer checks. To learn more, see [Document classes for Latin America](ltm-core-document-class.md).
4. In the **Document Number** field, enter the customer's check number.
5. In the **Document Date** field, enter the date the check was issued.
6. In the **Amount in Transaction Currency** field, enter the check amount.
7. In the **Exchange Rate** field, enter the exchange rate value. By default, if the currency isn't the base currency, the nearest exchange rate is assigned.
8. In the **Due Date** field, enter the post-date check expiration date.
9. In the **Bank group** field, select the bank group of the received check.
10. In the **Check source** field, select an option.
    > [!NOTE]
    > The **Own** option is used when the check the customer is using for the payment belongs to them and not to a third party. If it's an endorsed check, select **Third Party**.
11. Close the page, and check the information in the **Customer payment journal** before posting.
