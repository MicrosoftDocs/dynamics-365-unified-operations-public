---
title: Customers set for Latin America 
description: This article provides information about the Customer set configuration for Latin America. 
author: Fhernandez0088
ms.date: 11/10/2022
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Customers set for Latin America
You will be able to define which **Document classes** are allowed in transactions with customers. It also will be possible to define the predetermined **Document classes** for transactions with specific customers.
## Prerequisites
To complete a customer set the **Document classes** that are included need to be previously created.
## Set up a customer set
1. Access the **Customers set** configuration from **Accounts receivable > Setup > LATAM > Customers set**.
2. In the **Customers set** section complete the following fields:

| Field                 | Description                                                                             |
|-----------------------|-----------------------------------------------------------------------------------------|
| Customer/Vendor       | This field shows if the register belongs to a customer.                        |
| Customers/Vendors set | This field is completed manually with a code identifying the set that is being created. |
| Description           | This field is completed manually with a description.                                    |
3. Complete the **Authorized voucher** grid with the **Document classes** desired.
4. In the **Default vouchers** section complete the following fields to set the predetermined **Document classes** when the customer is used in a transaction:

| Field                        | Transaction                                                                 |
|------------------------------|-----------------------------------------------------------------------------|
| Sales invoice                | Invoice from sales order.                                                   |
| Sales credit note            | Credit note from sales order.                                               |
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
