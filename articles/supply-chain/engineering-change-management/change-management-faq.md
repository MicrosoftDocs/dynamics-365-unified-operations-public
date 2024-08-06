---
title: Engineering change management FAQ
description: Acess answers to frequently asked questions about the engineering change management feature, including questions about tracking versions in transactions.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 03/25/2021
ms.reviewer: kamaybac
ms.search.form:
---

# Engineering change management FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about the engineering change management feature.

## Should I track the version in transactions?

When you create an engineering change category, the **Engineering change category details** page provides an option that is named **Track version in transactions**. What is this setting, and what does it do?

- If you set the **Track version in transactions** option to *Yes*, the **Dimension group** field will be filtered so that it shows only dimension groups where version is an active dimension.
- If you set the **Track version in transactions** option to *No*, the **Dimension group** field will be filtered so that it shows only dimension groups where the version dimension is **not** an active dimension.

### If you track the version in transactions

For engineering categories where you've selected a dimension group where version is an active dimension, you will track versions in transactions for products in that category. In this case, the engineering product will be a product master, and each version of the product will be a product variant that uses the version dimension. Other dimensions can be used together with the version dimension.

In this case, each engineering version will be treated as a variant in all processes. Therefore, if you have a specific variant in a transaction (so that you can determine which variant was sold or purchased), you must manage stock for each version, master planning will plan supply for each version, and so on. If you retire a version from the market, you must manually adjust its effective-from and effective-to dates so that they reflect the change. You must also manage your inventory to make sure that you don't have unused versions of items in your warehouses.

Although this option requires more management effort, we recommend it if you require high traceability of the specific versions that are used in each transaction.

### If you don't track the version in transactions

For engineering categories where you've selected a dimension group where version is **not** an active dimension, you will **not** track versions in transactions for products in that category. In this case, if you don't use any other dimension, the engineering product will be a distinct product. The product will still be versioned, and you can manage information about specific versions (for example, their bill of materials \[BOM] and route), but you won't be able to trace which specific version was used in each transaction. The effective-from and effective-to dates indicate the validity of each version.

This option is much easier to manage, because if you want to change from one version to another, you just have to make the required changes in a change order, and then update the effective-from and effective-to dates in the engineering version. The production processes will then pick up the required BOM and route for the product (and its specific version).

Most organizations choose this option because it provides version and change management, but it doesn't add the extra overhead of tracking the version in each transaction, in inventory, and during master planning.

## Which fields are copied from the released item template?

When an engineering company creates an engineering product, that product is created as a released product in the engineering company. The released product that is created is based on the selected *released item template*. (The released item template is itself an existing released product.) The released item template is also used when the product is released to an operational company. In each case, the released item template defines most of the field values for the released product, and those values come from the associated **Released product details** page.

The following tables shows the fields that are copied during these processes.

| FastTab | Fields that are copied on product creation in the engineering company | Fields that are copied on release to an operational company |
|---|---|---|
| **General** | All fields in the **Administration** section | The same fields that are copied for the engineering company |
| **Purchase** | All fields | All fields except **Unit** |
| **Sell** | All fields in the following sections: **Sales order**, **Administration**, **Taxation**, **Price update**, **Base sales price**, **Charges**, **Discounts**, and **Alternative product** | All the same fields that are copied for the engineering company, except **Unit** |
| **Foreign trade** | All fields | All fields |
| **Manage inventory** | All fields and sections *except* **Physical dimensions** and **Catch weight** | All the same fields that are copied for the engineering company, except **Unit** |
| **Engineer**, **Plan**, **Manage costs**, **Manage projects**, **Financial dimensions**, and **Warehouse** | All fields | All fields except **BOM Unit** |
| **Product variants** | All fields in the **Default product variant** section | The same fields that are copied for the engineering company |

In addition to the fields that are shown in the previous table, all default order settings are copied from the released item template, both when the product is created in the engineering company and when it's released to an operational company. (To view the default order settings for a released item template, open the relevant **Released product details** page, and then, on the Action Pane, on the **Manage inventory** tab, select **Default order settings**.)

> [!NOTE]
>
> - The unit is defaulted from the template.
> - For retailers using Dynamics 365 Commerce functionality, when assigning a retail category to a product, the retail category applies default values for many of the fields for the released product level. These defaults overwrite default values that may have already been set by the template or copied from engineering.

## Should I create a separate legal entity for engineering products or use an existing legal entity?

Your business requirements determine whether you should create a new legal entity for engineering products.

By creating a separate engineering company, you can keep engineering data separate and then add modifications as they are required for your local operational companies. In this way, you can achieve the following goals:

- Keep a separate entity where the engineering products are created and managed.
- Prevent engineering products from appearing together with the rest of your released products until they are ready and released.
- Clearly distinguish data that is dictated by engineering and local data.

On the other hand, you should probably use an existing legal entity as an engineering company if the following conditions apply to you:

- You have only one legal entity in your system, and/or you don't require a clear separation between products that are being engineered.
- You don't want to duplicate some data, such as resource groups, resources, operations, and (perhaps) sites.

## What is the nomenclature for engineering versions and variants?

The nomenclature for engineering products and product variants works in the following way:

- For the engineering product (that is, the distinct product if no dimensions are used, or the product master if any dimension is used), the number rule nomenclature is defined in the engineering product category. There, you have the option to use a number sequence, text constants, and attribute names and values.
- For each variant of an engineering product (if your engineering product is a product master, variants are set up in the engineering product category where you specify the dimension group), the number rule nomenclature for each variant is defined in the dimension group. In this case, you can use the product ID of the master, and the dimension values and names.
