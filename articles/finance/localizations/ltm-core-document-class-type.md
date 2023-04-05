---
title: Document class types for Latin America 
description: This article provides information about the document class type configuration for Latin America. 
author: Fhernandez0088
ms.date: 04/03/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Document class type for Latin America

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

You can configure the different types of document classes that your company will use. Use this configuration to group the document classes according to the characteristics that they have in common.

## Prerequisites

Before you can configure a document class type, the prefix length configuration must already be set on the **LATAM Parameters** menu.

## Set up a document class type for Latin America

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class type**.
2. On the Action Pane, select **New**.
3. In the **General** section, set the following fields.

    | Field                       | Description |
    |-----------------------------|-------------|
    | Document class type Id.     | Enter a code to identify the register. |
    | Description                 | Enter a description of the document class type. |
    | Prefix                      | Enter a prefix to use in the complete document number. |
    | Unique document per voucher | Activate this option to specify that only one document of this document class type can be posted in a voucher. |
    | Unique account per voucher  | Activate this option to specify that only one account type can be posted in a voucher that uses this document class type. |

4. In the **Payment method**, **Invoices**, **Credit notes**, and **Packing Slip** sections, set the following options.

    | Option                          | Description |
    |---------------------------------|-------------|
    | Payment method                  | Set this option to **Yes** to use the document as a payment document. |
    | Unique per voucher              | Set this option to **Yes** to specify that only one payment document is allowed per voucher posting. |
    | Replicates header information   | Set this option to **Yes** to copy the information of the document class to the rest of the voucher's lines. |
    | Sales invoice                   | Set this option to **Yes** to use the document as a sales invoice in a sales order. |
    | Free text invoice               | Set this option to **Yes** to use the document in a free text invoice transaction. |
    | Purchase invoice                | Set this option to **Yes** to use the document in an invoice journal and a purchase order. |
    | Project invoice                 | Set this option to **Yes** to use the document as a project invoice. |
    | Sales credit note               | Set this option to **Yes** to use the document as a credit note. |
    | Free text credit note           | Set this option to **Yes** to use the document as a credit note in a free text invoice transaction. |
    | Purchase credit note            | Set this option to **Yes** to use the document as a credit note in purchase orders. |
    | Project credit note             | Set this option to **Yes** to use the document as a project credit note. |
    | Packing slip                    | Set this option to **Yes** to use the document as a packing slip in sales and purchase orders. |
    | Return packing slip             | Set this option to **Yes** to use the document as a return packing slip in sales and purchase orders. |
    | Inventory transfer packing slip | Set this option to **Yes** to use the document as a packing slip in inventory transfer transactions. |
    | Project packing slip            | Set this option to **Yes** to use the document as a packing slip in a project. |
    | Project return delivery note    | Set this option to **Yes** to use the document as a return packing slip in a project. |

    > [!NOTE]
    > The options in the different sections are mutually exclusive. Therefore, if you set an option to **Yes** in one section, the same option is automatically set to **No** in the other sections.

5. In the **Journals** section, set the options to use the document on journal lines that use the defined account type.

    | Option       | Description |
    |--------------|-------------|
    | Ledger       | Activate this option to use the document on ledger type voucher lines. |
    | Vendor       | Activate this option to use the document on vendor type voucher lines. |
    | Project      | Activate this option to use the document on project type voucher lines. |
    | Customer     | Activate this option to use the document on customer type voucher lines. |
    | Fixed assets | Activate this option to use the document on fixed assets type voucher lines. |
    | Bank         | Activate this option to use the document on bank type voucher lines. |

## Add the fiscal codification provided by the fiscal authorities

You can use the **Tax application** option to add this codification.

1.	Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class type**.
2.	On the Action Pane, select **Tax application**.
3.	Select **New** to add a line to the grid.
4.	In the **Tax application Id.** field, select a value.
5.	In the **Tax application code** field, enter the code that the fiscal authority uses to identify the document class type.
6.	Select **Save**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
