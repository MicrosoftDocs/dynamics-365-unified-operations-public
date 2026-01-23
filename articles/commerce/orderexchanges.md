---
# required metadata

title: Configure and process an exchange on a return order
description: Learn how to configure an exchange on a return in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/23/2026
ms.topic: how-to
ms.reviewer: v-griffinc 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.author: josaw

---
# Configure and process an exchange on a return order

[!include [banner](includes/banner.md)]

This article explains how to configure an exchange on a return in Microsoft Dynamics 365 Commerce.

In previous versions of Dynamics 365 Commerce, you process returns against customer orders by using the return order document in Headquarters. However, you can use the return order document to process only products that you're returning. You indicate the returned products by using a negative quantity on the return order lines. By contrast, you use a positive quantity to indicate sales. However, the return order document doesn't support positive quantities. Because of this limitation, previous versions of the app didn't support scenarios where product exchanges are done by using the return order document.

However, Microsoft added functionality to support scenarios where exchanges are done on return orders. Commerce now uses the sales order document instead of the return order document to process these types of transactions.

## Configure Commerce to support exchanges on return orders

> [!NOTE]
> In Commerce version 10.0.20 and later, a new feature called **Unified return processing experience in POS** is available. If you enable this feature, the setup steps in this article aren't required. **Process returns as sales orders** becomes a permanently configured setting and you can't change it.

Follow these steps to configure the system to support exchanges on return orders if you don't enable the **Unified return processing experience in POS** feature.

1. Go to **Retail and Commerce > Headquarters setup > Parameters > Commerce parameters**. On the **Customer orders** FastTab, set the **Process return orders as sales orders** option to **Yes**.
1. Run the **Global configuration distribution schedule** job (**1110**).

## Make an exchange

After you configure the system as described in the previous section, the point of sale (POS) user still selects a sales order or sales invoice to process a return, as in previous versions of the app. However, after the user adds the return items to the cart, they can add new sales lines to the cart.

For these new sales lines, the user must define all the attributes that are required to process a customer order line. These attributes include the delivery method and fulfillment location. The payment that's due for the transaction is a net of the return order lines and sales order lines. When the user tenders payment for the transaction, the return order posts as a sales order document in Headquarters, and the system immediately invoices the return lines.

To provide better visibility into the various amounts for the cart, the system adds three new amount fields to the cart. Use the screen designer to make these new fields available in the POS user interface (UI).

- **Deposit applied** – The deposit amount applied on a transaction when the user does a customer order pickup. If there's no deposit override, and a 10-percent deposit is configured, the amount in this field is 90 percent of the total amount of the customer order.
- **Carry out amount** – The total amount for lines where the delivery mode was set to **Carry out** when the customer order was created or edited, or during a customer order exchange. The amount in this field includes taxes and charges.
- **Return amount** – The total amount for lines that have negative quantities during the customer order exchange. The amount in this field includes taxes and charges.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
