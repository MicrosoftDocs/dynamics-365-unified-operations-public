---
title: Review impact of purchase order changes from vendors (production ready preview)
description: Purchase order impact analysis helps you review and respond to vendor changes. Learn how to assess and manage supply chain risks.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/24/2026
ms.custom:
  - bap-template
---

# Review impact of purchase order changes from vendors (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Impact analysis can automatically run based on supplier changes received through emails or the vendor collaboration interface. Whichever options you configure also show the results of the impact analysis for review directly in Dynamics 365 Supply Chain Management, so purchasers can decide how to respond in their existing workflow.

## Set up sources that automatically trigger impact analysis

To use impact analysis on incoming change requests received through emails or the vendor collaboration interface, first enable the relevant sources. Learn more in [Supplier communications features of the Procurement Agent (production ready preview)](procurement-agent-supplier-com-overview.md) and [Vendor collaboration with external vendors](vendor-collaboration-work-external-vendors.md).

To enable impact analysis to run based on change requests coming through one or both sources, follow these steps:

1. Sign in to the Supply Chain Management environment as a user who has permissions to manage the agent configuration.
1. Go to **Agents** \> **Agents**.
1. Open the **Library** tab.
1. Find the *Show impact of changes in purchase orders - Impact analysis - Procurement Agent* tile and select **Select** for that tile.
1. Open the **Source** dropdown list and select one or both of the following options:
    - *Vendor emails* – Select this option if you're using supplier communications features of the Procurement Agent to receive and classify emails from vendors.
    - *Vendor collaboration module* – Select this option if you're using the vendor collaboration interface to receive and manage vendor responses.
1. Select **Activate**.

## Review changes received via email (supplier communications)

The supplier communications features of the Procurement Agent classify whether emails from vendors are confirmations, change requests, or related to something else (indicated as *Other*). If you enable impact analysis, it runs automatically for all the change requests you receive.

1. Open the **(Preview) Emails from vendors** page by doing one of the following steps:
    - Go to **Procurement and sourcing** \> **Purchase order receipt and follow-up** to open the **Purchase order receipt and follow-up** workspace. Then select the **(Preview) Emails from vendors** tile.
    - Go to **Procurement and sourcing** \> **(Preview) Procurement Agent - Supplier communications** \> **(Preview) Emails from vendors**.

1. Select an email classified as a *Change request* in the list pane, and then look at the change summary table, where changed fields are highlighted in bold. <!-- KFM: I didn't see any of these features here. I couldn't confirm the remaining part of this procedure. -->
1. Look for the **Impact** column, which shows one of the following values based on the impact analysis results:
   - *Has impact* - Change affects downstream orders and/or inventory levels.
   - *No impact* - Change can be safely accepted.

1. The **Purchase order line impact** section shows a brief summary of impact.
1. Select **View details** to see the complete impact analysis.

## Review changes received via vendor collaboration interface

When vendors respond to purchase orders through the vendor collaboration interface, you can review proposed changes and their downstream effects directly from the purchase order preparation workspace. If you enabled impact analysis for the vendor collaboration source, the impact results are available alongside the vendor's response so you can decide how to proceed. To review the impact of changes received through the vendor collaboration interface, follow these steps:

1. Go to **Procurement and sourcing** \> **Purchase order preparation**.
1. On the **Orders** FastTab, open the **In external review requires action** tab.
1. Find and select a purchase order with a **Vendor response status** of *Accepted with changes*.
1. To view more details about the impact of the proposed change on the selected purchase order, do one of the following steps:
    - On the toolbar, select **View impact analysis** to open the **View details** page, which is described in the next section.
    - On the toolbar, select**View responses to latest sent order** to open the vendor's proposed changes. In the **Purchase order line impact** section, review the impact summary and select **View details** to see the full impact analysis on the **View details** page, which is described in the next section. <!-- KFM: Is it correct that this is the page described in the next section? -->

## Impact analysis view details page

When you open the impact analysis **View details** page (as described in the previous section), you can see all the downstream effects of the proposed change in one place. The **View details** page includes a summary of the impact, a detailed list of impacted orders, and a detailed list of inventory impacts including a graph showing projected inventory levels over time. The following subsections describe the various parts of the **View details** page.

### Filter and item information

The **Filter and item information** section shows key information about the purchase order and item affected by the proposed change, along with a selector to switch between different lines if the purchase order has multiple lines. If you are using master planning, you can also select the link to see the net requirements details for how the impact was calculated. The information in this section helps you understand which item and purchase order line you're analyzing, and gives you quick access to related information and planning details.

