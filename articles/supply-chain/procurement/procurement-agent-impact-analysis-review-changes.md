---
title: procurement-agent-impact-analysis-review-changes
description: Purchase order impact analysis helps you review and respond to vendor changes in Dynamics 365. Learn how to assess and manage supply chain risks.
#customer intent: As a purchaser, I want to review the impact of vendor-initiated purchase order changes so that I can make informed decisions before accepting or rejecting them.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: lisascholz
ms.date: 04/24/2026
ms.topic: how-to
---

# Review impact of purchase order changes from vendors

[This article is prerelease documentation and is subject to change.]

The impact analysis can automatically run based on supplier changes received through emails or the Vendor Collaboration Module. Whichever is configured will also show the results of the impact analysis for review directly in existing pages in Dynamics 365, so the purchaser can decide how to respond in their existing workflow.

## Set up sources that automatically trigger impact analysis

If impact analysis is to be used on incoming change requests received through emails or the Vendor Collaboration Module, then these must be enabled first.

Learn more in [Supplier communications features of the Procurement Agent (production ready preview)](procurement-agent-supplier-com-overview.md) and [Vendor collaboration with external vendors](vendor-collaboration-work-external-vendors.md).

To enable the impact analysis to run based on change requests coming through one or both sources, follow these steps:

1. Sign in to the Microsoft Dynamics 365 Supply Chain Management environment as a user who has permissions to manage the agent configuration.
2. Go to **Agents** > **Agents**.
3. On the **Library** tab, look for *(Production-ready preview) Impact analysis - Procurement Agent*, select **Select**.
4. Select *Source* to enable *vendor emails* if using supplier communications and/or the *Vendor Collaboration Module*.
5. Select **Activate**.

## Review changes received via email (supplier communications)

Supplier communications classifies whether emails from vendors are confirmations, change requests, or related to something else (i.e. "Other"). If enabled, impact analysis runs automatically for all change requests received.

1. Go to: **Procurement and sourcing > Purchase order receipt and follow-up workspace > Emails from vendors** or **Supplier communications > Emails from vendors**
2. Click on an email classified as a **Change request** in the left-hand navigation pane, and locate the change summary table. Changed fields are **highlighted in bold**.
3. Look for the **Impact** column, which shows:
   - **Has impact** - Change affects downstream orders and/or inventory levels
   - **No impact** - Change can be safely accepted
4. The **Purchase order line impact** section shows a brief summary of impact.
5. Click **View details** to see the complete impact analysis

## Review changes received via Vendor Collaboration Module

1. Go to: **Procurement and sourcing > Purchase order preparation workspace**
2. Click: **In external review requires action**
3. Filter for or navigate to a purchase order with vendor response status: **Accepted with changes**
4. To view more details about the impact, either:
    - Click **View impact analysis** button, which directs to the **View details** page described below
    - Click **View responses to latest sent order** button to see the vendor's proposed changes. In the **Purchase order line impact** section, review the impact summary and click **View details** to see the full impact analysis.

## Impact analysis view details page

When you click **View details** or **View impact analysis**, the impact analysis page opens with the following sections:

### Filter and item information

Here, you can find:

- Purchase order and line selector (for multi-line POs)
- Item number and item name being analyzed
- Link to **Net requirements** (if using Planning Optimization or Classic Planning)

You can:

- Switch between different lines on the same PO with impact
- Click the net requirements link to see the detailed planning logic used for the impact calculation

### Purchase order line impact

This is an AI-generated summary of the downstream impact, including specific mentions of affected orders and inventory issues. The agent analyzes the full impact details and provides a concise natural language explanation to provide a quick overview before diving into detailed tables and graphs.

### Impacted orders (table)

This section shows a detailed table of all downstream orders affected by the purchase order change:

| Column | Description |
|--------|-------------|
| **Order Type** | Sales order, Production order, Transfer order, Safety stock order or Forecast |
| **Order Number** | Specific order ID |
| **Customer/Reference** | Customer name for sales orders, or production/transfer number |
| **Tracing Method** | How the order is linked: **Pegging** (from planning) or **Marking** (explicit reservation) |

Here, you can: use the **View order**, **View item** and **View customer** buttons to re-direct to pages in Dynamics 365 Supply Chain Management.

If this table is empty, the change has no direct impact on specific orders.

### Impacted inventory (table and graph)

This section shows if the purchase order change causes inventory to drop below safety stock or go negative.

The table in the **Impacted inventory** section shows the following information:

| Column | Description |
|--------|-------------|
| **Site** | The site where inventory will be affected |
| **Warehouse** | The warehouse where inventory will be affected |
| **Expected impact type** | Type of inventory issue: **Below minimum** or **Negative** (see below) |
| **Expected impact date** | When the inventory breach will occur |
| **Product dimensions** | Shows the specific product variant affected (e.g., configuration, size, color, style) if the item has product dimensions configured |

**Impact types:**

- **Below minimum** - Inventory drops below configured safety stock level but remains positive. You still have inventory, but your safety buffer is consumed
- **Negative** - Inventory goes below zero (complete stockout). You cannot fulfill orders from on-hand inventory

#### Inventory projection graph

The graph visualizes inventory levels over time, showing how the purchase order change affects your projected inventory.

**Graph elements:**

The graph includes a **legend** with two lines:

- **Projected inventory before change** - Shows expected inventory levels based on the original purchase order and plan (displayed as a stepped line)
- **Projected inventory after change** - Shows projected inventory levels if you accept the vendor's proposed change (displayed as a stepped line). If the "after change" line drops below the safety stock reference line, this will be highlighted as a **Below minimum** impact. If it goes below zero, it is highlighted as a **Negative** impact.

The two lines might diverge without resulting in an impact, meaning that projected inventory levels after the vendor change may be lower, but still above minimum level.

Additional visual elements:

- **X-axis** - Timeline showing dates
- **Y-axis** - Inventory quantity
- **Horizontal reference line(s)** - Shows the safety stock threshold or if available

> [!IMPORTANT]
> This is a projection based on current planning data. It shows what **would happen** if you accept the change, but the plan has not been updated yet. Once you accept the change and update the purchase order, planning will need to run to create the new official plan.

## Accept change and apply it to the purchase order

Purchasers may accept changes that:

- Have no or low downstream impact.
- Have an impact, but the purchaser decides to accept anyway. This could be because there is no other option but to accept. The purchaser may have followed up with the supplier to request options such as expedited production or shipping and split deliveries, but concluded that nothing else can be done.
  
They can accept changes without navigating back to the purchase order by following the steps:

- Learn how to accept changes when using supplier communications in [Review and apply purchase order changes received in vendor emails](procurement-agent-supplier-com-apply-email-changes.md).
- Learn how to accept changes when using the Vendor Collaboration Module in [Updating a PO when a vendor suggests changes](vendor-collaboration-work-external-vendors.md#updating-a-po-when-a-vendor-suggests-changes)

For changes with impact that the purchaser accepts, they now know what the exact impact will be, and can communicate in a targeted manner to relevant colleagues in sales, production, planning, senior management and so on.
