---
title: Release product structures
description: Learn how you can release complete product structures in addition to releasing products together with their engineering versions.
author: sgmsft
ms.author: shwgarg
ms.topic: article
ms.date: 05/21/2026
ms.custom:
ms.reviewer: kamaybac
ms.search.form: EngChgProductReleaseSiteBulkEdit, EngChgProductReleaseSendListPage, EngChgProductReleaseSendDetails,EngChgProductReleaseSelection,EngChgProductReleaseReceiveListPage, EngChgProductReleaseReceiveDetails, EngChgProductReleasePreviewPane, EngChgProductReleasePolicy, EngChgProductReleasePart, EngChgProductReleaseNote
---

# Release product structures

[!include [banner](../includes/banner.md)]

To ensure that engineering-relevant product data can be easily reused in different legal entities, release complete product structures in addition to releasing products together with their engineering versions. You can release multilevel bill of materials (BOM) structures together with the parent in a single release action. In this case, the BOM and the lower-level products are also released.

Engineering companies create and maintain engineering products to meet quality requirements as they're designed. Each operational company that manufactures a product needs the same product and underlying BOM. Depending on the production facility, you might create the route locally. In this case, you don't release a route together with the product. For legal entities that sell the products but don't manufacture them, the BOM might not be required.

To make the process more efficient, all engineering-relevant data can be released to other operational companies at the same time. This data includes the product structure. During the release process, you can choose which part of the product data to release.

For more information about engineering companies and operational companies, see [Engineering companies and data ownership rules](engineering-org-data-ownership-rules.md).

You can release both standard products and engineering products together with the release product structure. During this process, the whole product structure is released, even the BOM and route from the company that the products are being released in.

