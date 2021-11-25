---
# required metadata

title: Extend inventory on-hand data entities
description: This topic provides an example that shows how to add extended fields to the INVENTORSITEONHANDENTITY and INVENTWAREHOUSEONHANDENTITY views, so that the capabilities of the inventory on-hand data entities can work with the extensions.
author: yufeihuang
ms.date: 07/27/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: yufeihuang
ms.search.validFrom: 2020-07-27
ms.dyn365.ops.version: 10.0.13
---

# Extend inventory on-hand data entities

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management provides [extensibility](../../fin-ops-core/dev-itpro/extensibility/extensibility-home-page.md) features that let you [add fields to tables through extension](../../fin-ops-core/dev-itpro/extensibility/add-field-extension.md). This topic provides an example that shows how to add extended fields to the `INVENTORSITEONHANDENTITY` and `INVENTWAREHOUSEONHANDENTITY` views, so that the capabilities of the inventory on-hand data entities can work with the extensions. For more information about data entities, see [Data management overview](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

> [!NOTE]
> Here is a list of some of the inventory on-hand data entities:
>
> - Inventory on-hand by site
> - Inventory on-hand by site V2
> - Inventory on-hand by warehouse
> - Inventory on-hand by warehouse v2

After you add fields to tables that are used by the `inventSiteOnHandView` view, you must sync the engine so that the extensions are correctly recognized.

1. Extend the `InventSiteOnHandView` view by adding the extension field.
1. Extend the `InventSiteOnHandAggregatedView` view with the extension fields.
1. Extend the `InventSiteOnHandAggregatedViewBuilder` viewBuilder class by modifying the `getExtensionFields()` method. In this way, you map old view fields to new view fields when viewBuilder synchronization is run.

For example, you've added the following four fields to the `InventTable` table through extension:

- Custom field 1
- Custom field 2
- Custom field 3
- Custom field 4

In the case, you must modify the `getExtensionFields()` method in the following way.

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

After you complete these steps, you can extend the inventory on-hand by site and inventory on-hand by warehouse data entities by adding the new fields. In this way, you ensure that the extended fields are recognized and included during data migration that uses those data entities.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]