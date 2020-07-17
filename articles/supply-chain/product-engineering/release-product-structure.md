---
# Release product structure

title: Release management
description: To ensure that engineering relevant data of products can easily be reused in different legal entities, you can release complete product structures in addition to releasing products with their engineering versions. This means that you can release multi-level bill of material structures together with the parent in a single release action.
author: XXXX
manager: tfehr
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
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

To ensure that engineering relevant data of products can easily be reused in different legal entities, you can release complete product structures in addition to releasing products with their engineering versions. This means that you can release multi-level bill of material structures together with the parent in a single release action. The bill of materials and the lower level products are also released in this case.

Engineering products are created and maintained in their engineering organization. The engineering products are created in the engineering organization in such way that they meet the quality requirements as they are designed. In all operational organizations which manufacture this product, the same product and underlying bill of materials are needed. Depending on the production facility itself, the route might be a local exercise to create, in which case you do not want to release a route with it. If there are other legal entities that will not manufacture the products, but they only sell them, the bill of materials may not be required.

To increase the efficiency in the process, the engineering relevant data including the product structure, can be released at once to other operational organizations. In this release process, you can make choices which part of the product data will be released. For more information on the engineering organization and operational organization, see <!-- KFM: Add link -->

Note that you can release both standard products and engineering products with the "Release product structure". When doing so the whole product structure will be released, including the BOM and route from the company where they are being released.

## Released data for a product when using "Release product structure"

The following data is part of releasing engineering products:

- **Product data**: when releasing a new engineering product, a new released product is created
- **Engineering version** data: when releasing engineering products, the engineering version and its data is created or updated. Note: when you release the same engineering version again to an operational organization, the engineering data will be overridden.
- **Engineering attributes**: when releasing engineering products, the engineering attributes and its values are created or updated
- **Engineering bill of materials**: when releasing engineering products, the engineering bill of materials and its lines can be created or updated. See below for more information how this can be chosen. For more information on the data ownership, see <!-- KFM: Add link -->
- **Engineering routes**: when releasing engineering products, the engineering routes and its operations can be created or updated. See below for more information how this can be chosen. For more information on the data ownership, see <!-- KFM: Add link -->
- **Engineering documents**: when releasing engineering products, the engineering documents connected to the engineering version are created or updated.

For a standard product, the BOM and the route will also be released.

## Automatically accept products

**Automatically accept products** is a key parameter that influences the release process. You can set this per-company on the **Product engineering parameters** page.

### Automatically accept products = yes

Each release of engineering products starts from the engineering organization, by selecting the products to be released. When automatically accept products is set to yes, the user in the engineering organization decides what product data is released and this is received (automatically released) in the operational organization(s). The products released will be automatically released in the company selected in the release wizard.

### Automatically accept products = no

Each release of engineering products starts from the engineering organization, by selecting the products to be released. When automatically accept products is set to no, the user in the engineering organization decides what product data is released to the operational organization(s). In the operational organization(s), you will be able to decide if to accept the release or not and to review the products data before they are released in the company. You can also control how you receive the data:

- If the product (updates) are not relevant for the operational organization, you can choose to not accept the release
- Change the item template for new products
- If you want to the product to be released with bill of materials and/or routes and if they should be released approved and active
- Change the effective from dates of the products

Note that for standard products you can release from any legal entity to any other legal entity. For engineering products, you can only release from the engineering organization legal entity.

## Release policies

Not all operational organizations need the same product data. In case you release to an operational organization which is **manufactures engineering products** , the bill of material is needed there. In case you release to an operational organization which is a **sales company** that only sells the engineering products, the bill of materials is not per definition needed. While this scenario can be different for different types of products, you can use release policies to establish parameters used for the release of products.

For engineering products the release policy is assigned in the engineering product category (mandatory field), and for standard products it is assigned to the shared product (optional).

For more information on the engineering product categories, see <!-- KFM: Add link -->

During the release process, you can influence the settings as well.

### Parameters on the release policy

The following settings apply to the release policies: <!-- KFM: Where do these settings apply (in contrast to the other two tables)? -->

| **Setting** | **Description** |
| --- | --- |
| **Apply templates** | <ul><li>Always = use it when you want to make it mandatory that a template released product is used for releasing. The template indicated in the field (Template released product) is used. If it is set to yes and template item is blank and user tries to save error will appear "You must fill in the Template released product". </li><li>Optional = use it when you would like to use the templates indicated in the template fields (released template product, template BOM, template route). If there is a template in the field it will be used, if there are no templates they will not be used. No warning will be shown. </li><li>Never = the template indicated in the product template field (if any) will not be used. The template columns (Template released product, template BOM, template route) are disabled.</li></ul> |
| **Active** | Is intended to help you with the maintenance of the release policies. You can mark a release policy as inactive when it is not used. Note that you cannot make inactive a release policy that is assigned to an engineering product category. You will be able to delete it when it is inactive. |

#### Setting that apply for both standard and engineering products

The following settings apply for both standard and engineering products:

| **Setting** | **Description** |
| --- | --- |
| Company | Select the company for which you want to create the line. The parameters on the line will apply when the products are released to this company |
| Template released product | Adds a template for the product – (need to add which are the fields in the template released product here – need a developer to take a look at this) |
| Copy BOM approval | Should the approval information of the bill of material be copied to the receiving company |
| Copy BOM activation | Should the active checkmark of the bill of material be copied to the receiving company |
| Copy Route approval | Should the approval information of the route be copied to the receiving company |
| Copy Route activation | Should the active checkmark of the route be copied to the receiving company |

#### Setting that apply only to engineering products

The following settings apply only to engineering products:

| **Setting** | **Description** |
| --- | --- |
| Template BOM | When a product with a BOM is released, the lines of this template BOM will be added. This is useful for adding local components such as the local packaging or a manual of instructions in the local language. |
| Template route | When a product is released with a route, the lines of this template will be added. |
| Auto release | Should the product be part of automatic releasing on the engineering change order. This will give you the option to automatically release products of this engineering product type, to this operational organization. You can do this as part of the workflow on the engineering change order. For more information see <!-- KFM: Add link (Engineering change management) --> |

### Review each product when releasing

When engineering products with bill of materials or routes are released, the parameters will be defaulted as indicated in the release policy. As a user you can influence this on the releasing side: in the **release details** form the fields Receive BOM, Copy BOM approval, Copy BOM activation, Receive BOM, Copy route approval and Copy route activation can be changed. In the push-pull scenario, you can change the same fields on the receiving side (in case the bill of material and route are send over).

<!-- KFM: In the above, we need to review the following parameters, which we may change: "Receive BOM, Copy BOM approval, Copy BOM activation, Receive BOM" -->

## Product owners and releasing products

While product owners know which legal entities need their products, the product can only be released by the members of the product owner group. In case another user will select the product for releasing, the product will not be available in the release form.

This behavior is only applicable in case the product is directly selected for releasing. In the situation the product is via a bill of material line part of a product structure, the product can be released by other users in case the parent of the product is released.

As an example: product X has product owner group &#39;Design cabinets&#39; assigned. Product X is also part of the bill of material of product Y which has product owner group &#39;Design Speakers&#39; assigned. In case a user of the product owner group &#39;Design Speakers&#39; releases product Y and its bill of material, product X will be released along with it.

For more information about product owners, see [Product owner](product-owner.md) <!-- KFM: Is this the link you mean? -->