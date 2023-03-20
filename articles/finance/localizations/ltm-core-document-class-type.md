---
title: Document class types for Latin America 
description: This article provides information about the document class type configuration for Latin America. 
author: Fhernandez0088
ms.date: 03/17/2022
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Document class type for Latin America

[!include [banner](../includes/banner.md)]

You can configure the different types of document classes that your company will use. Use this configuration to group the document classes according to the characteristics that they have in common.

## Prerequisites

To configure a **Document class type**, the prefix length configuration in **LATAM Parameters** menu must already be set.

## Set up a Document class type for Latin America

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class type**.
2. Select **New** from the action pane.
3. In the **General** section, configure the following fields and sliders.

    | Field/Slider                | Description           |
    |-----------------------------|-----------------------|
    | Document class type Id.     | Enter a code to identify the register. |
    | Description                 | Enter a description of the document class type. |
    | Prefix                      | Enter a prefix to udr in the document complete number.   |
    | Unique document per voucher | Activate this slider to limit the amount of this document class type that can be posted in a voucher to one. |
    | Unique account per voucher  | Activate this slider to limit the amount of account types that can be posted in a voucher with this document class type to one. |

4. Set the sliders in the **Payment method**, **Invoices**, **Credit notes** and **Packing Slip** sections.

    | Slider                          | Description                                                                                  |
    |---------------------------------|----------------------------------------------------------------------------------------------|
    | Payment method                  | Set the slider to **Yes** to use as a payment document.                                                     |
    | Unique per voucher              | Set the slider to **Yes** to limit the amount of payment documents allowed per voucher post to one.         |
    | Replicates header information   | Set the slider to **Yes** to copy the information of the document class to the rest of the voucher's lines. |
    | Sales invoice                   | Set the slider to **Yes** to use the document as a sales invoice in a sales order.                          |
    | Free text invoice               | Set the slider to **Yes** to use the document in a free text invoice transaction.                           |
    | Purchase invoice                | Set the slider to **Yes** to use the document in an invoice journal and a purchase order.                   |
    | Project invoice                 | Set the slider to **Yes** to use the document as a project invoice.                                         |
    | Sales credit note               | Set the slider to **Yes** to use the document as a credit note.                                             |
    | Free text credit note           | Set the slider to **Yes** to use the document as a credit note in a free text invoice transaction.          |
    | Purchase credit note            | Set the slider to **Yes** to use the document as a credit note in purchase orders.                          |
    | Project credit note             | Set the slider to **Yes** to use the document as a project credit note.                                     |
    | Packing slip                    | Set the slider to **Yes** to use the document as a packing slip in sales and purchase orders.               |
    | Return packing slip             | Set the slider to **Yes** to use the document as a return packing slip in sales and purchase orders.        |
    | Inventory transfer packing slip | Set the slider to **Yes** to use the document as a packing slip in inventory transfer transactions.        |
    | Project packing slip            | Set the slider to **Yes** to use the document as a packing slip in a project.                               |
    | Project return delivery note    | Set the slider to **Yes** to use the document as a return packing slip in a project.                        |

    > [!NOTE]
    > Setting sliders to **Yes** one section turns off sliders in another section as they are mutually exclusive.

5. In the **Journals** section, configure the sliders to use the document in the journal lines with the defined account type.

    | Slider       | Description                                                       |
    |--------------|-------------------------------------------------------------------|
    | Ledger       | Use the document in ledger type voucher lines.       |
    | Vendor       | Use the document in vendor type voucher lines.       |
    | Project      | Use the document in project type voucher lines.      |
    | Customer     | Use the document in customer type voucher lines.     |
    | Fixed assets | Use the document in fixed assets type voucher lines. |
    | Bank         | Use the document in bank type voucher lines.         |

## Add the fiscal codification provided by the fiscal authorities

You can use the **Tax application** option to add this codification.

1.	Go to **Organization administration** > **Setup** > **LATAM** > **Document class type**.
2.	On the Action Pane, select **Tax application**.
3.	Select **New** to add a line to the grid.
4.	In the **Tax application Id.** field, select a value from the list.
5.	In the **Tax application code** field, type the code with which the fiscal authority identifies the document class type.
6.	Select **Save**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
