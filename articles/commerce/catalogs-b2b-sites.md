---
title: Create Commerce catalogs for B2B sites
description: Learn how to create Commerce catalogs for Microsoft Dynamics 365 Commerce business-to-business (B2B) sites.
author: ashishmsft
ms.date: 01/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2022-02-28
ms.custom: 
  - bap-template
---

# Create Commerce catalogs for B2B sites

[!include [banner](includes/banner.md)]

This article describes how to create Commerce product catalogs for Microsoft Dynamics 365 Commerce business-to-business (B2B) sites. For answers to frequently asked questions about Commerce catalogs for B2B sites, see [Commerce catalogs for B2B FAQ](catalogs-b2b-sites-FAQ.md).

> [!NOTE]
> This article applies to Dynamics 365 Commerce version 10.0.27 and later releases.

Use Commerce catalogs to identify the products that you want to offer in your B2B online stores. When you create a catalog, you identify the online stores that the products are offered in, add the products that you want to include, and enhance the product offerings by adding merchandising details. You can create multiple catalogs for each B2B online store, as shown in the following illustration.

:::image type="content" source="./media/Commerce_Catalogs.png" alt-text="Screenshot of Commerce product catalogs preview.":::

Commerce product catalogs let you define the following information:

- **Catalog type** – Configure the value as **B2B**. You can define B2B catalog-specific properties such as a navigation hierarchy, a customer hierarchy, and attribute metadata for the catalog.
- **Catalog-specific navigation hierarchy** – Organizations can create a distinct category structure for their specific catalog.
- **Catalog-specific attribute metadata** – Attributes contain details about a product. By assigning attributes to a category of the navigation hierarchy, you can define values for those attributes at the level of products that are assigned to that category. Organizations can then complete these tasks:

  - Define catalog-specific attribute values.
  - Control the visibility of attributes at the catalog level.
  - Select the refiners that are specific to an individual catalog.

