---
# required metadata

title: Catch weight product processing with warehouse management
description: This topic describes how to use work templates and location directives to determine how and where work is done in the warehouse.
author: perlynne
manager: AnnBe
ms.date: 03/18/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSCatchWeightTag, WHSCatchWeightItemHandlingPolicy
ROBOTS: NOINDEX, NOFOLLOW 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
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
[!include [preview banner](../includes/preview-banner.md)]

## Feature exposure

To use warehouse management to process catch weight products, you must use a license configuration key to turn on the functionality. (Go to **System administration \> Setup \> License configuration**. Then, on the **Configuration keys** tab, expand **Trade \> Warehouse and Transportation management**, and select the check box for **Catch weight for warehouse**).

> [!NOTE]
> Both the **Warehouse and Transportation management** license configuration key and the **Process distribution \> Catch weight** license configuration keys must also be turned on.

After the license configuration key is turned on, when you create a released product, you can select **Catch weight**. You can also associate the released product with a storage dimension group that the **Use warehouse management processes** parameter is selected for.

Before you can use the product in Warehouse management, you must do some basic product-specific setup for catch weight:

- Define the nominal weight conversion between the catch weight unit (box) and the inventory unit (kilogram \[kg\]) as part of a unit conversion definition.
- Define the minimum and maximum weight tolerances as part of the catch weight unit setup.
- Set up a unit sequence group where the catch weight unit is defined as the lowest stock keeping unit (SKU).
- Set up a catch weight item handling policy.

For more information, see [Setting up and maintaining catch weight items](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/setting-up-and-maintaining-catch-weight-items).

## Transaction adjustments

Because the weight of inventory when it comes into a warehouse can differ from the weight when the inventory is issued out of the warehouse, the catch weight product processing must adjust the inventory.

**Example 1**

During a **Report as finished** production process, the inbound weight of a license plate that contains eight boxes of a catch weight product is captured as 80.1 kg. The license plate is then stored away in the finished goods area, and during the storage period, some weight is lost into the air.

Later, as part of a sales order picking process, the weight of the same license plate is captured as 79.8 kg. Therefore, in the system, you now have a weight difference as part of the physical dimension set.

In this case, the system automatically adjusts the difference by posting a transaction for the missing 0.3 kg.

**Example 2**

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

If the actual weight is captured at the packing station during the container packing processes, warehouse workers won't be prompted to capture the weight during picking work. Instead, the average weight of the physical inventory will be used as the weight of the picked inventory that goes to the packing area.

For internal warehouse management processes like counting and adjustment corrections it is possible to define if the weight should be captured or not. If not captured the nominal weight will be used.

You can also define how the weight is captured. In one of the two main flows, catch weight tags are tracked and used to capture the weight. In the other flow, catch weight tags aren't tracked.

- **Yes** – The item uses catch weight tags. Each tag number represents one catch weight unit (box), and a weight and other information are associated with the tag. For outbound processes, the weight that is associated with the tag is used.
- **No** – The item doesn't use catch weight tags. The inbound and outbound weighing processes are based on the actual weight that is captured during each process.

The process of tracking catch weight tags can be used for items that won't change weight during the storage period. The weight will be captured only during the inbound warehouse process. During the outbound process, the catch weight tags will just be scanned, and the weights that are associated with the tags will be used for the outbound transactional processing.

### How to capture catch weight

When catch weight tag tracking is used, a tag must always be created for every catch weigh unit that is received, and every tag must always be associated with a weight.

For example, **Box** is the catch weight unit, and you receive one pallet of eight boxes. In this case, eight unique catch weight tags must be created, and a weight must be associated with each tag. Depending on the inbound catch weight tag, either the weight of all eight boxes can be captured, and the average weight can then be distributed to each box, or a unique weight can be captured for each box.

When catch weight tag tracking isn't used, the weight can be captured for each dimension set (for example, for each license plate and tracking dimension). Alternatively, the weight can be captured based on an aggregated level, such as five license plates (pallets).

For the methods for capturing outbound weight, you can define whether the weighing is done for each catch weight unit (that is, per box), or whether the weight is captured based on the quantity that will be picked (for example, three boxes). Note that for the production line picking and internal movement processes, the average weight will be used if the **Not captured** option is used.

To restrict the warehouse management picking processes from capturing weights resulting in catch weight profit/loss adjustments, the Outbound weight variance method can be used.

## Supported scenarios

Not all workflows support catch weight product processing with warehouse management. The following restrictions currently apply.
 
### Configuring catch weight products for warehouse management processes

