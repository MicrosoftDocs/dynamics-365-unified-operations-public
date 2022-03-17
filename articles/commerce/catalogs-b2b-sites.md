---
  
# required metadata

title: Create Commerce catalogs for B2B sites
description: This topic describes how to create Commerce catalogs for Microsoft Dynamics 365 Commerce business-to-business (B2B) sites.
author: ashishmsft
ms.date: 03/17/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2022-02-28
---

# Create Commerce catalogs for B2B sites 

[!include [banner](includes/banner.md)]

This topic describes how to create Commerce catalogs for Microsoft Dynamics 365 Commerce business-to-business (B2B) sites. For answers to frequently asked questions regarding Commerce catalogs for B2B sites, see [Commerce catalogs for B2B FAQ](catalogs-b2b-sites-FAQ.md).

> [!NOTE]
> This topic applies to Dynamics 365 Commerce version 10.0.26 and later releases.

You can use Commerce product catalogs to identify the products that you want to offer in your B2B online stores. When you create a catalog, you identify the online stores that the products are offered in, add the products that you want to include, and enhance the product offerings by adding merchandising details. You can create multiple catalogs for a B2B online store.

Commerce product catalogs allow you to define the following:

- **Catalog-specific navigation hierarchy** - Allows organizations to create a distinct category structure for their specific catalog.
- **Catalog-specific attribute metadata** - Attributes contain details about a product. You can assign attributes to a category of navigation hierarchy to define values for those attributes at product level that are assigned to that category. Organizations will then be able to:
    - Define catalog-specific attribute values.
    - Control the visibility of attributes at the catalog level. 
    - Choose the refiners specific to an individual catalog.
- **Channels** - Organizations are able to associate more than one B2B online channel with a catalog. End-to-end support for catalogs is currently only available for B2B online stores.  
- **Customer hierarchies** - For a given B2B channel, organizations can choose to make a specific catalog available to their select B2B partners by associating customer hierarchies with a catalog. 
- **Price groups** - A core reason for defining a catalog to use with a B2B channel is to be able to configure specific prices and promotions for that catalog. B2B customers ordering from a configured catalog can benefit form special prices and promotions after signing in to a Commerce B2B site. To configure catalog-specific prices, select the **Price groups** on the **Catalogs** tab to link one or more price groups to the catalog. All trade agreements, price adjustment journals, and advanced discounts (such as threshold, quantity, mix and match) that have been linked to the same price group will be applied when customers order from this catalog.
    - Price groups for catalogs allow organizations to make products available to their intended B2B organizations with their preferred pricing and discounts. 
    - For more information on price groups, see [Price groups](price-management.md#price-groups).
  
> [!NOTE]
> This feature is available starting with the Dynamics 365 Commerce version 10.0.26 release. To configure catalog-specific configurations like navigation hierarchy and customer hierarchy in Commerce headquarters, in Commerce headquarters go to the Feature management workspace (**System administration \> Workspaces \> Feature management**), enable the **Enable use of multiple catalogs on retails channels.** feature, and then run the **1110 CDX** job. 

## Catalog process flow

Creating and processing a catalog is a four step process, as outlined in the following catalog process flow:

1. **[Configuration](#configure-the-catalog)** 
    - Associate navigation hierarchy.
    - Specify effective and expiration dates (if applicable).
    - Add and categorize products. 
    - Associate price groups.
    - Associate customer hierarchy (specific to your B2B organizations). 
    - Associate default dimension attribute group for refiners like size, style, color. 
    - Set attribute metadata.  
1. **[Validation](#validate-the-catalog)** - Runs validation rules that enforce behavior, such as: 
    - Ensure there are no uncategorized products. 
    - Ensure that all items assorted to each channel are associated with a catalog.
1. **[Approval](#approve-the-catalog)** 
1. **[Publishing](#publish-the-catalog)**

## Set up the catalog

Follow the steps below to set up your catalog.

### Configure the catalog

In Commerce headquarters, go to **Retail and Commerce \> Catalogs and assortments \> All catalogs** to configure your catalog.

When you create a new catalog, you must first associate the catalog with one or more channels. Only items linked to your selected channel [assortments](/dynamics365/unified-operations/retail/assortments) can be used when creating the catalog. This is done on the **Commerce channels** FastTab of the **Catalog setup** form. Select **Add** to associate one or more channels. 

#### Associate the navigation hierarchy

To add products to a catalog, a navigation hierarchy must first be chosen. The navigation hierarchy supports the category structure for the catalog. You must pick from one of the navigation hierarchies associated with the channels selected on the **Commerce channels** FastTab of the **Catalog** page. To associate a navigation hierarchy default with each of your channels, go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.

#### Specify time-effective and expiration dates

To specify time-effective and expiration dates for a catalog, select the top node of the catalog hierarchy to return to the main catalog header view, and then on the **General** FastTab configure effective and expiration dates as necessary.

#### Add and categorize products

To configure products to add to the catalog, on the **Catalogs** menu tab of the **Catalog setup** page select **Add products**. Alternatively, you can select a node in the navigation hierarchy, which will change the screen presentation and allow you to add products directly to a category within the catalog.

<!--NEED CATEGORIZATION STEPS-->

#### Associate price groups

<!--NEED INTRO, STEPS-->

For more information on price groups, see [Price groups](price-management.md#price-groups).

> [!NOTE]
> - You cannot create a new price group from the catalogs form. Instead you must create the new price group from the **All price groups** form and then be able to associate in this view.
> - You cannot create a new customer hierarchy from the catalogs form. Instead must create a new customer hierarchy from the **Customer hierarchies** form and then be able to associate in this view.

#### Associate customer hierarchy

<!--NEED INTRO, STEPS-->

#### Associate default dimension attribute group for refiners like size, style, color

Associate default dimension attribute group for refiners like size, style, color through attribute groups from top-ribbon. 

<!--NEED STEPS-->

#### Set attribute metadata

Choose which attributes are supposed to be viewable and refinable. By default, all viewable attributes are searchable as well.

<!--NEED STEPS-->

### Validate the catalog

Before a new catalog is available to use, it must be validated and published. 

To validate a catalog, follow these steps.

1. Select **Validate catalog** on the **Catalogs** menu to process a validation. This is required action and will validate that the required setup is accurate. 
1. Select **View results** to see the details of the validation. If errors are found, you must correct the data and run validation again until the validation has passed.

### Approve the catalog

After a catalog is validated, it must be approved. 

To start the catalog approval workflow, follow these steps.

1. Select **Workflow** on the menu. 
1. Select **Workflow \> Submit** to execute the process. 
1. Go to **Retail and Commerce \> Headquarters setup \> Commerce workflows** to configure the steps and authorized users for the workflow. The workflow will define the steps needed to get the catalog into an **Approved** status.

### Publish the catalog

When the catalog is in an **Approved** status, to publish the catalog select **Publish** option on the **Catalogs** menu. After the catalog is in a **Published** state, it can be used in call center order entry and send catalog processes. You can publish a catalog manually or by using a batch process. The effective date that you defined for the catalog determines when the products are available in the online store. The expiration date that you defined for the catalog determines when the products are removed from the online store.
 
> [!NOTE]
> You can publish a catalog that contains products that have warnings, but those products won't appear in the online store.

## Additional resources

[Commerce catalogs for B2B FAQ](catalogs-b2b-sites-FAQ.md)
