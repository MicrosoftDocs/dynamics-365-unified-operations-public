---
# required metadata

title: Extend inventory on-hand data entities
description: This topic provides an example of how to add extended fields to the INVENTORSITEONHANDENTITY and INVENTWAREHOUSEONHANDENTITY views so that the inventory on-hand data entity capabilities can work with the extensions.
author: sherry-zheng
manager: tfehr
ms.date: 07/27/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2020-07-27
ms.dyn365.ops.version: Release 10.0.13
---

# Extend inventory on-hand data entities

[!include [banner](../includes/banner.md)]

Dynamics 365 Supply Chain Management provides [extensibility](../../fin-ops-core/dev-itpro/extensibility/extensibility-home-page.md) features that let you [add fields to tables through extension](../../fin-ops-core/dev-itpro/extensibility/add-field-extension). This topic provides an example of how to add extended fields to the `INVENTORSITEONHANDENTITY` and `INVENTWAREHOUSEONHANDENTITY` views so that the inventory on-hand [data entity](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages) capabilities can work with the extensions. For data entities details, see [Data Management](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages).

> [!NOTE]
> Inventory on-hand by site data entities include the following:
> - Inventory on-hand by site
> - Inventory on-hand by site V2
> - Inventory on-hand by warehouse
> - Inventory on-hand by warehouse v2

After you add fields to tables used by `invenSiteOnHandView`, you must sync the engine to correctly recognize the extensions by doing the following:

1. Extend the view `InventSiteOnHandView`  by adding the extension field.
1. Extend the view `InventSiteOnHandAggregatedView` with the extension fields.
1. Extend the viewBuilder class `InventSiteOnHandAggregatedViewBuilder`, by modifying the `getExtensionFields()` method. This maps old view fields to new view fields during the viewBuilder sync execution.

For example, you have added the following four fields to the table `InventTable` through extension:

- Custom field 1
- Custom field 2
- Custom field 3
- Custom field 4

Therefore, you must modify the `getExtensionFields()` method as follows:

```xpp
[ExtensionOf(classStr(InventSiteOnHandAggregatedViewBuilder))]
public final class InventOnHandAggregatedViewBuilder\_Extension
{
    protected Map getExtensionFields()
    {
        next getExtensionFields();
        Map extensionFields = new Map(Types::Int64, Types::Int64);
        extensionFields.insert(fieldNum(InventSiteOnHandView, Custom field 1), fieldNum(InventSiteOnHandAggregatedView, Custom field 1));
        extensionFields.insert(fieldNum(InventSiteOnHandView, Custom field 2), fieldNum(InventSiteOnHandAggregatedView, Custom field 2));
        extensionFields.insert(fieldNum(InventSiteOnHandView, Custom field 3), fieldNum(InventSiteOnHandAggregatedView, Custom field 3));
        extensionFields.insert(fieldNum(InventSiteOnHandView, Custom field 4), fieldNum(InventSiteOnHandAggregatedView, Custom field 4));
        return extensionFields;
    }
}
```

After you complete these steps, you can extend the inventory on-hand by site and inventory on-hand by warehouse data entities by adding the new fields. This will ensure that during data migration with those data entities, the extended fields are recognized and included.
