---
title: Customers set for Latin America 
description: This article provides information about the Customer set configuration for Latin America. 
author: Fhernandez0088
ms.date: 11/14/2022
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Customers set for Latin America
You can define which **Document classes** are allowed in transactions with customers. You can also define the predetermined **Document classes** for transactions with specific customers.

## Prerequisites
To complete a customer set, the **Document classes** that will be included must already exist.

## Set up a customer set
Complete the following steps to set up a customer set. 

1. Go to **Accounts receivable** > **Setup** > **LATAM** > **Customers set**.
2. In the **Customers set** section, enter the following field information:
 
   - **Customer/Vendor** - Select whether the register belongs to a customer.
   - **Customers/Vendors set** - Enter a unique code for the set you are creating.
   - **Description** - Enter a brief description of the set you are creating.

3. In the **Authorized voucher** grid, select the **Document classes** for the set.
4. In the **Default vouchers** section set the field values that will default for the selected **Document classes** when the customer is used in a transaction.

    | Field                        | Transaction                                                                 |
    |------------------------------|-----------------------------------------------------------------------------|
    | Sales invoice                | Invoice from a sales order.                                                   |
    | Sales credit note            | Credit note from a sales order.                                               |
    | Free text invoice            | Free text invoice.                                                          |
    | Free text credit note        | Free text credit note.                                                      |
    | Project invoice              | Invoice from projects.                                                      |
    | Project credit note          | Credit note from projects.                                                  |
    | Packing slip                 | Packing slip from sales order.                                              |
    | Return delivery note         | Packing slip from return sales orders.                                      |
    | Free trade zone packing slip | Packing slips from sales order with customers that are in free trade zones. |
    | Project packing slip         | Packing slip from projects.                                                 |
    | Project return deliver note  | Packing slip from return sales projects.                                    |

5. On the Action Pane, select **Save**.
