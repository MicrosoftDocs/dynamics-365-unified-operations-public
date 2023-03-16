---
title: Document class for Latin America 
description: This article provides information about the document class configuration for Latin America. 
author: Fhernandez0088
ms.date: 03/15/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Document classes for Latin America

You can create the different documents that the company uses to register transactions with third parties. Documents can include invoices, credit notes, and debit notes. These documents can also represent payment methods like checks and wire transfers, and treasury documents like receipts and payment orders.

## Prerequisites

The following prerequisites must be met before you set up document classes:

- The prefix lengths must be set in the **LATAM Parameters*
- A sales point must be created
- At least one bank must be created and configured to use in a document class
- Journals must be created for assignment in document classes
- **Document class letters** must be previously created
- **Document class types** must be previously created

## Set up a Document class
1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class**
2. On the Action Pane, select **New**.
3. In the **General** section, enter or select the following information:

    | Field                         | Description                                          |
    |-------------------------------|------------------------------------------------------|
    | Document class Id             | Enter a unique code to identify the document class.  |
    | Description                   | Enter a brief description of the document class.     |
    | Legal Description             | Enter the text to be printed in a legal document for the document class.              |
    | Document class type Id.       | Select a document class type from the list.          |
    | Document class letter Id      | Select a document class letter from the list.        |
    | Prefix                        | Enter a prefix to be used in the complete document number.                            |
    | Inactive                      | Activate this slider to make the document class invisible when posting transactions.  |
    | Apply withholding calculation | Activate this slider to enable the withholding calculation on the document class.     |
    | Original exchange rate        | Activate this slider to prevent generating currency exchange rate differences in payments.  |
    | Document number separator     | Enter the character to use as the document number separator prefixes-salespoint.            |
    | Copy document number in       | Select an option form this field to copy the document number generated to the native fields **Invoice** and **Document number**.     |
    | Require AC number             | Activate this slider to make the AC number mandatory when posting a transaction.            |
    | Concept labels 1, 2, 3        | Complete any necessary labels for the fields in LATAM information when posting a transaction.  |
    | Require control code          | Activate the control code if necessary.              |
    | Type of control code          | Select between automatic and manual.                 |
    | Report/Service Id.            | Select an option if necessary for docucment printing.|
    | Bank transaction type         | Choose a transaction type when creating a payment method that has an impact on bank accounts.  |
    | Notes 1, 2, 3                 | Enter text to include in the document printing if necessary.  |
    | Details Taxpayer              | Enable this option to make the tax related information mandatory when posting a transaction.   |
    | Document with tax             | When enabled, no more than one line of the vendor/client type with this document class assigned can be created in a journal. When enabled, there can't be two or more lines with foreign currency and different exchange rates. |
4. If the **Document class type** is not a payment method, proceed to **step 6**. If the **Document class type** is a payment method, update the following field information in the **Payment method type** section:

    | Field                    | Description                                                                                           |
    |--------------------------|-------------------------------------------------------------------------------------------------------|
    | Payment method type      | Select an option from the list that represents the document created.                                  |
    | Entry action             | Enable this to allow the **Entry** action in the payment journal. For example, reciept of a third-party check.   |
    | Exit action              | Enable this to allow the **Exit** action in the payment journal. For example, a third-party check deposit.       |
    | Re-entry action          | Enable this to allow the **Re-entry** action in the payment journal. For example, a third-party check rejected. |
    | Emission action          | Enable this to allow the **Emission** action in the payment journal. For example, the company's own check emission.  |
    | Accrual action           | Enable this to allow the **Accrual** action in the payment journal. For example, deferred checks accrual.     |
    | Cancellation action      | Enable this to allow the **Cancellation** action in the payment journal.      |
    | Posting profile          | Select the posting profile to use when posting a transaction with the document class.             |
    | Enable currency exchange | Enable changing the default currency when posting a transaction.                                         |
    | Currency                 | Select the default currency for the payment method.                                                   |
    | Require deferred date    | Require the due date to be higher than the emission date.                                            |

5. When you configure a payment method, add at least one bank to the **Bank accounts** grid for use.
6. Add at least one journal name to the grid **Journal names** to be used when posting a transaction with the document class.
7. In the **Additional data** section, determine which fields must be shown in the **LATAM** information section when posting a transaction.
8. In the **Document mask** section, enable the sales points required and configure the format mask for them.
9. In the **Dimensions** section, select the predetermined dimensions that will be applied to the voucher lines when posting a transaction.

## Add the fiscal codification provided by the fiscal authorities

You can use **Tax application** option to add this codification.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class**.
2. On the Action Pane, select **Tax application**.
3. Select **New** to add a line to the grid.
4. In the **Tax application Id.** field, select a value from the list.
5. In the **Tax application code field**, enter the code that the fiscal authority uses to identify the document class type.
6. Select **Save**.

