---
title: Cross-company product sharing
description: This topic explains how to share released-product data across companies (legal entities), thereby reducing the volume of data that must be maintained while simplifying the task of maintaining product master data.
author: t-benebo
ms.date: 11/04/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-11-04
ms.dyn365.ops.version: 10.0.24
---

# Cross-company product sharing

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Companies with many companies (legal entities) and a large product portfolio (such as large sales and distribution networks) often experience a high level of duplicated product data. This feature lets you share released-product data across companies, thereby reducing the volume of data that must be maintained while simplifying the task of maintaining product master data.

The [cross-company data sharing capabilities](../../fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing.md) of Supply Chain Management enable you to share product information across multiple companies.

<!-- KFM: Throughout this document, it's hard to tell when we mean "products" and when we mean "released products". Please review each example of "product" and clarify. -->

## How to get the cross-company product sharing public preview

To sign up for the public preview for this feature, send your LCS environment ID by email to the [cross-company product sharing team](mailto:GlobalInvAccount@microsoft.com). After you're approved for the program, the team will send you a follow-up email that contains the information required to start setting up the feature.

<!-- KFM: The above is taken directly from GIA. It must be reviewed and updated with a new mail address and other details as they apply for this feature. -->

## Prepare your system to enable cross-company data sharing for products

Before enabling cross-company data sharing for products, work through the following checklist:

