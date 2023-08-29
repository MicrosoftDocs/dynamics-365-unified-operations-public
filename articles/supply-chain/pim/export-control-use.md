---
title: Work with advanced export control for products and sales orders
description: Learn how to work with advanced export control for products and sales orders.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: EcoResProductDetails, EcoResProductDetailsExtended
ms.topic: overview
ms.date: 08/29/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Work with advanced export control for products and sales orders

The advanced export control feature lets you apply export control rules to sales orders. Individual jurisdictions can be enabled or disabled for each legal entity (company). Therefore, each company can have different export control behaviors and rules.

## Set up jurisdictions, codes, restrictions, exceptions, and licenses

To define the export controls that apply to the items that you trade in, set up the required *export control jurisdictions* in Dataverse. Then configure the *codes*, *restrictions*, *exceptions*, and *licenses* that apply for each jurisdiction. (For more information about these terms, see [Advanced export control overview](export-control-overview.md).)

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. Go to **Environments**, and select your environment.
1. On the page for the selected environment, in the **Details** section, select the link under **Environment URL**.
1. Your Dataverse environment is opened. On the left navigation pane, select **Export control jurisdictions**.
1. A list of existing export control jurisdictions is shown. Use the buttons on the toolbar to add or remove jurisdictions as you require.
1. Select a jurisdiction to open its details page. Use the jurisdiction details page to define the jurisdiction, and to add or remove codes, restrictions, exceptions, and licenses as you require.

## Assign export control classifications for global products

When advanced export control is [enabled](export-control-configure.md), it adds a new **Advanced export control configuration** FastTab to the **Product details** page for products and product masters. Use this FastTab to specify the Export Control Classification Number (ECCN) and other export control settings for the product in different jurisdictions.

To set up advanced export control for a product or product master, follow these steps.

1. Sign in to Microsoft Dynamics 365 Supply Chain Management.
1. Go to **Product information management \> Products \> All products and product masters**.
1. Find and open the product that you want to work with.
1. On the **Product details** page, select the **Advanced export control configuration** FastTab.

    [<img src="media/export-control-product-jurisdictions.png" alt="Export control settings for products." title="Export control settings for products" width="720" />](media/export-control-product-jurisdictions.png#lightbox)

1. The grid lists each export control that applies to the current product. Use the buttons on the toolbar to add and remove rows as you require. For each row, set the following fields:

    - **Export control jurisdiction** – Select the jurisdiction where the current row applies. Because global products can be released to different legal entities, the list shows all available jurisdictions, not just the jurisdictions that are enabled for the currently selected legal entity.
    - **Export control classification** – Select the ECCN that applies to the current row. The ECCN establishes the set of export control rules that apply to the current product for the jurisdiction that's selected in this row.

1. On the Action Pane, select **Save**.

## Assign export control classifications for released products

When you create a released product that's based on a global product, the **Advanced export control configuration** settings for the global product become default export control values for the released product. If the **Advanced export control configuration** settings for the global product are changed after the product is released, those new settings aren't updated on the related released product unless the product is re-released. Because released products are associated with a specific legal entity, only the ECCNs for jurisdictions that are enabled for that legal entity are inherited from the global product.

To set up advanced export control for a released product, follow these steps.

1. Use the company picker to select the legal entity where you want to work.
1. Go to **Product information management \> Products \> Released products**.
1. Find and open the product that you want to work with.
1. On the **Released product details** page, select the **Foreign trade** FastTab.

    [<img src="media/export-control-item-jurisdictions.png" alt="Export control settings for released products." title="Export control settings for released products" width="720" />](media/export-control-item-jurisdictions.png#lightbox)

1. If at least one jurisdiction is [enabled](export-control-configure.md) for the selected legal entity, the **Foreign trade** FastTab includes an **Export control codes** section. (Otherwise, simpler [dual-use goods](dual-use.md) functionality is shown instead.) The grid in this section lists each export control that applies to the current released product. Use the buttons on the toolbar to add and remove rows as you require. For each row, set the following fields:

    - **Export control jurisdiction** – Select the jurisdiction where the current row applies. This list is filtered so that it shows only the jurisdictions that are used in the currently selected legal entity.
    - **Export control classification** – Select the ECCN that applies to the current row. The ECCN establishes the set of export control rules that apply to the current product for the jurisdiction that's selected in this row.

1. On the Action Pane, select **Save**.

## Checking and enforcing export control rules for sales orders

When advanced export control is [enabled](export-control-configure.md) for a legal entity, a **Check export control** button is provided on the **Sell** tab of the Action Pane for sales orders. Select this button to check the export control status of the current order. The same check is performed during confirmation, picking, packing, shipping, and invoicing. License quantity is consumed and history is tracked only during confirmation and similar steps. Manual checks don't change license consumption and aren't tracked in history.

[<img src="media/export-control-sales-order-check.png" alt="Check export control dialog box." title="Check export control dialog box" width="720" />](media/export-control-sales-order-check.png#lightbox)

The sales order header has a tab where you can specify licenses per jurisdiction. Licenses that are specified on the header are assumed to be used by default on all lines of the document. However, the licenses can be overridden at the line level. Licenses must pass export control checks only if restrictions and exceptions require a license. Blanket exemptions or corporate policies don't require licenses.

During confirmation and similar posting steps, the system tracks the history of export control checks. You can view this history from the sales order header by selecting **Result**.

[<img src="media/export-control-sales-order-header.png" alt="Export control settings for sales order headers." title="Export control settings for sales order headers" width="720" />](media/export-control-sales-order-header.png#lightbox)

Licenses from the sales order header can be overridden on the sales order lines. In this way, different lines can be related to different licenses. You can also override the export control check at the line level. In this case, the export control check is still performed and tracked, but failures don't block the document processing. The user who edited the override information is automatically tracked on the record. This information can be audited by using the standard [logging](../../fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log.md) functionality for finance and operations apps.

[<img src="media/export-control-sales-order-line.png" alt="Export control settings for sales order lines." title="Export control settings for sales order lines" width="720" />](media/export-control-sales-order-line.png#lightbox)
