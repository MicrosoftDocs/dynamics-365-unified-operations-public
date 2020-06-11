---
# required metadata

title: Release management
description: When an engineering product traverses through its lifecycle, it's important that you can control which transactions are allowed per lifecycle state. As an example, when products aren't yet in a mature state, they shouldn't be put on a sales order and on the other end, if a product is reaching its end-of-life state, you want to ensure that the inflow of this product can be controlled.
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

# Release management

To ensure that engineering relevant data of products can easily be reused in different legal entities, it is possible to next to release products with their engineering versions, also to release complete product structures. This means that you can release multi-level bill of material structures together with the parent in a single release action. The bill of materials and the lower level products are also released in this case. <!-- KFM: This paragraph is confusing. Let's discuss it. -->

Engineering products are created and maintained in their engineering organization, and are created in such way that they meet the quality requirements as they are designed. In all operational organizations that manufacture this product, the same product and underlying bill of materials are needed. Depending on the production facility itself, route creation might be a local exercise, in which case you don't want to release a route with it. If there are other legal entities that won't manufacture the products, but they only sell them, the bill of materials may not be required.

To increase the efficiency in the process, the engineering relevant data including the product structure, can be released at once to other operational organizations. In this release process, you can make choices which part of the product data will be released. For more information on the engineering organization and operational organization, see … <!-- KFM: See what? -->

## Content of released data

The following data is part of releasing engineering products:

- *Product* data: when releasing a new engineering product, a new released product is created
- *Engineering version* data: when releasing engineering products, the engineering version and its data is created or updated. Note: when you release the same engineering version again to an operational organization, the engineering data will be overridden.
- *Engineering attributes* : when releasing engineering products, the engineering attributes and its values are created or updated
- Engineering *bill of materials* : when releasing engineering products, the engineering bill of materials and its lines can be created or updated. See below for more information how this can be chosen. For more information on the data ownership, see … <!-- KFM: See what? -->
- Engineering *routes* : when releasing engineering products, the engineering routes and its operations can be created or updated. See below for more information how this can be chosen. For more information on the data ownership, see … <!-- KFM: See what? -->
- Engineering *documents* : when releasing engineering products, the engineering documents connected to the engineering version are created or updated.

## Methods of releasing

There are two possible release methods. They can be set up in the module"s parameters and will be applicable for all companies.

### Push release

Each release of engineering products starts from the engineering organization, by selecting the products to be released. With the push release, the user in the engineering organization decides what product data is released and this is received like this in the operational organization(s).

### Push-pull release

Each release of engineering products starts from the engineering organization, by selecting the products to be released. With the push-pull release, the user in the engineering organization decides what product data is released and send this to the operational organization(s). In the operational organization(s), you will be able to review the received products data before receiving. You can also control how you receive the data:

- If the product (updates) are not relevant for the operational organization, you can choose to not receive the release
- Change the item template for new products
- If you want to receive the bill of materials and routes and if they should be received approved and active
- Change the effective from dates of the products

## Control if bill of materials and routes are part of the released data

Not all operational organizations need the same product data. In case you release to an operational organization which is *manufactures engineering products* , the bill of material is needed there. In case you release to an operational organization which is a *sales company* that only sells the engineering products, the bill of materials is not per definition needed. While this scenario can be different for different types of products, you can setup defaults per engineering product type. For more information on the engineering product types, see … <!-- KFM: See what? -->

During the release process, you can influence the settings as well.

### Default settings

To create the defaults on the **engineering product type**, open the **Release control** FastTab. The following table describe the options that can be used for the bill of material and route:

| Field | Description |
| --- | --- |
| **Company accounts ID** | Select the company for which you want to create the line |
| **Priority** | In case you have multiple lines for the same company, select the search order. The system will search from lowest to highest number |
| **Filter** | In case you have multiple lines for the same company, use the filter to make a query on product data that will determine under what conditions this line will be used |
| **Receive&nbsp;BOM** | Should the selected company receive the bill of material when there is one |
| **Copy BOM approval** | Should the approval information of the bill of material be copied to the receiving company |
| **Copy BOM activation** | Should the active checkmark of the bill of material be copied to the receiving company |
| **Receive Route** | Should the selected company receive the route when there is one |
| **Copy route approval** | Should the approval information of the route be copied to the receiving company |
| **Copy route activation** | Should the active checkmark of the route be copied to the receiving company |
| **Auto release** | Should the product be part of automatic releasing on the engineering change order. This will give you the option to automatically release products of this engineering product type, to this operational organization. You can do this as part of the workflow on the engineering change order. For more information see ... <!-- KFM: See what? --> (Engineering change management) |

### Manual control

When engineering products with bill of materials or routes are released, the default settings are used. As a user you can influence this on the releasing side: in the **Release details** page, the fields **Receive BOM**, **Copy BOM approval**, **Copy BOM activation**, **Receive BOM**, **Copy route approval**, and **Copy route activation** can be changed. In the push-pull scenario, you can change the same fields on the receiving side (in case the bill of material and route are send over).

## Product owners and releasing products

While product owners know which legal entities need their products, the product can only be released by the members of the product owner group. In case another user will select the product for releasing, the product will not be available in the release form.

This behavior is only applicable in case the product is directly selected for releasing. In the situation the product is via a bill of material line part of a product structure, the product can be released by other users in case the parent of the product is released.

As an example: product X has product owner group "Design cabinets" assigned. Product X is also part of the bill of material of product Y which has product owner group "Design Speakers" assigned. In case a user of the product owner group "Design Speakers" releases product Y and its bill of material, product X will be released along with it.

For more information on the product owners, see <!-- KFM: See what? -->