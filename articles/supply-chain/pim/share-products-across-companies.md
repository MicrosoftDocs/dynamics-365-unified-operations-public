---
title: Cross-company product sharing
description: This topic explains how to share released-product data across companies (legal entities), to reduce the volume of data that must be maintained and simplify the task of maintaining product master data.
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

Organizations that have many companies (legal entities) and a large product portfolio (for example, large sales and distribution networks) often experience a high level of duplicated product data. The [cross-company data sharing capabilities](../../fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing.md) of Microsoft Dynamics 365 Supply Chain Management let you share data about released products across multiple companies. In this way, you can reduce the volume of data that must be maintained and at the same time simplify the task of maintaining product master data.

## Get the cross-company product sharing public preview

To sign up for the public preview for this feature, email the environment ID of your environment in Microsoft Dynamics Lifecycle Services (LCS) to the [Cross-Company Product Sharing team](mailto:productsharing@service.microsoft.com). The Microsoft team that is responsible for the feature will send you a follow-up email to get in contact, evaluate whether your business is a match for the functionality, and finally evaluate whether you can join the preview.

## Prepare your system to enable cross-company data sharing for products

Before you enable cross-company data sharing for products, work through the following checklist:

- **Set up the currency.** Either the currency must be the same across all companies in the data sharing policy, or you must avoid using the base price fields.
- **Align number sequences.** Number sequences must be aligned across all companies in the data sharing policy.
- **Enable policies in the correct order.** Duplicate shared policies must be enabled before single record sharing policies.
- **Specify the default parameters for each company.** You might want to align default parameters across all companies in the data sharing policy.
- **Consider whether any of your business processes are affected by the single record sharing functionality.** Read the detailed list of [limitations and notes that apply for shared products](#limitations) later in this topic, and prepare your system as required.

## Set up the products and product-related information sharing policies

To share products and product-related information, you must create and set up your sharing policies on the **Configure cross-company data sharing** page. Each sharing policy establishes a set of tables and fields that are shared. To get started quickly, you can edit the sharing policy templates that are provided and then use them to set up your own default sharing policies. For more information about how to use a template, see [Configure financial cross-company data sharing](../../fin-ops-core/dev-itpro/data-entities/tasks/configure-financial-cross-company-data-sharing.md).

You can use either of the following sharing policies to share product information:

- **Duplicate record sharing** – Each company has its own copy of the shared product record. Every time that product information is edited in any company, the update is immediately replicated to every other company's copy of the product record.
- **Single record sharing** – Just one shared record exists for each product in the database, and all relevant companies can view and edit that record.

When you share product information, we recommend that you use a single record sharing policy, because it uses database resources more efficiently, especially for companies that have large product portfolios. However, for related data and policies that indicate how a product is managed in different companies, we recommend that you use a duplicate record sharing policy. In this way, you can manage products differently in each company where they are used (for example, for production-related policies such as production pools).

> [!IMPORTANT]
> If a field is included in a table that is part of a single record sharing policy, the field and its table will also be shared as a single record, unless duplicate record sharing is specified by a policy that was previously enabled. Therefore, duplicate record sharing policies must be enabled before single record sharing policies. For example, if you use duplicate record sharing for production pools, you must enable the production pool policy before you enable the products.

### Templates for duplicate record sharing of product information

The following product-related templates are available for duplicate record sharing:

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

The following product-related template is available for single record sharing:

- Products

## Shared product-related tables and fields

Many tables and fields are related to products. Most of them are included in the template policies that are provided.

To enable fields and tables to be shared, you must specify sharing metadata for each table. If a table isn't included in the template, you can add it to a cross-company sharing policy and share it only if sharing metadata has previously been set by Microsoft. If you want to share a table that isn't currently set up for sharing, submit a request to Microsoft Support.

## <a name="limitations"></a>Limitations and notes that apply to shared products

This section provides notes and summarizes the limitations that apply when you share product information between companies in different scenarios.

### Item templates

You can't apply item templates to child companies, because the `SysRecordTemplateTable` table isn't shared. Therefore, the **Apply template** command is unavailable in child companies.

### Currencies and base prices

Base prices (such as the sales price, purchase price, and inventory price) are implicitly expressed in the accounting currency of each company.

The accounting currency for each company is set up in the **Accounting currency** field on the **Ledger** page (**General ledger \> Ledger setup \> Ledger**).

For companies that are part of a cross-company policy, the following cases apply:

- **All companies in the policy use the same accounting currency** – There are no special limitations to consider.
- **Companies in the policy use different accounting currencies** – The currency isn't explicitly specified. Instead, it's implicit for each company. Therefore, if one amount (such as the base sales price) is shared across companies, each company will assume a different currency. For example, the USMF company uses US dollars (USD), whereas the JPM company uses Japanese yen (JPY). If the base sales price is 20, the USMF company will assume that the amount is 20 USD, but the JPM company will assume that it's 20 JPY. Because 20 USD and 20 JPY don't represent the same monetary value, one of the companies will sell the item at a price that is either too high or too low.

Therefore, only one of the following rules applies:

- **All companies that are part of a cross-company data sharing policy for sharing products must use the same accounting currency.** If you rely on fields that use an implicit currency (such as the base sales price or purchase sales price), you must set the same accounting currency in all companies that are part of the product sharing policy.
- **You must not rely on the value of these fields.** Use trade agreements for purchase and sales prices, and don't use the inventory price or its related processes.

### Country/region-specific fields

By default, most country/region-specific fields are disabled in product tables, because they aren't supported. Therefore, if you want to share those fields, you must add them as an extension. Add the country/region-specific tables to the policy, and then select the fields that must be shared.

### Default unit of measure

When you create a product, you must specify several different units of measure, each for a specific purpose. For example, you might specify an inventory unit, a purchase unit, and a sales unit. The **New released product** dialog box shows the same default unit for all of them, based on the default setting for the current company. However, you can edit the unit for each unit of measure separately in the dialog box.

To assign the default unit for a company, follow these steps.

1. On the navigation bar, select the company (legal entity) that you want to set defaults for.
1. Go to **Inventory management \> Setup \> Inventory and warehouse management parameters**.
1. On the **General** tab, in the **Default values** section, in the **Unit** field, set the default unit for the current company.

> [!IMPORTANT]
> The default unit depends on the company that the product is created in. If you want the default behavior to be aligned, set the same default unit for all companies.

### Physical dimensions units

The **Released products** page shows physical dimensions for each released product. These dimensions include weight and height. However, the unit for the measurements isn't shown on the page and is therefore implicit. The unit that is used for each measurement is the system unit in each unit class. Because these system units are cross-company, there are no specific actions or limitations that you must consider in this area.

> [!NOTE]
> The system unit for each class is set up on the unit itself, and only one unit in the unit class can be a system unit. If no unit is set up as the system unit, the value of the fields will have no meaning, and processes (such as warehousing) that rely on the existence of a system unit can't be completed. For more information, see [Manage units of measure](tasks/manage-unit-measure.md).

### Bills of materials, formulas, and routes

We recommend that you manage bills of materials (BOMs), formulas, and routes in each company. Therefore, BOMs, formulas, and routes aren't shared in the provided templates.

### Coverage groups – Calendar

When you share the coverage groups for an item, the calendar on a coverage group isn't shared in the provided templates. If you want to share it, create a new policy for calendar sharing, or add the calendar table to the coverage group policy.

### Product configurator

Constraint-based configuration products don't have any limitations. The product is shared when it's created, and the variant that is created on the fly is also shared cross-company.

### Number sequences

Number sequences can be used for product numbers and other purposes. Number sequences must be shared if they are used with single record sharing of products.

### Dual-write

Dual-write isn't currently supported when you use cross-company data sharing for products.

### Dynamics 365 Commerce

Dynamics 365 Commerce isn't supported when you use cross-company data sharing for products.

### Financial dimensions

Fields that reference financial dimensions (for example, the Ledger or Default dimension) can't be shared across companies. This limitation is a restriction of cross-company data sharing. For more information, see [Cross-company data sharing](../../fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing.md).

### Vendors

There is no template policy for the vendors table (`vendtable`). Because the vendors table is marked as a single record shared table, you can create a policy for single record sharing and add the table.

### Item sales tax group and item purchase tax groups

Item sales tax groups and item purchase tax groups are specified at the product level. The item sales tax group value automatically enters a default tax group on each sales order line, and the item purchase tax group value automatically enters a default tax group on each purchase order line. For convenience when default values are entered, the values are set to duplicate record sharing and are added in the SRS products template. Although the names of the tax groups are shared across companies, their details and settings are company-specific. Therefore, because tax groups are specific to each item in the company context, you must set up those details and settings in the company part of the sharing policy.

### Distributed hybrid environment

If you're using a [distributed hybrid environment](../cloud-edge/cloud-edge-landing-page.md) that includes cloud or edge scale units, cross-company data sharing for products isn't supported.

### Engineering change management

Some functionality that engineering change management provides might conflict with single record sharing of products or, when it's used in specific ways, might be complementary.

The following engineering change management concepts will be affected if you use single record sharing of products:

- **Definition of engineering companies** – Engineering change management lets you set up one or more engineering companies. These engineering companies might be organizations that represent one or more existing companies where your engineering department is located. Alternatively, you might set up a dedicated company that doesn't represent an actual engineering department, but that you use to manage master data and control the release of products for your organization. For more information about engineering companies, see [Engineering companies and data ownership rules](../engineering-change-management/engineering-org-data-ownership-rules.md).
- **Release product structure** – From the engineering company, you can use a controlled process to release a product to other companies. For more information about the release product structure, see [Release product structures](../engineering-change-management/release-product-structure.md).

The tables that are related to engineering versions aren't shared, because they are meant to be contained in engineering and to be shared only with a controlled release. Therefore, if you use engineering change management, you might choose one of the following setups:

- **Your engineering company is part of the single record sharing policy** – In this case, most of the engineering-related functionality isn't applicable, especially the controlled release. As soon as the product is created as a released product in the engineering company, it's shared (that is, made available) to the rest of your companies. Therefore, the engineering company loses its engineering character, because it's longer a space where the engineering team can work on products, and only those products that continue forward are used in the system.

    Because the engineering versions aren't shared, the version information is available only in the engineering company. Therefore, this setup has the following implications:

    - Engineering versions exist only in the engineering company, unless they are shared by using the release product structure.
    - The lifecycle state at the version level works only in those companies where the version information has been shared. Therefore, you can't control the processes that a version of a product is being used in unless the version is shared with its released product structure.
    - Release control is lost, because the product is shared across all companies.
    - The BOM and route are kept locally. You must manage the BOMs and BOM versions (and also the routes and route versions) at the company level. Therefore, you can still use the release product structure to share the BOM and route.

    We don't recommend this setup, because much of the value of engineering change management is lost.

- **Your engineering company isn't part of the single record sharing policy for products** – You can set up your engineering company so that it isn't part of the shared product policy. You can then make a sharing policy that includes all the companies where product introduction is done at the same time. In this case, you can release a product to one company to make it available in all the companies.

    Note that if you require version management, you must still release the version information with the release product structure. Therefore, your organization must have an engineering company where products are designed and managed. Then, when a product is ready, you do a controlled release to the rest of the companies. (This type of controlled release is the main goal of the engineering change management functionality.) In this case, you create the product in the engineering company and then release it to all the companies that are part of the sharing policy. Note that the released product will be released to all the companies at the same time, because they are sharing the same product record.

    Be aware that version-related tables (such as engineering versions) aren't shared. Therefore, you must not rely on version management outside the engineering organization. Alternatively, if you require version management in all companies, you must release version-related information with the release product structure.

### Sites and warehouses

Sites and warehouses aren't shared. The `InventLocation` and `InventSite` tables aren't shared. We expect that you will keep sites and warehouses at the company level.

## Existing products

When you enable single record sharing for products, it's important that you create and enable the single record sharing policies, and then start to import or create your product portfolio.

If you already have existing products in the system before you enable the single record sharing policies, they won't be shared.

## More information about cross-company data sharing

To learn more about cross-company data sharing, see [Cross-company data sharing](../../fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing.md).
