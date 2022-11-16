---
title: Vendors set for Latin America 
description: This article provides information about the Vendors set configuration for Latin America. 
author: Fhernandez0088
ms.date: 11/10/2022
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Vendor set configuration

You can define which **Document classes** are allowed in transactions with vendors. You can also define the predetermined **Document classes** for transactions with specific vendors.

## Prerequisites

To complete a vendor set, you must have already created the **Document classes** that you will include.

## Set up a customer or vendor set

1. Go to **Accounts payable** > **Setup** > **LATAM** > **Vendors set**.
2. In the **Vendors set** section, in teh **Customers/Vendors set** field, enter a code that identified the set you are creating.
3. In the **Description** field, enter a brief description of the set.
4. I the **Authorized voucher** grid, select the **Document classes** for the set.
5. In the **Default vouchers** section, select or enter values in the following fields to define the predetermined **Document classes** for when the vendor is used in a transaction.

  | Field                | Transaction                              |
  |----------------------|------------------------------------------|
  | Purchase invoice     | Invoice from purchase order.             |
  | Purchase credit note | Credit note from purchase order.         |
  | Packing slip         | Packing slip from purchase order.        |
  | Return delivery note | Packing slip from return purchase order. |
  | Credit journal       | Credit movement in an invoice journal.   |
  | Debit journal        | Debit movement in an invoice journal.    |
  | Value document       | Payment line in a journal.               |
  
6. On the Action Pane, select **Save**.
