---
# required metadata

title: Filter intercompany Orders to avoid synchronizing Orders and OrderLines
description: 
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

# Filter intercompany Orders to avoid synchronizing Orders and OrderLines

[!include [banner](../../includes/banner.md)]

You can filter the intercompany orders to avoid synchronizing the **Orders** and **OrderLines** entities. The intercompany accounts do not synchronize if the accounts are linked to the legal entities in the different companies in the Finance and Operations apps. This is because the accounts have a `PartyType=LegalEntity` reference that is not handled by the mappings. Then either the **Customer account** or the **sales header** fails to synchronize, causing downstream dependency failures. You can resolve this by manually creating the missing **Account** records in the customer engagement app, but in some scenarios, the intercompany order details are not necessary in customer engagement app.

Each of the standard Common Data Service entities is extended with references to intercompany, and the dual-write maps are modified to refer to the additional fields in the filters. The result is that the intercompany orders are no longer synchronized. This avoids unnecessary data in the customer engagement app.

1. Add a reference to **IntercompanyOrder** to **CDS Sales Order Headers**. It is populated on only Intercompany orders. The field **InterCompanyOrder** is available in **SalesTable**.

    :::image type="content" source="media/filter-sales-order-header-field-display.png" alt-text="Map staging to target, SalesOrderHeader":::

    :::image type="content" source="media/filter-sales-order-header.png" alt-text="Sales orders headers, edit query":::

2. Add a reference to **IntercompanyInventTransId** to **CDS Sales Order Lines**.  It is populated on only Intercompany orders. The field **InterCompanyInventTransID** is available in **SalesLine**.

    :::image type="content" source="media/filter-sales-order-line-field-display.png" alt-text="Map staging to target, SalesOrderLine":::

    :::image type="content" source="media/filter-sales-order-lines.png" alt-text="Sales order lines, edit query":::

3. Extend **Sales Invoice Header V2** and **Sales Invoice Lines V2** in the same waqy you extended the Common Data Service entities in steps 1 and 2.

    :::image type="content" source="media/filter-sales-invoice-header-field-display.png" alt-text="Map staging to target, Sales Invoice Headers":::

    :::image type="content" source="media/filter-sales-invoice-header-filter.png" alt-text="Sales invoice headers, edit query":::

    :::image type="content" source="media/filter-sales-invoice-lines-filter.png" alt-text="Sales invoice lines, edit query":::

4. **Quotations** doesn't have an intercompany relationship. If someone creates a quote for one of your intercompany Customers, you can put all of these customers in one Customer Group.  Header and lines can be extended to add the customer group field and filter to not include this group.

    :::image type="content" source="media/filter-cust-group.png" alt-text="Map staging to target, Sales Quotation Header":::

    :::image type="content" source="media/filter-cust-group-edit.png" alt-text="Sales Quotation Header, edit query":::