- **Currency** – Either the currency must be the same across all companies in the data sharing policy or you must avoid using the base prices fields.
- **Number sequence** – Number sequences must be aligned across all companies in the data sharing policy.
- **Policies must be enabled in the right order**: Duplicate shared policies must be enabled before single record sharing policies.
- **Specify the default parameters per company** – You may want to align default parameters across all companies in the data sharing policy.
- **Consider if any of your business processes are affected by the single record sharing functionality** – Read in detail the list of [Limitations and notes that apply for shared products](#limitations) and prepare your system as necessary.

## Set up the products and product-related information sharing policies

To share products and product related information, you must create and set up your sharing policies using **Configure cross-company data sharing** page.

<!-- KFM: Add an introduction about what a "template" is, why we need them, how to get them, and what we are supposed to do with them. Explain how a "policy" and a "template" are related. -->

For details about how to use a template, see [Configure financial cross-company data sharing](../data-entities/tasks/configure-financial-cross-company-data-sharing.md).

You can use the templates given as they are or as a base to create your own.

You can choose to share product information using either of the following sharing policies:

- **Duplicate record sharing** – <!-- KFM: Add a brief description-->
- **Single record sharing (SRS)** – <!-- KFM: Add a brief description. ->

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

- SRS products

<!-- KFM: The above is not the final name (check with Lars-Bo). -->

## Shared product-related tables and fields

There are many tables and fields that relate to products. Most of them are included in the provided template policies.

To enable fields and tables to be shared, sharing metadata must be specified for each table <!-- KFM: By the template? -->. If you want to share a table that isn't included in the template, metadata for sharing must have been previously set by Microsoft<!-- KFM: How, where? -->, otherwise you won't be able to add the table to a cross-company sharing policy. If you would like to share a table that isn't currently set up for sharing, please submit your request to Microsoft Support.

## <a name="limitations"></a>Limitations and notes that apply for shared products

The following subsections provide notes and summarize the various limitations that apply when you share product information between companies under various scenarios.

### Item templates

It is not possible to apply item templates on child companies, so the  **Apply template** menu item is disabled in child companies <!-- KFM: Where is this menu item? -->. This is because the table `SysRecordTemplateTable` isn't shared.

### Currencies and base prices

Base prices (such as sales price, purchase price, and inventory price) are implicitly expressed in the accounting currency of each company.

The accounting currency for each company is set up under **General Ledger \> Ledger Setup \> Ledger \> Field Accounting currency**.

For companies that are part of a cross-company policy, the following cases apply:

- **All companies in the policy use the same accounting currency** – There are no special limitations to consider.
- **Companies in the policy use different accounting currencies** – Currency conversions are not applied, which implies that if there is one amount (such as the base sales price) that is shared, each company might assume a different currency and therefore a different value. For example, if the base sales price is 20, company USMF (which uses US dollars) would assume that amount is $20, while company JPM (which uses Japanese yen) would assume the amount is &#165;20, which does not represent the same value, so the item would be either too expense or too cheap for one of these companies. <!-- KFM: I rewrote this point. Please review and confirm. -->

Therefore, only one of the following applies:

- **All companies that are part of a cross-company data sharing policy for sharing products must use the same accounting currency** – You must ensure the shared products are used in transactions and do not change the accounting currency. Then you can use the <!-- KFM: Text is missing. -->
- **You must not rely on the value of these fields** – Use trade agreements for purchase and sales prices and do not use the inventory price or its related processes.

### Country specific

Most language-specific fields are disabled by default on product tables <!-- KFM: Are we talking about language-specific or country-specific? -->. This means that if you want to share these fields, you must add them as an extension <!-- KFM: Please clarify "add them as an extension". -->. Microsoft does not currently support this.  <!-- KFM: So, it isn't actually possible to "add them as an extension"? -->

### Default unit of measure

When you create a product, you must specify several different units of measure, each for a specific purchase, such as inventory unit, purchase unit, and sales unit. The **New released product** dialog shows the same default unit for each of these based on the default setting for the current company (though you can edit each of them separately in the dialog). To assign the default unit for a company: <!-- KFM: The original seemed to imply that we would have three different default settings, but I only found one and adjusted the text to match. Please confirm. -->

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

Dual-write isn't currently supported when using cross-company data sharing for products. <!-- KFM: //Do we have a check for this? Check with Par. Is there any check anywhere that prevents when enabling it? Or how would the experience be? -->

### Dynamics 365 Commerce

Dynamics 365 Commerce is not supported when using cross-company data sharing for products. <!-- KFM: //Do we have a check for this? Check with Par -->

### Financial dimensions

Fields that reference financial dimensions (for example Ledger or Default dimension) can't be shared across companies. This is a restriction of cross-company data sharing. For details, see [Cross-company data sharing](../../fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing.md)

### Vendors

There is no template policy for the vendors table. The vendors table (`vendtable`) is marked as a single record shared table, so you can actually create a policy for single record sharing and add the table. <!-- KFM: //Should we recommend this? Has it been tested? Ask Par -->

### Item sales tax group and item purchase tax groups

Item sales tax group and item purchase tax groups at specified at the product level. These values default the tax group on each of the sales and purchase order lines, respectively. For convenience of defaulting, these values are set to duplicate record sharing and are added in the SRS products template. However, you must set up each of the tax groups and parameters in each of the companies part of the sharing policy as not this is information that is company specific and is not shared cross-company <!-- KFM: This sentence isn't clear. Please revise.-->. This is because tax groups are specific to each item in the company context.

### dDistributed hybrid environment

If you are using a [distributed hybrid environment](../cloud-edge/cloud-edge-landing-page.md) with cloud or edge scale units, cross-company data sharing for products isn't supported.

### Catch weight

<!-- KFM: //Ask Sanjay/Per  -->

### Engineering Change Management

Engineering change management provides some functionality that may conflict with the single record sharing of products, but when used in certain ways, may be complimentary.

Let's summarize on: <!-- KFM: A better list intro is needed. I'm not sure what this means. -->

- **Definition of engineering company** – With engineering change management, you can set up one or more engineering companies. These organizations may represent the one (or more) existing companies where your engineering department is, or a separate one that you only use for engineering that functions more for master data management <!-- KFM: This text isn't clear. Please revise.  -->. For more information about engineering companies, see [Engineering companies and data ownership rules](../engineering-change-management/engineering-org-data-ownership-rules.md).
- **Release product structure** – From the engineering company, you can release a product to other companies using a controlled process. For more information about the release product structure, see [Release product structures](../engineering-change-management/release-product-structure.md)

The tables related to engineering versions aren't shared because they are meant to be contained in engineering and only be shared with a controlled release. Therefore, if you use engineering change management, you might choose any of the following setups:

- **Your engineering company is part of the single record sharing policy** – In this case, most of the engineering related functionality would not be applicable, especially the controlled release. As soon as the product is created in the engineering company (as a released product), the product is shared (made available) to the rest of your companies. Therefore, the engineering company would lose its "engineering" character, in the sense that it would no longer be a space where the engineering team can work on products, and only those <!-- KFM: Those what? Products? --> who continue forward are used in the system. Because the engineering versions are not shared, the version information would only be available in the engineering company. This would mean that:
  - Engineering versions would only exist within the engineering company unless shared using the release product structure
  - The lifecycle state at the version level would only work in those companies where the version information has been shared. This means that you would not be able to control the processes in which a version of a product is being used unless the version is shared with its released product structure.
  - Release control is lost because the product is shared across all companies.
  - BOM and route are kept locally. You would manage it at the company level, so you could still use the release product structure to share the BOM and route. As well as the specific versions. <!-- KFM: This last sentence isn't clear (and is a fragment). Please revise -->

  We don't recommend this setup because it disabled much of the value of engineering change management.

- **Your engineering company is not part of the single record sharing policy for products** – In this case, your organization needs to have an engineering company where products are designed and managed. When a product is ready, you then do a controlled release to the rest of the companies (which is main goal of the engineering change management functionality). You may also have companies where the product introduction would be at the same time, but with no need of version level management. You could setup your engineering company so that it isn't part of the shared product policy, and then make a sharing policy that includes all companies where the product introduction is done at the same time. In this case, you could release to one company to make the product available in all the companies. Note that if you do need version management, you would still need to release the version information with the release product structure. <!-- KFM: This point was not clear in the original, so I edited it heavily. Please review and confirm this version. -->

### Sites and warehouses

Sites and warehouses are not shared. The `InventLocation` and `InventSite` tables are not shared. We expect that you keep sites and warehouses at the company level.

## Existing products

When enabling single record sharing for products, it is important that you create and enable the single record sharing policies and then start importing/creating your product portfolio.

If you already have products (existing products) in the system before enabling the single record sharing, these will not be shared.

## More information on cross-company data sharing

To learn more about cross-company data sharing, please refer to [Cross-company data sharing](../../fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing.md).
