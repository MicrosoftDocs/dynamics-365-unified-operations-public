---
title: Use LATAM functionality for checks 
description: This article explains how use LATAM functionality for checks.
author: Cpicon85 
ms.date: 10/20/2023 
ms.topic: Article
ms.reviewer: kfend
ms.author: v-cpicon 
ms.custom: bap-template
---

# Use LATAM functionality for checks 

[!include [banner](../../includes/banner.md)]

This article explains how to use the LATAM functionality for certain check operations, such as the accrual of own checks, depositing third-party checks, cancellations, and re-entries.

## Prerequisites
Before you complete the tasks in this article, the following prerequisites must be met.

- Enable the **LATAM** globalization feature with a valid country/region.
- Create a document class for each payment method.
- Go to **General ledger** > **Ledger setup** > **General ledger parameters**, and on the **Ledger** tab, select to allow multiple transactions within one voucher option.

## Accrual of own checks
Follow these steps to accrual of checks provided by your company.

1. Go to **General ledger** > **Journal entries** > **General journals**.
2. On the Action Pane, select **New**.
3. In **Name** field, select an accrual journal. 
4. On the Action Pane, select **Lines**.
5. On the **Journal** page, on the Action Pane, select **LATAM**, and then select **Payment methods**.
6. On the **Payment methods** page, in teh **Action** field, select **Accrual action**.
7. In the **Document class Id** field, select a document class ID for the check type.
8. Select one or more checks and then close the page.

> [!NOTE]
> After you close the page, confirm the selection in the verification message. After you select the checks, as many lines will be automatically created as checks have been selected on the **Payment methods** page.


### Check a transaction in a vendor's account

To check the impact of accruals on transactions made with a vendor, go to **Accounts Payable** > **Vendors** > **All Vendors**. Select and open the vendor record you want to review and select the **Transaction** tab.

If the check was previously listed as pending with the vendor, it's now settled with the accrual transaction. This process is automatic.

## Check cancellation 
If you need to void checks provided by your company, whether they are accrued or not, complete the following steps.

1. Go to **General ledger** > **Journal entries** > **General journals** and on the Action Pane, select **New**.
2. In **Name** field, select a general journal.
3. On the Action Pane, select **Lines**.
4. On the **Journal** page, on the Action Pane, select **LATAM**, and then select **Payment methods**. 
5. On the **Payment methods** page, in the **Action** field, select **Cancelation**.
6. In the **Document class Id** field, select a document class ID for the check type.
7. Select one or more checks in either the **Open book** section, for the pending accrual of issued checks, or in the **History book** section for accrued checks.
8. Close the page.

> [!NOTE]
> After you close the page, confirm the selection in the verification message. After the checks are selected, as many lines will be automatically created as checks have been selected on the **Payment method** page.

## Deposit received check from customer
Follow these steps to deposit checks from customers.

### Configure Latam extension from bank account 

1. Go to **Cash and bank management** > **Bank accounts** > **Bank accounts**.
2. Select a bank account.
3. In the **LATAM** extension, in the **Counterpart Behavior** field, select an option.

   > [!NOTE]
   > To record the consolidated deposit of multiple checks, select **Consolidated**. For the individual deposit of a single check, select **Individual**.

### Post a check deposit

1. Go to **General ledger** > **Journal entries** > **General journals** and on the Action Pane, select **New**.
2. In **Name** field, select an bank deposit journal. 
3. On the Action Pane, select **Lines**.
4. On the **Journal** page, on the Action Pane, select **LATAM**, and then select **Payment methods**.
5. On the **Payment methods** page, in the **Action** field, select **Exit action**.
6. In the **Document class Id** field, select the document class ID of the customer check.
7. Select one or more checks and then close the page.

> [!NOTE]
> After you close the page, confirm the selection in the verification message. After the checks have been selected, as many lines will be automatically created as checks have been selected on the **Payment method** page.

## Re-entrering customer checks
If you need to re-enter customer checks, follow these steps. 

1. Go to **General ledger** > **Journal entries** > **General journals** and on the Action Pane, select **New**.
2. In **Name** field, select a general journal.
3. On the Action Pane, select **Lines**.
4. On the **Journal** page, on the Action Pane, select **LATAM**, and then select **Payment methods**.
5. On the **Payment methods** page, in the **Action** field, select **Re-entry action**.
6. In the **Document class Id** field, select the document class ID of the customer check.
7. Select one or more checks. For customer checks that haven't been deposited, select from the **Open book** section. For checks that have been deposited or given to vendors, select from the **history book** section.
8. Close the page.

> [!NOTE]
> After you close the page, confirm the selection in the verification message. After the checks have been selected,as many lines will be automatically created as checks have been selected on the **Payment methods** page.

## More resources

* [Use latam extension in customer payments](ltm-latam-in-customer-payment.md)
* [Use latam extension in vendor payments](ltm-latam-in-vendor-payment.md)



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
