---
title: Enable change management on existing products
description: Learn how you can enable change management for existing products, with a description on cases where your ability to enable change management is limited.
author: sgmsft
ms.author: shwgarg
ms.topic: article
ms.date: 02/05/2021
ms.custom: 
ms.reviewer: kamaybac
ms.search.form: 
---

# Enable change management on existing products

[!include [banner](../../includes/banner.md)]

This article explains how you can enable change management for existing products. It also describes cases where your ability to enable change management is limited.

When you enable change management for an existing product, you can create versions of that product and trace changes that are made to it throughout its life. Therefore, you can track those changes by using change orders. To enable change management, you must convert the relevant products to *engineering items* (also referred to as engineering products). Engineering products are products that are versioned and managed through change management. A wizard is provided to guide you through the conversion process.

## Turn this feature on or off

The functionality described in this article requires that both the *Engineering Change Management* and *Enable change management on existing products* features be turned on for your system. For details about how to turn these features on or off, see [Engineering change management overview](product-engineering-overview.md).

## Restrictions and limitations

Not all product types can be converted to all other types. The following restrictions and limitations apply:

- When you convert a product to an engineering product, it remains a *product*. It doesn't become a *product master*.
- When you convert a product master that has a specific set of dimensions, those dimensions are maintained after the change. For example, if you convert a product master that has the size dimension, it will keep the size dimension.

Therefore, if you have a distinct product, you can change it only to an engineering product that doesn't track the product dimension in transactions (that is, the version dimension isn't used). See the remaining sections of this article for more information about these issues.

## Prepare for conversion by creating all required engineering product categories

An *engineering product category* must be assigned to every engineering product. You will do this assignment when you run the **Convert to engineering product** wizard. Engineering product categories must exist for all relevant standard products *before* you can convert those products.

The engineering product category provides a basis for creating an engineering product, and it establishes a set of default values and policies. Engineering attributes and their default values (as defined for the engineering category) are also applied to the resulting engineering product. You can edit the attribute values and/or add more engineering attributes to the resulting product as needed.

The engineering product category must match the product that you assign it to. For example, the product type and dimension group must match both the product and its engineering product category. Learn more in [Engineering versions and engineering product categories](engineering-versions-product-category.md).

> [!IMPORTANT]
> The **Convert to engineering product** wizard can convert product only to engineering products where the version isn't tracked in transactions. Therefore, the **Track version in transactions** option must be set to *No* for engineering product categories that you create to convert existing products.

For information about how to create engineering product categories, see [Engineering versions and engineering product categories](engineering-versions-product-category.md).

## Run the Convert to engineering product wizard

The **Convert to engineering product** wizard helps you convert one or more existing products to engineering products. It converts the products into engineering products (versioned products) where the version isn't tracked in transactions (that is, the version dimension isn't used). After the conversion is completed, you can manage the products by using Engineering change management.

The conversion is permanent. Therefore, you won't be able to reverse it later. 

Each converted engineering product will continue to be released in the same companies that the original product was released in. However, the engineering bill of materials (BOM) and routes won't automatically be released to those companies.

Follow these steps to run the **Convert to engineering product** wizard and convert a product to an engineering product.

1. Go to **Product information management \> Products \> Released products**.
1. In the grid, select the check box for each product that you want to convert.
1. On the Action Pane, on the **Engineer** tab, in the **Engineering change management** group, select **Convert to engineering product** to open the wizard.
1. The first page of the wizard is the **Welcome** page. If you aren't already familiar with the conversion process, carefully read the information on this page. When you're ready to continue, select **Next**.
1. The **Select details for the products to be converted** page shows each product that you selected before you opened the wizard. Inspect the list. Use the **New** and **Delete** buttons on the toolbar to add or remove products as you require.
1. Use the following fields at the top of the grid to assign default values to every product that is listed. (You will be able to change these values for individual products after the conversion is completed.) Default values won't be assigned to products where a relevant value has already been assigned.

    - **Default engineering category** – Select an initial engineering product category to assign to every listed product. The category that you select will be applied only to products that are compatible with it.
    - **Default version** – Enter the initial product version to assign to every listed product. Every engineering product has at least one engineering version.
    - **Default lifecycle state** – Select the initial product lifecycle state to assign to every listed product.
    - **Current BOM will be part of the engineering product** – Select this check box if the current BOM for each listed product should be used as a BOM for the engineering product.

    For more information about product settings, see the next step.

1. Review each product that is listed in the grid, and evaluate how well the default values that you assigned apply to it. For each row, review the following information and set any relevant fields:

    - **Product number** – The product number.
    - **Product name** – The name of the product.
    - **Engineering category** – Select the engineering product category that the product should belong to after it's converted. An appropriate category must already exist for each product, as was explained in the previous section of this article. You must assign a category to every product.
    - **Version** – Enter the product version to assign to the product after it's converted. For example, you might select a number that fits in the number sequence that your category already uses. Each engineering version stores the engineering-relevant data that is specific to that version. Learn more in [Engineering versions and engineering product categories](engineering-versions-product-category.md).
    - **Product lifecycle state** – Select the product lifecycle state that the product should be in after it's converted. The product lifecycle state lets you to control which transactions are allowed for a given engineering version. Learn more in [Product lifecycle states and transactions](product-lifecycle-state-transactions.md).
    - **Has BOM** – A selected check box indicates that the product has a BOM. The setting of this check box can help you decide how to set the **Current BOM will be part of the engineering product** check box.
    - **Current BOM will be part of the engineering product** – Select this check box if the current BOM of the product should be used as a BOM for the engineering product. That BOM will then be managed by Engineering change management. If the product doesn't have a BOM, or if you prefer to manually create a BOM for the converted product later, clear this check box.
    - **Has errors** – A selected check box indicates that the product setup has one or more errors. For example, the product type or the dimension group might not match in the category. Products that have errors will be skipped and won't be converted.

1. When you've finished, select **Validate** on the toolbar to validate the product setup. For each row, the **Has errors** check box will be updated to indicate the product's status. Adjust the values until the setup of every product is free of errors.
1. When all the products are set up correctly, select **Next** to continue.
1. The **Confirm selection** page shows the number of products that have no errors in their setup and are therefore ready for conversion. It also shows the number of products that will be skipped because of errors. To run the conversion as a batch job, set the **Run in batch** option to *Yes*.
1. Select **Finish** to apply your settings and start to convert the products to engineering products.

> [!NOTE]
> If your system is set up to manually accept products before they are released, you must accept each converted product by using the **Open product releases** page in the appropriate companies. Learn more in [Review and accept the product before you release it in the local company](engineering-scenarios.md#accept).
