---
# required metadata

title: Enable change management on existing products
description: This topic explains how you can enable change management on existing products and the restrictions on the cases where you are able to do so
author: t-benebo
manager: tfehr
ms.date: 02/05/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  EngChgProductAttributeSearch, EngChgMaintainAttributeInheritance, EngChgAttribute
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2021-05-02
ms.dyn365.ops.version: Release 10.0.17
---

# Enable change management on existing products

[!include [banner](../includes/banner.md)]

This topic explains how you can enable change management on existing products and the restrictions on the cases where you are able to do so.

You probably have some existing products in your system and you would like to start using the change management capabilities in some of them. This would allow you to version the item and have traceability of the changes along its life, so you would be able to track those change with change orders. So, to be able to use the change management capabilities on an existing item, you would need to make those items *engineering items* (items that are versioned and managed with change management).

From there, a wizard will open and guide you through the process.

## Prerequisites

Configuration key Engineering Change Management enabled
Turn on feature "Enable change management on existing products" in feature management

## Run the wizard

From the **Released products** page, select the product(s) that you would like to convert to engineering products and then select **Convert to engineering product**, found on the top ribbon on the Engineering tab, in the Engineering change management field group.

In the welcome page you will find the following information that you will need to take into account:

This wizard helps you convert one or more existing product(s) into engineering products. Once converted, you'll be able to manage these products using Engineering Change Management. This conversion is permanent, so you won't be able to revert it later. The wizard will convert the product into an engineering product, a versioned product, where the version is not tracked in transactions (version dimension is not used). Be aware that once a product is converted into an engineering product, this change cannot be reverted. Once converted, the product will have versions and will be managed through change management.

After the conversion, each converted engineering product will still be released in the same companies as the original product was. However, the engineering bill of materials (BOM) and routes won't automatically be released to those companies. Be sure to review each of the converted products and decide whether you need to release the BOM and/or route. Select the release product structure button for those products that have a BOM and/or route that should be released. Note that if the system is setup to manually accept the products before released, you would need to accept the product in the Open product releases page in the respective companies.

### Is there any restrictions to the changes of what type of product can be converted to what type?

Yes, there are some restrictions. For example, if changing a product the product will remain a product. And in the case of a product master with a specific set of dimensions, those dimensions will be maintained after the change.

This means that if you have a distinct product, you will be able to change it to an engineering product that does not track the product dimension in transactions (does not use the version dimension).

Another example is that if you want to change a product master with the size dimension

## Set up needed before conversion

You will manage engineering products based on their engineering categories. For each product that you convert, you must therefore specify the engineering category to which it will be assigned. Therefore, the required engineering categories must exist before you convert the products. The engineering category must match the product you assign it to. For example, the product type and dimension group must match both the product and its engineering category. Because the wizard can only convert to engineering products where the version is not tracked in transactions, the engineering categories that you select must have Track version in transactions option set to No.

In the following page, called "Select details for the products to be converted" you will find the set of products that you selected from the released products page, and you will also be able to add more products using the +New button. You can also remove a product from the list of products to be converted by using Delete. Using Validate you can select a specific product and validate that the setup you entered is correct.

### Apply default values to the products

On top of the product grid you will find some options to default values to all products in the grid:

- Default engineering category: Select an engineering category to apply to the converted products if possible. The category you choose here will only be applied to those products that are compatible with it. You will be able to override this default for some products and, assign compatible categories to unmatched products. The default will not be applied if a value has already been specified.
- Default version: enter a default version number to assign to the initial version of the converted products. For example, you might select a number sequence that follows the number sequence already used by your category, or follow some other number version scheme that you are already using. The default will not be applied if a value has already been specified.
- Default lifecycle state: select an initial lifecycle state to be applied to the converted product version.
- Current BOM will be part of engineering product: select this checkbox for each product that should use its current bill of materials (BOM) as a BOM for the engineering product. This BOM will then be managed by Engineering Change Management. Clear this checkbox for products that don't have a BOM, or if you prefer to manually create a BOM for the converted product later.

Select values for each of the products.

Leveraging the defaults and completing manually, you'll need to enter the needed fields for all the products in the grid:

- Engineering category
- Version
- Product lifecycle state
- Current BOM will be part of the engineering product

To ease this work, there are two fields that can be helpful:

- Has BOM: it will be automatically checked if the product has a BOM. This will help you think if you want to associate the BOM or not to the engineering version.
- Has errors: if the engineering category or version are not valid. For example, the product type, the dimension group do not match in the category, you will find that "has errors" will be checked. Use validate to check if the line (product) has errors.

The products that have errors will be skipped and will not be converted.

## Confirm selection

In the last page, you will be able to see how many products are going to be converted and how many are going to be skipped.
