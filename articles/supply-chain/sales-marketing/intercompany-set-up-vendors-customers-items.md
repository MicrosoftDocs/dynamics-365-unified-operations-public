---
title: Set up vendors, customers, and items for intercompany trade
description: This topic explains how to set up vendors, customers, and items for intercompany trade
author: Henrikan
ms.date: 09/01/2021
ms.topic: article
ms.search.form: CustTable, VendTable, EcoResProductListPage
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: henrikan
ms.search.validFrom: 2021-09-01
ms.dyn365.ops.version: 10.0.22
---

# Set up vendors, customers, and items for intercompany trade

[!include [banner](../../includes/banner.md)]

To prepare your organization for intercompany trade, you must define the vendors and customers with whom you will be trading internally. You must then associate these vendors and customers with the items that you will be purchasing or selling.

1. Go to **Procurement and sourcing \> Vendors \> All vendors**.
1. Select the vendor to define as an intercompany vendor.
1. On the Action Pane, on the **General** tab, select **Intercompany**.
1. Specify intercompany setup parameters for the vendor account. These parameters include the customer legal entity and account, sales order policies, purchase order policies, value mapping, and purchase agreement and sales agreement policies. You also specify whether to use base data values from the vendor account or from the customer account in the other legal entity.
1. Go to **Product information management \> Products \> Released products**.
1. On the **Released products** list page, select the items to assign to the vendor, so that the items are available for intercompany trade. For each item, open the **Released product details** page. On the **Purchase** tab, in the **Vendor** field, type the vendor number.
1. Go to **Accounts receivable \> Customers \> All customers**.
1. Select the customer to define as an intercompany customer.
1. On the Action Pane, on the **General** tab, select **Intercompany**.
1. Specify intercompany setup parameters for the customer account. These parameters include the vendor legal entity and account, purchase order policies, sales order policies, value mapping, and sales agreement and purchase agreement policies. You also specify whether to use base data values from the customer account or from the vendor account in the other legal entity.
1. On the **Customers** page, on the **Invoice and delivery** FastTab, select the **Create intercompany orders** check box. If you want orders to be delivered directly to customers, select the **Direct delivery** check box.

    > [!NOTE]
    > If there are some items that your organization stocks and delivers to customers, you might not want to create intercompany orders automatically, even when you have the item in stock. To inactivate the automatic generation of orders for items that you might sometimes have in stock, clear the **Create intercompany orders** check box.

1. If you want to allow extra lines to be created indirectly on a sales order, select the **Create indirect order lines** check box. A user can then add lines to the original sales order from the intercompany sales order.

> [!WARNING]
> If you allow order lines to be created indirectly, you are permitting all additions to the original sales order from the intercompany sales order. Each addition is then processed through to the customer, and is added to the order and the invoice. Additionally, every document that is involved in the sale is printed and posted automatically. Users are not alerted about the addition.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