- **Channels** – Organizations can associate more than one B2B online channel with a catalog. End-to-end support for catalogs is currently available only for B2B online stores.
- **Customer hierarchies** – For a given B2B channel, organizations can make a specific catalog available to selected B2B partners by associating customer hierarchies with that catalog.
- **Price groups** – You can configure prices and promotions that are specific to a given catalog. This capability is a core reason for defining a catalog for a B2B channel. Price groups for catalogs enable organizations to make products available to their intended B2B organizations and apply their preferred pricing and discounts. B2B customers who order from a configured catalog can benefit from special prices and promotions after they sign in to a Commerce B2B site. To configure catalog-specific prices, select **Price groups** on the **Catalogs** tab to link one or more price groups to the catalog. All trade agreements, price adjustment journals, and advanced discounts that are linked to the same price group are applied when customers order from that catalog. (Advanced discounts include threshold, quantity, and mix and match discounts.) For more information about price groups, see [Price groups](price-management.md#price-groups).

> [!NOTE]
>
> - The **Enable use of multiple catalogs on retails channels** feature is available starting with the Commerce version 10.0.27 release. To configure catalog-specific configurations such as navigation hierarchy and customer hierarchy in Commerce headquarters, go to the **Feature management** workspace (**System administration \> Workspaces \> Feature management**), enable the **Enable use of multiple catalogs on retails channels** feature, and then run the **1110 CDX** job.
> - When you enable this feature, all the existing catalogs that are used for POS stores or a call center are marked as **Catalog type = B2C** on the **Catalogs** page. Only existing and new catalogs that are marked as **Catalog type = B2C** are applicable to POS stores and a call center.
> - After you enable this feature, associate at least one catalog with every B2B partner organization (customer hierarchy). Otherwise, even successfully onboarded and signed-in B2B partner site visitors aren't able to find any categories or products, and they see the message "No catalogs found, please contact system administrator."

## B2B catalog process flow

The process of creating and processing a catalog has four general steps. Each step is explained in detail in the next section.

> [!NOTE]
> Before you proceed, ensure that the catalog is marked as **Catalog type = B2B**.

1. **[Configuration](#configure-the-catalog)**

    - Associate the navigation hierarchy.
    - Specify time-effective and expiration dates, if they're applicable.
    - Add and categorize products.
    - Associate price groups.
    - Associate a customer hierarchy that's specific to your B2B organizations.
    - Associate default dimension attribute group for refiners such as size, style, and color.
    - Set attribute metadata.

1. **[Validation](#validate-the-catalog)** – In this step, run validation rules that enforce specific behavior. Here are some examples:

    - Ensure that there are no uncategorized products.
    - Ensure that all the items that are assorted to each channel are associated with a catalog.

1. **[Approval](#approve-the-catalog)**
1. **[Publishing](#publish-the-catalog)**

## Set up the catalog

Use the information in this section to set up your catalog.

### Configure the catalog

In Commerce headquarters, go to **Retail and Commerce \> Catalogs and assortments \> All catalogs** to configure your catalog.

When you create a new catalog, you must first associate it with one or more channels. You can only use items that are linked to your selected channel [assortments](/dynamics365/unified-operations/retail/assortments) when you create the catalog. To associate the catalog with one or more channels, select **Add** on the **Commerce channels** FastTab of the **Catalog setup** page. Ensure that the catalog is marked as **Catalog type = B2B**.

#### Associate the navigation hierarchy

To add products to a catalog, you must select a navigation hierarchy. The navigation hierarchy supports the category structure for the catalog. You must select one of the navigation hierarchies that are associated with the channels that you selected on the **Commerce channels** FastTab of the **Catalog setup** page. To associate a default navigation hierarchy with each of your channels, go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.

#### Specify time-effective and expiration dates

To specify time-effective and expiration dates for a catalog, select the top node of the catalog hierarchy to return to the main catalog header view. Then, on the **General** FastTab, configure effective and expiration dates as required.

#### Add and categorize products

To configure products to add to the catalog, in Commerce headquarters, go to **Retail and Commerce \> Catalogs and assortments \> All catalogs**. Then, on the **Catalogs** tab, select **Add products**.

Alternatively, select a node in the navigation hierarchy. You can then add products directly to a category in the catalog.

#### Associate price groups

To configure products to add to the catalog, in Commerce headquarters, go to **Retail and Commerce \> Catalogs and assortments \> All catalogs**. Then, on the **Catalogs** tab, select **Add products**.

Products that you add to a catalog from the root node of the navigation hierarchy by selecting **Add products** on the Action Pane inherit their categories if the source navigation hierarchy is also associated with the catalog. Changes to categories that you make on the source navigation hierarchy immediately reflect in the catalogs. You must republish the catalogs to update the channels.

Alternatively, you can select a node in the navigation hierarchy and add products directly to a selected category in the catalog.

When you add products, the **Automatically include all variants when only product master is selected** option is available. To prevent the inclusion of all variants, select at least one variant for the product master.

> [!NOTE]
> If you choose to automatically include all variants in a large product masters selection, you might experience longer processing times. For large selections, we recommend that you select **Include all variants** on the Action Pane of the catalogs page to run the operation in batch mode. If you included only the product master in the catalog and didn't include any variants, the variant picker might not be available when you navigate to a product details page.

To configure catalog-specific prices, you must link one or more price groups to the catalog. To associate price groups with a catalog, in Commerce headquarters, go to **Retail and Commerce \> Catalogs and assortments \> All catalogs**. Then, on the **Catalogs** tab, under **Pricing**, select **Price groups**. All trade agreements, price adjustment journals, and advanced discounts (threshold, quantity, and mix and match discounts) that are linked to the same price group apply when customers order from the catalog.

For more information about price groups, see [Price groups](price-management.md#price-groups).

> [!NOTE]
> You can't create a new price group from the **All catalogs** page. Instead, create it from the **All price groups** page. Then associate it with the catalog on the **All catalogs** page.

#### Associate a customer hierarchy

To associate customer hierarchies, in Commerce headquarters, go to **Retail and Commerce \> Catalogs and assortments \> All catalogs**. Then, on the **Catalogs** tab, under **Customer hierarchy**, select **Assign hierarchies** to link one or more customer hierarchies to the catalog.

> [!NOTE]
> You can't create a new customer hierarchy from the **All catalogs** page. Instead, create it from the **Customer hierarchies** page. Then associate it with the catalog on the **All catalogs** page.

#### Associate default dimension attribute group for refiners such as size, style, and color

To associate a default dimension attribute group for refiners such as size, style, and color, in Commerce headquarters, go to **Retail and Commerce \> Catalogs and assortments \> All catalogs**. Then, on the **Catalogs** tab, under **Attributes**, select **Attribute groups**.

#### Set attribute metadata

To configure attribute metadata, in Commerce headquarters, go to **Retail and Commerce \> Catalogs and assortments \> All catalogs**. Then, on the **Catalogs** tab, under **Attributes**, select **Set attribute metadata**. To select the attributes that should be viewable and refinable, select a category in the associated catalog-specific navigation hierarchy, and then, under **Catalog product attributes**, select an attribute. Then select **Show attribute on channel**. By default, all viewable attributes are also searchable. To optionally make attributes refinable, select **Can be refined**.

### Validate the catalog

Before you can use a new catalog, you must validate and publish it.

To validate a catalog, follow these steps:

1. On the **Catalogs** tab of the **All catalogs** page, under **Validate**, select **Validate catalog** to run a validation. This step is required. It validates that the required setup is accurate.
1. Select **View results** to view the details of the validation. If errors are found, correct the data and then run the validation again until it passes.

> [!NOTE]
> If **Catalog type = B2B**, validation fails if you add POS stores or a call center to the catalog. B2B catalogs must have only B2B online channels associated with them. Validation also fails if no customer hierarchy is associated with a B2B catalog.

### Approve the catalog

After you validate a catalog, you must approve it.

To start the catalog approval workflow, follow these steps:

1. On the action pane of the **All catalogs** page, select **Workflow \> Submit**.
1. Go to **Retail and Commerce \> Headquarters setup \> Commerce workflows** to configure the steps and authorized users for the workflow. The workflow defines the steps that are required to get the catalog into an **Approved** status.

### Publish the catalog

After a catalog is in an **Approved** status, you can publish it by selecting **Publish** on the **Catalogs** menu. After the catalog is in a **Published** state, you can use it in call center order entry and send catalog processes. You can publish a catalog either manually or by using a batch process. The effective date that you define for the catalog determines when the products are available in the online store. The expiration date that you define determines when the products are removed from the online store.

> [!NOTE]
> You can publish a catalog that contains products that have warnings. However, those products don't appear in the online store.

## Additional resources

[Extensibility impact of Commerce catalogs for B2B customizations](dev-itpro/catalogs-b2b-sites-dev.md)

[Commerce catalogs for B2B FAQ](catalogs-b2b-sites-FAQ.md)

[Catalog picker module](catalog-picker.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
