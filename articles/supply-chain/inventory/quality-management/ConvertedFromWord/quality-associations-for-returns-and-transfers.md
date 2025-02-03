---
title: 
description: 
ms.date: 04/25/2025
ms.topic: how-to
ms.service: 
author: johanhoffmann
ms.author: johanho
manager: 
---

# Quality Associations for Returns and Transfers

Quality associations establish the criteria for what events should trigger the automatic creation of Quality orders to test product quality. For this feature, we have added two triggers: Sales returns and Transfer orders.

## Setting up Quality associations for Returns and Transfers

Quality associations drive automatic creation of quality orders. Standard Supply Chain Management supports the following Reference Types: Sales, Purchase, Production, Co-Product Production, Route operation, Quarantine. This feature adds the ability to create a Quality association for a Reference type of Sales Return and Transfer.

All existing functionality provided by the Quality association feature is supported from these two new types. For example, subsequent processing can be blocked until the created quality order is validated.

For the Reference type of Sales return, the Document type option of Packing slip will trigger the creation of the quality order. Blocking subsequent processing of the packing slip or invoice is available. For Sales returns, the quality order can be triggered based on Customer, Customer group, or All Customers and based on Item, Item group or All Items.

For the Reference type of Transfer, the Document type option of Picking list, Ship transfer order or Receive could trigger the creation of the quality order. Blocking subsequent processing of the Picking list, shipping the transfer order or receiving the transfer order are all available options. For Transfer orders, the quality order can be triggered based on Item, Item group or All Items.

Here we demonstrate an example of setting up a quality association that indicates that a Quality order should be automatically triggered for a **Sales return** after the Packing slip process is posted for Item: RM1. The quality association tells the system what test group and item sampling should be used on the quality order. Additionally, this example indicates that subsequent invoicing of that sales return should be blocked until the quality order is validated.

Here we demonstrate an example of setting up a quality association that indicates that a Quality order should be automatically triggered for a **Transfer** before the Ship transfer order process is completed Item: RM1. The quality association tells the system what test group and item sampling should be used on the quality order. Additionally, this example indicates that receiving that transfer should be blocked until the quality order is validated.

## Inquiring on Quality related topics from Sales Returns and Transfers

This feature also added inquiries from the sales return and the transfer so that the user has easy visibility into the associated quality orders. For example, the above Quality association generated this quality order when the Ship transfer order process was attempted to be posted from the Transfer order. From the transfer order, access from Inquiries directly to the related quality order now available. The same visibility is provided from a sales return.
