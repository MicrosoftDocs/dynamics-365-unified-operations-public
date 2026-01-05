---
title: Document class types for Latin America 
description: Learn about the document class type configuration for Latin America, including prerequisites and an outline on setting up document class types. 
author: Fhernandez0088
ms.author: v-federicohe 
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Document class type for Latin America

[!include [banner](../../includes/banner.md)]

[!include [banner](../includes/does-not-apply-to.md)]

You can configure the different types of document classes that your company uses.

## Prerequisites

Before you can configure a document class type, make sure the following prerequisites are met:

- The legal entity must have an address in a country/region within the LATAM localization.
- Both the region-specific LATAM feature and the general feature are enabled.
- The prefix length configuration is already set on the **LATAM Parameters** menu.

## Set up a document class type for Latin America

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class type**.
1. On the Action Pane, select **New**.
1. In the **General** section, enter a code that represents the record in the **Document class type Id.** field.
1. Enter a brief description of the document class type in the **Description** field.
1. Enter a prefix to use as part of the complete document number in the **Prefix** field.
1. Select the **Unique document per voucher** toggle to ensure that the document class linked with this document class type can only be selected once within the same journal entry.
1. Select the **Unique account per voucher** toggle to ensure that only one account type can be posted in a voucher that uses this document class type.
1. Configure the following options in the **Payment methods** section.

    | Option                          | Description |
    |---------------------------------|-------------|
    | Payment media                  | Set this option to **Yes** to use the document as a payment document. You can only select this option if you don't enable any other toggles. |
    | Unique per voucher              | Set this option to **Yes** to specify that only one payment document is allowed per voucher posting. |
    | Replicates header information   | Set this option to **Yes** to copy the information of the document class to the rest of the voucher lines in the transaction. |

1. Configure the following options in the **Invoices** section.

    | Option                          | Description |
    |---------------------------------|-------------|
    | Sales invoice                   | Set this option to **Yes** to use the document as a sales invoice in a sales order. |
    | Free Text Invoice               | Set this option to **Yes** to use the document in a free text invoice transaction. |
    | Purchase invoice                | Set this option to **Yes** to use the document as a purchase invoice in a purchase order. |
    | Project invoice                 | Set this option to **Yes** to use the document as a project invoice. |

1. Configure the following options in the **Credit notes** section.

    | Option                          | Description |
    |---------------------------------|-------------|
    | Sales credit note               | Set this option to **Yes** to use the document as a credit note in sales orders |
    | Free text credit note           | Set this option to **Yes** to use the document as a credit note in a free text invoice transaction. |
    | Purchase credit note            | Set this option to **Yes** to use the document as a credit note in purchase orders. |
    | Project credit note             | Set this option to **Yes** to use the document as a project credit note. |

1. Configure the following options in the **Packing Slip** section.

    | Option                          | Description |
    |---------------------------------|-------------|
    | Packing slip                    | Set this option to **Yes** to use the document as a packing slip in sales and purchase orders. |
    | Return packing slip             | Set this option to **Yes** to use the document as a return packing slip for credit notes in sales and purchase orders. |
    | Inventory transfer packing slip | Set this option to **Yes** to use the document as a packing slip in inventory transfer transactions. |
    | Project packing slip            | Set this option to **Yes** to use the document as a packing slip in a project. |
    | Project return delivery note    | Set this option to **Yes** to use the document as a return packing slip for project credit notes. |

1. In the **Journals** section, define how the document can be used on journal lines for each account type.

    | Option       | Description |
    |--------------|-------------|
    | Debit       | Activate this option to indicate that the document can be applied to journal lines with debit amounts for the selected account type. |
    | Credit       | Activate this option to indicate that the document can be applied to journal lines with credit amounts for the selected account type. |
    | Admits reverse       | Activate this option to indicate that the document can be used when reversing transactions for the selected account type. |
    | Ledger       | Activate this option to use the document on ledger type voucher lines. |
    | Vendor       | Activate this option to use the document on vendor type voucher lines. |
    | Project      | Activate this option to use the document on project type voucher lines. |
    | Customer     | Activate this option to use the document on customer type voucher lines. |
    | Fixed assets | Activate this option to use the document on fixed assets type voucher lines. |
    | Bank         | Activate this option to use the document on bank type voucher lines. |

## Add the fiscal codification provided by the fiscal authorities

Use the **Tax application** option to add this codification.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class type**.
1. On the Action Pane, select **Tax application**.
1. Select **New** to add a line to the grid.
1. In the **Tax application ID.** field, select a value.
1. In the **Tax application code** field, enter the code that the fiscal authority uses to identify the document class type.
1. Select **Save**.

Learn more in [Tax application for Latin America](ltm-core-tax-application.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
