---
title: Product dimensions
description: There are five product dimensions - color, configuration, size, style, and version. You combine product dimensions in dimension groups and assign dimension groups to product masters. The combinations of product dimensions determine how product variants are defined.
author: t-benebo 
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: EcoResProductDimension, EcoResProductDimensionGroup, EcoResProductMasterDimension, RetailEcoResColor, RetailEcoResSize, RetailEcoResStyle, EcoResVersionNameLookup, RetailStyleGroupTable
ms.topic: how-to
ms.date: 01/06/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Product dimensions

[!include [banner](../includes/banner.md)]

There are five product dimensions: color, configuration, size, style, and version. You combine product dimensions in dimension groups and assign dimension groups to product masters. The combinations of product dimensions determine how product variants are defined.

Product dimensions are characteristics that serve to identify a product variant. You can use combinations of product dimensions to define product variants. You must define at least one product dimension for a product master in order to create a product variant.

> [!NOTE]
> You can't use physical dimensions to create product variants. Physical dimensions are specified on the product master and are shared by all its variants. 

## Product variants

Product variants are also referred to as items. An item is a tangible product, which isn't the same as a service. It's also possible to define a product master with the service type. By using the service type, you can specify product variants that include services. For example, you can specify a product master for consultancy work and product variants for work that is performed by senior consultants and junior consultants.

## Set up product dimensions

A product variant can be generated based on the product dimension values.

Product dimension values for the size, color, and style dimensions can be created in the following locations:

- **Size** page (**Product information management \> Setup \> Dimension and variant groups \> Sizes**)
- **Color** page (**Product information management \> Setup \> Dimension and variant groups \> Colors**)
- **Style** page (**Product information management \> Setup \> Dimension and variant groups \> Styles**)

Product dimension values for the configuration dimension are typically created by using either the Product configurator or the Dimension-based configurator.

Product versions are usually created for specific versions as the product evolves during its lifecycle. Product versions are covered in detail later in this article.

Product dimensions can also be created and maintained on the **Product dimensions** page, which can be accessed from the following locations:

- Go to **Product information management \> Products \> Product masters**. On the Action Pane, select **Product dimensions**.
- Go to **Product information management \> Products \> All products and product masters**. Select a product master. On the Action Pane, select **Product dimensions**.
- Go to **Product information management \> Released products**. Select a product master. On the Action Pane, on the **Product** tab, in the **Product master** group, select **Product dimensions**.

The number of variants that you can create for an item is limited by the number of possible product dimension combinations.

> [!TIP]
> When you use a product on an order line, for example, you select the product dimensions to identify the product variant that you want to work with.

## Example

A company sells denim jeans. The item, *Jeans*, uses the color and size product dimensions. The jeans are sold in three different colors and six different sizes. The colors are blue, black, and brown. The sizes are XS, S, M, L, XL, and XXL. Not all sizes are available in all three colors. If all combinations were available, there would be 18 different types of jeans. However, in this example, only the following nine product variant combinations are produced.

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

Version is a product dimension that is intended to help you maintain and track multiple versions of a product throughout the supply chain. Version tracking is essential to the success of manufacturers that operate in a world of constantly shrinking product lifecycles, increased quality and reliability requirements, and increased focus on product safety.

As a standard product dimension, version will behave similarly to the existing product dimensions (size, style, color, and configuration). Therefore, you can use it for other purposes besides tracking product versions.

### <a name="enable-version-dim"></a>Turn on the version dimension

#### Before you turn on the version dimension

When you turn on the version dimension, some functionality could become broken or stop working as expected if you've installed other solutions that add customizations to the inventory dimensions. For the version dimension to be fully functional, you might have to update those solutions so that they include the version dimension in their references to the inventory dimensions.

When you're testing your solutions for compatibility with the version dimension, look for the following elements:

1. **Functionality:** Most importantly, any customizations that involve the inventory dimensions must be assessed to ensure that they can work with the version dimension.
1. **References to the inventory dimensions:** Look out for references to the inventory dimensions (that is, places where the dimensions are explicitly referenced). References to `InventDimId` should work out of the box, but look out for references to style or color. For example, be sure to check the following elements:

    - API calls in extended classes
    - All references to specific inventory dimensions in extension code (This code must float the version dimension together with the style, color, and size dimensions.)

