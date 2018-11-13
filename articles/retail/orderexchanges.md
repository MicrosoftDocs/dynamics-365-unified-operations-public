---
# required metadata

title: Configure and process an exchange on a return order
description: This topic describes how to configure an exchange on a return in Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 11/12/2018
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-11-15
ms.dyn365.ops.version: 

---
# Make an exchange on a return order

In Dynamics 365 for Retail, returns against customer orders have been processed using the return order document in HQ. The return order only supports the processing of products being returned, which is denoted by the negative quantity on the return order lines. Sales are denoted by a positive quantity, which the return order document doesn't support. Because of this limitation, it hasn't been possible to achieve scenarios like exchanges using the return order document in previous versions of Dynamics 365 for Retail.

Functionality has been added to support exchange scenarios on return orders. Retail now leverages the Sales order document instead of the Return order document to process these types of transactions.

## Configure Retail to support exchanges on return orders

Below are the steps to configure the system to support exchange scenarios on return orders.

1.  On the **Retail > Headquarters setup > Parameters > Retail parameters > Customer orders** fast tab, set the parameter **Process return orders as sales orders** to **Yes**.

2.  Run the 1110 Global configuration distribution schedule job.

## Make an exchange

If the system is configured as above, the experience in the point of sale (POS) for selecting a sales order or sales invoice to process a return will be the same. However, once the return items are added to the cart, the user will be able to add new sales line to the cart.

The newly added sales lines need to have all the attributes defined for it that is required to process a customer order line, including delivery method, fulfillment location, etc. The payment due for the transaction will be a net of the return order lines and sales order lines. On tendering the transaction, the return order will be posted as a sales order document in the HQ and the return lines will be invoiced immediately by the system.

To provide better visibility of the different amounts for the cart, three additional amount fields have been added to the cart. The additional fields can be enabled on the POS user interface (UI) through the screen designer. The three fields are:

1.  Deposit applied: This field denotes the deposit amount applied on a transaction when the user is doing a customer order pick up. With no deposit override, and with a 10% deposit configuration, this would be 90% of the total customer order amount.

1.  Carry out amount: The total amount for lines that have their delivery mode set to **Carry out** during the customer order creation, editing of the order, or exchange. The amount shown for this field includes taxes and charges.

1.  Return amount: The total amount for lines that have negative quantities during the customer order exchange. The amount shown for this field includes taxes and charges.



