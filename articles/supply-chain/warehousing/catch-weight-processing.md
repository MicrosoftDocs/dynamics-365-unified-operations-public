---
# required metadata

title: Catch weight product processing with warehouse management
description: This article describes how to use work templates and location directives to determine how and where work is done in the warehouse.
author: perlynne
ms.date: 08/13/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSCatchWeightTag, WHSCatchWeightItemHandlingPolicy, TMSLoadBuildWorkbench, WHSCatchWeightTagRegistration, WHSCatchWeightTagFullDimDiscrepancies, WHSCatchWeightTagChangeWeightDropDownDialog, WHSCatchWeightLinkWorkLineTagDropDownDialog
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2019-1-31
ms.dyn365.ops.version: 8.1.3

---

# Catch weight product processing with warehouse management

[!include [banner](../includes/banner.md)]

## Feature exposure

To use warehouse management to process catch weight products, you must use a license configuration key to turn on the functionality. Go to **System administration \> Setup \> License configuration**. Then, on the **Configuration keys** tab, expand **Trade \> Warehouse and Transportation management**, and select the check box for **Catch weight for warehouse**.

> [!NOTE]
> Both the **Warehouse and Transportation management** license configuration key and the **Process distribution \> Catch weight** license configuration keys must also be turned on. To set the configuration keys for catch weight, you must also turn on the feature by using the **Feature management** workspace. The main feature that must be turned on is **Catch weight product processing with warehouse management**. Two related but optional features that you might want to turn on are **Inventory status changes for catch weight products** and **Use existing catch weight tags when reporting production orders as finished**.

After the license configuration key is turned on, when you create a released product, you can select **Catch weight**. You can also associate the released product with a storage dimension group that the **Use warehouse management processes** parameter is selected for.

Before you can use the product in Warehouse management, you must do some basic product-specific setup for catch weight:

- Define the nominal weight conversion between the catch weight unit (box) and the inventory unit (kilogram \[kg\]) as part of a unit conversion definition.
- Define the minimum and maximum weight tolerances as part of the catch weight unit setup.
- Set up a unit sequence group where the catch weight unit is defined as the lowest stock keeping unit (SKU).
- Set up a catch weight item handling policy.

For more information, see [Setting up and maintaining catch weight items](/dynamicsax-2012/appuser-itpro/setting-up-and-maintaining-catch-weight-items).

## Transaction adjustments

Because the weight of inventory when it comes into a warehouse can differ from the weight when the inventory is issued out of the warehouse, the catch weight product processing must adjust the inventory.

> [!NOTE]
> Mobile device activity will trigger the transaction adjustments only if the Outbound weight variance method of the item's catch weight item handling policy is **Allow weight variance**.

### Example 1

During a **Report as finished** production process, the inbound weight of a license plate that contains eight boxes of a catch weight product is captured as 80.1 kg. The license plate is then stored away in the finished goods area, and during the storage period, some weight is lost into the air.

Later, as part of a sales order picking process, the weight of the same license plate is captured as 79.8 kg. Therefore, in the system, you now have a weight difference as part of the physical dimension set.

In this case, the system automatically adjusts the difference by posting a transaction for the missing 0.3 kg.

### Example 2

In its definition, a product is set up to tolerate a minimum weight of 8 kg and a maximum weight of 12 kg for the **Box** catch weight unit.

You have two boxes of the product, and they have a registered weight of 16 kg. If a warehouse worker picks and weighs one of the boxes, and the weight is captured as 9 kg, the remaining box will weigh 7 kg. However, because 7 kg is below the minimum weight, the system does an automatic adjustment to increase the weight of the on-hand inventory by 1 kg.

To set up the accounts that these adjustments are posted to, go to **Cost management \> Ledger integration policies setup \> Posting**. Then, on the **Inventory** tab, define the following accounts:

- Catch weight loss account
- Catch weight profit account

## Catch weight item handling policy

The catch weight item handling policy defines two primary warehouse management flows for the items: when the weight of the items is captured, and how it's captured.