You can see the following information in this section:

- Purchase order and line selector (for multi-line purchase orders)
- Item number and item name being analyzed
- Link to **Net requirements** (if you're using master planning)

You can do the following actions in this section:

- Switch between different lines on the same purchase order with impact
- Select the net requirements link to see the detailed planning logic used for the impact calculation

### Purchase order line impact

The **Purchase order line impact** section provides an AI-generated summary of the downstream impact, including specific mentions of affected orders and inventory issues. The agent analyzes the full impact details and provides a concise natural language explanation to give you a quick overview before you dive into detailed tables and graphs.

### Impacted orders

The **Impacted orders** section shows a detailed table of all downstream orders affected by the purchase order change. It includes sales orders, production orders, transfer orders, safety stock orders, and forecasts that are impacted by the proposed change. This detailed view helps you understand exactly which orders are affected and how, so you can make informed decisions about accepting the change and communicating with relevant stakeholders. The following table summarizes the columns shown in the **Impacted orders** section:

| Column | Description |
|--------|-------------|
| **Order Type** | Sales order, Production order, Transfer order, Safety stock order, or Forecast |
| **Order Number** | Specific order ID |
| **Customer/Reference** | Customer name for sales orders, or production/transfer number |
| **Tracing Method** | How the order is linked: *Pegging* (from planning) or *Marking* (explicit reservation) |

Use the **View order**, **View item**, and **View customer** buttons to open related pages in Supply Chain Management.

If this table is empty, the change has no direct impact on specific orders.

### Impacted inventory

The **Impacted inventory** section shows if the purchase order change causes inventory to drop below safety stock or go negative. The following table summarizes the columns shown in the **Impacted inventory** section:

| Column | Description |
|--------|-------------|
| **Site** | The site where inventory is affected |
| **Warehouse** | The warehouse where inventory is affected |
| **Expected impact type** | Shows one of the following values to indicate the type of impact:<ul><li>*Below minimum* – Inventory drops below configured safety stock level but remains positive. You still have inventory, but your safety buffer is consumed.</li><li>*Negative* – Inventory goes below zero (complete stockout). You can't fulfill orders from on-hand inventory.</li></ul> |
| **Expected impact date** | When the inventory breach occurs |
| **Product dimensions** | Shows the specific product variant affected (for example, configuration, size, color, style) if the item has product dimensions configured |

#### Inventory projection graph

The **Inventory projection** graph visualizes inventory levels over time, showing how the purchase order change affects your projected inventory.

The graph includes a legend with two lines:

- **Projected inventory before change** – Shows expected inventory levels based on the original purchase order and plan (displayed as a stepped line).
- **Projected inventory after change** – Shows projected inventory levels if you accept the vendor's proposed change (displayed as a stepped line). If the after-change line drops below the safety stock reference line, this condition is highlighted as a **Below minimum** impact. If it goes below zero, it is highlighted as a **Negative** impact.

The two lines might diverge without resulting in an impact, which means that projected inventory levels after the vendor change might be lower, but still above minimum level.

Additional visual elements:

- **X-axis** – Timeline showing dates
- **Y-axis** – Inventory quantity
- **Horizontal reference lines** – Show the safety stock threshold if available

> [!IMPORTANT]
> This projection is based on current planning data. It shows what *would happen* if you accept the change, but the plan isn't updated yet. Once you accept the change and update the purchase order, planning needs to run to create the new official plan.

## Accept a change and apply it to the purchase order

Purchasers can accept changes that:

- Have no or low downstream impact.
- Have an impact, but the purchaser decides to accept the change anyway. This decision might be because there's no other option but to accept. The purchaser might have followed up with the supplier to request options such as expedited production or shipping and split deliveries, but concluded that nothing else can be done.
  
To accept changes without going back to the purchase order, see one of the following articles based on how you receive changes from vendors:

- To accept changes processed by the supplier communications features of the Procurement Agent, see [Review and apply purchase order changes received in vendor emails](procurement-agent-supplier-com-apply-email-changes.md).
- To accept changes when received through the vendor collaboration interface, see [Updating a PO when a vendor suggests changes](vendor-collaboration-work-external-vendors.md#updating-a-po-when-a-vendor-suggests-changes).

When purchasers choose to accept a change that has a downstream impact, they now have a clear understanding of that impact and can communicate it directly to the relevant colleagues, such as those in sales, production, planning, and senior management.
