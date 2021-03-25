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

When you create an engineering change category, the **Engineering change category details** page provides a settings called **Track version in transactions**. So, what is this setting and what does it do?

- When you set **Track version in transactions** to *Yes*, you will see the dimension groups where version is an active dimension.
- When you set **Track version in transactions** to *No*, you will see the dimension groups where the version dimension is not used.

### If you do track the version in transactions

If you *do* track the version in transactions, then the engineering product created will be a product master and each of the versions of the product will be a product variant using the version dimension. Note other dimensions can also be used together with the version dimension.

This means that each engineering version will be treated as a variant in all processes. This means, for example that you have the specific variant in the transactions (you can know which variant was sold/purchased…), would have to manage stock for each version, master planning would plan supply for the specific version etc. In the case where you want to retire a version from the market for example, you would need to manually adjust the effective from and to dates of the versions to reflect the change and make sure you use well your inventory so you do not have items in a version non-used in your warehouses.

This may have a managing burden for you that you may not want to necessarily handle.

This is in general recommended to use when you need high traceability of the versions in each of the transactions.

### If you don't track the version in transactions

If you *don't* track the version in transactions, then the engineering product (if you do not use any other dimension) will be a distinct product. The product will still be versioned and you can manage information on the specific versions such as its BOM and route, but you do not have the traceability of what each specific version is used in each transaction. It is the effective from and to dates that indicate the validity of each of the versions.

This is much easier to manage as changing from a version to another is as easy as making the needed changes in a change order and updating the effective from and to dates in the engineering version. Then the production processes will pick up the needed BOM and route for the product (for its specific version).

This is commonly most used as gives the version management and change management having a minimum management.

## What fields are copied on the released item template?

From the released product, the following fields are copied on the released item template:

- In tab General, field group Administration.
- In tab Purchase everything with creating in engineering company. When receiving initially from releasing, everything except unit.
- In tab Sell, field groups Sales order, Administration, Taxation, Price update, Base sales price, Charges, Discounts and Alternative product with creating in engineering company. When receiving initially from releasing, same except unit.
- In tab Foreign trade, everything both with creating in engineering company and receive initially from releasing.
- In tab Manage inventory, everything except field groups Physical dimensions and Catch weight with creating in engineering company. When receiving initially from releasing, same except unit.
- In tabs Engineer, Coverage, Manage costs, Manage projects, Financial dimensions and Warehouse everything with creating in engineering company. When receiving initially from releasing, everything except BOM Unit.
- In tab Variants, field group Default product variant. Both with creating in engineering company and receive initially from releasing.
- The options default order settings and Warehouse items, both with creating in engineering company and receive initially from releasing.

## Should I create a separate legal entity for engineering products or use an existing one?

It depends on your business needs. If you would like a separate entity where the engineering products are created and managed, do not appear together with the rest of released products until they are actually ready and released, and you want to clearly distinguish what data is dictated by engineering versus what is local, then you probably want to create a separate engineering company, so you are able to separate that engineering data and then add any modifications needed on your local companies.

If you only have one legal entity in your system and/or do not really need a clear separation between products being engineered, you would not like to duplicate some data like resource groups, resources or operations, maybe sites, you most probably want to use your current legal entity as engineering company. Or one of your existing ones where engineering is being performed.

## What is the nomenclature for engineering versions and variants in engineering change management?

The nomenclature for the engineering product and the product variant work in the following way:

- For the engineering product (the distinct product in case no dimensions are used or the product master in case any dimension is used) the number rule nomenclature is defined on the Engineering product category. There you have the option to use a number sequence, text constants and attribute names and values (as in your image above)
- For each of the variants of an engineering product (in the case your engineering product is a product master, this is setup in the category where you specify the dimension group). The number rule nomenclature for each of the variants is the nomenclature defined in the dimension group. In this case you can use the product ID of the master and also the dimension values and names.
