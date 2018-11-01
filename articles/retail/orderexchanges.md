---
# required metadata

title: Enhancement to Pay Invoices
description: Enhancement to Pay Invoices
author: josaw1
manager: AnnBe
ms.date: 10/31/2018
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
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 

---
# Support for exchange scenario with customer orders

## Overview

Returns against customer orders are processed using the Return order document in HQ. Return order in HQ only supports the processing of products being returned which is denoted by the negative qty on the return order lines. The Return order document does not support the sales of item which could have been denoted with positive quantity on the Return order lines. Given this limitation, where products cannot be sold using the Return order document type, it was not possible to achieve scenarios like exchanges using the return order document.

Now, capability has been introduced to support exchange scenarios on Return orders by leveraging the Sales order document instead of the Return order document in HQ to process these transactions.

**Setup**

Below are the steps to configure the system to support exchange scenarios on Return orders:

1.  Set the parameter ‘Process return orders as sales orders’ to Yes which is available as per the path: **Retail > Headquarters setup > Parameters > Retail parameters > Customer orders** fast tab

2.  Run the 1110 Global configuration distribution schedule job

**Processing**

With the above configuration, the experience in POS in terms of selecting a Sales order / Sales invoice to process a return will be the same. However, once the return items are added to the cart, the user will be able to add new sales line to the cart, which was restricted without the above configuration.

The newly added sales lines need to have all the attributes defined for it that is required to process a customer order line in terms of delivery method, fulfillment location etc. The payment due for the transaction will be a net of the Return order lines and Sales order lines (Deposit for Pick / Ship and Full Amount for Carry out lines). On tendering the transaction, the Return order will be posted as a Sales order document in the HQ and the return lines will be invoiced immediately by the system.

In the exchange scenario, to provide better visibility to the users in terms of the different amounts for the cart, three additional amount fields have been added to the cart which can be enabled on the POS UI through the screen designer. The details of the same are as follows:

1.  Deposit applied: This field denotes the deposit amount applied on transaction when user is doing customer order pick up. With no deposit override, and with a 10% deposit configuration, this would be 90% of the total customer order amount

2.  Carry out amount: The total amount for lines that have their delivery mode set to ‘Carry out’ during customer order creation, edit, or exchange. This amount shown for this field includes taxes and charges.

3.  Return amount: The total amount for lines that have negative quantities during customer order exchange. This amount shown for this field includes taxes and charges.



