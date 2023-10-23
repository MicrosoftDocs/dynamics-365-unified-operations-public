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

[!include [banner](../../includes/banner.md)]

This article explains how to use the vendor payment process with the LATAM extension and the Payment Methods functionality the vendor payment journal. The fields included with the LATAM localization allow you to provide additional data to represent the payment methods according to the legislation of each country.

## Prerequisites
Before you complete the tasks in this article, the following prerequisites must be met:

- Enable the **LATAM** globalization feature with a valid country/region.
- Create a document class for each payment method.

## Add LATAM-specific information to Vendor journal lines

1.	Go to **Accounts payable** > **Payments** > **Vendor payment journal**, and om the Action Pane, select **New**.
2.	In **Name** field, select a vendor payment journal.
3.	On the Action Pane, select **Lines**.
4.	In the **Account** field, select a vendor account.
5.	On the **LATAM** tab, in the **Document class Id** field, select **OP** as the payment order document.
6.	Select **Settle transactions** and the select the invoices you want to pay to the vendor.

## Complete the Payment method page

Use the **Payment method** page to select one or more payment methods for the same transaction. After you complete the **LATAM** tab on the vendor line, for each payment method to be used, follow the detailed steps in each of the following sections.

### Use a bank transfer
Follow these steps to select bank transfer payment.

1. Go to **Accounts payable** > **Payments** > **Vendor payment journal**, and on the Action Pane, select **LATAM** > **Payment methods**.
2. On the **Payment method** page, select **New**.
3. In the **Document class id.** field, select **TRB**. To learn more, see [Document classes for Latin America](tm-core-document-class.md).
4. In the **Account number** field select a bank account.
5. In the **Document number** field enter the bank transfer number assigned by the bank. If the document class id is configured as automatic, the number is filled in automatically.
6. Close the page, and check the information in the **Vendor payment journal** before you post.

### Use own checks
Follow the steps to register your own current-date and deferred checks. You can use them for both because the entry of these values is similar for both and has the same impact on the vendor account. The only difference is the entry of additional data.

1. Go to **Accounts payable** > **Payments** > **Vendor payment journal**, and on the Action Pane, select **LATAM** > **Payment methods**.
2. On the **payment method** page, select **New**.
3. In the **Document class id.** field, select a document class ID that represents your company checks. To learn more, see [Document classes for Latin America](ltm-core-document-class.md).
4. In the **Document Number** field, enter the check number. If numbering is configured as automatic, the check number is assigned automatically.
5. In the **Document Date** field, enter the date the check was issued.
6. In the **Amount in Transaction Currency** field, enter the check amount.
7. In the **Exchange Rate** field, enter the exchange rate value. By default, if the currency isn't the base currency, the nearest exchange rate is assigned.
8. In the **Due Date** field, enter the post-date check expiration date.
9. Close the page, and check the information in the **Vendor payment journal** before you post.

### Use checks received from customers
1. Go to **Accounts payable** > **Payments** > **Vendor payment journal**, and on the Action Pane, select **LATAM** > **Payment methods**.
2. On the **payment method** page, select **Select payment media**.
3. On the **Select payment media** page in the **Action** field, select **Exit action**.
4. In the **Document class Id** field, select a document class ID for the type of customer check.
5. Select one or more checks and then close the page.

> [!NOTE]
> After you close the page, confirm the selection in the verification message.

After the checks are selected, on the **Payment method** page, as many lines will be automatically created as checks have been selected.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