1. **References to obsolete API calls:** In its introduction of the version dimension, Microsoft has tried to make as few APIs as possible obsolete. The few APIs that have been made obsolete will issue a warning when you turn on the **Product dimension - version** configuration key. Calls to those APIs must be fixed in your extended solutions before you turn on the version dimension in a production system. Here are the version-specific obsolete APIs:

    - RetailTransactionServiceInventory::getProductRecordId
    - EcoResProductNumberIdentifiedProductVariantEntity::find
    - EGAISAlcoholProduction_RU::findByItemDim
    - PCVariantConfiguration::findByProductMasterAndDimensions

1. **Maps:** If any maps use the inventory dimensions, the corresponding relation mapping to these maps must be updated so that they include the version dimension. In the extended model or table extensions, look out for tables where the fields include inventory dimensions.
1. **Microsoft Dynamics 365 Commerce functionality:** After it's turned on, the version dimension will appear throughout the Commerce-specific code in Dynamics 365 Supply Chain Management. However, the version dimension isn't yet supported by the Commerce channel database or in the Point of Sale (POS) or e-Commerce applications. These Commerce-specific applications won't support users selling/shipping or returning/receiving inventory by version dimension. Inventory availability lookup functions won't discern inventory by version dimension in Commerce apps. This behavior resembles the current behavior of the config dimension throughout Commerce.

#### Turn on the version dimension

Before you can use the version dimension, it must be turned on for your system. This task requires admin permissions.

1. Go to **System administration \> Workspaces \> Feature management**.
1. Turn on the feature that is named *Product dimension version*. (For more information, see [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).)
1. Put your system into [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. Go to **System administration \> Setup \> License configuration**.
1. On the **Configuration keys** tab, expand **Trade**, and select the check box for **Product dimension - version**.
1. Turn off [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).

### Areas where the version dimension isn't supported

The following areas don't support the version dimension (you can still use these areas but you won't be able to add versioned products (products where the version dimension is used) to them). For example, you can't add a versioned item to a vendor catalog. This is because adding products with the version dimension to these areas would cause breaking changes.

- Cost object monthly statement
- Cost object statement cache
- MCR sales statistics per item
- Vendor catalogs
- EcoResProductDimensionGroupEntity

In addition, the order creation and order processing features in Commerce (for example, for POS, call center, and e-commerce orders) don't support the version dimension. There's no confirmed timeline as to when Commerce orders will be enhanced to support it.

### Functional characteristics of the version dimension

The version dimension works like the other product dimensions. However, because of its specific nature, and because it's intended to maintain and track multiple versions of a product, it behaves slightly differently. Here are some of the differences and similarities:

- **There is no version group.**

    Although the concept of groups exists for size, color, and style (color group, size group, and style group), no version group concept exists. Groups let you predefine the applicable values so that when, for example, you assign a color group to a product, the product can use all the colors in that color group. This concept doesn't apply to the version dimension, because the versions that a product takes aren't predefined when the product is created. Instead, versions are created during the lifecycle of the product, as they're required. Typically, if the form, fit, and function of the product remain the same, you create a new version instead of a new product.

- **Product variant suggestions work as they currently do.**

    Product variant suggestions will create suggestions for all version dimension values, just as they do for other dimensions. The process of creating and releasing versioned products is the same as it is for products that use other dimensions. When you create a versioned product, the first version (V1) will be created as a product dimension, and the variants will be released. As the product changes and a new version is needed, the new version value (V2) will be added, and the required variants will be released. There's no expectation  that all the versions (V1, V2, and V3) will be created in advance for the product.

> [!IMPORTANT]
> If you turn on and use the version dimension, some solutions that reference the inventory dimensions might stop working as expected. To confirm and fix these issues, contact the independent software vendor (ISV) for your affected solutions. For more information, see [Enable the version dimension](#enable-version-dim).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