- For catch weight products, the storage dimension group for items can't be changed (so that warehouse management processes can be used for them).
- Only formula processing is supported for catch weight products (not bill of materials).
- Catch weight products can't be associated with a tracking dimension group by using the Owner dimension.
- Catch weight products can't be used as services.
- Catch weight products can be used as "stocked products" only as part the item model group.
- Catch weight products can't be used together with the functionality for tracking "Active in sales process."
- Catch weight products can't be used together with the functionality for capturing serial numbers. Therefore, products can't be transferred from a "blank" to a serial number as part of the picking/packing process.
- Catch weight products can't be used together with the functionality for registering serials before consumption.
- Catch weight products that are variant-enabled can't be used together with the functionality for converting variant units of measure.
- Catch weight products can't be marked as a retail "product kit."
- Catch weight products can be used only with a unit sequence group that has catch weight handling units, and that has the catch weight unit as the lowest sequence.
- For catch weight products, the inventory unit can be converted to the catch weight unit only if the conversion produces a nominal quantity that is more than 1.
- The setup of bar codes for catch weight products doesn't support a variable weight setup.
 
### Order processing

- The creation of advance ship notice (ASN/packing structures) doesn't support weight information.
- The order quantity must be maintained based on the catch weight unit.
 
### Inbound warehouse processing

- Receiving license plates requires that weights be assigned during registration, because weight information isn't supported as part of the advance ship notice. When catch weight tag processes are used, the tag number must be manually assigned per catch weight unit.
 
### Inventory and warehouse operations

- Manual creation of quarantine orders isn't supported for catch weight products.
- Manual movement of inventory that is related to work isn't supported for catch weight products.
- Consolidation of license plates isn't supported for catch weight products.
- Changes to warehouse inventory status as part of a periodic task aren't supported for catch weight products.
- Changes to inventory status that are defined by a query aren't supported for catch weight products. (Changes to quality order inventory status aren't supported either.)
- For catch weight products, the inventory status can't be changed from the **On-hand by location** page.
- For catch weight products, the inventory status can't be changed as part of warehouse app movement work.
- License plate loading to initialize warehouse stock isn't supported for catch weight products.
- Batch balancing processes aren't supported for catch weight products.
- Handling of negative physical inventory isn't supported for catch weight products.
- Inventory marking can't be used for catch weight products.
 
### Outbound warehouse processing

- The functionality for cluster picking isn't supported for catch weight products.
- Pick and pack warehouse processing isn't supported for catch weight products.
- For catch weight products, work can't be completed from the **Work** page.
- For catch weight products, work that is defined in a work template can be run automatically.
- The functionality for reversing work isn't supported for catch weight products.
- For catch weight products, manual packing station processing where work is created after containers are closed isn't supported.
- The functionality for pcs-by-pcs scanning isn't supported for catch weight products.
 
### Production processing

- For catch weight products, only batch orders for formula products are supported.
- Kanban functionality isn't supported for catch weight products.
- For catch weight products, serial numbers can't be registered before consumption.
- The functionality for reversing license plates isn't supported for catch weight products.
- For catch weight products, reporting as finished can be registered by serial number.

### Transportation management processing

- Load building workbench processing isn't supported for catch weight products.
- Transport request lines aren't supported for catch weight products.
 
### Other restrictions and behaviors for catch weight product processing with warehouse management

- During picking processes where the user isn't prompted to identify tracking dimensions, the weight assignment is done based on the average weight. This behavior occurs when, for example, a combination of tracking dimensions is used in the same location and, after a user processes picking, only one tracking dimension value is left in the location.
- When inventory is reserved for a catch weight product that is configured for warehouse management processes, the reservation is done based on the minimum weight that is defined, even if this quantity is the on-hand last handling quantity. This behavior differs from the behavior for items that aren't configured for warehouse management processes.
- Processes that use the weight as part of capacity calculations (wave thresholds, work maximum breaks, container maximums, location load capacities, and so on) don't use the actual weight of the inventory. Instead, the processes are based on the physical handling weight that is defined for the product.
- In general, Retail functionality isn't supported for catch weight products.
 
### Catch weight tags

Currently, the functionality for catch weight tags is supported only as part of the following scenarios:

- When processing purchase order warehouse app receiving.
- When processing load receiving via warehouse app.
- For license plate receiving that is related to a purchase order load, weight assignment is requested during the receiving process. By contrast, for transfer order receiving, the weight from the shipment data for the transfer order is used.
- For transfer order item and line receiving that comes from a non-warehouse management process warehouse.
- The processing of sales return order receiving can record catch weight tags, but the processing won't be validated if the tags are the same tags that were originally shipped for a particular sales order line.
- When processing a inventory status changed by using the warehouse app.
- When a warehouse transfer is done by using the warehouse app.
- When processing adjustment in and out via the warehouse app.
- When picking work is processed for sales and transfer orders. (Note that catch weight tags can't be recorded for production component picking.)
- When picked quantities are reduced from load lines, regardless of whether containers are used.
- When products are packed into containers at a packing station.
- When containers are reopened.
- When formula products are reported as finished by using the warehouse app.
- When transport loads are processed by using the warehouse app.

A catch weight tag can either be created using a warehousing app process, manually created in the form, or creating using a data entity process. If a catch weight tag gets associated with an inbound source document line, such as purchase order line, the tag will be registered. If the line is used for outbound processing. The tag will be updated as shipped.
