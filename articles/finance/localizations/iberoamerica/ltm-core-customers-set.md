---
title: Customer sets for Latin America
description: Learn about the customer set configuration for Latin America, including prerequisites and an outline for setting up a customer set.
author: Fhernandez0088
ms.author: v-federicohe 
ms.topic: how-to
ms.date: 07/01/2024
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Customer sets for Latin America

[!include [banner](../../includes/banner.md)]

You can define which document classes are allowed in transactions for customers assigned to this customer set. Additionally, you can predefine default document classes for each transaction type.

## Prerequisites

Before you set up a customer set, the following prerequisites must be met:
- The legal entity has an address in a country or region within the LATAM localization.
- The country or region-specific LATAM feature and the general feature are enabled.
- Document classes that will be included must already exist.

## Set up a customer set

Follow these steps to set up a customer set.
1. Go to **Accounts receivable** \> **Setup** \> **LATAM** \> **Customers set** and create a new record.
1. In the **Customers/Vendors set** section, complete the **Customers/Vendors set** field with a unique code for the set.
1. Complete the **Description** field with a brief description of the set.
1. In the **Authorized vouchers** section, select the document classes for the set.
1. In the **Default document class for documents** section, set the predetermined document classes that will be selected by default for each transaction type.

    | Field                        | Transaction                                                                 |
    |------------------------------|-----------------------------------------------------------------------------|
    | Sales invoice                | Invoice from a sales order                                                  |
    | Sales Credit Note            | Credit note from a sales order                                              |
    | Free Text Invoice            | Free text invoice                                                           |
    | Free text credit note        | Free text credit note                                                       |
    | Project invoice              | Invoice from a project                                                      |
    | Project credit note          | Credit note from a project                                                  |
    | Packing Slip                 | Packing slip from a sales order                                             |
    | Return delivery note voucher         | Packing slip from a return sales order                                      |
    | Trade zone packing slip document | Packing slip from a sales order with a customer that is in a free trade zone |
    | Project packing slip         | Packing slip from a project                                                 |
    | Project return delivery note  | Packing slip from a return sales project                                    |

1. On the Action Pane, select **Save**.
