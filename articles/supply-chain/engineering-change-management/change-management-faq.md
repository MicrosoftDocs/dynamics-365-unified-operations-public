---
title: Engineering change management FAQs
description: This topic presents several frequently asked questions (FAQs), and their answers, regarding the engineering change management feature
author: t-benebo
manager: tfehr
ms.date: 03/25/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-03-25
ms.dyn365.ops.version: 10.0.18
---

# Engineering change management FAQs

[!include [banner](../includes/banner.md)]

This topic presents several frequently asked questions (FAQs), and their answers, regarding the engineering change management feature

## Should I choose to track the version in transactions?

When you create an engineering change category, the **Engineering change category details** page provides a settings called **Track version in transactions**. What is this setting and what does it do?

- When you set **Track version in transactions** to *Yes*, you will see the dimension groups where version is an active dimension.
- When you set **Track version in transactions** to *No*, you will see the dimension groups where the version dimension is not used.

<!-- KFM: what do we mean by "you will see"? Where do we see these? -->

### If you do track the version in transactions

If you *do* track the version in transactions, then the engineering product will be a product master and each version of the product will be a product variant that uses the version dimension. Other dimensions can also be used together with the version dimension.

This means that each engineering version will be treated as a variant in all processes. Therefore, if you have a specific variant in a transaction (so that you can know which variant was sold or purchased), you would also have to manage stock for each version, master planning would plan supply for each version, and so on. If you choose to retire a version from the market, you would need to manually adjust its effective-from and -to dates  to reflect the change and also manage your inventory to make sure you don't have non-used versions of items in your warehouses.

We recommend this option if you need high traceability of the specific versions used in each transaction. However, it does require more management effort.

### If you don't track the version in transactions

If you *don't* track the version in transactions, then the engineering product (if you don't use any other dimension) will be a distinct product. The product will still be versioned, and you can manage information on the specific versions such as its BOM and route, but you won't be able to trace which specific version was used in each transaction. The effective-from and -to dates indicate the validity of each of version.

This option is much easier to manage because changing from one version to another is as easy as making the needed changes in a change order and then updating the effective-from and -to dates in the engineering version. The production processes will then pick up the needed BOM and route for the product (and its specific version).

Most organizations choose this option because it provides version and change management without adding the extra overhead of tracking the version in each transaction, in inventory, and during master planning.

## Which fields are copied to the released item template?

From the **Released product details** page, the following fields are copied to the released item template: <!-- KFM: What is a "released item template"? This is a new term. What process are we describing here? -->

| FastTab | Fields copied on creation by the engineering company | Fields copied on release to an operational company |
|---|---|---|
| **General** | All fields from the **Administration** field group. | <!--KFM: Same as for the engineering company? --> |
| **Purchase** | All fields. | All fields except **Unit**. |
| **Sell** | All fields from the following field groups: **Sales order**, **Administration**, **Taxation**, **Price update**, **Base sales price**, **Charges**, **Discounts**, and **Alternative product**. | Same as for the engineering company, but excluding the **Unit** field. |
| **Foreign trade** | All fields | All fields |
| **Manage inventory** | All fields and field groups *except* **Physical dimensions** and **Catch weight**.  | Same as for the engineering company, but excluding the **Unit** field. |
| **Engineer**, **Plan**, **Manage costs**, **Manage projects**, **Financial dimensions**, and **Warehouse** | All fields | All fields except **BOM Unit**. |
| **Product variants** | All fields from the **Default product variant** field group. | Same as for the engineering company. |
| <!--KFM: Where is this? --> | The options default order settings and Warehouse items. <!--KFM: Are these field names? --> | Same as for the engineering company. |

<!-- KFM: Here is the original list (remove when done):
 
- In tab General, field group Administration.
- In tab Purchase everything with creating in engineering company. When receiving initially from releasing, everything except unit.
- In tab Sell, field groups Sales order, Administration, Taxation, Price update, Base sales price, Charges, Discounts and Alternative product with creating in engineering company. When receiving initially from releasing, same except unit.
- In tab Foreign trade, everything both with creating in engineering company and receive initially from releasing.
- In tab Manage inventory, everything except field groups Physical dimensions and Catch weight with creating in engineering company. When receiving initially from releasing, same except unit.
- In tabs Engineer, Coverage, Manage costs, Manage projects, Financial dimensions and Warehouse everything with creating in engineering company. When receiving initially from releasing, everything except BOM Unit.
- In tab Variants, field group Default product variant. Both with creating in engineering company and receive initially from releasing.
- The options default order settings and Warehouse items, both with creating in engineering company and receive initially from releasing.

-->

## Should I create a separate legal entity for engineering products or use an existing one?

The choice of whether or not to create a new legal entity for engineering products depends on your business needs.

By creating a separate engineering company, you will be able to keep engineering data separate and then add modifications as needed for your local operational companies. This will allow you to:

- Keep a separate entity where the engineering products are created and managed.
- Prevent engineering products from appearing together with the rest of your released products until they are ready and released.
- Clearly distinguish which data is dictated by engineering and which is local.

On the other hand, you should probably use an existing legal entity as an engineering company if the following apply to you:

- You only have one legal entity in your system and/or do not require a clear separation between products being engineered.
- You don't want to duplicate some data such as resource groups, resources, operations, and possibly sites.

## What is the nomenclature for engineering versions and variants?

The nomenclature for engineering products and product variants work in the following way:

- For the engineering product (the distinct product in cases where no dimensions are used or the product master in case any dimension is used) the number rule nomenclature is defined on the engineering product category. There, you have the option to use a number sequence, text constants, and attribute names and values.
- For each variant of an engineering product (in cases where your engineering product is a product master, this is set up in the category where you specify the dimension group) the number rule nomenclature for each of the variants is defined in the dimension group. In this case, you can use the product ID of the master and also the dimension values and names.
