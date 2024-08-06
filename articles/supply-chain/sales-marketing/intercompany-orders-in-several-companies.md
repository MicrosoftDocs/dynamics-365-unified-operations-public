---
title: Creating intercompany purchase and sales orders in several companies
description: Learn how to create intercompany purchase orders or sales orders in several companies for both trading companies and production companies.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
---

# Creating intercompany purchase and sales orders in several companies

[!include [banner](../../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management is not limited to handling only one production company and several sales companies. All companies that are set up for intercompany can be both trading companies and production companies.

If more companies can deliver the same item, you can freely choose whom to buy from, and updates are processed even if one sales order becomes several purchase orders.

In the same way that you automatically create one intercompany purchase order, you can create an original sales order in your company and then have several intercompany vendor companies fulfill the order by creating more than one intercompany purchase order. Microsoft Dynamics 365 Supply Chain Management automatically creates intercompany sales orders in the vendor companies.

To do this, all the companies must be set up as trading relationships. The vendor companies must be set up in Microsoft Dynamics 365 Supply Chain Management as intercompany vendors, and they must be the primary vendor for the relevant item. On the sales order, in **Header view**, you must select the **Autocreate intercompany orders** field and the **Direct delivery** field on the **Intercompany settings** FastTab. This is the default setting.

You create the sales lines in the usual way. When you leave the record, a message appears informing you that intercompany purchase orders and intercompany sales orders have been created. The message contains links to the new orders. To view the intercompany sales orders created in your vendor companies, open the original sales order and on the **General** tab, in the **Related information** group, select **References**.

If you open the intercompany purchase orders for the vendors, you see that Microsoft Dynamics 365 Supply Chain Management automatically fills in the original sales order number and the intercompany sales order number for each vendor.

Similarly, if you open the intercompany sales orders for the vendors, you see that Microsoft Dynamics 365 Supply Chain Management automatically fills in the original sales order number and the intercompany purchase order number for each vendor.

> [!NOTE]
> If the items on order exist in one of your intercompany vendor companies but not in the other, Microsoft Dynamics 365 Supply Chain Management creates the intercompany orders for the vendor company where the items exist but stops the order creation for the other company. A notification message is displayed when this happens.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
