---
title: Document classes for Latin America
description: This article provides information about the document class configuration for Latin America.
author: Fhernandez0088
ms.date: 04/03/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Document classes for Latin America

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

You can create the different documents that a company uses to register transactions with third parties. Documents can include invoices, credit notes, and debit notes. These documents can also represent payment methods such as checks and wire transfers, and treasury documents such as receipts and payment orders.

## Prerequisites

The following prerequisites must be met before you set up document classes:

- The prefix lengths must be set in the LATAM parameters.
- A sales point must be created.
- At least one bank must be created and configured for use in a document class.
- Journals must be created for assignment in document classes.
- Document class letters must previously be created.
- Document class types must previously be created.

## Set up a document class

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
2. On the Action Pane, select **New**.
3. In the **General** section, specify the following information.

    | Field                         | Description |
    |-------------------------------|-------------|
    | Document class Id             | Enter a unique code to identify the document class. |
    | Description                   | Enter a brief description of the document class. |
    | Legal Description             | Enter the text to print on legal documents for the document class. |
    | Document class type Id.       | Select a document class type. |
    | Document class letter Id      | Select a document class letter. |
    | Prefix                        | Enter a prefix to use in the complete document number. |
    | Inactive                      | Activate this option to make the document class invisible when transactions are posted. |
    | Apply withholding calculation | Activate this option to enable the withholding calculation on the document class. |
    | Original exchange rate        | Activate this option to prevent currency exchange rate differences from being generated in payments. |
    | Document number separator     | Enter the character to use as a separator between the document prefix, sales point prefix and the document number. For example, FCA-0001-12345678. |
    | Copy document number in       | Select an option to copy the document number that's generated to the native **Invoice** and **Document number** fields. |
    | Require AC number             | Activate this option to make the Authorization code (AC) number mandatory when a transaction is posted. |
    | Concept labels 1, 2, 3        | Complete any required labels for the fields that are shown in the **LATAM** information section when a transaction is posted. |
    | Require control code          | Activate the control code if it's required. |
    | Type of control code          | Select between automatic and manual control codes. |
    | Report/Service Id.            | Select an option if it's required for document printing. |
    | Bank transaction type         | Select the transaction type to use if a payment method that's created has an impact on bank accounts. |
    | Notes 1, 2, 3                 | Enter text to include in the document printing, if any text is required. |
    | Details Taxpayer              | Activate this option to make the tax-related information mandatory when a transaction is posted. |
    | Document with tax             | When this option is activated, no more than one line of the vendor/client type that this document class is assigned to can be created in a journal. In this case, there can't be two or more lines that have foreign currency and different exchange rates. |

4. If the document class type represents a payment method, update the following information in the **Payment method type** section. If the document class type doesn't represent a payment method, skip ahead to step 6.

    | Field                    | Description |
    |--------------------------|-------------|
    | Payment method type      | Select an option that represents the document that's created. |
    | Entry action             | Enable this option to allow the **Entry** action in the payment journal (for example , receipt of a third-party check). |
    | Exit action              | Enable this option to allow the **Exit** action in the payment journal (for example, deposit of a third-party check). |
    | Re-entry action          | Enable this option to allow the **Re-entry** action in the payment journal (for example, rejection of a third-party check). |
    | Emission action          | Enable this option to allow the **Emission** action in the payment journal (for example, emission of the company's own check). |
    | Accrual action           | Enable this option to allow the **Accrual** action in the payment journal (for example, deferred check accrual). |
    | Cancellation action      | Enable this option to allow the **Cancellation** action in the payment journal. |
    | Posting profile          | Select the posting profile to use when a transaction that has the document class is posted. |
    | Enable currency exchange | Enable the default currency to be changed when a transaction is posted. |
    | Currency                 | Select the default currency for the payment method. |
    | Require deferred date    | Require the due date to be later than the emission date. |

5. When you configure a payment method, add at least one bank to the **Bank accounts** grid.
6. Add at least one journal name to the **Journal names** grid, so that it can be used when a transaction that has the document class is posted.
7. In the **Additional data** section, specify which fields must be shown in the **LATAM** information section when a transaction is posted.
8. In the **Document mask** section, enable the sales points that are required, and configure the format mask for them.
9. In the **Dimensions** section, select the predetermined dimensions that should be applied to the voucher lines when a transaction is posted.

## Add the fiscal codification provided by the fiscal authorities

You can use the **Tax application** option to add this codification.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
2. On the Action Pane, select **Tax application**.
3. Select **New** to add a line to the grid.
4. In the **Tax application Id.** field, select a value.
5. In the **Tax application code field**, enter the code that the fiscal authority uses to identify the document class type.
6. Select **Save**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
