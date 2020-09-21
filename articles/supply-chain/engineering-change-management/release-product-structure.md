---
# required metadata

title: Release product structure
description: To ensure that engineering relevant data of products can easily be reused in different legal entities, you can release complete product structures in addition to releasing products with their engineering versions. This means that you can release multi-level bill of material structures together with the parent in a single release action.
author: t-benebo
manager: tfehr
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: EngChgProductReleaseSiteBulkEdit, EngChgProductReleaseSendListPage, EngChgProductReleaseSendDetails,EngChgProductReleaseSelection,EngChgProductReleaseReceiveListPage, EngChgProductReleaseReceiveDetails, EngChgProductReleasePreviewPane, EngChgProductReleasePolicy, EngChgProductReleasePart, EngChgProductReleaseNote
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Release 10.0.13
---

# Release product structure

[!include [banner](../includes/banner.md)]

To ensure that engineering relevant data of products can easily be reused in different legal entities, you can release complete product structures in addition to releasing products with their engineering versions. This means that you can release multi-level bill of materials structures together with the parent in a single release action. The bill of materials (BOM) and the lower-level products are also released in this case.

Engineering products are created and maintained by their engineering company in such way that they meet the quality requirements as they are designed. Each operational company that manufactures the product needs the same product and underlying BOM. Depending on the production facility, the route might be created locally, in which case you wouldn't release a route with it. For legal entities that won't manufacture the products, but only sell them, the BOM may not be required.

To make process more efficient, the engineering relevant data, including the product structure, can be released all at once to other operational companies. In this release process, you can make choices which part of the product data will be released. For more information on the engineering company and operational company, see [Engineering companies and data ownership rules](engineering-org-data-ownership-rules.md).

Note that you can release both standard products and engineering products with the release product structure. When doing so, the whole product structure will be released, including the BOM and route from the company where they are being released.

