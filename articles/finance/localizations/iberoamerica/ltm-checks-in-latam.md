---
title: Use LATAM functionality for checks 
description: Learn how to use LATAM functionality for checks, including prerequisites and outlines on accruing checks provided by your company and canceling checks.
author: Cpicon85
ms.author: v-cpicon 
ms.topic: article
ms.date: 10/20/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Use LATAM functionality for checks 

[!include [banner](../../includes/banner.md)]

This article explains how to use LATAM functionality for specific check operations, such as the accrual of your company's own checks, deposits of third-party checks, cancellations, and re-entries.

## Prerequisites

Before you complete the procedures in this article, the following prerequisites must be met:

- Enable the **LATAM** globalization feature with a valid country/region.
- Create a document class for each payment method.
- Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**. On the **Ledger** tab, select the option to allow multiple transactions in one voucher.

## Accrue checks that are provided by your company

Follow these steps to accrue checks that are provided by your company.

1. Go to **General ledger** \> **Journal entries** \> **General journals**.
2. On the Action Pane, select **New**.
3. In the **Name** field, select an accrual journal.
4. On the Action Pane, select **Lines**.
5. On the **Journal** page, on the Action Pane, select **LATAM**, and then select **Payment methods**.
6. On the **Payment methods** page, in the **Action** field, select **Accrual action**.
7. In the **Document class Id** field, select a document class ID for the check type.
8. Select one or more checks, and then close the page.

> [!NOTE]
> After you close the page, confirm the selection in the verification message. After you select checks on the **Payment methods** page, lines are automatically created. The number of lines matches the number of selected checks.

### Review a transaction in a vendor's account

To determine the impact of accruals on transactions that occur with a vendor, go to **Accounts payable** \> **Vendors** \> **All vendors**. Select and open the vendor record that you want to review, and select the **Transaction** tab.

If the check was previously listed as pending with the vendor, it's now settled with the accrual transaction. This process is automatic.

## Cancel checks

If you must cancel (void) checks that are provided by your company, regardless of whether they're accrued, follow these steps.

1. Go to **General ledger** \> **Journal entries** \> **General journals**.
2. On the Action Pane, select **New**.
3. In the **Name** field, select a general journal.
4. On the Action Pane, select **Lines**.
5. On the **Journal** page, on the Action Pane, select **LATAM**, and then select **Payment methods**.
6. On the **Payment methods** page, in the **Action** field, select **Cancelation**.
7. In the **Document class Id** field, select a document class ID for the check type.
8. Select one or more checks in either the **Open book** section (for the pending accrual of issued checks) or the **History book** section (for accrued checks).
9. Close the page.

> [!NOTE]
> After you close the page, confirm the selection in the verification message. After you select checks on the **Payment methods** page, lines are automatically created. The number of lines matches the number of selected checks.

## Deposit checks that are received from customers

Follow these steps to deposit checks from customers.

### Configure the LATAM extension from a bank account

1. Go to **Cash and bank management** \> **Bank accounts** \> **Bank accounts**.
2. Select a bank account.
3. In the **LATAM** extension, in the **Counterpart Behavior** field, select an option:

   - To record the consolidated deposit of multiple checks, select **Consolidated**.
   - To record the individual deposit of a single check, select **Individual**.

### Post a check deposit

1. Go to **General ledger** \> **Journal entries** \> **General journals**.
2. On the Action Pane, select **New**.
3. In the **Name** field, select a bank deposit journal.
4. On the Action Pane, select **Lines**.
5. On the **Journal** page, on the Action Pane, select **LATAM**, and then select **Payment methods**.
6. On the **Payment methods** page, in the **Action** field, select **Exit action**.
7. In the **Document class Id** field, select the document class ID of the customer check.
8. Select one or more checks, and then close the page.

> [!NOTE]
> After you close the page, confirm the selection in the verification message. After you select checks on the **Payment methods** page, lines are automatically created. The number of lines matches the number of selected checks.

## Re-enter customer checks

If you must re-enter customer checks, follow these steps.

1. Go to **General ledger** \> **Journal entries** \> **General journals**.
2. On the Action Pane, select **New**.
3. In the **Name** field, select a general journal.
4. On the Action Pane, select **Lines**.
5. On the **Journal** page, on the Action Pane, select **LATAM**, and then select **Payment methods**.
6. On the **Payment methods** page, in the **Action** field, select **Re-entry action**.
7. In the **Document class Id** field, select the document class ID of the customer check.
8. Select one or more checks in either the **Open book** section (for customer checks that haven't been deposited) or the **History book** section (for checks that have been deposited or given to vendors).
9. Close the page.

> [!NOTE]
> After you close the page, confirm the selection in the verification message. After you select checks on the **Payment methods** page, lines are automatically created. The number of lines matches the number of selected checks.

## More resources

- [Use the LATAM extension in customer payments](ltm-latam-in-customer-payment.md)
- [Use the LATAM extension in vendor payments](ltm-latam-in-vendor-payment.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
