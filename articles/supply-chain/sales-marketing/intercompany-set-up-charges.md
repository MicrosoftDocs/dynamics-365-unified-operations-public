---
title: Set up charges on intercompany orders
description: Learn how to set up charges on intercompany orders, including a step-by-step process for setting up charges for intercompany customers.
author: adpattanaik
ms.author: adpattanaik
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: CustTable, VendTable, EcoResProductListPage
---

# Set up charges on intercompany orders

[!include [banner](../../includes/banner.md)]

You can set up charges to be added to intercompany orders. When a charge is added to an intercompany sales order, it is automatically synchronized to the intercompany purchase order. This works both ways—from the intercompany sales order to the purchase order and the other way around.

You can also use charges to add a profit to an intercompany sales order by defining the charge as an intercompany percentage.

When you set up charges to be applied to intercompany orders, you enable the calculation of internal profit for an intercompany sales order from the net amount of the original sales order. You might want to do this if your intercompany vendor sells to you at cost price. The following procedure describes how to do this for intercompany customers. You can use the same procedure for vendors.

1. Go to **Accounts receivable \> Setup \> Charges \> Customer charge groups**.
1. Create a charges group.
1. Go to **Accounts receivable \> Customers \> All customers**. Select customer account link. On the Action Pane, select the **Customer** tab, and then select the **Sales order** FastTab.
1. Select **Edit** on the Action Pane to enable edits to the field. In the **Charges group** field, select the intercompany charges group that you set up in step 2.
1. Go to **Accounts receivable \> Setup \> Charges \> Auto charges**.
1. Set up the charges by filling in the relevant fields.
1. In the **Customer relation** field, select the intercompany charges group that you set up in step 2.
1. On the **Lines** FastTab, in the **Category** field, select **Intercompany percent**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
