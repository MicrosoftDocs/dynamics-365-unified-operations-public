---
title: Use Latam functionality for checks 
description: This article explains how use Latam functionality for checks
author: Cpicon85 
ms.date: 10/18/2023 
ms.topic: Article
ms.reviewer: kfend
ms.author: v-cpicon 
ms.custom: bap-template
---

# Use Latam functionality for checks 
## In this article
1. [Prerequisites]()
2. [Accrual of own checks]()
3. [Own checks cancelation]()
4. [Deposit received check from customer]()
5. [Re-entry of customer checks]()

This article explains how to use the LATAM functionality for certain check operations, such as the accrual of own checks, depositing third-party checks, cancellations, or re-entries.

## Prerequisites
* Enable the **LATAM** globalization feature with a valid country/region
* Create a document class for each payment method.
* Go to General ledger > Ledger setup > General ledger parameters, in Ledger tab select in **yes** allow multiple transactions within one voucher option.

## Accrual of own checks

Follow these steps to accrual of own checks
1. Go to General ledger > Journal entries > General journals.
2. On the Action pane, Click **New**.
3. In **Name** field, select an accrual journal. 
4. On the Action pane, select **Lines**.
5. On the Journal page, on the Action Pane, select **LATAM**, and then select Payment methods form.
6. On the **select payment media** page:
   - In **Action** field, select **accrual action**.
   - In the Document class Id field, select a document class id for the type of own check.
   - Select one or more checks.
   - Close the page.
> [!NOTE]
>After closing the page, you could confirm the selection in the verification message.
Once the checks have been selected, on the payment method page, as many lines will be automatically created as checks have been selected.


### Check the transaction in the vendor's account

To check the impact of accruals on transactions made with the vendor, you could enter in vendor account, located in Accounts Payable >> Vendors >> All Vendors >> TRANSACTION TAB. 
The check that was previously listed as pending with the vendor is settled with the accrual transaction. This process is automatic.

## Own checks cancelation
In case you need to void own checks, follow these steps, whether they are accrued or not.

1. Go to General ledger > Journal entries > General journals.
2. On the Action pane, Click **New**.
3. In **Name** field, select a general journal.
4. On the Action pane, select **Lines**.
5. On the Journal page, on the Action Pane, select **LATAM**, and then select Payment methods form.6. 
6. On the **select payment media** page:
   - In **Action** field, select **cancelation action**.
   - In the Document class Id field, select a document class id for the type of own check.
   - Select one or more checks:
     1. In **open book** section, for pending accrual of issued checks.
     2. In **history book** section, For accrued checks.
7. Close the page.

> [!NOTE]
>After closing the page, you could confirm the selection in the verification message.
Once the checks have been selected, on the payment method page, as many lines will be automatically created as checks have been selected.

## Deposit received check from customer.
Follow these steps to deposit checks from customers

### Configure Latam extension from bank account 

1. Go to Cash and bank management > Bank accounts > Bank accounts.
2. Select a bank account.
3. On the Latam extension, In the Counterpart Behavior field, select an option.
   > [!NOTE]
   > If you want to record the consolidated deposit of multiple checks, select the **Consolidated** option. For the individual deposit of a single check, select the **Individual** option

### Post a check deposit

1. Go to General ledger > Journal entries > General journals.
2. On the Action pane, Click **New**.
3. In **Name** field, select an bank deposit journal. 
4. On the Action pane, select **Lines**.
5. On the Journal page, on the Action Pane, select **LATAM**, and then select Payment methods form.
6. On the **select payment media** page:
   - In **Action** field, select **exit action**.
   - In the Document class Id field, select a document class id of customer check.
     - Select one or more checks.
     - Close the page.

> [!NOTE]
>After closing the page, you could confirm the selection in the verification message.
Once the checks have been selected, on the payment method page, as many lines will be automatically created as checks have been selected.

## Re-entry of customer checks
In case you need to re-entry customer checks, follow these steps, whether they are deposit or not.

1. Go to General ledger > Journal entries > General journals.
2. On the Action pane, Click **New**.
3. In **Name** field, select a general journal.
4. On the Action pane, select **Lines**.
5. On the Journal page, on the Action Pane, select **LATAM**, and then select Payment methods form.
6. On the **select payment media** page:
   - In **Action** field, select **re-entry action**.
   - In the Document class Id field, select a document class id of customer check.
   - Select one or more checks:
     1. In **open book** section, for customer checks not yet deposited.
     2. In **history book** section, for checks deposited or handed over to vendors.
7. Close the page.

> [!NOTE]
>After closing the page, you could confirm the selection in the verification message.
Once the checks have been selected, on the payment method page, as many lines will be automatically created as checks have been selected.

## Additional resources

* [Use latam extension in customer payments](ltm-latam-in-customer-payment.md)
* [Use latam extension in vendor payments](ltm-latam-in-vendor-payment.md)
