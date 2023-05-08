---
title: Cross-company product sharing
description: This article explains how to share released-product data across companies (legal entities), to reduce the volume of data that must be maintained and simplify the task of maintaining product master data.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/30/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Cross-company product sharing

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice.-->

Organizations that have many companies (legal entities) and a large product portfolio (for example, large sales and distribution networks) often experience a high level of duplicated product data. The [cross-company data sharing capabilities](../../fin-ops-core/dev-itpro/sysadmin/srs-overview.md) of Microsoft Dynamics 365 Supply Chain Management let you share data about released products across multiple companies. In this way, you can reduce the volume of data that must be maintained and at the same time simplify the task of maintaining product master data.

## Get the cross-company product sharing public preview

To sign up for the public preview for this feature, email the environment ID in Microsoft Dynamics Lifecycle Services to the [Cross-company product sharing team](mailto:productsharing@service.microsoft.com). The Microsoft team that is responsible for the feature will send you a follow-up email to get in contact, evaluate whether your business is a match for the functionality, and finally evaluate whether you can join the preview.

## Get started with cross-company data sharing

Single record sharing and duplicate record sharing work in the following way:

- **Single record sharing** – Just one shared record exists in the database, and all relevant companies can view and edit that record.
- **Duplicate record sharing** – Each company has its own copy of every shared record. Each time that the shared record is edited in any company, the edit is immediately replicated to every other company's copy of the record.

When you share product information across companies, the sharing works in the following way:

- The released products table (`Inventtable`) must use *single record sharing*.
- For related tables (which typically hold policies for handing a product, such as the bar code setup and the cost group), you must decide whether you want to use *single record sharing* or *duplicate record sharing*. In most cases, you'll probably decide to use duplicate record sharing for related tables, because single record sharing imposes several restrictions that duplicate record sharing doesn't impose. (For more information, see [Cross-company data sharing overview](../../fin-ops-core/dev-itpro/sysadmin/srs-overview.md).)

Before you continue to read this article, we recommend that you read [Cross-company data sharing overview](../../fin-ops-core/dev-itpro/sysadmin/srs-overview.md) to learn more about how data sharing works in Supply Chain Management.

## Prepare your system to enable cross-company data sharing for products

Before you enable cross-company data sharing for products, work through the following checklist:

- **Set up the currency.** Either the currency must be the same across all companies in the data sharing policy, or you must avoid using the base price fields.
- **Align number sequences.** Number sequences must be aligned across all companies in the data sharing policy.
- **Enable policies in the correct order.** Duplicate shared policies must be enabled before single record sharing policies.
- **Specify the default parameters for each company.** You might want to align default parameters across all companies in the data sharing policy.
- **Consider whether any of your business processes are affected by the single record sharing functionality.** Read the detailed list of [limitations and notes that apply for shared products](#limitations) later in this article, and prepare your system as required.

## Set up your system for product sharing

After you contact Microsoft, if you're accepted for the preview, Microsoft will enable a flight for you. You can then set up your system to share products across companies.

To set up your system for product sharing, follow these steps.

1. If you're running Supply Chain Management version 10.0.31, follow these steps. (You can skip them if you're running version 10.0.32 or later.)

    1. Enable the following flights:
 
        - `DbSyncEnableSingleRecordSharing`
        - `EnableSysSharing`

    1. Do a database synchronization.

    If you don't know how to complete these steps, contact Microsoft Support.

1. Go to the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md), and enable the following features:

    - *(Preview) Master company data sharing*
    - *(Preview) Cross-company data sharing for products*

## Set up sharing policies for products and product-related information

To share products and product-related information, you must create and set up your sharing policies on the **Configure cross-company data sharing** page. Each sharing policy establishes a set of tables and fields that are shared.

> [!IMPORTANT]
> If a field in a table that's being enabled for single record sharing holds a foreign key for a related table, that related table will also be shared by using single record sharing, unless a duplicate record sharing policy for it already exists and is enabled. Therefore, all the duplicate record sharing policies that you require must be enabled before you start to set up your single record sharing policies. For example, if you plan to use duplicate record sharing for production pools, you must enable the production pool policy before you enable the products (and the products must use single record sharing).

### Set up duplicate record sharing policies

