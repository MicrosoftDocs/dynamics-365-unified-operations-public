---
# required metadata

title: Filter intercompany orders to avoid syncing Orders and OrderLines
description: This topic explains how to filter intercompany orders so that the Orders and OrderLines entities aren't synced.
author:  negudava
manager: tfehr
ms.date: 11/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: negudava
ms.dyn365.ops.version: 
ms.search.validFrom: 2019-09-20

---

# Filter intercompany orders to avoid syncing Orders and OrderLines

[!include [banner](../../includes/banner.md)]

You can filter intercompany orders so that the **Orders** and **OrderLines** entities aren't synced. In some scenarios, the intercompany order details aren't required in a customer engagement app.

Each standard Common Data Service entity is extended through references to the **IntercompanyOrder** field, and the dual-write maps are modified so that they refer to the additional fields in the filters. Therefore, the intercompany orders are no longer synced. This process helps prevent unnecessary data in the customer engagement app.

1. Extend the **CDS Sales Order Headers** entity by adding a reference to the **IntercompanyOrder** field. This field is filled in only on intercompany orders. The **IntercompanyOrder** field is available in **SalesTable**.

    :::image type="content" source="media/filter-sales-order-header-field-display.png" alt-text="Map staging to target page for CDS Sales Order Headers":::

2. After **CDS Sales Order Headers** is extended, the **IntercompanyOrder** field is available in the mapping. Apply a filter that has `INTERCOMPANYORDER == ""` as the query string.

    :::image type="content" source="media/filter-sales-order-header.png" alt-text="Edit query dialog box for CDS Sales Order Headers":::

3. Extend the **CDS Sales Order Lines** entity by adding a reference to the **IntercompanyInventTransId** field. This field is filled in only on intercompany orders. The **InterCompanyInventTransId** field is available in **SalesLine**.

    :::image type="content" source="media/filter-sales-order-line-field-display.png" alt-text="Map staging to target page for CDS Sales Order Lines":::

4. After **CDS Sales Order Lines** is extended, the **IntercompanyInventTransId** field is available in the mapping. Apply a filter that has `INTERCOMPANYINVENTTRANSID == ""` as the query string.

    :::image type="content" source="media/filter-sales-order-lines.png" alt-text="Edit query dialog box for CDS Sales Order Lines":::

5. Repeat steps 1 and 2 to extend the **Sales Invoice Header V2** entity and add a filter query. In this case, use `(INTERCOMPANYORDER == "") && (SALESORDERNUMBER != "")` as the query string for the filter.

    :::image type="content" source="media/filter-sales-invoice-header-field-display.png" alt-text="Map staging to target page for Sales Invoice Header V2":::

    :::image type="content" source="media/filter-sales-invoice-header-filter.png" alt-text="Edit query dialog box for Sales Invoice Header V2":::

6. Repeat steps 3 and 4 to extend the **Sales Invoice Lines V2** entity and add a filter query. In this case, use `INTERCOMPANYINVENTTRANSID == ""` as the query string for the filter.

    :::image type="content" source="media/filter-sales-invoice-lines-filter.png" alt-text="Edit query dialog box for Sales Invoice Lines V2":::

7. The **Quotations** entity doesn't have an intercompany relationship. If someone creates a quotation for one of your intercompany customers, you can use the **CustGroup** field to put all those customers into one customer group. You can extend the header and lines by adding the **CustGroup** field, and then filter so that the group isn't included.

    :::image type="content" source="media/filter-cust-group.png" alt-text="Map staging to target page for CDS Sales Quotation Header":::

8. After **Quotations** is extended, apply a filter that has `CUSTGROUP != "<company>"` as the query string.

    :::image type="content" source="media/filter-cust-group-edit.png" alt-text="Edit query dialog box for CDS Sales Quotation Header":::