For an example of how to release a product, see [Release an engineering product to a local company](engineering-scenarios.md#release).

## Released data for a product when the release product structure is used

The release of engineering products includes the following data:

- **Product data** – A new released product is created.
- **Engineering version data** – The engineering version and its data are created or updated. If you release the same engineering version again to an operational company, the engineering data is overwritten.
- **Engineering attributes** – The engineering attributes and their values are created or updated.
- **Engineering bill of materials** – The engineering BOM and its lines can be created or updated. For more information about data ownership, see [Product owners](product-owner.md).
- **Engineering routes** – The engineering routes and their operations can be created or updated. For more information about data ownership, see [Product owners](product-owner.md).
- **Engineering documents** – The engineering documents that are connected to the engineering version are created or updated.

When you turn on engineering change management on your system, the release product structure is available. In addition, standard products include their BOMs and routes when they're released.

## Product acceptance

**Product acceptance** is a key parameter that influences the release process. Set this parameter for each company by going to **Engineering change management > Setup > Engineering change management parameters**. For more information, see [Engineering change management parameters](engineering-parameters.md).

### Automatic product acceptance

Each release of engineering products starts when someone from the engineering company selects a product to release. When the **Product acceptance** parameter is set to *Automatic*, the user at the engineering company decides which product data to automatically release to the operational companies. The product is then automatically released to the companies that the user selects in the release wizard.

### Manual product acceptance

Each release of engineering products starts when someone from the engineering company selects a product to release. When the **Product acceptance** parameter is set to *Manual*, the user at the engineering company decides which product data to release to the operational companies. A user from each operational company then reviews the product data and decides whether to accept the release. The user at the operational company can set the following options when the data is received:

- If the products (updates) aren't relevant for the operational company, the user can choose not to accept the release.
- The user can change the item template for new products.
- The user can choose whether the product should be released together with their BOMs and/or routes, and whether they should be released as approved and active.
- The user can change the effective-from dates of the products.

For an example of how to accept a product, see [Review and accept the product before you release it in the local company](engineering-scenarios.md#accept).

> [!NOTE]
> For standard products, you can release from any legal entity to any other legal entity. For engineering products, the only legal entity that you can release from is the engineering company.

## Release policies

Not all operational companies need the same product data. In general, operational companies that manufacture engineering products require a BOM, whereas operational companies that only sell engineering products don't require a BOM. Use release policies to establish the parameters that are used for the release of products.

For more information about engineering product categories, see [Engineering versions and engineering product categories](engineering-versions-product-category.md).

During the release process, you can influence the settings.

## Create and manage product release policies

To work with product release policies, go to **Engineering change management > Setup > product release policies**. Then follow one of these steps.

- To create a new policy, select **New** on the Action Pane, and then set the fields as described in the following subsections.
- To edit an existing policy, select it in the list pane, select **Edit** on the Action Pane, and then set the fields as described in the following subsections.
- To delete an existing policy, select it in the list pane, select **Edit** on the Action Pane, and then, on the **General** FastTab, make sure that the **Active** option is set to *No*. Then select **Delete** on the Action Pane.

### Header

Set the following fields on the header of a product release policy.

| Field | Description |
|---|---|
| Name | Enter a name for the policy. |
| Description | Enter a description of the policy. |

### General FastTab

Set the following fields on the **General** FastTab of a product release policy.

| Field | Description |
|---|---|
| Product type | Select whether the policy applies to products of the *Item* or *Service* type. You can't change this setting after you save the record. |
| Production type | This field appears only when you enable [formula change management](manage-formula-changes.md) in your system. Select the type of production that this release policy applies to:<ul><li>**Co-product** – Use this release policy to manage co-products. Co-products are produced during process manufacturing, and aren't versioned or engineering products. Release policies for co-products can help ensure that important settings, such as **Storage dimension group** and **Tracking dimension group**, are set up by using a Released product template before they're released to a company.</li><li>**By-product** – Use this release policy to manage by-products. By-products are produced during process manufacturing, and aren't versioned or engineering products. Release policies for by-products can help ensure that important settings, such as **Storage dimension group** and **Tracking dimension group**, are set up by using a Released product template before they're released to a company.</li><li>**None** – Use this policy to manage standard products that aren't versioned or engineering products, or co-products or by-products.</li><li>**Planning item** – Use this release policy to manage planning items that are produced by using process manufacturing. Planning items use formulas. They resemble formula items, but they're used to produce only co-products and by-products, not finished products.</li><li>**BOM** – Use this release policy to manage engineering products, which don't use formulas and typically (but not necessarily) include BOMs.</li><li>**Formula** – Use this release policy to manage finished items that are produced by using process manufacturing. These items have a formula but not a BOM.</li></ul> |
| Apply templates | Select one of the following options to specify whether and how product release templates should be applied when the policy is used:<ul><li>**Always** – Always use a template released product for releases. If you select this option, use the **All products** FastTab to specify the template that is used for each company that you release to. If you don't specify a template for each company that is listed on the **All products** FastTab, you receive an error when you try to save the policy.</li><li>**Optional** – If a template released product is specified for a company that is listed on the **All products** FastTab, that template is used when you release to that company. Otherwise, no template is used. If you select this option, you can save the policy without assigning templates to all companies. (No warning is shown.)</li><li>**Never** – No template released product is used for any companies that you release to, even if a template is specified for companies that are listed on **All products** FastTab. The template columns are unavailable.</li></ul> |
| Active | Use this option to help maintain your release policies. Set it to *Yes* for all release policies that you use. Set it to *No* to mark a release policy as inactive when it isn't used. You can't deactivate a release policy that is assigned to an engineering product category, and you can delete only inactive release policies. |

### All products FastTab

On the **All products** FastTab, add a row for each operational company that you want to use this policy to release to. Use the buttons on the **All products** FastTab to add and remove rows as needed. For each row that you add, set the following fields.

> [!NOTE]
> The settings on the **All products** FastTab apply to both engineering products and standard products.

| Field | Description |
|---|---|
| Company accounts ID | Select the company that the row applies to. The parameters on the row apply when products are released to this company. |
| Template released product | Add a template for the product. |
| Copy BOM approval | Select this check box to copy the BOM approval status to the receiving company. |
| Copy BOM activation | Select this check box to copy the BOM activation status to the receiving company. |
| Copy route approval | Select this check box to copy the route approval status to the receiving company.|
| Copy route activation | Select this check box to copy the route activation status to the receiving company. |

### Option parameters for engineering products FastTab

Every time you add a row on the **All products** FastTab, a row that has a matching **Company accounts ID** value is also created on the **Option parameters for engineering products** FastTab. If you remove a row from the **All products** FastTab, the row that has a matching **Company accounts ID** value is also removed from the **Option parameters for engineering products** FastTab.

For each row shown on the **Option parameters for engineering products** FastTab, set the following fields.

> [!NOTE]
> The settings on the **Option parameters for engineering products** FastTab apply only to engineering products.

| Field | Description |
|---|---|
| Template BOM | When a product that has a BOM is released, the lines of the specified template BOM are added. This field is useful for adding local components, such as packaging or instructions in the local language. |
| Template route | When a product that has a route is released, the lines of the specified template are added. |
| Copy effectivity | Select whether to copy effectivity dates from the engineering company to the operational company when you release products. |
| Automatically add to release proposal | Select this check box for products that should automatically be released on the engineering change order. In this way, products that belong to engineering product categories that use this release policy can automatically be released to operational companies where this option is set up. (Learn more in [Manage changes to engineering products](engineering-change-management.md).) |

### Review each product when you release it

When engineering products that have BOMs or routes are released, the parameters default to values indicated in the release policy. As a user, you can influence this behavior on the releasing side when you use the release product structure.

To release engineering products, on the **Released products** page, select the products to release, and then select **Release product structure** to open the release wizard. The **Select engineering products to release** page shows the products. Select a single product, and then select **Release details** to review the release details for the product.

On the **Release details** page, you can change the value of the **Receive BOM**, **Copy BOM approval**, **Copy BOM activation**, **Receive BOM**, **Copy route approval**, and **Copy route activation** fields. In the push-pull scenario, you can change the value of the same fields on the receiving side, provided that the BOM and route are released.

## Product owners and product releases

Because product owners know which legal entities need their products, only members of a product's product owner group can release that product. Other users can't release products that they don't own.

This behavior applies only when a product is directly selected for release. Non-owner users *can* release products that are part of another product's structure via a BOM when they release the parent product, provided that they own the parent product.

For example, product X is assigned to the *Design cabinets* product owner group. Product X is also part of the BOM of product Y, which is assigned to the *Design speakers* product owner group. If a user from the *Design speakers* product owner group releases product Y and its BOM, product X is released together with product Y.

Learn more in [Product owners](product-owner.md).

## Release multiple BOMs/formulas

In older versions of Supply Chain Management, when you release a product, only the first active BOM or formula (as of the date of release) is released. If there are no active BOMs or formulas, the engineering version isn't released.

Starting in Supply Chain Management version 10.0.34, you can release multiple BOMs or formulas. To enable this new functionality, use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to enable the *Release multiple BOMs/formulas for Engineering Change Management* feature. As of Supply Chain Management version 10.0.43, this feature is mandatory and can't be turned off.

When the *Release multiple BOMs/formulas for Engineering Change Management* feature is enabled, all BOMs or formulas that are active for a product are released when you release the product. This functionality can be relevant, for example, if you have multiple active formulas that apply for various from quantities. You can view the different BOMs or formulas and their respective routes on the BOM designer when releasing on the **Release product structure** page and when reviewing the release on **Open product releases** page.

## A product template is required for release

The release policy for the company where a product is to be released must have a product template assigned. This requirement exists because some fields in the local company (such as item model group) are required to create a BOM, and many of these fields are company specific. These field values are copied to the released product from the release template and can be updated as needed.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