We recommend that you set up duplicate record sharing for tables that handle policies and related information.

To create a duplicate record sharing policy, follow these steps. You can create as many duplicate record sharing policies as you want.

1. Go to **System administration \> Setup \> Configure cross-company data sharing**.
1. On the Action Pane, select **New**.
1. In the **Name** field, enter a name for the policy (for example, *Product policies - duplicate sharing*).
1. Leave the **Master company data sharing policy** option set to *No*. (This option doesn't apply to *duplicate record sharing* policies.)
1. On the Action Pane, select **Save**.
1. In the **Companies which share the records in these tables** section, add each company that will share the tables that you'll add for this policy.
1. In the **Tables and fields to share** section, select **Add** on the toolbar.
1. In the drop-down dialog box, in the **Table name** field, select a table. For more information about which tables you might select, see the [Product information tables that can be shared](#tables) section later in this article.

    > [!NOTE]
    > Not all tables are enabled for record sharing. If the table that you want to share isn't available for selection in the **Table name** field, send a request to Microsoft Support, and we'll consider adding sharing support for the requested table in the future.

1. Select **Add table**. Your table is added.
1. Select which fields (and which related tables, if any) should be shared by selecting and clearing the different checkboxes.
1. Repeat steps 7 through 10 for each additional table that you want to share by using this policy.
1. On the Action Pane, select **Save**.

### Set up single record sharing policies

The *Released product* table (`Inventtable`) must be set up for single record sharing.

To create single record sharing policies for the **Released product** table and other tables, follow these steps.

1. Go to **System administration \> Setup \> Configure cross-company data sharing**.
1. On the Action Pane, select **New**.
1. In the **Name** field, enter a name for the policy (for example, *Products - single record sharing*).
1. Set the **Master company data sharing policy** option to *Yes*. This setting is required for *single record sharing* policies.
1. Set the **Master company** field to the company that will be used as the master. This company is the one that the single record is assigned to.
1. On the Action Pane, select **Save**.
1. In the **Child companies** section, add each company that will share the tables that you'll add for this policy.
1. In the **Tables and fields to share** section, select **Add** on the toolbar.
1. In the drop-down dialog box, in the **Table name** field, select a table (for example, *Inventtable*). Then select **Add table**.
1. Expand the newly added table, and review the status of each of its fields. (A check mark indicates enabled fields.) Take special note of the status of fields that reference another table. (These are labeled with the text "foreign key.") Either make sure that you've included the related table as part of a duplicate record sharing policy or be aware that the related tables will now also be shared by using single record sharing.

<!-- KFM: We have an issue with the templates, so hide this until we solve it:

To get started quickly, you can edit the sharing policy templates that are provided and then use them to set up your own default sharing policies. For more information about how to use a template, see [Configure financial cross-company data sharing](../../fin-ops-core/dev-itpro/data-entities/tasks/configure-financial-cross-company-data-sharing.md).

-->

## <a name="tables"></a>Product information tables that can be shared

To share products across companies, the following table *must* be shared by using *single record sharing*:

- Released products (`Inventtable`)

The following product-related tables can be shared by using either *duplicate record sharing* or *single record sharing*:

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

Number sequences can be used for product numbers and other purposes. Number sequences must be shared if they're used with single record sharing of products.

### Dual-write

Dual-write isn't currently supported when you use cross-company data sharing for products.

### Dynamics 365 Commerce

Dynamics 365 Commerce isn't supported when you use cross-company data sharing for products. You can't use Commerce and cross-company data sharing in the same system, because shared products won't be synced to the point of sale (POS) system.

### Financial dimensions

Fields that reference financial dimensions (for example, the Ledger or Default dimension) can't be shared across companies. This limitation is a restriction of cross-company data sharing. For more information, see [Cross-company data sharing overview](../../fin-ops-core/dev-itpro/sysadmin/srs-overview.md).

### Vendors

There's no template policy for the vendors table (`vendtable`). Because the vendors table is marked as a single record shared table, you can create a policy for single record sharing and add the table.

### Item sales tax group and item purchase tax groups

Item sales tax groups and item purchase tax groups are specified at the product level. The item sales tax group value automatically enters a default tax group on each sales order line, and the item purchase tax group value automatically enters a default tax group on each purchase order line. For convenience when default values are entered, the values are set to duplicate record sharing and are added to the *Products* template for single record sharing. Although the names of the tax groups are shared across companies, their details and settings are company-specific. Therefore, because tax groups are specific to each item in the company context, you must set up those details and settings in the company part of the sharing policy.

### Distributed hybrid environment

If you're using a [distributed hybrid environment](../cloud-edge/cloud-edge-landing-page.md) that includes cloud or edge scale units, cross-company data sharing for products isn't supported.

### Engineering change management

Some functionality that engineering change management provides might conflict with single record sharing of products or, when it's used in specific ways, might be complementary.

The following engineering change management concepts will be affected if you use single record sharing of products:

- **Definition of engineering companies** – Engineering change management lets you set up one or more engineering companies. These engineering companies might be organizations that represent one or more existing companies where your engineering department is located. Alternatively, you might set up a dedicated company that doesn't represent an actual engineering department, but that you use to manage master data and control the release of products for your organization. For more information about engineering companies, see [Engineering companies and data ownership rules](../engineering-change-management/engineering-org-data-ownership-rules.md).
- **Release product structure** – From the engineering company, you can use a controlled process to release a product to other companies. For more information about the release product structure, see [Release product structures](../engineering-change-management/release-product-structure.md).

The tables that are related to engineering versions aren't shared, because they're meant to be contained in engineering and to be shared only with a controlled release. Therefore, if you use engineering change management, you might choose one of the following setups:

- **Your engineering company is part of the single record sharing policy** – In this case, most of the engineering-related functionality isn't applicable, especially the controlled release. As soon as the product is created as a released product in the engineering company, it's shared (that is, made available) to the rest of your companies. Therefore, the engineering company loses its engineering character, because it's longer a space where the engineering team can work on products, and only those products that continue forward are used in the system.

    Because the engineering versions aren't shared, the version information is available only in the engineering company. Therefore, this setup has the following implications:

    - Engineering versions exist only in the engineering company, unless they're shared by using the release product structure.
    - The lifecycle state at the version level works only in those companies where the version information has been shared. Therefore, you can't control the processes that a version of a product is being used in unless the version is shared with its released product structure.
    - Release control is lost, because the product is shared across all companies.
    - The BOM and route are kept locally. You must manage the BOMs and BOM versions (and also the routes and route versions) at the company level. Therefore, you can still use the release product structure to share the BOM and route.

    We don't recommend this setup, because much of the value of engineering change management is lost.

- **Your engineering company isn't part of the single record sharing policy for products** – You can set up your engineering company so that it isn't part of the shared product policy. You can then make a sharing policy that includes all the companies where product introduction is done at the same time. In this case, you can release a product to one company to make it available in all the companies.

    If you require version management, you must still release the version information with the release product structure. Therefore, your organization must have an engineering company where products are designed and managed. Then, when a product is ready, you do a controlled release to the rest of the companies. (This type of controlled release is the main goal of the engineering change management functionality.) In this case, you create the product in the engineering company and then release it to all the companies that are part of the sharing policy. The released product will be released to all the companies at the same time, because they're sharing the same product record.

    Version-related tables (such as engineering versions) aren't shared. Therefore, you must not rely on version management outside the engineering organization. Alternatively, if you require version management in all companies, you must release version-related information with the release product structure.

### Sites and warehouses

Sites and warehouses can be shared. To share them, include the `InventLocation` table (for warehouses) and/or the `InventSite` table (for sites) in a sharing policy. If you don't share these tables, all sites and warehouses will be company specific. Therefore, they will have to be created in every company.

## Existing products

When you enable single record sharing for products, it's important that you create and enable the single record sharing policies, and then start to import or create your product portfolio.

> [!IMPORTANT]
> A company that already has product records can never be made into a child company for single record sharing. Therefore, in most cases, you can set up product sharing only when you're setting up a new system.

If you already have existing products in the system before you enable the single record sharing policies, they won't be shared.

## Modifying policies

Note it is not possible to add more fields to a data sharing policy once it has been created and enabled. 

## More information about cross-company data sharing

To learn more about cross-company data sharing, see [Cross-company data sharing overview](../../fin-ops-core/dev-itpro/sysadmin/srs-overview.md).
