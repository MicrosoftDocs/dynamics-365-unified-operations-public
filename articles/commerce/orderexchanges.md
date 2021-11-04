---
# required metadata

title: Configure and process an exchange on a return order
description: This topic explains how to configure an exchange on a return in Dynamics 365 Commerce.
author: josaw1
ms.date: 07/28/2021
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-11-15
ms.dyn365.ops.version: 

---
# Configure and process an exchange on a return order

[!include [banner](includes/banner.md)]

In previous versions of Dynamics 365 Commerce, returns against customer orders were processed by using the return order document in Headquarters. However, the return order document can be used to process only products that are being returned. The returned products are indicated by a negative quantity on the return order lines. By contrast, sales are indicated by a positive quantity. However, the return order document doesn't support positive quantities. Because of this limitation, previous versions of the app didn't support scenarios where product exchanges are done by using the return order document.

However, functionality has been added to support scenarios where exchanges are done on return orders. Commerce now uses the sales order document instead of the return order document to process these types of transactions.

## Configure Commerce to support exchanges on return orders

> [!NOTE]
> In Commerce version 10.0.20 and later, a new feature called "Unified return processing experience in POS" is available. If you enable this feature, the setup steps below are not required. **Process returns as sales orders** becomes a permanently configured setting and you won't be able to change it.

Follow these steps to configure the system to support exchanges on return orders (if you do not have the **Unified return processing experience in POS** feature enabled.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**. On the **Customer orders** FastTab, set the **Process return orders as sales orders** option to **Yes**.
2. Run the **Global configuration distribution schedule** job (**1110**).

## Make an exchange

After the system is configured as described in the previous section, the point of sale (POS) user will still select a sales order or sales invoice to process a return, as in previous versions of the app. However, after the return items are added to the cart, the user will be able to add new sales lines to the cart.

For these new sales lines, the user must define all the attributes that are required in order to process a customer order line. These attributes include the delivery method and fulfillment location. The payment that is due for the transaction will be a net of the return order lines and sales order lines. When payment is tendered for the transaction, the return order will be posted as a sales order document in Headquarters, and the system will immediately invoice the return lines.

To provide better visibility into the various amounts for the cart, three new amount fields have been added to the cart. You can use the screen designer to make these new fields available in the POS user interface (UI).

- **Deposit applied** – The deposit amount that is applied on a transaction when the user does a customer order pickup. If there is no deposit override, and a 10-percent deposit is configured, the amount in this field is 90 percent of the total amount of the customer order.
- **Carry out amount** – The total amount for lines where the delivery mode was set to **Carry out** when the customer order was created or edited, or during a customer order exchange. The amount in this field includes taxes and charges.
- **Return amount** – The total amount for lines that have negative quantities during the customer order exchange. The amount in this field includes taxes and charges.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
