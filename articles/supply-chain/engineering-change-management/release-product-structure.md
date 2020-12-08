---
# required metadata

title: Release product structures
description: This topic explains how you can release complete product structures in addition to releasing products together with their engineering versions. In this way, you can ensure that engineering-relevant product data can easily be reused in different legal entities.
author: t-benebo
manager: tfehr
ms.date: 09/28/2020
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
ms.search.validFrom: 2020-09-28
ms.dyn365.ops.version: Release 10.0.15
---

# Release product structures

[!include [banner](../includes/banner.md)]

To ensure that engineering-relevant product data can easily be reused in different legal entities, you can release complete product structures in addition to releasing products together with their engineering versions. Therefore, you can release multilevel bill of materials (BOM) structures together with the parent in a single release action. In this case, the BOM and the lower-level products are also released.

Engineering products are created and maintained by their engineering company in such way that they meet quality requirements as they are designed. Each operational company that manufactures a product needs the same product and underlying BOM. Depending on the production facility, the route might be created locally. In this case, you won't release a route together with the product. For legal entities that will sell the products but won't manufacture them, the BOM might not be required.

To make the process more efficient, all engineering-relevant data can be released to other operational companies at the same time. This data includes the product structure. During the release process, you can choose which part of the product data should be released.

For more information about engineering companies and operational companies, see [Engineering companies and data ownership rules](engineering-org-data-ownership-rules.md).

Note that you can release both standard products and engineering products together with the release product structure. During this process, the whole product structure will be released, even the BOM and route from the company that the products are being released in.

