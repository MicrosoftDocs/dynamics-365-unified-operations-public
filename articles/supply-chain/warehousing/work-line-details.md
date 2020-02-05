---
# required metadata

title: Work line details
description: Advanced wave load building automatically assigns shipments to existing waves during wave execution, which can help you create meaningful loads that represent trucks without requiring you to use the load-planning workbench.
author: mirzaab
manager: AnnBe
ms.date: 02/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: Release 10.0.8
---

# Work line details

Work line details provide all the information needed to get a good overview of the work being planned and executed in the warehouse. You can switch between viewing all work lines or only the open work lines for a specific company. The details provided for each line include: work status, item number, location, work quantity, load ID, shipment ID, and more.

While work directly with a work order in the system, you can: <!-- KAMAYBAC: Is it OK to refer to this as a "work order"? -->

- Change the location of any opened work line (which will override the location directive setup)
- Cancel any work line
- Adjust quantities
- View transactions behind any work line

## Enable the location directive inventory picking aging feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - Warehouse management
- **Feature name** - Work line details

## Feature demo

This section provides a three-part example of how to work with work line details.

### Enable sample data

To work through these demos using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

You can also use these demos as guidance for how to use this feature when working on a production system, but then you must then substitute your own values, and you may be missing some types of required records that would otherwise be provided by the standard demo data.

### Make sure the demo setup includes enough available inventory

If you are working with **USMF** demo data, then start by making sure your system is set up with enough inventory at each relevant pick location. This demo expects that you have the following inventory available:

- **Item M9200** - 45 ea. (or more)
- **Item M9202** - 10 ea. (or more)

To confirm that you have enough inventory available and make adjustments as needed:

1. Go to **Warehouse management > Setup > Location directives** and find out which picking locations are used for sales order picking at warehouse 51 (see also [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md)). <!-- KAMAYBAC: What am I looking for here? Seems like I am already expecting to use warehouse 51--isn't that the location? I don't see anything useful here. -->
1. Check the inventory levels at the relevant locations. <!-- where/how do I do this? Can we give a link? -->
1. Adjust inventory as required. You can create manual movements, use replenishment, or apply any other flow as needed to adjust the inventory. <!-- where/how do I do this? Can we give a link? -->

### Part 1: Create picking work

Before you start creating work, make sure that your warehouse is set up to respond to work requests as expected.

1. Go to **Accounts receivable > Orders > All sales orders**.


Navigate to _Accounts receivable_ - _Sales orders_ - _ All sales order_. Click New to create a new sales order. Pick any customer. In the _General_ section specify Warehouse 51.

1. Sales order 1 (any customer): Add a new line to the sales order, item M9200, quantity 20 ea.
2. Sales order 2 (any customer): Add a new line to the sales order, item M9200, quantity 25 ea. Add a second line for item M9202, quantity 10 ea.

Before releasing the orders to warehouse, ensure there is enough inventory on the pick locations for all the items on the orders.

Default Contoso data should support this scenario but review the Location Directive setting to be sure what picking locations are used for sales order picking. You can create manual movements, use replenishment, or any other flow if needed to adjust the inventory.

Reserve the inventory and Release it to warehouse. Two different Work IDs should have been created.

### Part 2: Change the location

Navigate to _Warehouse management_ - _Work_ - _Work line details_ and open the form.

Select a work line and click on &#39;Change location&#39; in the action bar. Enter the new location that should be associated with the work line. If the location you selected has available inventory (for a pick) or if it matches the location type validation (for a put), the location on the work line will be updated.

### Part 3: Cancel a work line

Navigate to _Warehouse management_ - _Work_ - _Work line details_ and open the form.

Select a work line and click on &#39;Cancel work line&#39; in the action bar. Cancel full quantity for this example but be aware that you can also cancel only part of the quantity.

Note that the first Pick work line has been cancelled.

Let&#39;s continue with this example and cancel only a partial quantity of the second pick line. Select the second line on the Work line details form and press &#39;Cancel work line&#39;. In the new screen, specify qty 7ea.

Now, the new line will have qty 3, as we have cancelled 7ea (10ea - 7ea).

Note that only the Work created quantity field on the matching Load line will be changed as a result. The user must take other measures to remove the obsolete quantity from the load line, otherwise it won&#39;t be possible to be ship confirmed (unless under delivery is set up correctly).