You can define when the weight is captured for sales and transfer order processing. The weight can be captured during either of the following processes:

- **Picking** – The weight is captured during the initial pick work lines of order work.
- **Packing** – The weight is captured during manual packing. (You must send the items to a packing station.)

If the actual weight is captured at the packing station during the container packing processes, warehouse workers aren't prompted to capture the weight during picking work. Instead, the average weight of the physical inventory is used as the weight of the picked inventory that goes to the packing area. This concept also applies to catch weight items that are tracked by tags. For tag-tracked items, these parameters determine when the tag is captured. The tag can be captured either at picking time by using the mobile device or during manual packing.

> [!NOTE]
> Because the **Packing** option causes inventory to be updated with the average picked weight, this could trigger a discrepancy that could cause a catch weight profit/loss adjustment and/or a difference between on-hand inventory weight and catch weight tag weight.

For internal processes, such as counting and adjustment corrections, you can define whether the weight should be captured. If it isn't captured, the nominal weight is used. Other options let you capture weight per catch weight unit and per counting quantity.

You can also define how the weight is captured. In one of the two main flows, catch weight tags are tracked and used to capture the weight. In the other flow, catch weight tags aren't tracked.

- **Yes** – The item uses catch weight tags. Each tag number represents one catch weight unit (box), and a weight and other information are associated with the tag. For outbound processes, the weight that is associated with the tag is used.
- **No** – The item doesn't use catch weight tags. The inbound and outbound weighing processes are based on the actual weight that is captured during each process.

The process of tracking catch weight tags can be used for items that won't change weight during the storage period. The weight will be captured only during the inbound warehouse process. During the outbound process, the catch weight tags will just be scanned, and the weights that are associated with the tags will be used for the outbound transactional processing.

Another important parameter that is related to the processing of catch weight tags is **Catch weight tag dimension tracking method**. Tags can be either partially tracked or fully tracked. If a tag is partially tracked, it tracks product dimensions, tracking dimensions, and inventory status. If a tag is fully tracked, it tracks product dimensions, tracking dimensions, and **all** storage dimensions.

Additionally, when an item is tag-tracked, there is an **Outbound tag capturing method** parameter. You can set this parameter so that you're always prompted for the tag on outbound transactions from the mobile device. Alternatively, you can set the parameter so that you're prompted for tags only when they are required. For example, there are five catch weight tags in inventory on a given license plate, and you've indicated that you want to pick all five tags from the license plate. In this case, if the **Outbound tag capturing method** parameter is set to **Only prompt for tag when needed**, the five tags are automatically picked. You don't have to scan each tag. If the parameter is set to **Always prompt for tag**, you must scan each tag, even if all five tags are being picked.

> [!NOTE]
> As a rule, tags are captured and updated only from the mobile device menu items. Nevertheless, there are a few scenarios where tags are captured somewhere else (for example, from the manual packing station). However, in general, the mobile device menu items should be used for all warehouse activity if tags are used.

### How to capture catch weight

**When catch weight tag tracking is used**, a tag must always be created for every catch weight unit that is received, and every tag must always be associated with a weight.

For example, **Box** is the catch weight unit, and you receive one pallet of eight boxes. In this case, eight unique catch weight tags must be created, and a weight must be associated with each tag. Depending on the inbound catch weight tag, either the weight of all eight boxes can be captured, and the average weight can then be distributed to each box, or a unique weight can be captured for each box.
When using the **Use existing catch weight tags when reporting production orders as finished** feature with the process enabled via a mobile device menu item, the inventory gets updated based on existing catch weight tag information. As a result, the Warehouse Management mobile app does not prompt for capturing the catch weight tag data as part of a production report as a finished operation.

**When catch weight tag tracking isn't used**, the weight can be captured for each dimension set (for example, for each license plate and tracking dimension). Alternatively, the weight can be captured based on an aggregated level, such as five license plates (pallets).