<!-- KFM: Add a link somewhere here to the demo script for how to release a product (when we've converted the demo). -->

## Released data for a product when using the release product structure

The following data are part of releasing engineering products:

- **Product data** - A new released product is created.
- **Engineering version data** - The engineering version and its data are created or updated. Note that if you release the same engineering version again to an operational company, the engineering data will be overwritten.
- **Engineering attributes** - The engineering attributes and their values are created or updated.
- **Engineering bill of materials** - The engineering BOM and its lines can be created or updated. Information about how to set this option is given later in this topic. For more information on data ownership, see [Product owner](product-owner.md).
- **Engineering routes** - The engineering routes and their operations can be created or updated. Information about how to set this option is given later in this topic. For more information on data ownership, see [Product owner](product-owner.md).
- **Engineering documents** - The engineering documents connected to the engineering version are created or updated.

When you enable engineering change management on your system, then the release product structure is available, and standard products will also include their BOMs and routes when released.

## Product acceptance

**Product acceptance** is a key parameter that influences the release process. You can set this per-company by going to **Engineering change management \> Setup \> Engineering change management parameters**. See also [Engineering change management parameters](engineering-parameters.md).

### When "Product acceptance" is set to Automatic

Each release of engineering product starts when somebody from the engineering company selects a product to release. When **Product acceptance** is set to *Automatic*, the user at the engineering company decides which product data to include (automatically release) for the operational company(s). The product will be automatically released to the company selected in the release wizard.

### When "Product acceptance" is set to Manual

Each release of engineering product starts when somebody from the engineering company selects a product to release. When **Product acceptance** is set to *Manual*, the user at the engineering company decides which product data is released to the operational company(s). A user from the operational company(s) reviews the products data and decides whether to accept the release or not. The user at the operational company can set the following options when they receive the data:

- If the product (updates) are not relevant for the operational company, the user can choose to not accept the release.
- The user can change the item template for new products.
- The user can choose whether the product should be released with BOM and/or routes and if they should be released approved and active.
- The user can change the effective-from dates of the products.

<!-- KFM: Add a link somewhere here to the demo script for how to accept a product (when we've converted the demo). -->

> [!NOTE]
> For standard products, you can release from any legal entity to any other legal entity. For engineering products, you can only release from the engineering company legal entity.

## Release policies

Not all operational companies need the same product data. operational companies that manufactures engineering products require a BOM, while operational company that only sell the engineering products don't need the BOM. While this scenario can be different for different types of products, you can use release policies to establish the parameters used for the release of products.

For engineering products the release policy is assigned in the engineering product category (mandatory field), and for standard products it is assigned to the shared product (optional).

For more information on the engineering product categories, see [Engineering versions and engineering product categories](engineering-versions-product-category.md)

During the release process, you can influence the settings as well.

## Create and manage product release policies

To work with product release policies, go to **Engineering change management \> Setup \> product release policies**. Then do one of the following:

- To create a new policy, select **New** from the Action Pane and then make settings as described in the following subsections.
- To edit an existing policy, select it from the list pane, select **Edit** on the Action Pane, and then make settings as described in the following subsections.
- To delete an existing policy, select it from the list pane. Select **Edit** on the Action Pane and, on the **General** FastTab, set **Active** to *No* if it isn't already. Then select **Delete** on the Action Pane.

### Settings in the header

Make the following settings in the header of a product release policy:

| Setting | Description |
| --- | --- |
| **Name** | Enter a name for the policy. |
| **Description** | Enter a description of the policy. |

### The General FastTab

The following table describes the settings available on **General** FastTab of a product release policy.

| Setting | Description |
| --- | --- |
| **Product type** |  Select whether the policy will apply to products of type *Item* or *Service*. You can't change this setting after saving the record. |
| **Apply templates** | Choose one of the following options to establish whether and how product release templates should be applied when using this policy:<ul><li>**Always** - A template released product must always be used for releasing. Use the **All products** FastTab to establish the template to use for each company that you release to. When you use this option, you must set a template for each company listed on the **All products** FastTab (otherwise, an error will be shown when you try to save the policy). </li><li>**Optional** - If a company listed on **All products** FastTab has a template released product set, then that template will be used when releasing to that company. Otherwise, no template will be used. When you use this option, then you will be able to save the policy without assigning templates to all companies (no warning is shown). </li><li>**Never** - No template released product will be used for any companies, even if a template is set in the listed on **All products** FastTab. The template columns are disabled.</li></ul> |
| **Active** | Use this setting to help maintain your release policies. Set this to *Yes* for all release policies that you use; set it to *No* to mark a release policy as inactive when it is not used. Note that you can't deactivate a release policy that is assigned to an engineering product category, and you can only delete inactive release policies. |

### The All products FastTab

Add a row on the **All products** FastTab for each operational company that you will release to using this policy. Use the buttons on the **All products** toolbar to add and remove rows as needed. For each row you add, make the settings described in the following table.

These settings apply for both engineering products and standard products.

| Setting | Description |
| --- | --- |
| **Company accounts ID** | Select the company that the line applies for. The parameters on the line will apply when products are released to this company. |
| **Template released product** | Adds a template for the product <!-- KFM: We should describe what affect this has. (Note from original doc: need to add which are the fields in the template released product here – need a developer to take a look at this) --> |
| **Copy BOM approval** | Select this check box to copy bill of materials approval status to the receiving company. |
| **Copy BOM activation** | Select this check box to copy the bill of materials activation status to the receiving company. |
| **Copy route approval** | Select this check box to copy route approval status to the receiving company.|
| **Copy route activation** | Select this check box to copy the route activation status to the receiving company. |

### The Option parameters for engineering products FastTab

Each time you add (or remove) a row to the **All products** FastTab, a row with a matching **Company accounts ID** values is also created (or removed) on the **Option parameters for engineering products** FastTab. For each row shown here, make the settings described in the following table.

These settings only apply to engineering products.

| Setting | Description |
| --- | --- |
| **Template BOM** | When a product with a BOM is released, the lines of this template BOM will be added. This is useful for adding local components, such as packaging or instructions in the local language.  |
| **Template route** | When a product is released with a route, the lines of this template will be added. |
| **Copy effectivity** | Choose whether to copy effectivity dates from the engineering company to the operational company when releasing. |
| **Automatically add to release proposal** | Select this check box for products that should be released automatically on the engineering change order. Products belonging to engineering product categories that use this release policy can therefore be released automatically to operational company where this option is set. You can do this as part of the workflow on the engineering change order (see also [Engineering change management](engineering-change-management.md)).

### Review each product when releasing

When engineering products with BOMs or routes are released, the parameters will be defaulted as indicated in the release policy. As a user, you can influence this on the releasing side when using the release product structure.

To release an  engineering product, select the product(s) you would like to release from the **Released products** page and select **Release product structure** to open a release wizard. The **Select engineering products to release** page shows the product(s). Select a single product and select **Release details** to review the release details for the product.

In the **Release details** page. the fields **Receive BOM**, **Copy BOM approval**, **Copy BOM activation**, **Receive BOM**, **Copy route approval** and **Copy route activation** can be changed. In the push-pull scenario, you can change the same fields on the receiving side (provided the bill of material and route are released).

## Product owners and releasing products

Because product owners know which legal entities need their products, a product can only be released by the members of that product's owner group. Other users won't be able to release products they don't own.

This behavior only applies when directly selecting a product for release. Products that are part of another product's structure via a bill of materials *can* be released by non-owner users when they release the parent product (provided they owners of the parent product).

For example: product X is assigned to product owner group *Design cabinets*. Product X is also part of the bill of material of product Y, which is assigned to product owner group *Design speakers*. If a user from product owner group *Design speakers* releases product Y and its bill of materials, product X will be released along with it.

For more information, see [Product owner](product-owner.md).
