---
title: Assortment management
description: This article provides an overview of the basic concepts of assortment management in Microsoft Dynamics 365 Commerce and provides implementation considerations for your project.
author: josaw1
ms.date: 01/15/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-11-21

---

# Assortment management

[!include [banner](../includes/banner.md)]

This article provides an overview of the basic concepts of assortment management in Microsoft Dynamics 365 Commerce and provides implementation considerations for your project.

Dynamics 365 Commerce provides *assortments* that you can use to manage product availability across channels. Assortments determine which products are available at specific stores and during a specific period.

In Commerce, an assortment is a mapping of one or more channels (or groups of channels, when using organization hierarchies) to one or more products (or groups of products, when using category hierarchies).

The published assortments that you assign to a channel determine the overall product mix of that channel. You can configure multiple active assortments per channel.

### Basic assortment setup

In the following example, you configure a unique assortment for each store. In this case, only product 1 is available at store 1, and only product 2 is available at store 2.

:::image type="content" source="./media/Managing-assortments-figure1.png" alt-text="Screenshot of assortment configuration showing each product available at one store.":::

To make product 2 available at store 1, add the product to assortment 1.

:::image type="content" source="./media/Managing-assortments-figure2.png" alt-text="Screenshot of product 2 added to assortment 1.":::

Alternatively, add store 1 to assortment 2.

:::image type="content" source="./media/Managing-assortments-figure3.png" alt-text="Screenshot of store 1 added to assortment 2.":::

### Organization hierarchies

When multiple channels share the same product assortments, configure the assortments by using the Commerce assortment organization hierarchy. When you add nodes from this hierarchy, you include all channels in that node and its child nodes.

:::image type="content" source="./media/Managing-assortments-figure4.png" alt-text="Screenshot of organization hierarchy for assortment management.":::

### Product categories

Similarly, on the product side, include groups of products by using product category hierarchies. Configure assortments by including one or more category hierarchy nodes. In this case, the assortment includes all products in that category node and its child nodes.

:::image type="content" source="./media/Managing-assortments-figure5.png" alt-text="Screenshot of product categories in assortment configuration.":::

### Excluded products or categories

In addition to including products and categories in assortments, use the **Exclude** option to define specific products or categories that you want to exclude from assortments. In the following example, you want to include all the products in a specific category, except product 2. You don't need to define the assortment product by product or create additional category nodes. Instead, just include the category but exclude the product.

> [!NOTE]
> If a product is both included and excluded in one or more assortments by definition, the product is always considered to be excluded.

:::image type="content" source="./media/Managing-assortments-figure6.png" alt-text="Screenshot of excluded product configuration in assortment.":::

### Global and released products

Define assortments at a global level. They can contain channels from multiple legal entities. Share the products and categories that you include in assortments across legal entities. However, a product must be released before it can actually be sold, ordered, counted, or received in the channel (for example, in the point of sale (POS)). Although two stores in different legal entities can share an assortment that contains the same products, the products are only available if they're released to those legal entities.

### Dynamic and static assortments

You can define assortments by using specific channels and products or by including organization units and categories. Assortments that include references to these groups are dynamic assortments. If the definition or contents of those groups change while the assortment is active, the definition of the assortment also changes.

For example, you define and publish an assortment that references a category of products. If you later add products to the category, those products are automatically included in the definition of the existing assortment. You don't have to manually add the products to the assortment. Similarly, if you add an organization unit to a different node, the organization unit's assortment is automatically adjusted based on that definition.

### Stopped products

You can stop released products for the sales process by turning on a setting in the **Default order** settings. Enable this setting when a product is at the end of its life and shouldn't be sold through any channel. Assortments respect this setting. If you stop a product in all legal entities to which it's released, it isn't assorted, regardless of the assortment configuration.

### Blocked products

In addition to stopping sales of a product, you can temporarily block sales of a product. You can configure this setting on the **Commerce** tab of a released product. Blocked products are still assorted, but you receive a message in the POS that states that the product can't be sold.

### Date effectivity

Assortments are date-effective so that retailers can configure when products should or shouldn't be available per channel. You can specify the start and end dates when you define and publish assortments ahead of time. The affected products automatically become available or unavailable during the specified date ranges.

### Process assortments batch job

You must process assortments that you define in Commerce before they take effect. Process these assortments for the following reasons:

- Assortment definitions must be denormalized so that channels can more easily consume them. A product mix for a channel can be defined through multiple assortments that span various date ranges. When some of this information is calculated ahead of time on the server, performance at the channel is improved.
- The products and channels in the assortment can change outside the assortment itself. Dynamic assortments that contain references to categories or organization units must be processed periodically so that they include or exclude records, based on their current assignment.

## Implementation considerations

Consider the following implementation requirements as you plan and manage assortments for your Commerce implementation:

- **Data replication and database size** – Although assortments help you manage product availability, they're also an important tool for managing the size of channel and offline databases. Well-managed assortments reduce the amount of data that must be processed and replicated to channel and offline databases. They also reduce the number of records that must be persisted. Having fewer records in channel and offline databases improves performance when you add items to a transaction, search, and browse for products.
- **Date-effective/expiring assortments** – One of the most effective tools for managing the number of products in channel and offline databases is the date effectivity of assortments. If you leave open-ended (nonexpiring) assortments for seasonal products or products that are at the end of their life, these databases grow indefinitely. You can use various approaches to help manage this situation. For example, you can maintain separate assortments for seasonal products and products that are always available.
- **Sales and returns outside assortments** – This capability helps retailers effectively manage their assortments by letting them limit the number of available products to products that belong to the core product mix for the store. This capability also helps retailers handle situations where a product is mistakenly omitted from an assortment, or where a product is returned outside the effective dates for the assortment.

If product data doesn't exist in the channel database, the POS makes real-time calls to headquarters to retrieve the required information, so that the product can be sold, returned, or put on a customer order. Product information that is retrieved in this manner is available only during the scope of that transaction. The product isn't added to the assortment definition. Therefore, subsequent real-time calls are made as required.

> [!NOTE]
> When POS makes real-time calls to headquarters to retrieve product information to download to the channel database, depending on the data size of product information such as the number of product variants, product attributes, and inventory dimensions, you might experience performance problems during real-time calls or when saving the data to the channel database. These performance problems can lead to Commerce Scale Unit (CSU) API failures. To avoid performance problems related to real-time calls, add products with large amounts of product information data to the channel's assortment.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