For the methods for capturing outbound weight, the **Per catch weight unit** option lets you specify that the weighing should be done for each catch weight unit (for example, per box). The **Per picking unit** option lets you specify that the weight should be captured based on the quantity that will be picked (for example, three boxes). Note that for the production line picking and internal movement processes, the average weight will be used if the **Not captured** option is used.

Multiple weight capturing methods are defined on the catch weight item handling policy. Each weight capturing method parameter is used by various transactions. The following table summarizes which parameters are used by which transactions.

| Method                                     | Transaction                                |
|--------------------------------------------|--------------------------------------------|
| Outbound weight capturing method           | Sales picking, Transfer picking            |
| Production picking weight capturing method | Production picking, Production consumption |
| Movement weight capturing method           | Movement                                   |
| When to capture correction of weight       | Adjustments, Counting                      |
| Counting weight capturing method           | Counting                                   |
| Warehouse transfer weight capturing method | Warehouse transfer                         |

To prevent the warehouse management picking processes from capturing weights that cause catch weight profit/loss adjustments, you can use the Outbound weight variance method. The Outbound weight variance method applies during the following mobile device processes: sales picking, transfer picking, production picking, movements, counting, and warehouse transfers. You can use the **Restrict weight variance** option if the weight of the catch weight item doesn't fluctuate during warehouse storage, and if catch weight profit/loss adjustments aren't required. You can use the **Allow weight variance** option if the weight can fluctuate, and if catch weight profit/loss adjustments are required when a weight fluctuation is recorded.

## Unsupported scenarios

Not all workflows support catch weight product processing with warehouse management. The following restrictions currently apply. They apply to all catch weight items, regardless of whether they are tagged.

### Configuring catch weight products for warehouse management processes

- Only formula processing is supported for catch weight products (not bill of materials).
- Catch weight products can't be associated with a tracking dimension group by using the Owner dimension.
- Catch weight products can't be used as services.
- Catch weight products can be used as "stocked products" only as part of the item model group.
- Catch weight products can't be used together with the functionality for tracking "Active in sales process."
- Catch weight products can't be used together with the functionality for capturing serial numbers. Therefore, products can't be transferred from a "blank" to a serial number as part of the picking/packing process.
- Catch weight products can't be used together with the functionality for registering serials before consumption.
- Catch weight products that are variant-enabled can't be used together with the functionality for converting variant units of measure.
- Catch weight products can't be marked as a commerce "product kit."
- Catch weight products can be used only with a unit sequence group that has catch weight handling units, and that has the catch weight unit as the lowest sequence.
- The setup of bar codes for catch weight products doesn't support a variable weight setup.

### Order processing

- The creation of advance ship notice (ASN/packing structures) doesn't support weight information.
- The order quantity must be maintained based on the catch weight unit.

### Inbound warehouse processing

- Receiving license plates requires that weights be assigned during registration, because weight information isn't supported as part of the advance ship notice. When catch weight tag processes are used, the tag number must be manually assigned per catch weight unit.
- Inbound quality check work isn't supported for catch weight products. If configured, the quality check work will be skipped.

### Inventory and warehouse operations

- Manual creation of quarantine orders isn't supported for catch weight products.
- Manual movement of inventory that is related to open work isn't supported for catch weight products.
- License plate loading to initialize warehouse stock isn't supported for catch weight products.
- Batch balancing processes aren't supported for catch weight products.
- Handling of negative physical inventory isn't supported for catch weight products.
- Inventory marking can't be used for catch weight products.

### Outbound warehouse processing

- The functionality for cluster picking isn't supported for catch weight products.
- Pick and pack warehouse processing isn't supported for catch weight products.
- For catch weight products, work that is defined in a work template cannot be run automatically.
- For catch weight products, the system doesn't support manual packing station processing where packed container picking work is created after containers are closed.
- The functionality for pcs-by-pcs scanning isn't supported for catch weight products.

### Production processing

- For catch weight products, only batch orders for formula products are supported.
- Kanban functionality isn't supported for catch weight products.
- For catch weight products, serial numbers can't be registered before consumption.
- The functionality for reversing license plates from production isn't supported for catch weight products.
- For catch weight products, reporting as finished can't be registered by serial number.

