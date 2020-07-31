---
# required metadata

title: Product dimensions
description: There are five product dimensions - color, configuration, size, style and version. You combine product dimensions in dimension groups and assign dimension groups to product masters. The combinations of product dimensions determine how product variants are defined.
author: cvocph
manager: tfehr
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: EcoResProductDimension, EcoResProductDimensionGroup, EcoResProductMasterDimension, RetailEcoResColor, RetailEcoResSize, RetailEcoResStyle
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac

ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 19171
ms.assetid: 81fa3709-4ab8-4fbf-9806-359892a05985
ms.search.region: Global
ms.search.industry: Retail
ms.author: conradv
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: 10.0.13

---

# Product dimensions

[!include [banner](../includes/banner.md)]

There are five product dimensions: color, configuration, size, style and version. You combine product dimensions in dimension groups and assign dimension groups to product masters. The combinations of product dimensions determine how product variants are defined.

Product dimensions are characteristics that serve to identify a product variant. You can use combinations of product dimensions to define product variants. You must define at least one product dimension for a product master in order to create a product variant.

## Product variants

Product variants are also referred to as items. An item is a tangible product, which is not the same as a service. It is also possible to define a product master with the service type. By using the service type, you can specify product variants that include services. For example, you can specify a product master for consultancy work and product variants for work that is performed by senior consultants and junior consultants.

## Product dimensions

A product variant can be generated based on the product dimension values.

Product dimensions values such as size, color and style can be created on the **Size**, **Color** and **Style** pages, which can be accessed from the following locations: **Product information management \> Setup \> Dimension and variant Groups \> Sizes/Colors/Styles**.

Product dimension values for the configuration dimension are typically created using either the Product configurator or the Dimension-based configurator. 

Product versions are usually created for the specific version as the product evolves in its lifecycle. Product versions are covered in detail later in this topic.

Product dimensions can also be created and maintained on the **Product dimensions** page, which can be accessed from the following locations:

- Go to **Product information management \> Products \> Product masters**. On the Action Pane, select **Product dimensions**.
- Go to **Product information management \> Products \> All products and product masters**. Select a product master. On the Action Pane, select **Product dimensions**.
- Go to **Product information management \> Released products**. Select a product master. On the Action Pane, select **Product** and, in the **Product master** group, select **Product dimensions**.

The number of variants that you can create for an item is limited by the number of possible product dimension combinations.

> [!TIP]
> When you use a product on, for example, an order line, you select the product dimensions to identify the product variant that you want to work with.

## Example

A company sells denim jeans. The item, *Jeans*, uses the color and size product dimensions. The jeans are sold in three different colors and six different sizes. The colors are: blue, black, and brown. The sizes are: XS, S, M, L, XL, and XXL. Not all sizes are available in all the three colors. If all combinations were available, it would create 18 different types of jeans. In this example, only the following nine product variant combinations are produced.

| Color | Size |
|-------|------|
| Blue  | XS   |
| Blue  | S    |
| Blue  | M    |
| Black | M    |
| Black | L    |
| Black | XL   |
| Brown | L    |
| Brown | XL   |
| Brown | XXL  |

## The version product dimension

Version is a product dimension that is intended to help you maintain and track multiple versions of a product throughout the supply chain. Version tracking is essential to the success of manufacturers operating in a world of constantly shrinking product lifecycles, increased quality and reliability requirements, and increased focus on product safety.

As a standard product dimension, version will behave similarly to the existing product dimensions of size, style, color and configuration, which means that you could also choose to use it for purposes other than tracking product versions.

### Enable the version product dimension

Before you can use the version dimension, it must be enabled on your system (which requires admin permissions). To enable the feature:

1. Go to **System administration \> Workspaces \> Feature management**.
1. Enable the feature named *Product dimension version*. (See also [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).)
1. Put your system into [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. Go to **System administration \> Setup \> License configuration**.
1. On the **Configuration keys** tab, expand **Trade**, and select the check box for **Product dimension - version**.
1. Turn off [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).

### Areas where version isn't supported

The following areas don't support the version dimension because introducing it would cause breaking changes:

- Cost object monthly statement
- Cost object statement cache
- MCR sales statistics per item
- Vendor catalogs
- EcoResProductDimensionGroupEntity

In addition, Dynamics 365 Commerce order-creation and order-processing features (such as point of sale, call center, and e-commerce orders) don't support the version dimension. There is no confirmed timeline as to when Commerce orders will be enhanced to support it.

### Functional characteristics of version

The product dimension version works similarly to the other product dimensions. However, due to its specific nature, and because it is intended to maintain and track multiple versions of a product, it behaves slightly differently. Differences include:

- **There is no version group**<br>Unlike size, color, and style (which have color group, size group, and style group) no version group exists. Groups let you predefine the applicable values so that when, for example, you assign a color group to a product, the product can use all the colors in that color group. This concept doesn't apply for teh version dimension because the versions that a product will take aren't predefined when the product is created. Instead. versions are created during the lifecycle of the product as needed. You would typically create a new version (rather than a new product) when the form, fit, and function of the product otherwise remain the same.
- **Product variant suggestions work as they currently do**<br>It is expected that there are no changes to the process of creating and releasing versioned products.<!--KFM: I don't understand what this first sentence means--should it mention variants? -->. When creating a versioned product, the first version (V-1) will be created as a product dimension and the variant(s) will be released. As the product changes and a new version is needed, then the new version value (V-2) will be added and the needed variants will be released. It is not expected that all the versions (V-1, V-2, V-3) will be created in advance for the product.

> [!IMPORTANT]
> By enabling this, and using the version dimension in any functionalities could potentially not work as expected if there are any solutions installed that reference the Inventory dimensions. The ISV that owns the solution would be able to determine this. <!--KFM: I'm not sure what we are trying to say here. I think it's this: "If you enable and use the version dimension, then some solutions that reference the inventory dimensions may stop working as expected. Please contact the independent software vendor (ISV) for your affected solutions to confirm and fix these issues." -->

### Before turning on the version dimension

When you enable the the version dimension, some functionality could become broken or stop working as expected if you have installed other solutions that add customizations to the inventory dimensions. For the version dimension to be fully functional, you may need to update those solutions to include the version dimension in their references to the inventory dimensions.<!--KFM: Is this the same issue we are referring to in the previous IMPORTANT box? Also, we should probably put this info together with or before the instructions on how to enable the feature. -->

When you are testing your solutions for compatibility with the version dimension, look for the following:

1. **Functionality**<br>Most importantly, any customizations that involve the inventory dimensions must be assessed so they can work accordingly in conjunction with the version dimension.

1. **References to the inventory dimensions**<br>Look out for references to the inventory dimensions (where the dimensions are referenced specifically). References to `InventDimId` should work out of the box, but look out for references to style or color.
    - API calls in extended classes <!-- KFM: what about them? -->
    - All references to specific inventory dimensions in extension code must float the version dimension along with the style, color, size dimensions.

1. **References to obsoleted API calls**<br>With the introduction of the version dimension, we have tried to minimize the obsoleting of APIs as much as possible. Those few APIs that have been obsoleted will issue a warning when you turn on the **Product dimension - version** configuration key. Those API calls must be fixed in your extended solutions before you activate the version dimension on a production system. Here are the version-specific obsoleted APIs:
    - RetailTransactionServiceInventory::getProductRecordId
    - EcoResProductNumberIdentifiedProductVariantEntity::find
    - EGAISAlcoholProduction_RU::findByItemDim
    - PCVariantConfiguration::findByProductMasterAndDimensions

1. **Maps**<br>For any maps that use the inventory dimensions, the corresponding relation mapping to these maps must be updated to include the version dimension. Look out for tables in the extended model or table extensions where the fields include inventory dimensions.

1. **Retail functionality**<br>The version dimension floats through retail code on standard<!-- KFM: what do we mean by "on standard"? -->, however the version dimension isn't otherwise supported by Dynamics 365 Commerce at this time. This is similar to the way the config dimension is currently handled in Commerce.
