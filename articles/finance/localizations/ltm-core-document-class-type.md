---
title: Document class types for Latin America 
description: This topic provides information about the document class type configuration for Latin America. 
author: Fhernandez0088
ms.date: 03/15/2022
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---
# Document class type for Latin America
You can configure the different types of document classes that the company will use. This configuration is used to group the document classes according to the characteristics that they have in common.
## Prerequisites
To configure a **Document class type** the prefix length configuration in **LATAM Parameters** menu must be previously set.
## Set up a Document class type for Latin America
1. Go to **Organization administration > Setup > LATAM > Document class type**.
2. Select **New** from the action pane.
3. In the **General** section configure the following fields and sliders:

| Field/Slider                | Description                                                                                                                         |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Document class type Id.     | Enter a code to identify the register.                                                                                              |
| Description                 | Enter an extended description of the document class type.                                                                           |
| Prefix                      | Enter a prefix that will be used in the document complete number.                                                                   |
| Unique document per voucher | Activate this slider to limit to one the amount of this document class types permitted to be posted in a voucher.                   |
| Unique account per voucher  | Activate this slider to limit to one the amount of account types permitted to be posted in a voucher with this document class type. |

4. Configure the sliders in sections **Payment method**, **Invoices**, **Credit notes** and **Packing Slip**.

| Slider                          | Description                                                                                  |
|---------------------------------|----------------------------------------------------------------------------------------------|
| Payment method                  | Set to yes to use as a payment document.                                                     |
| Unique per voucher              | Set to yes to limit to one the amount of payment documents allowed per voucher post.         |
| Replicates header information   | Set to yes to copy the information of the document class to the rest of the voucher's lines. |
| Sales invoice                   | Set to yes to use the document as a sales invoice in a sales order.                          |
| Free text invoice               | Set to yes to use the document in a free text invoice transaction.                           |
| Purchase invoice                | Set to yes to use the document in an invoice journal and a purchase order.                    |
| Project invoice                 | Set to yes to use the document as a project invoice.                                         |
| Sales credit note               | Set to yes to use the document as a credit note.                                             |
| Free text credit note           | Set to yes to use the document as a credit note in a free text invoice transaction.          |
| Purchase credit note            | Set to yes to use the document as a credit note in purchase orders.                           |
| Project credit note             | Set to yes to use the document as a project credit note.                                     |
| Packing slip                    | Set to yes to use the document as a packing slip in sales and purchase orders.               |
| Return packing slip             | Set to yes to use the document as a return packing slip in sales and purchase orders.        |
| Inventory transfer packing slip | Set to yes to use the document as a packing slip in inventory transfers transactions.        |
| Project packing slip            | Set to yes to use the document as a packing slip in a project.                               |
| Project return delivery note    | Set to yes to use the document as a return packing slip in a project.                        |

> [!NOTE]
> Enabling one section sliders disables the others, they are mutually exclusives.

5. In the **Journals** section configure the sliders to allow the usage of the document in the journal lines with the defined account type.

| Slider       | Description                                                       |
|--------------|-------------------------------------------------------------------|
| Ledger       | Allow the use of the document in ledger type voucher lines.       |
| Vendor       | Allow the use of the document in vendor type voucher lines.       |
| Project      | Allow the use of the document in project type voucher lines.      |
| Customer     | Allow the use of the document in customer type voucher lines.     |
| Fixed assets | Allow the use of the document in fixed assets type voucher lines. |
| Bank         | Allow the use of the document in bank type voucher lines.         |

## Add the fiscal codification provided by the fiscal authorities

You can use **Tax application** option to add this codification.

1.	Go to **Navigation pane > Organization administration > Setup > LATAM > Document class type**.
2.	Select the **Tax application** button on the action pane.
3.	Select **New** to add a line to the grid.
4.	In the **Tax application Id.** field select a value from the list.
5.	In the **Tax application code field** type the code with which the fiscal authority identifies the document class type.
6.	Select **Save**.