### Transportation management processing

- Load building workbench processing isn't supported for catch weight products.
- Transport request lines aren't supported for catch weight products.

### Other restrictions and behaviors for catch weight product processing with warehouse management

- During picking processes where the user isn't prompted to identify tracking dimensions, the weight assignment is done based on the average weight. This behavior occurs when, for example, a combination of tracking dimensions is used in the same location and, after a user processes picking, only one tracking dimension value is left in the location.
- When inventory is reserved for a catch weight product that is configured for warehouse management processes (WMS), the reservation is done based on the minimum weight that is defined, even if this quantity is the on-hand last handling quantity. This behavior differs from the behavior for items that aren't configured for WMS. There is one exception to this restriction. For production picking, when the last handling quantity of a catch weight product that is serial number–controlled is picked, the actual weight is used.
- Processes that use the weight as part of capacity calculations (wave thresholds, work maximum breaks, container maximums, location load capacities, and so on) don't use the actual weight of the inventory. Instead, the processes are based on the physical handling weight that is defined for the product.
- In general, Commerce functionality isn't supported for catch weight products.
- For catch weight products, inventory status can't be updated from **Warehouse status change**.

### Catch weight tags

A catch weight tag can be created by using a Warehouse Management mobile app process, it can be manually created in the form **Warehouse management > Enquiries and reports > Catch weight tag** or it can be created by using a data entity process. If a catch weight tag is associated with an inbound source document line, such as purchase order line, the tag will be registered. If the line is used for outbound processing, the tag will be updated as shipped. You can view all the historical catch weight tag registration events via the **Catch weight tag registration** option from the **Catch weight tag** page.

You can use the **Change tag captured weight** option to manually update the weight value for a catch weight tag. Note that the weight for the inventory on-hand won't get adjusted as part of this manual process, but you can easily use the **On-hand discrepancies for catch weight tagged items** page to look up any discrepancies between the currently active catch weight tags and the current inventory.

Other manual options are to **Register tag** to a source document line and **Register work** against an existing warehouse work.

In addition to the restrictions that currently apply for catch weight products, tagged catch weight products have other restrictions that currently apply.

- All manual updates to inventory (that is, updates that aren't done using a mobile device) must include corresponding manual updates to the associated catch weight tags because these updates aren't done automatically. For example, manual adjustment journals will update inventory but not the associated catch weight tags.
- You must manually update catch weight tags to reflect replenishment work movements. This is because the system can't capture weights while processing replenishment work and therefore records the average weight instead.
- Mixed licensing place receiving isn't currently supported for tagged catch weight items.
- The processing of sales return order receiving can record catch weight tags. However, the process doesn't validate that the returned tag is the same tag that was originally shipped for a sales order.
- The mobile device menu item that has the **Register material consumption** activity code doesn't currently support recording catch weight tags.
- Although counting processes are supported for tagged catch weight items, they are limited. For example, you can use the mobile device options for counting tagged catch weight items, and the average weight is used. However, catch weight tags aren't automatically updated by the counting transaction. After the counting transaction is completed, the catch weight tags must be manually updated so that they reflect the inventory. If items that weren't originally in a location are counted into that location, the nominal weight is used.
- License plate consolidation doesn't currently support tagged catch weight items.
- Reverse work functionality isn't supported for catch weight items that are tag number–tracked.

> [!NOTE]
> The preceding information about catch weight tags is valid only if the catch weight product has a catch weight tag dimension tracking method that is fully tracked (that is, if the **Catch weight tag dimension tracking method** parameter on the catch weight item handling policy is set to **Product dimensions, tracking dimensions and all storage dimensions**). If the catch weight item is only partially tag-tracked (that is, if the **Catch weight tag dimension tracking method** parameter on the catch weight item handling policy is set to **Product dimensions, tracking dimensions and Inventory Status**), additional restrictions apply. Because visibility is lost between the tag and inventory in this case, some additional scenarios aren't supported.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
