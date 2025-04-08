---
title: Trace an item or raw material
description: Learn how to use item tracing to identify where items or raw materials have been used or are being used, including a step-by-step process.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form: InventTrackingDimTracing, InventTrackingDimTracingCriteria, InventTrackingItemIdLookup, InventBatchIdLookup, CustTable, SalesLine 
ms.topic: how-to
ms.date: 02/11/2025
ms.custom: 
  - bap-template
---

# Trace an item or raw material

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to use item tracing to identify where items or raw materials have been used or are being used. With this procedure, you can identify an item, trace it back to the source, and then trace forward through the production and sale of the finished product. The process can be used to investigate the customers impacted, the sales orders affected, and more. This procedure uses demo data company USP2.

## Trace an item backwards using a known batch number

1. Go to **Inventory management** \> **Inquiries and reports** \> **Tracking dimensions** \> **Item tracing**.
2. In the **Item number** field, select *P9100*.
3. In the list, select the link in the selected row.
4. In the **Forward or backward** field, select *Backward*.
5. In the **Batch number** field, select *as-12-344-01*.
6. In the list, select the link in the selected row.
7. Select **OK**.

## Identify an item, trace it forward, and make an analysis

The top node of the tree represents the on hand quantity of the selected item and batch. You need to expand the nodes of the tree to find the item that the forward trace should be executed on.

1. In the tree, expand the following nodes and then select the last node.

    Expand: *P9100 / 1 / 10 / as-12-344-01 ● 2 keg ● 7.00 gal  \P9100 ● Picked ● Sales order 000072 ● 12/22/2015  ● -1 keg ● -4.00 gal ● Site=1, Warehouse=10, Batch number=as-12-344-01  \P9100 ● Production B-000050 ● 12/9/2015● 7 keg ● 27.00 gal ● Site=1,Warehouse=10,Batch number=as-12-344-01 ● Co-products: P9101* and then select that node.

2. In the tree, expand the following node and then select that node.

    Starting from the node that you just selected, expand *M9103 ● Production line B-000050 ● 12/9/2015  ● -160.00 lb ● Size=70, Color=OK, Site=1, Warehouse=10, Batch number=App01* and then select that node.  

3. Select **Trace from node**.
4. Select **Forward**.
5. On the Action Pane, select **Tracing**.

    There are several tracing options which provide information about the customers impacted by the item that you're tracing, and the sales orders related to the item which have and haven't been shipped.

6. Select **Customers**.
7. Close the page.
8. On the Action Pane, select **Tracing**.
9. Select **Shipped sales orders**.
10. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
