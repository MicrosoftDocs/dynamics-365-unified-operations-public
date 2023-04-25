---
title: Vendor sets for Latin America
description: This article provides information about the vendor set configuration for Latin America.
author: Fhernandez0088
ms.date: 01/31/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Vendor sets for Latin America

[!include [banner](../includes/banner.md)]

You can define which document classes are allowed in transactions with vendors. You can also define the predetermined document classes for transactions with specific vendors.

## Prerequisites

Before you set up a vendor set, you must create the document classes that you will include.

## Set up a vendor set

1. Go to **Accounts payable** \> **Setup** \> **LATAM** \> **Vendors set**.
2. In the **Vendors set** section, in the **Customers/Vendors set** field, enter a code that identifies the set that you're creating.
3. In the **Description** field, enter a brief description of the set.
4. In the **Authorized voucher** grid, select the document classes for the set.
5. In the **Default vouchers** section, set the following fields to define the predetermined document classes that will be used when the vendor is used in a transaction.

    | Field                | Transaction                                |
    |----------------------|--------------------------------------------|
    | Purchase invoice     | Invoice from a purchase order.             |
    | Purchase credit note | Credit note from a purchase order.         |
    | Packing slip         | Packing slip from a purchase order.        |
    | Return delivery note | Packing slip from a return purchase order. |
    | Credit journal       | Credit movement in an invoice journal.     |
    | Debit journal        | Debit movement in an invoice journal.      |
    | Value document       | Payment line in a journal.                 |

6. On the Action Pane, select **Save**.
