---
title: Extend inventory on-hand data entities
description: Learn how to add fields to the INVENTORSITEONHANDENTITY and INVENTWAREHOUSEONHANDENTITY views, so that inventory on-hand data entities work with extensions.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 02/11/2025
ms.custom: 
  - bap-template
---

# Extend inventory on-hand data entities

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management provides [extensibility](../../fin-ops-core/dev-itpro/extensibility/extensibility-home-page.md) features that let you [add fields to tables through extension](../../fin-ops-core/dev-itpro/extensibility/add-field-extension.md). This article provides an example that shows how to add extended fields to the `INVENTORSITEONHANDENTITY` and `INVENTWAREHOUSEONHANDENTITY` views, so that the capabilities of the inventory on-hand data entities can work with the extensions. For more information about data entities, see [Data management overview](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

> [!NOTE]
> Here's a list of some of the inventory on-hand data entities:
>
> - Inventory on-hand by site
> - Inventory on-hand by site V2
> - Inventory on-hand by warehouse
> - Inventory on-hand by warehouse v2

After you add fields to tables that are used by the `inventSiteOnHandView` view, you must sync the engine so that the extensions are correctly recognized.

1. Extend the `InventSiteOnHandView` view by adding the extension field.
1. Extend the `InventSiteOnHandAggregatedView` view with the extension fields.
1. Extend the `InventSiteOnHandAggregatedViewBuilder` viewBuilder class by modifying the `getExtensionFields()` method. In this way, you map old view fields to new view fields when viewBuilder synchronization is run.

For example, you added the following four fields to the `InventTable` table through extension:

- Custom field 1
- Custom field 2
- Custom field 3
- Custom field 4

In this case, you must modify the `getExtensionFields()` method in the following way.

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
