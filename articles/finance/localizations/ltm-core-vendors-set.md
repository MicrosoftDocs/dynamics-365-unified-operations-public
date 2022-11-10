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
You will be able to define which **Document classes** are allowed in transactions with vendors. It also will be possible to define the predetermined **Document classes** for transactions with specific vendors.
## Prerequisites
To complete a vendor set the **Document classes** that are included need to be previously created.
## Set up a customer or vendor set
1. Access the **Vendors set** configuration from ** Accounts payable > Setup > LATAM > Vendors set**.
2. In the **Vendors set** section complete the following fields:

| Field                 | Description                                                                             |
|-----------------------|-----------------------------------------------------------------------------------------|
| Customer/Vendor       | This field shows if the register belons to customers or vendors.                        |
| Customers/Vendors set | This field is completed manually with a code identifying the set that is being created. |
| Description           | This field is completed manually with a description.                                    |
3. Complete the **Authorized voucher** grid with the **Document classes** desired.
4. In the **Default vouchers** section complete the following fields to set the predetermined **Document classes** when the vendor is used in a transaction:

| Field                | Transaction                              |
|----------------------|------------------------------------------|
| Purchase invoice     | Invoice from purchase order.             |
| Purchase credit note | Credit note from purchase order.         |
| Packing slip         | Packing slip from purchase order.        |
| Return delivery note | Packing slip from return purchase order. |
| Credit journal       | Credit movement in an invoice journal.   |
| Debit journal        | Debit movement in an invoice journal.    |
| Value document       | Payment line in a journal.               |
5. On the Action Pane, select **Save**.