For an example of how to release a product, see [Release an engineering product to a local company](engineering-scenarios.md#release)

## Released data for a product when the release product structure is used

The following data is included in the release of engineering products:

- **Product data** – A new released product is created.
- **Engineering version data** – The engineering version and its data are created or updated. Note that if you release the same engineering version again to an operational company, the engineering data will be overwritten.
- **Engineering attributes** – The engineering attributes and their values are created or updated.
- **Engineering bill of materials** – The engineering BOM and its lines can be created or updated. For more information about data ownership, see [Product owners](product-owner.md).
- **Engineering routes** – The engineering routes and their operations can be created or updated. For more information about data ownership, see [Product owners](product-owner.md).
- **Engineering documents** – The engineering documents that are connected to the engineering version are created or updated.

When you turn on engineering change management on your system, the release product structure is available. In addition, standard products will include their BOMs and routes when they are released.

## Product acceptance

**Product acceptance** is a key parameter that influences the release process. You can set this parameter for each company by going to **Engineering change management \> Setup \> Engineering change management parameters**. For more information, see [Engineering change management parameters](engineering-parameters.md).

### Automatic product acceptance

Each release of engineering products starts when somebody from the engineering company selects a product to release. When the **Product acceptance** parameter is set to *Automatic*, the user at the engineering company decides which product data should be automatically released to the operational companies. The product will then automatically be released to the companies that are selected in the release wizard.

### Manual product acceptance

Each release of engineering products starts when somebody from the engineering company selects a product to release. When the **Product acceptance** parameter is set to *Manual*, the user at the engineering company decides which product data should be released to the operational companies. A user from each operational company then reviews the product data and decides whether to accept the release. The user at the operational company can set the following options when the data is received:

- If the products (updates) aren't relevant for the operational company, the user can choose not to accept the release.
- The user can change the item template for new products.
- The user can choose whether the product should be released together with their BOMs and/or routes, and whether they should be released as approved and active.
- The user can change the effective-from dates of the products.

For an example of how to accept a product, see [Review and accept the product before you release it in the local company](engineering-scenarios.md#accept).

> [!NOTE]
> For standard products, you can release from any legal entity to any other legal entity. For engineering products, the only legal entity that you can release from is the engineering company.

## Release policies

Not all operational companies need the same product data. In general, operational companies that manufacture engineering products require a BOM, whereas operational company that only sell engineering products don't require a BOM. You can use release policies to establish the parameters that are used for the release of products.

For engineering products, the release policy is assigned in the engineering product category, and the field is mandatory. For standard products, the policy is assigned to the shared product, and the field is optional.

For more information about engineering product categories, see [Engineering versions and engineering product categories](engineering-versions-product-category.md).

During the release process, you can influence the settings.

## Create and manage product release policies

To work with product release policies, go to **Engineering change management \> Setup \> product release policies**. Then follow one of these steps.

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
| Apply templates | Select one of the following options to specify whether and how product release templates should be applied when the policy is used:<ul><li>**Always** – A template released product must always be used for releases. If you select this option, use the **All products** FastTab to specify the template that is used for each company that you release to. If you don't specify a template for each company that is listed on the **All products** FastTab, you will receive an error when you try to save the policy.</li><li>**Optional** – If a template released product is specified for a company that is listed on the **All products** FastTab, that template will be used when you release to that company. Otherwise, no template will be used. If you select this option, you can save the policy without assigning templates to all companies. (No warning will be shown.)</li><li>**Never** – No template released product will be used for any companies that you release to, even if a template is specified for companies that are listed on **All products** FastTab. The template columns will be unavailable.</li></ul> |
| Active | Use this option to help maintain your release policies. Set it to *Yes* for all release policies that you use. Set it to *No* to mark a release policy as inactive when it isn't used. Note that you can't inactivate a release policy that is assigned to an engineering product category, and you can delete only inactive release policies. |

### All products FastTab

On the **All products** FastTab, add a row for each operational company that you want to use this policy to release to. Use the buttons on the **All products** FastTab to add and remove rows as you require. For each row that you add, set the following fields.

> [!NOTE]
> The settings on the **All products** FastTab apply to both engineering products and standard products.

| Field | Description |
|---|---|
| Company accounts ID | Select the company that the row applies to. The parameters on the row will apply when products are released to this company. |
| Template released product | Add a template for the product. |
| Copy BOM approval | Select this check box to copy the BOM approval status to the receiving company. |
| Copy BOM activation | Select this check box to copy the BOM activation status to the receiving company. |
| Copy route approval | Select this check box to copy the route approval status to the receiving company.|
| Copy route activation | Select this check box to copy the route activation status to the receiving company. |

### Option parameters for engineering products FastTab

Every time that you add a row on the **All products** FastTab, a row that has a matching **Company accounts ID** value is also created on the **Option parameters for engineering products** FastTab. Then, if you remove a row from the **All products** FastTab, the row that has a matching **Company accounts ID** value is also removed from the **Option parameters for engineering products** FastTab.

For each row that is shown on the **Option parameters for engineering products** FastTab, set the following fields.

> [!NOTE]
> The settings on the **Option parameters for engineering products** FastTab apply only to engineering products.

| Field | Description |
|---|---|
| Template BOM | When a product that has a BOM is released, the lines of the specified template BOM will be added. This field is useful for adding local components, such as packaging or instructions in the local language. |
| Template route | When a product that has a route is released, the lines of the specified template will be added. |
| Copy effectivity | Select whether effectivity dates should be copied from the engineering company to the operational company when you release products. |
| Automatically add to release proposal | Select this check box for products that should automatically be released on the engineering change order. In this way, products that belong to engineering product categories that use this release policy can automatically be released to operational companies where this option is set up. (For more information, see [Manage changes to engineering products](engineering-change-management.md).)

### Review each product when you release it

When engineering products that have BOMs or routes are released, the parameters will be set to default values, as indicated in the release policy. As a user, you can influence this behavior on the releasing side when you use the release product structure.

To release engineering products, on the **Released products** page, select the products to release, and then select **Release product structure** to open the release wizard. The **Select engineering products to release** page shows the products. Select a single product, and then select **Release details** to review the release details for the product.

On the **Release details** page, you can change the value of the **Receive BOM**, **Copy BOM approval**, **Copy BOM activation**, **Receive BOM**, **Copy route approval** and **Copy route activation** fields. In the push-pull scenario, you can change the value of the same fields on the receiving side, provided that the BOM and route are released.

## Product owners and product releases

Because product owners know which legal entities need their products, a product can be released only by the members of that product's product owner group. Other users can't release products that they don't own.

This behavior applies only when a product is directly selected for release. Products that are part of another product's structure via a BOM *can* be released by non-owner users when they release the parent product, provided that they own the parent product.

For example, product X is assigned to the *Design cabinets* product owner group. Product X is also part of the BOM of product Y, which is assigned to the *Design speakers* product owner group. If a user from the *Design speakers* product owner group releases product Y and its BOM, product X will be released together with product Y.

For more information, see [Product owners](product-owner.md).
