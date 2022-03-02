---
title: Cross-company product sharing
description: This topic explains how to share released-product data across companies (legal entities), thereby reducing the volume of data that must be maintained while simplifying the task of maintaining product master data.
author: t-benebo
ms.date: 02/21/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2022-02-01
ms.dyn365.ops.version: 10.0.26
---

# Cross-company product sharing

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Companies with many companies (legal entities) and a large product portfolio (such as large sales and distribution networks) often experience a high level of duplicated product data. This feature lets you share released-product data across companies, thereby reducing the volume of data that must be maintained while simplifying the task of maintaining product master data.

The [cross-company data sharing capabilities](../../fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing.md) of Supply Chain Management enable you to share product information across multiple companies.

## How to get the cross-company product sharing public preview

To sign up for the public preview for this feature, send your LCS environment ID by email to the [cross-company product sharing team](mailto:productsharing@service.microsoft.com). The Microsoft team responsible for the feature will send you a follow-up email to get in contact and evaluate if your business is a match for the functionality to finally evaluate if you can join the preview functionality.

## Prepare your system to enable cross-company data sharing for products

Before enabling cross-company data sharing for products, work through the following checklist:

- **Currency** – Either the currency must be the same across all companies in the data sharing policy or you must avoid using the base prices fields.
- **Number sequence** – Number sequences must be aligned across all companies in the data sharing policy.
- **Policies must be enabled in the right order**: Duplicate shared policies must be enabled before single record sharing policies.
- **Specify the default parameters per company** – You may want to align default parameters across all companies in the data sharing policy.
- **Consider if any of your business processes are affected by the single record sharing functionality** – Read in detail the list of [Limitations and notes that apply for shared products](#limitations) and prepare your system as necessary.

## Set up the products and product-related information sharing policies

To share products and product related information, you must create and set up your sharing policies using **Configure cross-company data sharing** page. Each sharing policy establish a set of tables and fields that are shared. To get started quickly, you can edit the provided sharing-policy templates as needed and then use them to set up your default sharing policies. For more information about how to use a template, see [Configure financial cross-company data sharing](../../fin-ops-core/dev-itpro/data-entities/tasks/configure-financial-cross-company-data-sharing.md).

You can choose to share product information using either of the following sharing policies:

- **Duplicate record sharing** – Each company has its own copy of the shared product record. Each time product information is edited in any company, the update is immediately replicated across all companies' copy of that product record.
- **Single record sharing (SRS)** – Just one shared record exists for each product in the database, and all relevant companies are able to view and edit that record.

When sharing product information, we recommended using a single record sharing policy because it makes more efficient use of database resources, especially for companies with large product portfolios. However, for related data and policies that indicate how a product is managed in different companies, we recommend using a duplicate record sharing policy, so you're able to manage products differently in each company where they are used (such as for production-related policies like production pools).

> [!IMPORTANT]
> Duplicate record sharing policies must be enabled before the single record sharing policy. This is because if a field is included in a table that is part of a single record sharing policy, the field and its table will also be shared as a single record unless specified otherwise (as duplicate record sharing) by a policy enabled previously. For example, if you use duplicate record sharing for production pools, you must enable the production pool policy before enabling the products.

### Templates for duplicate record sharing of product information

The product related templates for duplicate record sharing are:

- Barcode setup
- Batch attribute
- Batch disposition master
- Buyer group
- Calculation group
- Charges group
- Commission group
- Cost group
- Counting reason code policy
- Duty rates group
- Fiscal LIFO reporting group
- Freight allocation group
- Inventory level profile
- Item coverage group
- Item group
- Item model group
- Item price tolerance group
- Item rebate group
- Number group
- Packing group
- Price group
- Production group
- Production pool
- Property
- Revenue schedule
- Statistics procedure
- Supplementary item group
- Tax rate type
- Warehouse item setup

### Templates for single record sharing of product information

The product template for single record sharing is:

- Products

## Shared product-related tables and fields

There are many tables and fields that relate to products. Most of them are included in the provided template policies.

To enable fields and tables to be shared, sharing metadata must be specified for each table. If you want to share a table that isn't included in the template, metadata for sharing must have been previously set by Microsoft, otherwise you won't be able to add the table to a cross-company sharing policy. If you would like to share a table that isn't currently set up for sharing, please submit a request to Microsoft Support.

## <a name="limitations"></a>Limitations and notes that apply for shared products

The following subsections provide notes and summarize the various limitations that apply when you share product information between companies under various scenarios.

### Item templates

It is not possible to apply item templates on child companies, so the **Apply template** menu item is disabled in child companies. This is because the table `SysRecordTemplateTable` isn't shared.

### Currencies and base prices

Base prices (such as sales price, purchase price, and inventory price) are implicitly expressed in the accounting currency of each company.

The accounting currency for each company is set up under **General Ledger \> Ledger Setup \> Ledger \> Field Accounting currency**.

For companies that are part of a cross-company policy, the following cases apply:

- **All companies in the policy use the same accounting currency** – There are no special limitations to consider.
- **Companies in the policy use different accounting currencies** – Currency is implicit per company, rather than specified explicitly, which means that if there is one amount that is shared across companies (such as the base sales price), each company will assume a different currency. For example, if the base sales price is 20, company USMF (which uses US dollars) would assume that amount is $20, while company JPM (which uses Japanese yen) would assume the amount is &#165;20, which does not represent the same monetary value, so the item would be sold at a price that is either too expense or too cheap by one of these companies.

Therefore, only one of the following applies:

- **All companies that are part of a cross-company data sharing policy for sharing products must use the same accounting currency** – If you rely on fields that use an implicit currency (such as base sales price or purchase sales price) then you must set the same accounting currency in all companies that are part of the product sharing policy.
- **You must not rely on the value of these fields** – Use trade agreements for purchase and sales prices and do not use the inventory price or its related processes.

### Country specific

Most country-specific fields are disabled by default on product tables because they are not supported. This means that if you want to share these fields, you must add them as an extension (add the country specific tables to the policy and select the needed fields to be shared).

### Default unit of measure

When you create a product, you must specify several different units of measure, each for a specific purchase, such as inventory unit, purchase unit, and sales unit. The **New released product** dialog shows the same default unit for each of these based on the default setting for the current company (though you can edit each of them separately in the dialog). To assign the default unit for a company:

1. On the navigation bar, select the company (legal entity) you want to set defaults for.
1. Go to **Inventory management \> Setup \> Inventory and warehouse management parameters**.
1. Open the **General** tab.
1. In the **Default values** field group, use the **Unit** field to set the default for the current company.

> [!IMPORTANT]
> The default unit depends on the company the product is created in. If you would like the default behavior to be aligned, then set the same default units for all companies.

### Physical dimensions units

The **Released products** page shows physical dimensions, such as weight and height, for each released product. However, the unit for these measurements isn't shown on the page and is therefore implicit. The unit used for these measurement is the system unit in each of the unit classes. The system unit for each is cross-company, so there are no specific actions or limitations to consider in this area.

> [!NOTE]
> The system unit for each class is set up on the unit itself, and only one unit in the unit class can be a system unit. If no unit is set up as the system unit, the value of the fields will have no meaning, and processes (such as warehousing) that rely on having a system unit won't be able to complete. For more information, see [Manage units of measure](tasks/manage-unit-measure.md).

### Bills of material, formulas, and routes

We recommend that you manage bills of material (BOMs), formulas, and routes in each company. Therefore, these are not shared in the provided templates.

### Coverage group – calendar

When sharing the coverage groups for an item, the calendar on the coverage group isn't shared on the given templates. If you would like to share a calendar, create a new policy for calendar sharing or add the calendar table to the coverage group policy.

### Product configurator

Constraint-based configuration products do not have any limitations. The product is shared when created and the variant created on the fly is also shared cross-company.

### Number sequences

Number sequences may be used for product numbers and other purposes. Number sequences must be shared if used with single record sharing of products.

### Dual-write

Dual-write isn't currently supported when using cross-company data sharing for products. 

### Dynamics 365 Commerce

Dynamics 365 Commerce is not supported when using cross-company data sharing for products. 

### Financial dimensions

Fields that reference financial dimensions (for example Ledger or Default dimension) can't be shared across companies. This is a restriction of cross-company data sharing. For details, see [Cross-company data sharing](../../fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing.md)

### Vendors

There is no template policy for the vendors table. The vendors table (`vendtable`) is marked as a single record shared table, so you can actually create a policy for single record sharing and add the table.

### Item sales tax group and item purchase tax groups

Item sales tax group and item purchase tax groups at specified at the product level. These values default the tax group on each of the sales and purchase order lines, respectively. For convenience of defaulting, these values are set to duplicate record sharing and are added in the SRS products template. Although the names of the tax groups are shared across companies, their details and settings are company-specific, so you must set these up in the companies part of the sharing policy. This is because tax groups are specific to each item in the company context.

### Distributed hybrid environment

If you are using a [distributed hybrid environment](../cloud-edge/cloud-edge-landing-page.md) with cloud or edge scale units, cross-company data sharing for products isn't supported.

### Engineering Change Management

Engineering change management provides some functionality that may conflict with the single record sharing of products, but when used in certain ways, may be complimentary.

The following engineering change management concepts will be affected if you use single record sharing of products:

- **Definition of engineering company** – With engineering change management, you can set up one or more engineering companies. These organizations may represent the one (or more) existing companies where your engineering department is, or you might set up a dedicated company that doesn't represent an actual engineering department, but which you use for managing master data and the controlled release of products for your organization. For more information about engineering companies, see [Engineering companies and data ownership rules](../engineering-change-management/engineering-org-data-ownership-rules.md).
- **Release product structure** – From the engineering company, you can release a product to other companies using a controlled process. For more information about the release product structure, see [Release product structures](../engineering-change-management/release-product-structure.md).

The tables related to engineering versions aren't shared because they are meant to be contained in engineering and only be shared with a controlled release. Therefore, if you use engineering change management, you might choose any of the following setups:

- **Your engineering company is part of the single record sharing policy** – In this case, most of the engineering related functionality would not be applicable, especially the controlled release. As soon as the product is created in the engineering company (as a released product), the product is shared (made available) to the rest of your companies. Therefore, the engineering company would lose its "engineering" character, in the sense that it would no longer be a space where the engineering team can work on products, and only those products that continue forward are used in the system. Because the engineering versions are not shared, the version information would only be available in the engineering company. This would mean that:
  - Engineering versions would only exist within the engineering company unless shared using the release product structure
  - The lifecycle state at the version level would only work in those companies where the version information has been shared. This means that you would not be able to control the processes in which a version of a product is being used unless the version is shared with its released product structure.
  - Release control is lost because the product is shared across all companies.
  - BOM and route are kept locally. You must manage the BOM and BOM versions (as well as routes and route versions) at the company level, so you could still use the release product structure to share the BOM and route.

  We don't recommend this setup because it disabled much of the value of engineering change management.

- **Your engineering company is not part of the single record sharing policy for products** – You could set up your engineering company so that it isn't part of the shared product policy, and then make a sharing policy that includes all companies where the product introduction is done at the same time. In this case, you could release to one company to make the product available in all the companies. Note that if you do need version management, you would still need to release the version information with the release product structure. In this case, your organization needs to have an engineering company where products are designed and managed. When a product is ready, you then do a controlled release to the rest of the companies (which is main goal of the engineering change management functionality). In this case, you would create the product in the engineering company and then release it to all the companies that are part of the sharing policy. (Note that the released product will be released to all of the companies at the same time because they are sharing the same product record.) Be aware that version-related tables are not shared (such as engineering versions), so you must not rely on version management outside of the engineering organization (or, if you need version management in all companies, then you must release version-related information with the release product structure).

### Sites and warehouses

Sites and warehouses are not shared. The `InventLocation` and `InventSite` tables are not shared. We expect that you keep sites and warehouses at the company level.

## Existing products

When enabling single record sharing for products, it is important that you create and enable the single record sharing policies and then start importing/creating your product portfolio.

If you already have products (existing products) in the system before enabling the single record sharing, these will not be shared.

## More information on cross-company data sharing

To learn more about cross-company data sharing, please refer to [Cross-company data sharing](../../fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing.md).
