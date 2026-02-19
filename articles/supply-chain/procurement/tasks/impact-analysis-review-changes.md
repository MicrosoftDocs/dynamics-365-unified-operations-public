# Review impact of purchase order changes from vendors #

[This article is prerelease documentation and is subject to change.] 

## Review Changes Received via Email (Supplier Communications Agent)

Supplier Communications Agent classifies whether emails from vendors are confirmations, change requests, or related to something else (i.e. "Other"). The Impact Analysis runs automatically for all change requests received through the Supplier Communications Agent if enabled.

1. Go to: **Procurement and sourcing > Purchase order receipt and follow-up workspace > (Preview) Emails from vendors** or **(Preview) Supplier Communications Agent > (Preview) Emails from vendors**
2. Click on an email classified as a **Change request** in the lefthand navigation pane, and locate the change summary table. Changed fields are **highlighted in bold**.
4. Look for the **Impact** column, which shows:
   - **Has impact** - Change affects downstream orders and/or inventory levels
   - **No impact** - Change can be safely accepted
5. The **Purchase order line impact** section shows a brief summary of impact.
6. Click **View details** to see the complete impact analysis

## Review Changes Received via Vendor Collaboration Module

1. Go to: **Procurement and sourcing > Purchase order preparation workspace**
2. Click: **In external review requires action**
3. Filter for or navigate to a purchase order with vendor response status: **Accepted with changes**
4.	To view more details about the impact, either: 
- Click **View impact analysis** button, which directs to the **View details** page described below
- Click **View responses to latest sent order** button to see the vendor's proposed changes. In the **Purchase order line impact** section, review the impact summary and click **View details** to see the full impact analysis.
---

## Impact analysis View Details page

When you click **View details** or **View impact analysis**, the impact analysis page opens with the following sections:

### Filter and Item Information (Top)
Here, you can find:
- Purchase order and line selector (for multi-line POs)
- Item number and item name being analyzed
- Link to **Net requirements** (if using Planning Optimization or Classic Planning)
You can:
- Switch between different lines on the same PO, both lines with and without impact
- Click the net requirements link to see the detailed planning logic used for the impact calculation

### Purchase Order Line Impact Summary
An AI-generated summary of the downstream impact, including specific mentions of affected orders (sales, production, transfer, forecast, safety stock requirements) and inventory issues. The agent analyzes the full impact details and provides a concise natural language explanation to provide a quick overview before diving into detailed tables and graphs.

### Impacted Orders (Table)
This section shows a detailed table of all downstream orders affected by the purchase order change:

| Column | Description |
|--------|-------------|
| **Order Type** | Sales order, Production order, Transfer order, Safety stock order or Forecast |
| **Order Number** | Specific order ID |
| **Customer/Reference** | Customer name for sales orders, or production/transfer number |
| **Tracing Method** | How the order is linked: **Pegging** (from planning) or **Marking** (explicit reservation) |

Here, you can: use the **View order**, **View item** and **View customer** buttons to re-direct to pages in Dynamics.

Note: If this table is empty, the change has no direct impact on specific orders.

**Understanding impacted Forecasts:**
When you see "Forecast orders" in the impacted orders list, this means the purchase order change affects your ability to fulfill anticipated demand based on your demand forecasts. Unlike sales orders, which represent actual customer commitments, forecast orders represent expected future demand used by the planning system to prepare inventory and production capacity ahead of actual orders.

**Understanding impacted Safety Stock Orders:**
When you see "Safety stock orders" in the impacted orders list, this means the planning system has created planned orders to maintain your safety stock levels, and the purchase order change affects those planned replenishment orders. This is different from inventory dropping below safety stock minimum (shown in the Inventory Projections section) - safety stock requirements indicate the planning system has actively created demand to rebuild the safety buffer.

### Impacted Inventory (Table and Graph)
This section shows if the purchase order change causes inventory to drop below safety stock or go negative.
The **Impacted inventory table** shows the following information:
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

#### Inventory Projection Graph
The graph visualizes inventory levels over time, showing how the purchase order change affects your projected inventory. 

**Graph elements:**

The graph includes a **legend** with two lines:
- **Projected inventory before change** - Shows expected inventory levels based on the original purchase order and plan (displayed as a stepped line)
- **Projected inventory after change** - Shows projected inventory levels if you accept the vendor's proposed change (displayed as a stepped line). If the "after change" line drops below the safety stock reference line, this will be highlighted as a **Below minimum** impact. If it goes below zero, it is highlighted as a **Negative inventory** impact.

The two lines might diverge without resulting in an impact, meaning that projected inventory levels after the vendor change may be lower, but still above minimum level.

Additional visual elements:
- **X-axis** - Timeline showing dates (typically several weeks or months forward)
- **Y-axis** - Inventory quantity
- **Horizontal reference line(s)** - May show safety stock threshold or zero inventory baseline
- **Highlighted areas** - When inventory drops below minimum or goes negative

**Important Note:**
> This is a projection based on current planning data. It shows what **would happen** if you accept the change, but the plan has not been updated yet. Once you accept the change and update the purchase order, master planning will need to run to create the new official plan.


## Accept changes and apply them to the purchase order ##

Purchasers may accept changes that:

- Have no or low downstream impact.
- Have an impact, but the purchaser decides to accept anyway. This could be because there is no other option but to accept.
  
They can accept changes without navigating back to the purchase order by following the steps:
- To accept changes when using the Supplier Communications Agent, see Review and accept changes suggested by the agent.
- To accept changes when using the vendor collaboration Module, see Updating a PO when a vendor suggests changes.

For changes with impact that the purchaser accepts, they now know what the exact impact will be, and can communicate in a targeted manner to relevant colleagues in sales, production, planning, senior management and so on.

## Push back on supplier on changes with impact and evaluate proposals ##
For changes with impact, purchasers may want to push back on the supplier to:
   - Request expedited production or shipping 
   - Ask for split or partial delivery options

The **Impact simulation** functionality within the Impact Analysis capability can help you evaluate proposals from suppliers on increases in quantity and earlier delivery dates than what was communicated in the change request. This can help evaluate whether proposals from suppliers reduce or eliminate the impact.

