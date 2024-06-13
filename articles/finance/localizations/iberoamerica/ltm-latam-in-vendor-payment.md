---
title: Use the LATAM extension in vendor payments journals
description: Learn how to use payment methods in vendor payments, including prerequisites and a process for adding LATAM information to vendor payment journal lines.
author: Cpicon85
ms.author: v-cpicon
ms.topic: article 
ms.date: 10/18/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Use the LATAM extension in vendor payments journals

[!include [banner](../../includes/banner.md)]

This article explains how to use the vendor payment process with the Latin American (LATAM) extension and the payment methods functionality in the vendor payment journal. The LATAM localization adds fields that let you provide additional data to represent payment methods according to the legislation of each country or region.

## Prerequisites

Before you complete the procedures in this article, the following prerequisites must be met:

- Enable the **LATAM** globalization feature with a valid country/region.
- Create a document class for each payment method.

## Add LATAM information to vendor payment journal lines

1. Go to **Accounts payable** \> **Payments** \> **Vendor payment journal**.
2. On the Action Pane, select **New**.
3. In the **Name** field, select a vendor payment journal.
4. On the Action Pane, select **Lines**.
5. In the **Account** field, select a vendor account.
6. On the **LATAM** tab, in the **Document class Id** field, select **OP** as the document class ID for a payment order document.
7. Select **Settle transactions**, and then select the invoices that you want to pay to the vendor.

## Add information to the Payment method page

Use the **Payment method** page to select one or more payment methods for the same transaction. After you complete the **LATAM** tab on the vendor line, complete the following procedures for each payment method that you must use.

### Use a bank transfer

Follow these steps to select a bank transfer payment.

1. Go to **Accounts payable** \> **Payments** \> **Vendor payment journal**.
2. On the Action Pane, select **LATAM** \> **Payment methods**.
3. On the **Payment method** page, select **New**.
4. In the **Document class id.** field, select **TRB** as the document class ID for a bank transfer. For more information, see [Document classes for Latin America](ltm-core-document-class.md).
5. In the **Account number** field, select a bank account.
6. In the **Document number** field, enter the bank transfer number that's assigned by the bank. If the document class ID is configured as automatic, the number is automatically filled in.
7. Close the page, and review the information in the vendor payment journal before you post.

### Use your own checks

Follow these steps to record your own checks. You can use the same steps for both current-date checks and deferred (post-dated) checks, because the entry of values is similar for both types and has the same impact on the vendor account. Only the entry of additional data differs.

1. Go to **Accounts payable** \> **Payments** \> **Vendor payment journal**.
2. On the Action Pane, select **LATAM** \> **Payment methods**.
3. On the **Payment method** page, select **New**.
4. In the **Document class id.** field, select a document class ID that represents your company checks. For more information, see [Document classes for Latin America](ltm-core-document-class.md).
5. In the **Document Number** field, enter the check number. If numbering is configured as automatic, the check number is automatically assigned.
6. In the **Document Date** field, enter the date when the check was issued.
7. In the **Amount in Transaction Currency** field, enter the check amount.
8. In the **Exchange Rate** field, enter the exchange rate value. By default, if the currency isn't the base currency, the nearest exchange rate is assigned.
9. In the **Due Date** field, enter the expiration date of the post-dated check.
10. Close the page, and review the information in the vendor payment journal before you post.

### Use checks that are received from customers

1. Go to **Accounts payable** \> **Payments** \> **Vendor payment journal**.
2. On the Action Pane, select **LATAM** \> **Payment methods**.
3. On the **Payment method** page, select **Select payment media**.
4. On the **Select payment media** page, in the **Action** field, select **Exit action**.
5. In the **Document class Id** field, select a document class ID that represents the type of customer check.
6. Select one or more checks, and then close the page.

> [!NOTE]
> After you close the page, confirm the selection in the verification message.

After the checks are selected, lines are automatically created on the **Payment method** page. The number of lines matches the number of selected checks.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
