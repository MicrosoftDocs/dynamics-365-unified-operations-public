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

You can define which document classes are allowed in transactions with customers. You can also define the predetermined document classes for transactions with specific customers.

## Prerequisites

Before you set up a customer set, the document classes that will be included must already exist.

## Set up a customer set

Follow these steps to set up a customer set.

1. Go to **Accounts receivable** \> **Setup** \> **LATAM** \> **Customers set**.
2. In the **Customers set** section, set the following fields:
 
    - **Customer/Vendor** – Select whether the register belongs to a customer.
    - **Customers/Vendors set** – Enter a unique code for the set that you're creating.
    - **Description** – Enter a brief description of the set that you're creating.

3. In the **Authorized voucher** grid, select the document classes for the set.
4. In the **Default vouchers** section, set the default field values that should be entered for the selected document classes when the customer is used in a transaction.

    | Field                        | Transaction                                                                 |
    |------------------------------|-----------------------------------------------------------------------------|
    | Sales invoice                | Invoice from a sales order                                                  |
    | Sales credit note            | Credit note from a sales order                                              |
    | Free text invoice            | Free text invoice                                                           |
    | Free text credit note        | Free text credit note                                                       |
    | Project invoice              | Invoice from a project                                                      |
    | Project credit note          | Credit note from a project                                                  |
    | Packing slip                 | Packing slip from a sales order                                             |
    | Return delivery note         | Packing slip from a return sales order                                      |
    | Free trade zone packing slip | Packing slip from a sales order with a customer that's in a free trade zone |
    | Project packing slip         | Packing slip from a project                                                 |
    | Project return deliver note  | Packing slip from a return sales project                                    |

5. On the Action Pane, select **Save**.
