---
# required metadata

title: Filter intercompany orders to avoid synchronizing Orders and OrderLines
description: This topic describes how to filter intercompany orders to avoid synchronizing Orders and OrderLines.
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

# Filter intercompany orders to avoid synchronizing Orders and OrderLines

[!include [banner](../../includes/banner.md)]

You can filter intercompany orders to avoid synchronizing the **Orders** and **OrderLines** entities. Intercompany accounts do not synchronize if the accounts are linked to the legal entities in the different companies in the Finance and Operations apps. They do not synchronize because the **Accounts** table has a `PartyType=LegalEntity` reference that is not handled by the mappings. Then either the **CustomerAccount** table or the **SalesHeader** table fails to synchronize, causing downstream dependency failures. You can resolve this by manually creating the missing **Account** records in the customer engagement app, but in some scenarios, the intercompany order details are not necessary in customer engagement app.

Each of the standard Common Data Service entities is extended with references to the **IntercompanyOrder** field, and the dual-write maps are modified to refer to the additional fields in the filters. The result is that the intercompany orders are no longer synchronized. This process avoids unnecessary data in the customer engagement app.

1. Add a reference to **IntercompanyOrder** to **CDS Sales Order Headers**. It is populated on only intercompany orders. The field **IntercompanyOrder** is available in **SalesTable**.

    :::image type="content" source="media/filter-sales-order-header-field-display.png" alt-text="Map staging to target, SalesOrderHeader":::
    
2. After **CDS Sales Order Headers** is extended, the **IntercompanyOrder** field is available in the mapping. Apply a filter with `INTERCOMPANYORDER == ""` as the query string.

    :::image type="content" source="media/filter-sales-order-header.png" alt-text="Sales orders headers, edit query":::

3. Add a reference to **IntercompanyInventTransId** to **CDS Sales Order Lines**.  It is populated on only intercompany orders. The field **InterCompanyInventTransID** is available in **SalesLine**.

    :::image type="content" source="media/filter-sales-order-line-field-display.png" alt-text="Map staging to target, SalesOrderLine":::

4. After **CDS Sales Order Lines** is extended, the **IntercompanyInventTransId** field is available in the mapping. Apply a filter with `INTERCOMPANYINVENTTRANSID == ""` as the query string.

    :::image type="content" source="media/filter-sales-order-lines.png" alt-text="Sales order lines, edit query":::

5. Extend **Sales Invoice Header V2** and **Sales Invoice Lines V2** in the same way you extended the Common Data Service entities in steps 1 and 2. Then add the filter queries. The filter strings are `(INTERCOMPANYORDER == "") && (SALESORDERNUMBER != "")` and `INTERCOMPANYINVENTTRANSID == ""`.

    :::image type="content" source="media/filter-sales-invoice-header-field-display.png" alt-text="Map staging to target, Sales Invoice Headers":::

    :::image type="content" source="media/filter-sales-invoice-header-filter.png" alt-text="Sales invoice headers, edit query":::

    :::image type="content" source="media/filter-sales-invoice-lines-filter.png" alt-text="Sales invoice lines, edit query":::

6. The **Quotations** entity doesn't have an intercompany relationship. If someone creates a quote for one of your intercompany customers, you can put all of these customers in one customer group by using the **CustGroup** field.  Header and lines can be extended to add the **CustGroup** field and then filter to not include this group.

    :::image type="content" source="media/filter-cust-group.png" alt-text="Map staging to target, Sales Quotation Header":::

7. After you extent the **Quotations** entity, apply a filter with `CUSTGROUP !=  "\<company\>"` as the query string.

    :::image type="content" source="media/filter-cust-group-edit.png" alt-text="Sales Quotation Header, edit query":::
