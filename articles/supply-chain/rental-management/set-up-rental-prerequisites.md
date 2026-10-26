---
title: Configure prerequisites for rental management (preview)
description: Configure the standard Dynamics 365 Finance and Supply Chain Management settings that rental management depends on before you set up the module.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Configure prerequisites for rental management (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Before you configure the rental management module itself, turn rental management on and set up several standard Dynamics 365 Finance and Supply Chain Management components. This article covers the prerequisite setup steps in the order that you complete them.

<a name="turn-on-feature"></a>

## Turn on rental management

Rental management requires both a configuration key and feature management. Turn on both before you configure anything else. You set these elements just once for the environment, but the rest of the rental setup is per legal entity, so you must repeat the other setup steps in each company that rents.

1. Put your system into maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. Go to **System administration** > **Setup** > **License configuration**.
1. On the **Configuration keys** tab, expand the **Trade** node and then select the check box for **Rental Management**.
1. Turn off maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. Go to **System administration** > **Workspaces** > **Feature management**.
1. Find and select *(Preview) Rental management*. Then select **Enable now** in the dialog.

The **Rental management (Preview)** module is now available in the navigation pane under **Modules**.

## Rental management setup sequence

To set up each legal entity that uses rental management, complete the steps described in this article first, and then continue by following the order given in [Rental management setup overview](set-up-rental-overview.md).

## Configure item model groups

Configure an item model group for fleet item products before you assign it to released products. Follow [Set up item model groups](configure-inventory-location-settings.md#set-up-item-model-groups) for the inventory costing, stocked product, and posting settings.

## Configure item groups

An *item group* classifies products for financial posting. Each group holds the ledger accounts that the inventory side of a product's transactions posts to, so the item group on a fleet item determines which accounts receive its purchases, fleet transfers, and sales. Rental management doesn't have a separate posting profile for fleet items, so these standard item group accounts carry every fleet item inventory posting.

To set up item groups, go to **Inventory management** > **Setup** > **Inventory** > **Item groups**.

Create at least one item group for fleet items. Assign this item group to the released products that you use as fleet items. If fleet items in different item groups need different fixed asset groups or books, use the **Posting configuration for fleet types** page to make settings for each item group. Learn more in [Configure fleet types](configure-inventory-location-settings.md#configure-fleet-types).

After you create an item group, configure its inventory posting so that purchase receipts and vendor invoices for fleet items post to the correct ledger accounts. Go to **Inventory management** > **Setup** > **Posting** > **Posting** and set up the posting rules for the fleet item group. Learn more in [Inventory posting profiles](../../finance/general-ledger/inventory-posting-profiles.md).

When a fleet item is transferred to a fleet type whose **Value tracking method** is *Fixed asset*, the inventory side of the transfer posts to the item group's **Fixed asset issue** account. If the item group has no **Fixed asset issue** account, the transfer posts to its **Inventory issue** account.

## Configure tracking dimension groups

Configure a tracking dimension group for serialized fleet items. Follow [Set up tracking dimension groups](configure-inventory-location-settings.md#set-up-tracking-dimension-groups) for serial-number tracking and valuation settings.

## Configure storage dimension groups

Configure a storage dimension group for fleet item products. Follow [Set up storage dimension groups](configure-inventory-location-settings.md#set-up-storage-dimension-groups) for site, warehouse, and optional location settings.

For product-level site, warehouse, and location defaults, follow [Configure the released product](configure-inventory-location-settings.md#configure-the-released-product).

## Configure sites

A *site* is a geographical grouping of warehouses within a legal entity. Sites let you separate inventory and its financial posting by physical operation, and each site can carry its own financial dimensions. Rental branches operate within standard Dynamics 365 Supply Chain Management sites, so the site on a fleet item determines which branch the item's inventory transactions are attributed to. Create one site per branch unless branches share a single site.

To set up sites, go to **Inventory management** > **Setup** > **Inventory breakdown** > **Sites**.

## Configure warehouses

Create a warehouse for each branch or site that holds rental fleet inventory. Follow [Warehouse setup for rental operations](configure-inventory-location-settings.md#warehouse-setup-for-rental-operations) to configure its site, address, and inventory settings.

## Configure sales categories and sales hierarchy

*Revenue categories* map to standard sales categories for financial posting. You must configure a sales category hierarchy before you can create rental revenue categories.

To set up sales categories, go to **Product information management** > **Setup** > **Categories and attributes** > **Category hierarchies**. Create or assign a sales hierarchy and populate it with the sales categories you plan to use for rental revenue posting (for example, *Rental revenue*, *Damage waiver*, *Environmental fee*).

Rental invoice revenue posts to the sales order revenue account that inventory posting assigns to the sales category. For each of these sales categories, set up a **Revenue** account on the **Sales order** tab of **Inventory management** > **Setup** > **Posting** > **Posting**, with **Item code** set to *Category*. Learn more in [Revenue posting for rental invoices](understand-rental-financial-integration.md#revenue-posting-for-rental-invoices).

## Configure journal names

A *journal name* is a reusable template for a journal. It sets the journal type, the number sequences that supply journal and voucher numbers, and the default posting behavior. Rental management posts several kinds of transaction through journals, and each of those transactions needs its own journal name before the process that creates it can run. Create the journal names described in this section, and then assign them on the **Rental parameters** page.

Learn more about the available types in [Inventory journals](../inventory/inventory-journals.md).

### Inventory journal names

To create the required inventory journal names, go to **Inventory management** > **Setup** > **Journal names** > **Inventory** and create journal names for the following:

| Purpose | Journal type |
|---|---|
| Location update journal (updating a fleet item's inventory location) | Transfer |
| Serial number update journal | Transfer |
| Transfer request movement journal | Movement |
| Transfer request inventory asset journal | Fixed assets |

### Ledger journal names

To create the required ledger journal names, go to **General ledger** > **Journal setup** > **Journal names** and create journal names for the following:

| Purpose | Journal type |
|---|---|
| Revenue split posting journal | Daily |
| Carrying cost journal | Post fixed assets |
| Transfer journal (fixed asset transactions of fleet transfers out of a fleet type whose **Value tracking method** is *Fixed asset*) | Post fixed assets |
| Cash register journal | Customer payment |

### Assign journal names to rental parameters

After you create these journal names, assign them to the corresponding fields on the **Rental parameters** page (for example, **Location update**, **Serial number update journal**, and **Transfer request inventory asset journal**). Learn more in [Configure posting journals](set-up-rental-reference-data.md#configure-posting-journals).

## Configure fixed asset groups

When you transfer a fleet item to a fleet type whose **Value tracking method** is *Fixed asset*, the system automatically creates a fixed asset and assigns it to a *fixed asset group*. You must create fixed asset groups before you can process fleet transfers.

To set up fixed asset groups, go to **Fixed assets** > **Setup** > **Fixed asset groups**.

Create at least one fixed asset group for rental fleet assets. The **Posting configuration for fleet types** page maps fleet types to fixed asset groups. Learn more in [Configure fleet types](configure-inventory-location-settings.md#configure-fleet-types).

When you create a new fixed asset, the system assigns it an asset ID according to the following rules:

- If **Autonumber fixed assets** is set to *Yes* for the fixed asset group, the asset ID comes from the number sequence of the fixed asset group.
- If **Autonumber fixed assets** is set to *No* for the fixed asset group, but is set to *Yes* on the **Fixed assets parameters** page, the asset ID comes from the fixed asset number sequence.
- If both of the mentioned **Autonumber fixed assets** settings are set to *No*, the asset ID is set to the fleet item number.
- For bulk fleet items, the asset ID always comes from a number sequence, regardless of the previous settings.

Set **Autonumber fixed assets** to *Yes* for the fixed asset group or on the **Fixed assets parameters** page before you transfer bulk fleet items.

## Configure depreciation profiles

*Depreciation profiles* control how the system depreciates rental fleet assets. Common depreciation methods for fleet items include:

- *Revenue based* – The system posts depreciation as a percentage of rental invoice revenue.
- *Straight line service life* – Even depreciation over a fixed period. Commonly used for attachments.
- *SMU based* – Depreciation based on the service meter unit (SMU) hours recorded on the fleet item's usage history.

To set up depreciation profiles, go to **Fixed assets** > **Setup** > **Depreciation profiles**.

Learn more about the available depreciation methods, and about how to configure and run the two rental-specific methods, in [Understand rental management financial integration](understand-rental-financial-integration.md#use-standard-depreciation-methods).

## Configure fixed asset books

*Fixed asset books* define the depreciation settings for each fleet asset. When you transfer a fleet item to a fleet type whose **Value tracking method** is *Fixed asset*, the system creates a fixed asset and assigns the asset book specified on the **Posting configuration for fleet types** page for that fleet type. Learn more in [Configure fleet types](configure-inventory-location-settings.md#configure-fleet-types).

To set up fixed asset books, go to **Fixed assets** > **Setup** > **Books**.

For each book that you use with rental fleet assets:

1. Assign the appropriate **Depreciation profile**.
1. On the **General** FastTab, verify that **Post to general ledger** is set to *Yes* if you want the depreciation to create ledger transactions.
1. Set **Carrying cost** to *Yes* if the *Calculate carrying cost* periodic job covers the book.

The *Revenue based* and *SMU based* depreciation methods take their percentage, useful life, and residual value from the fixed asset group book setup and from the fixed asset's own book. Learn more in [Understand rental management financial integration](understand-rental-financial-integration.md#understand-smu-based-depreciation).

## Configure fixed asset parameters

Fixed asset parameters set the legal-entity-wide defaults for fixed assets, including whether asset IDs come from a number sequence. These defaults apply to the fixed assets that rental management creates automatically when you transfer a fleet item to a fleet type whose **Value tracking method** is *Fixed asset*.

To configure fixed asset parameters, go to **Fixed assets** > **Setup** > **Fixed assets parameters**.

If you want the fixed asset that a fleet transfer creates to use the fleet item number as its asset ID, set **Autonumber fixed assets** to *No*. Set it to *Yes* if you transfer bulk fleet items, which always take their asset IDs from a number sequence.

Select a **Posting profile** because a fleet transfer out of a fleet type whose **Value tracking method** is *Fixed asset* posts its *Disposal - sale* transaction with the profile you choose here.

On the **Barcode** FastTab, set **Autonumber fixed assets** to *No*. Also set **Autonumber fixed assets** to *No* on the fixed asset groups configured on the **Posting configuration for fleet types** page. Learn more in [Configure fleet types](configure-inventory-location-settings.md#configure-fleet-types).

## Configure fixed asset posting profiles

The system tracks rental fleet items as fixed assets, so their acquisition, depreciation, and disposal transactions post to the general ledger through *fixed asset posting profiles*. A posting profile maps each fixed asset transaction type to the main and offset ledger accounts, per depreciation book.

To set up fixed asset posting profiles, follow these steps:

1. Go to **Fixed assets** > **Setup** > **Fixed asset posting profiles**.
1. Create or select a posting profile (for example, an *ALL* profile described as *FA general posting profile*), and then complete the following steps for each of the books that your rental fleet assets use.
1. On the **Ledger accounts** FastTab, select a posting type and add a line for it. The posting types commonly needed for rental fleet assets are *Acquisition*, *Depreciation*, *Net book value*, *Disposal - sale*, and *Disposal - scrap*. Rental management adds a *Fleet item transfer* posting type, which applies when a fleet item is transferred between two fleet types whose **Value tracking method** is *Fixed asset* and the fixed asset moves to a different book. For each line, specify:
    - **Book** – The depreciation book the accounts apply to (for example, *R90*).
    - **Groupings** – The scope of the entry: *All* (every asset), *Group* (a fixed asset group), or *Table* (a specific asset).
    - **Account relation** – The specific group or asset, used when **Groupings** is *Group* or *Table*.
    - **Main account** – The ledger account the transaction posts to.
    - **Offset account** – The account used for the balancing (offset) entry.

1. On the **Disposal** FastTab, configure how the system splits a disposal across value types when you sell or scrap an asset. Select the disposal method (*Sale* or *Scrap*) and add a line for each relevant **Post value** type. **Post value** types include *Acquisition (this year)*, *Acquisition (prior years)*, *Depreciation (this year)*, *Depreciation (prior years)*, *Net book value*, and *Depreciation adjustments (this year)*. For each line, specify the **Book**, **Groupings**, **Account relation**, **Post value** (the value type), **Sales value type**, **Main account**, and **Offset account** that apply.

    > [!TIP]
    > For transfers from a fleet type tracked as *Fixed asset* to one tracked as *Inventory* (for example, *Rental* to *Used*), use a dedicated transfer (bridge) account as the **Offset account** on the *Sale* disposal lines. The disposal and inventory receipt post to that account. The sale and cost of sale post later, when you invoice the fleet item on a sales order. Learn more in [Understand fleet transfer financial impact](understand-rental-financial-integration.md#understand-fleet-transfer-financial-impact).

    > [!TIP]
    > When a fleet item is transferred to a fleet type whose **Value tracking method** is *Fixed asset*, the fixed asset side of the transfer posts an *Acquisition* that uses the **Acquisition** account here. The inventory side posts to the item group's **Fixed asset issue** account (or its **Inventory issue** account) in inventory posting. Set up both so that the transfer and the ongoing fixed asset postings use consistent accounts. Learn more about how the system uses these accounts during posting in [Understand rental management financial integration](understand-rental-financial-integration.md#understand-how-ledger-accounts-are-determined).

After your fixed asset posting profiles are set up, go to **Rental management** > **Setup** > **Rental parameters** and make the following settings to select the fixed asset posting profile to use for rental-specific postings:

- On the **Fixed assets** tab, set the **Transfer posting profile** to use for *Fleet item transfer* transactions that post when a fleet item is transferred between two fleet types whose **Value tracking method** is *Fixed asset* and the fixed asset moves to a different book. The profile must have an offset account for the *Fleet item transfer* **Post value** type. Learn more in [Understand fleet transfer financial impact](understand-rental-financial-integration.md#understand-fleet-transfer-financial-impact).
- On the **Fleet items** tab, set the **Asset posting profile** to use for fixed asset disposal transactions that post when a sales invoice is posted for a fleet item that's still tracked as a fixed asset.

## Assign rental security roles

Rental management includes six security roles. Assign them in **System administration** > **Security** > **Assign users to roles**. *Rental manager* is the role that maintains the rental setup that's described in this article and in the setup articles that follow it. That setup includes rental parameters, rental templates, period codes, billing scenarios, rental rates, revenue categories, and posting configuration for fleet types.

| Role | What the role covers |
|---|---|
| *Rental clerk* | Shipping, receiving, inspection, and condition documentation for fleet items. |
| *Rental coordinator agent* | Rental desk processes: creating rental quotations and contracts, managing reservations, and generating rental invoices. |
| *Rental manager* | Monitoring fleet items and expenses, governing inventory and purchase decisions, and maintaining rental rates and sales prices across one or more legal entities. |
| *Rental purchasing manager* | Reviewing rental purchasing process performance and overseeing the rental purchasing process. |
| *Rental representative* | Rental sales: engaging customers, coordinating deals with the rental desk, and initiating rental quotations. |
| *Rental sales manager* | Reviewing rental sales process performance and overseeing the rental sales process. |

The roles correspond to the personas described in [Rental management overview](rental-management-overview.md).

## Related information

- [Configure inventory and location settings for rental management](configure-inventory-location-settings.md)
- [Set up rental reference data](set-up-rental-reference-data.md)
- [Configure rental parameters](configure-rental-parameters.md)
- [Understand rental management financial integration](understand-rental-financial-integration.md)
- [Add fleet items to the rental fleet](add-equipment-to-rental-fleet.md)
- [Set up fixed assets](../../finance/fixed-assets/set-up-fixed-assets.md)
