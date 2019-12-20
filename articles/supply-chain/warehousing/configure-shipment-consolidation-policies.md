---
# required metadata

title: [Configure shipment consolidation policies]
description: [The shipment consolidation process using shipment consolidation policies allows for automated shipment consolidation during automated and manual release to warehouse. Prior the introduction of this functionality the consolidation functionality allowed automated consolidation with hardcoded fields and based on the “Consolidate shipment at release to warehouse” filed at warehouse level.]
author: [GarmMSFT]
manager: PJacobse
ms.date: 12/31/2019
ms.topic: configure-shipment-consolidation-policies
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang:
ms.reviewer: [pjacobse]
ms.search.scope: [Which Operations client to show this topic as help for, to be set by content strategist, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
# ms.tgt_pltfrm:
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: [author's Microsoft alias]
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---
# Configure shipment consolidation policies

# Released in version 10.0.3

# Scenario 1: Configure default shipment consolidation policies

## Default policies setup – new environment:
1.	Navigate to _Warehouse management > Setup > Release to warehouse > Shipment consolidation policies_.
2.	Click Create default setup.
- A „Default“ policy will be created for Sales orders
- A “Default” policy will be created for Transfer orders

Note: Both policies will have the same set of fields taken into consideration by legacy logic, including order number (consolidate lines into shipments based on order number, warehouse, mode of delivery, address, etc.)

##	Default policies setup – upgrading an environment with warehouses already configured for cross-order consolidation:

1.	Navigate to _Warehouse management > Setup > Warehouse > Warehouses_.
2.	In the list, find and select the desired Warehouse record.
3.	Click Edit.
4.	Expand the Warehouse section.
5.	Select Yes in the Consolidate shipment at release to warehouse field.
- Repeat for all warehouses where consolidation is needed.
6.	Close the page.
7.	Go to Warehouse management > Setup > Release to warehouse > Shipment consolidation policies.
8.	Click Create default setup.
- A “CrossOrder” policy will be created for Sales orders

Note: The “CrossOrder” policy will have the same set of fields taken into consideration by legacy logic, excluding order number (consolidate lines into shipments based on warehouse, mode of delivery, address, etc.)

- A “Default” policy will be created for Sales orders
- A “Default” policy will be created for Transfer orders

Note: Both “Default” policies will have the same set of fields taken into consideration by legacy logic, including order number (consolidate lines into shipments based on order number, warehouse, mode of delivery, address, etc.)

9.	Select „CrossOrder“ policy, click Edit query.
- In the list, note that warehouses with the checkbox were included in the query.

# Scenario 2: Configure custom shipment consolidation policies

## Product filter codes

Navigate to _Warehouse management - Setup - Product filters - Product filters_ and create 2 warehouse Filter codes for products with Filter code 4 type.
-	For example, “Flammable”/”Explosive”.
-	Set up 2 different WHS-enabled items with filter code 4 as “Flammable” and 1 item with a code “Explosive”

## Mode of delivery

Navigate to _Sales and marketing - Setup - Distribution - Modes of delivery_ and create a mode of delivery different from a default mode of delivery used by the customer.
-	For example, customer US-001, mode of delivery set as default “10”, another mode of delivery “Air”

## Order pool

Navigate to _Sales and marketing - Setup - Sales orders - Order pools_ and create a new order pool used for consolidation query:
-	Create a new order pool, for example, “Consolidate”, set up customers US-003 and US-004

## Shipment consolidation policies

This setup assumes the script for Scenario 1 has been followed previously.

###	Add Policy 1

Example of a business case:

- “Customer+Mode” policy
- Query: Specific Customer account, specific Transportation mode of delivery “Air”
- Consolidation with open shipments is off
- Consolidation is per order id (separate shipments per order, warehouse, etc.)

1.	Click New.
2.	In the Policy name field, type a value (for example, “CustomerMode”).
3.	In the Policy description field, type a value (for example, “Customer account and mode of delivery”).
4.	In the list of Remaining fields, find and select the “Mode of delivery” record.
5.	Click Add.
6.	Click Edit query.
7.	In the list, find and select the “Customer account” record.
8.	In the Criteria field, enter or select a value, for example “US-001”.
9.	In the list, find or add the “Sales order lines.Mode of delivery” record.
10.	In the Criteria field, enter or select a value, for example “10”.
11.	Click OK.
- All order lines with the specified mode of delivery of customer US-001 will not be consolidated across orders. This is used as a first sequence in case we are consolidating for all other modes of delivery for this customer.

### Add Policy 2

Example of a business case:

- “Hazardous goods” policy
- Query: Specific “hazardous” filter code, specific Transportation modes of delivery “Air,Sea”
- Consolidation with open shipments is on
- Consolidation is across orders (separate shipments per account, warehouse, etc. but within the item group specified in the query)

12.	Click New.
13.	In the Policy name field, type a value, for example “Item type”.
14.	In the Policy description field, type a value, for example “Consolidate the same type of item across orders”.
15.	In the list of “Remaining fields”, find and select the record for “Mode of delivery”.
16.	Click Add.
17.	Select Yes in the Consolidate with open shipments field.
18.	Click Edit query
19.	Click the Joins tab.
20.	In the tree, expand 'Tables\Load details'.
21.	In the tree, select 'Tables\Load details'.
22.	Click Add table join.
23.	In the list, find and select “Items (InventTable)”.
24.	Click Select.
25.	Click Add table join.
26.	In the list, find and select “Warehouse items (WHSInventTable)”.
27.	Click Select.
28.	Click the Range tab.
29.	Click Add.
30.	Add a record for a filter code from Warehouse items, for example Filter code 4
- Any other grouping value can be used.
31.	In the Criteria field, enter or select a value.
32.	Click OK
- All order lines where items have the same Filter code 4, for example “Flammable”, will be consolidated across orders with other items of the same kind. If there is an open shipment for the same account, warehouse, and group of items, the new lines will be attached to it.

###	Add Policy 3

Example of a business case.

- Customer's' requirements policy
- Query: Specific Customer account
- Consolidation with open shipments is on
- Consolidation is across orders but based on Customer requisition (multiple orders are grouped into shipments based on the same Customer requisition number and warehouse)

33.	Click New.
34.	In the Policy name field, type a value, for example “CustomerOrderNo”.
35.	In the Policy description field, type a value, for example “Consolidate lines based on customer PO”.
36.	Select Yes in the Consolidate with open shipments field.
37.	In the list, find and select the “Customer requisition” record.
38.	Click Add.
39.	In the list, find and select the “Mode of delivery” record.
40.	Click Add.
41.	Click Edit query.
42.	In the list, find and select the “Customer account” record.
43.	In the Criteria field, enter or select a value, for example, “US-001”.
44.	Click OK.
- All order lines where sales orders have the same Customer requisition number (which is used as the customer’s PO number) will be consolidated into one shipment regardless of Sales order number. If there is an open shipment for the same account, warehouse, and customer requisition, the new lines will be attached to it. It can be used if the customer sends additional order lines with the same PO number several times a day and wants them all to be grouped in one shipment (resulting in one bill of lading and packing slip).

###	Add Policy 4

Example of a business case.

- Customers allowing consolidation policy
- Query: Specific Order pool to identify customers accepting consolidated shipments
- Consolidation with open shipments is off
- Consolidation is across orders with regular fields selected
- Rule can be overridden on a sales order by selecting another order pool

45.	Click New.
46.	In the Policy name field, type “Order pool”.
47.	In the Policy description field, type a value, for example “Consolidate across orders based on order pool”.
48.	In the list, find and select the “Mode of delivery” records.
49.	Click Add.
50.	Click Edit query.
51.	In the list, find and select the record, for example “Sales orders.Pool”.
52.	In the Criteria field, enter or select a value.
53.	Click OK.
- All order lines where sales orders belong to the same Order pool will be consolidated into one shipment across sales orders for the same account, warehouse, and mode of delivery. Order pool can be replaced with any other field setting a group of customers apart and defaulting to the sales order header. This can be used if the customer and not the warehouse (like in the legacy logic) is driving the need for consolidation.

### Add Policy 5.

Example of a business case.

- Warehouses allowing consolidation policy
- Query: Specific Order pool to identify warehouses that can consolidate shipments
- Consolidation with open shipments is off
- Consolidation is across orders with regular fields selected (replication of the current “Warehouse” checkbox)

54.	Click New.
55.	In the Policy name field, type a value, for example “CrossOrder”.
56.	In the Policy description field, type a value, for example “Cross-order consolidation for specific warehouses”.
57.	In the list, find and select the “Mode of delivery”.
58.	Click Add.
59.	Click Edit query.
60.	In the list, find and select the “Warehouse” record.
61.	In the Criteria field, type “61, 63”.
62.	Click OK.
- It is manual replication of the legacy logic where the consolidation decision was driven by specific warehouses.
63.	In the list, find and select the desired records.
64.	Use Move up/Move down buttons to arrange the policies in the order of applicability (pyramid-like approach) as follows:
- CustomerMode
- Item type
- CustomerOrderNo
- Order pool
- CrossOrder
- Default

# Demo scripts of the functionality included here (links TODO)
