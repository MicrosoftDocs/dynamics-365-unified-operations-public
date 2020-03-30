---
# required metadata

title: Quality management for warehouse processes
description: Quality management for warehouse processes extends the capabilities of quality management. It allows users to integrate item sampling controls into the warehouse receiving process using advanced warehouse management. 
author: Henrikan
manager: AnnBe
ms.date: 03/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: henrikan
ms.search.validFrom: 2020-03-16
ms.dyn365.ops.version: Release 10.0.11
---

# Quality management for warehouse processes

_Quality management for warehouse processes_ extends the capabilities of quality management. It lets you integrate item sampling controls into the warehouse receiving process using advanced warehouse management. Warehouse work can be automatically generated to take inventory to the quality area by percentage, fixed quantity, or based on every nth license plate.  Once a quality order has been completed, work can automatically be created to take inventory to the next location in the process (depending on the quality results). _Quality management for warehouse processes_ extends the capabilities of the basic quality management feature by providing the option of creating quality orders for the inventory being sent to the quality area, although quality orders aren't always required. This allows for a lightweight quality control process based only warehouse work.

## Enable quality management for warehouse processes

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Quality management for warehouse processes*
- **Feature name** - *Warehouse management*

## Key benefits

_Quality management for warehouse processes_ automatically creates work as part of the receiving process to move the inventory quantity required for quality control to a quality control location. Any received quantity that exceeds the quantity required for quality control, as per the item sampling setup, will move to an inbound location as per the location directive setup. Once the quality order is validated, work is automatically created to move the quantity for the quality order to a new, inbound location as per the location directive setup. The automatic creation of work with only the required quantity to move to and from quality control provides an integrated process experience.

<!-- KFM: Maybe the above paragraph should also mention the fail case, where inventory is moved to RETURN. -->

> [!NOTE]
> When _Quality management for warehouse processes_ is enabled, it's still possible to leverage the manual process of using inventory movement and movement-by-template to have a warehouse worker trigger the creation of warehouse work for moving inventory from a quality control location to a new location. It's also still possible to set up an inbound location directive that will move inventory in its entirety from a receiving location to a quality control location without considering the item-sampling setup.

## Quality management and Quality management for warehouse processes

When you enable _Quality management for warehouse processes_ it changes the setup of key warehouse management and quality management entities. The following figure provides an overview of the entities that enable quality orders for warehouse processes. The texts in parenthesis show suggested action for when quality management has been applied prior to enabling _Quality management for warehouse management processes_.

![Quality management entity diagram](media/quality-management-entity-diagram.png "Quality management entity diagram")

<!-- KFM: Graphics aren't translated and also aren't accessible. Is it possible instead to present this info as text or in a table? -->

## Enablers: Work order types "Quality item sampling" and "Quality order"

_Quality management for warehouse processes_ introduces the following work order types, which are used to enable the work creation process:

- **Quality item sampling** - used to create work that moves registered inventory to quality control
- **Quality order** - used to create work that moves inventory from quality control to a new location based on the location directive setup

### Work class, location directive, and work templates

The _Quality item sampling_ and _Quality order_ work order types are consumed by location directives, work classes, and work templates. 

For warehouse work to be automatically created for moving inventory to quality control, you must set up your system as follows:

1. Create work classes for _quality item sampling_ and _quality order_, respectively. This ensures that appropriate work can be automatically created off of the two work order types, and that this work  can subsequently be executed using the warehouse mobile application (WMA).

1. Set up a work template for each work order type:
    - Set up a template using the _quality item sampling_ work order type to move inventory registered to a quality control location automatically.
    - Setup a work template using the _quality order_ work order type to move inventory from a quality control location location, once quality control is completed

1. For each of the two work order types, set up location directives that apply the correct quality control locations to move the inventory to. Once quality control is completed, the location directive for _quality order_ ensures that that a new destination location will be selected for moving the inventory out of the quality control location.

1. Set up the relevant mobile device menu item(s) to support moving the received inventory to the quality control location, and for moving the inventory passing or failing control from the quality control location to a new location.

For a step-by-step example of how to set up these elements, see the [example scenario](#example-scenario) provided at the end of this topic.

## Enable a warehouse for quality management

Before _quality management for warehouse processes_ can be applied for a specific warehouse, you must enable the feature for that warehouse by doing the following:

1. Go to **Warehouse management > Setup > Warehouse > Warehouses**.
1. Select the warehouse you want to enable.
1. On the **Warehouse** FastTab, set **Enable quality order for warehouse processes** to _Yes_. (This parameter can only be set to _Yes_ for warehouses that use warehouse management processes.)

When **Enable quality order for warehouse processes** is set to _Yes_, the quality association setup controls whether _Quality management for warehouse processes_ is actually applied for this warehouse. You can revert this setting to _No_ at any time, in which case this feature will no longer apply for the warehouse, regardless of the quality association setup.

## Quality control

_Quality management for warehouse processes_ controls several key settings for quality associations and item sampling.

### Quality associations

<!-- KFM: please provide a short intro to this procedure. What are we about to do here? What is a "quality association"? -->

1. Go to **Inventory Management > Setup > Quality Control > Quality Associations**.
<!-- KFM: it seems like we need to select something here. Which do I choose and why? Can we link to a page where the purpose of these records and the other settings here are described?  -->
1. On the **Conditions** FastTab, set the **Applicable warehouse type** to one of the following:
    - **Quality management for warehouse processes only** - Activates the _Quality management for warehouse processes_ features. You can only select this option when the reference type is either **Purchase** or **Production**.
    - **All** - Disables _Quality management for warehouse processes_ features. Use this setting for all reference types other than **Purchase** or **Production**.

> [!NOTE]
> _Quality Management for warehouse processes_ only takes effect when the item on the source document line uses advanced warehouse management processes and the warehouse parameter **Enable quality order for warehouse processes** is set to _Yes_ for the warehouse on the source document line. <!-- KFM: I don't understand what we mean by "source document" here. How do we make these settings?  -->

<!-- KFM: We continue to talk about the "source document" here, and also something called "quality association search hierarchy", which we don't define. I don't understand what we are doing here, so it's hard to review this. I also don't understand the use of bold and italic here. -->

When _Quality management for warehouse processes_ is enabled, the applicable warehouse type is logically inserted into the fourth level of the quality association search hierarchy. The following table provides a logical representation of the search hierarchy.

| Level | Description |
| --- | --- |
| Level&nbsp;1 | **Reference type**, **Event type**, and **Execution match**. If there is a match against the source document line, then proceed to level 2. |
| Level 2 | **Item code**: _Table_, _Group_, or _All_. _Table_ is more specific than _Group_, and _Group_ is more specific than _All_. If there is a match for _Table_ (specific item), then proceed to level 3. If there is no match for _Table_, then search for a _Group_ match. If there is no match for _Group_, then _All_ applies. If there is a match, proceed to level 3. |
| Level 3 | **Account code** / **Resource code**. Similar search as applied for **Item code**. |
| Level 4 | **Applicable warehouse type**: _Quality order for warehouse processes only_ or _All_. If the warehouse on the source document has **Enable quality order for warehouse processes** set to _Yes_, and the item on the source document line is set to _Use warehouse management processes_, then associations with both _Quality management for warehouse processes only_ and _All_ will be applicable in parallel if both exist. If the warehouse on the source document has **Enable quality order for warehouse processes** set to _No_, and the item on the source document line is set to _Use warehouse management processes_, then only quality management will be applicable. |

For example, imagine that you have defined a warehouse with **Enable quality order for warehouse processes** set to _Yes_, and you have two quality associations defined for reference type purchase, All items, Event type Registration. The only difference between the two quality associations is the **Applicable warehouse type** setting&mdash;one is set to _All_, while the other is _Quality management for warehouse processes only_. In such a case, they are both equally specific and both quality associations will be applicable. However, if the test group is the same for both of the associations, then only one quality order will be created. The quality order will be created for the quality association where the **Applicable warehouse type** is set to _Quality order for warehouse processes only_.

If the test group is not the same for both of the associations, then two quality orders will be created. The first quality order will be created for the quality association where the **Applicable warehouse type** is _Quality order for warehouse processes only_. The second quality order will be created for the quality association where the **Applicable warehouse type** is _All_.

<!-- KFM : In the above, I sometimes see "Quality order for warehouse processes only". Should these actually be "Quality management for warehouse processes only"? -->

> [!NOTE]
> The applicable warehouse type _Quality management for warehouse processes only_, is considered more specific than _All_ in cases where the criteria for the quality associations for level 1 and 2 are the same and the test group is the same. Two quality orders will only be created when the test groups differ.

#### Reference types

When the **Reference type** is _purchase_ and the **Applicable warehouse type** is _Quality management for warehouse processes only_, then the **Event type** (on the **Process** FastTab) must be _Registration_. _Registration_ is the only supported event type for _purchase_ when using _Quality order for warehouse processes_.

#### Quality processing policy

The **Quality processing policy** setting is located on the **Quality order process** FastTab. It can have the value _Create quality order_ or _Create work only_. The default value is _Create quality order_. <!-- KFM: We should describe what this setting means and what those values do, not just what they are called. -->

If the conditions of the quality association are met for a reference type, then a quality order is created. <!-- KFM: I don't understand the purpose of this paragraph. Consider adding a bit more detail.  -->

_Quality management for warehouse processes_ introduces the ability to create work based only on item sampling. This to allow for a lightweight process. For example, it supports scenarios where only work is automatically created to move part of the registered quantity related to a purchase order line or production report as finished to a quality control location without creating a quality order upfront. <!-- KFM: the previous sentence is too complex. I'm not sure what you mean. Please simplify. --> The inventory for which work is created is based on the item sampling associated with the quality association. Once a worker has put the quantity at the quality control location, the quality department can manually create a quality order if needed.

> [!NOTE]
> If you using a **Quality processing policy** of *Create work only* then the system only creates quality item sampling work for moving inventory to the quality control location. When the quality department validates the quality order, the system automatically creates quality order work from a quality control location. <!-- KFM: The previous sentence was unclear, so I edited it. Please confirm. --> Therefore, if you want to automatically create work for moving the inventory from the quality location to a new location when the quality order is validated, you must manually create a quality order. Validating the quality order triggers the automatic creation of quality order work for moving inventory from the quality control location.

The creation of quality order work is unrelated to the quality association setup. If a work template exists with a **Work order type** of *Quality order* and the query criteria are met for that work template, then validating a quality order will trigger the creation of quality order work.

#### Referenced item sampling

Each quality association must reference an item sampling. An item sampling defines what quantity will be submitted to quality control. It can be set up so that it only applies to quality associations where the _**Applicable warehouse type** is _Quality management for warehouse processes only_. Item sampling where the **Sampling scope** is either _load_ or _shipment_, or where the **Quantity specification** is _Full license plate_, can only be referenced against quality associations where the **Applicable warehouse type** is _Quality management for warehouse processes only_.

If you define an item sampling that uses _Quality management for warehouse processes only_, then you'll get an error if you try to reference it from a quality association that doesn't use _quality order for warehouse processes_. <!-- KFM: Again, do we mean "quality **management** for warehouse processes" here? -->

> [!NOTE]
> Item sampling that uses full blocking isn't supported for quality associations with **Applicable warehouse type** set to _Quality management for warehouse processes only_.

### Item Sampling

<!-- KFM: add an intro that explains what "item sampling" means. -->

 _Quality management for warehouse processes_ introduces the concept of _item sampling scope_, which is used when evaluating if and how quality orders and/or quality item sampling work will be created.

To set up item sampling, go to **Inventory management > Setup > Quality Control > Item Sampling**, where you can use the **Sampling scope** field to set the item sampling scope to one of the following values:

- **Order** - The source document line will be the basis for evaluating if and how quality orders and/or quality item sampling and quality order work is created. This is the default value, and works the same as when _Quality management for warehouse processes_ isn't enabled.
- **Load** - loads will be used to as the basis for evaluating if and how a quality order and/or work is created. This value is only available when _Quality management for warehouse processes_ is enabled. 
- **Shipment** - shipments will be used to as the basis for evaluating if and how a quality order and/or work is created. This value is only available when _Quality management for warehouse processes_ is enabled. 

> [!NOTE]
> When the **Sampling scope** is set to *Shipment* or *Load*, those entities will be used if available. If not, then the order will be used.

 _Quality management for warehouse processes_ also introduces a **Quantity specification** value of *Full license plate*, which supports the creation of quality order and quality item sampling work based on license plates. When you choose this setting, the following occur:

- The **Break count by item** and **Per nth license plate** options on the **Process** FastTab become active
- The **Value** field on the **Sampling quantity** FastTab becomes inactive
- The **Per updated quantity**, **Location**, and **License plate** options are all set to *Yes* and can't be changed.

<!-- KFM: Continue from here -->

**Break count by item** controls if the license plate count is evaluated per item, or if the count is across all items within the sampling scope. Product variants are treated as the same item. _Break count by item_ controls if the license plate count is reset for each different item.

The value in **Per nth license plate** creates quality orders per every nth license plate that is receipt registered. _Per nth license plate_ requires a value greater than 0.

When receiving in the warehouse mobile application (WMA) and the item being received matches a _quality association_ then the referenced _item sampling_ will be used to control the creation of quality orders and what combination of _quality item sampling_ and _purchase order_ work is created.

> [!NOTE]
> When receipt registering in the client using the small registration form or item arrival journal for purchase order lines, if the item being registered matches a quality association, then the referenced item sampling will be used to control the creation of quality orders only. No quality item sampling work nor Purchase order work will be created regardless of the setup of the applicable warehouse type on the quality association.

## Quality order auto-generation examples

The following examples illustrate how the setup of a _quality association_ and associated _item sampling_ impacts the quality order generation when _Quality management for warehouse processes_ only is applied.

When the _quantity specification_ is _Full License Plate_, then the _Per nth license plate_ controls for which license plates _quality item sampling_ work is created. The first license plate will always go to quality, then the nth after that as controlled by this value.

The _Reference type_ for the examples below is _Purchase_, and the _Event type Registration_.

| Sampling Scope | Quantity Specification | Per updated quantity | Per storage dimension | Break count By item | Per nth license plate | Result |
| --- | --- | --- | --- | --- | --- | --- |
| Order | Full license plate | Yes _Locked (not editable)_ | Location: Yes<br>License Plate: Yes _Locked (not editable)_  | No | 3 | <p>**Order line quantity: 100 EA**</p><ol><li>Register receipt on WMA for 20 EA, LP1<br>Quality Item sampling work for 20 EA<br>Quality order #1 for 20 EA</li><li>Register receipt on WMA for 20 EA, LP2<br>Purchase order work for 20 EA (put away)</li><li>Register receipt on WMA for 20 EA, LP3<br>Purchase order work for 20 EA (put away)</li><li>Register receipt on WMA for 20 EA, LP4<br>Quality Item sampling work for 20 EA</li><li>Register receipt on WMA for 20 EA, LP5<br>Purchase order work for 20 EA (put away)</li></ol> |
| Order | Fixed quantity = 1 | Yes | Location: Yes<br>License Plate: Yes | No |   | <p>**Order line quantity: 100**</p><ol><li>Register receipt on WMA for 20 EA, LP1<br>Quality Item sampling work for 1 EA<br>Quality order #1 for 1 EA<br>Purchase order work for 19 EA (put away)</li><li>Register receipt on WMA for 20 EA, LP2<br>Quality Item sampling work for 1 EA<br>Quality order #1 for 1 EA<br>Purchase order work for 19 (put away)</li><li>Register receipt on WMA for 20 EA, LP3<br>Quality Item sampling work for 1 EA<br>Quality order #1 for 1 EA<br>Purchase order work for 19 EA (put away)</li><li>Register receipt on WMA for 20 EA, LP4<br>Quality Item sampling work for 1 EA<br>Quality order #1 for 1 EA<br>Purchase order work for 19 EA (put away)</li><li>Register receipt on WMA for 20 EA, LP5<br>Quality Item sampling work for 1 EA<br>Quality order #1 for 1 EA<br>Purchase order work for 19 EA (put away)</li></ol> |
| Order | Percent=10 | No | Location: No<br>License Plate: No | No |   | <p>**Order line quantity: 100 EA**</p><ol><li>Register receipt on WMA for 50 EA, LP1<br>Quality Item sampling work for 10 EA<br>Quality order #1 for 10 EA<br>Purchase order work for 40 EA (put away)</li><li>Register receipt on WMA for 50 EA, LP2<br>Purchase order work for 50 EA (put away)</li></ol> |
| Load | Percent=5 | Yes_Locked (not editable)_ | Location:NoLicense Plate:No | No |   | <p>**Order line quantity: 500 EA<br>Two Loads: 1st load 200 EA, 2nd load 300 EA**</p><ol><li>Register receipt on WMA 1st load for 100 EA<br>Quality Item sampling work for 5 EA<br>Quality order #1 for 5 EA<br>Purchase order work for 95 EA (put away)</li><li>Register receipt on WMA 1st load for 100 EA<br>Quality Item sampling work for 5 EA<br>Quality order #1 for 5 EA<br>Purchase order work for 95 EA (put away)</li><li>Register receipt on WMA 2nd load for 300 EA<br>Quality Item sampling work for 15 EA<br>Quality order #1 for 15 EA<br>Purchase order work for 285 EA (put away)</li></ol> |
| Order | Percent=10 | No | Location: Yes<br>License Plate: Yes | No |   | <p>**Order line quantity: 100**</p><ol><li>Register receipt on WMA for 50 EA, LP1<br>Quality Item sampling work for 5 EA<br>Quality order #1 for 5 EA<br>Purchase order work for 45 EA (put away)</li><li>Register receipt on WMA for 50 EA, LP2<br>Quality Item sampling work for 5 EA<br>Quality order #1 for 5 EA<br>Purchase order work for 45 (put away)</li></ol> |
| Load | Full license plate | Yes _Locked (not editable)_ | Location: Yes<br>License Plate: Yes _Locked (not editable)_ | No | 3 | <p>**Two items:**<ul><li>**Order line quantity Item A: 120 EA (4 pallets)**</li><li>**Order line quantity Item B: 90 EA (3 pallets)**</li></ul><p>**One Load, two load lines with each of the order lines.**</p><ol><li>Register receipt on WMA Item A, 30 EA, LP1<br>Quality Item sampling work for 30 EA<br>Quality order #1 for 30 EA</li><li>Register receipt on WMA Item A, 30 EA, LP2<br>Purchase order work for 30 EA (put away)</li><li>Register receipt on WMA Item A, 30 EA, LP3<br>Purchase order work for 30 EA (put away)</li><li>Register receipt on WMA Item A, 30 EA, LP4<br>Quality Item sampling work for 30 EA<br>Quality order #1 for 30 EA</li><li>Register receipt on WMA Item B, 30 EA, LP5<br>Purchase order work for 30 EA (put away)</li><li>Register receipt on WMA Item B, 30 EA, LP6<br>Purchase order work for 30 EA (put away)</li><li>Register receipt on WMA Item A, 30 EA, LP7<br>Quality Item sampling work for 30 EA<br>Quality order #1 for 30 EA</li></ol> |
| Load | Full license plate | Yes _Locked (not editable)_ | Location: Yes<br>License Plate: Yes _Locked (not editable)_ | Yes | 3 | <p>**Two items:**<ul><li>**Order line quantity Item A: 120 EA (4 pallets)**</li><li>**Order line quantity Item B: 90 EA (3 pallets)**</li></ul><p>**One Load, two load lines with each of the order lines.**</p><ol><li>Register receipt on WMA Item A, 30 EA, LP1<br>Quality Item sampling work for 30 EA<br>Quality order #1 for 30 EA</li><li>Register receipt on WMA Item A, 30 EA, LP2<br>Purchase order work for 30 EA (put away)</li><li>Register receipt on WMA Item A, 30 EA, LP3<br>Purchase order work for 30 EA (put away)</li><li>Register receipt on WMA Item A, 30 EA, LP4<br>Quality Item sampling work for 30 EA<br>Quality order #1 for 30 EA</li><li>Register receipt on WMA Item B, 30 EA, LP5<br>Quality Item sampling work for 30 EA<br>Quality order #1 for 30 EA</li><li>Register receipt on WMA Item B, 30 EA, LP6<br>Purchase order work for 30 EA (put away)</li><li>Register receipt on WMA Item A, 30 EA, LP7<br>Purchase order work for 30 EA (put away)</li></ol> |
| Load | Percent=10 | Yes_Locked (not editable)_ | Location: No<br>License Plate: No | No |   | <p>**Order line quantity: 100 EA**</p><p>**No load(s) created. Order scope is applied.**</p><ol><li>Register receipt on WMA for 50 EA, LP1<br>Quality Item sampling work for 5 EA<br>Quality order #1 for 5 EA<br>Purchase order work for 45 EA (put away)</li><li>Register receipt on WMA for 50 EA, LP2<br>Quality Item sampling work for 5 EA<br>Quality order #1 for 5 EA<br>Purchase order work for 45 EA (put away) |

The validation of the quality orders in above examples trigger the creation of _quality order_ work to move inventory from the quality location to a location as defined in the location directive for the _quality order_ work order type. This can be setup to be any location such as a return or storage location depending on the test result for the quality order. See the simple demo for an example of such setup.

It is possible to re-open a quality order already validated. However, when _Quality order_ work related to moving the inventory from the quality location is in status closed or in progress, then the quality order cannot be re-opened.

## Process insights when multiple quality associations co-exist

It is possible to have more quality associations defined and applied for the same source document line where both the applicable warehouse type equal **Quality management for warehouse processes only** and **All.**

Consider the following scenario for reference type _purchase_:

1. First quality association defined: **Applicable warehouse type** equal **Quality management for warehouse processes only** , **Item code** equal A0001, **Account code** equal All, **Test group** equal Enclosure. **Item sampling** is 5 pcs.
2. Second quality association defined: **Applicable warehouse type** equal All, **Item code** equal All, **Account code** equal All, **Test group** equal Enclosure. **Item sampling** is 1 pcs.
3. Third quality association defined: **Applicable warehouse type** equal **Quality management for warehouse processes only** , **Item code** equal All, **Account code** equal 104, **Test group** equal Impedance. **Item sampling** is every 2nd license plate. This implies that 1st license plate received, 3rd license plate received, 5th license plate received, etc. will create a quality order.
4. Fourth quality association defined: **Applicable warehouse type** equal All, **Item code** equal All, **Account code** equal All, **Test group** equal Impedance. **Item sampling** is 5 pcs.
5. Fifth quality association defined: **Applicable warehouse type** equal All, **Item code** equal All, **Account code** equal All, **Test group** equal Cone. **Item sampling** is 10%.

A purchase order is created for vendor 104, item A0001 with quantity 10.

Purchase order line quantity 10 is registered as received on one license plate using the warehouse mobile application.

The result will be the following:

- One quality order from the first quality association for test group Enclosure. Quantity 5. No quality order from the second quality association, as the criteria for the first quality association is more specific relative to the test group Enclosure.
- One quality order for the third quality association for test group Impedance. Quantity 10. No quality order from the fourth quality association, as the criteria for the first quality association is more specific relative to the test group Impedance.
- One quality order for the fifth quality association for test group Cone. Quantity 1.

In relation to creating one quality order for each of the 3 quality associations, quality item sampling work is also created. As the quantity registered is only 10, and the sum of the quality order quantities created for **Quality management for warehouse processes only** is 16 per the item sampling setup and  thereby exceeding the physical quantity registered of 10, work will not be created for the entire quality order quantities; the 16. Only 10 are physically available to be moved to the quality control location. The priority in which quality item sampling work creation is performed, follows the order of the quality order creation:

- 1st Quality order, quantity 5. Quality Item sampling work created for 5. Now quantity 5 (10-5) remains for subsequent quality item sampling work creation.
- 2nd Quality order, quantity 10. Quality Item sampling work created for 5. Now quantity 0 remains for subsequent quality item sampling work creation.
- 3rd Quality order, quantity 1. No quality item sampling work created.

As part of creating the quality orders, an inventory blocking of quantity 10 is created. This inventory blocking is referenced against each of the three quality orders. Sum of the quality order quantities is 16.

Upon **quality order validation** , quality order work will be attempted to be created for each quality order validated. As the sum of the quality order quantities exceeds what is actually blocked and hence available for work creation, quality order work cannot be created for the entire quality order quantities. This is exemplified by continuing with the example.

- First step: Validate the 2nd quality order created, quantity 10. Quality order work is created for quantity 4.
  - The creation of quality order work is triggered by a change in the inventory blocking quantity. As the sum of quality orders quantity was 16, validating quantity 10 will result in the remaining quality order quantities to validate equaling 6. The inventory blocking quantity is reduced to 6 (from 10 to 6); the reduced quantity of 4 is allotted to the quality order work creation.
- Second step: Validate the 1st quality order created, quantity 5. Quality order work is created for quantity 5.
  - The creation of quality order work is triggered by a change in the inventory blocking quantity. As the sum of quality orders quantity was 6, validating quantity 5 will result in the remaining quality order quantities to validate equaling 1. The inventory blocking quantity is reduced to 1 (from 6 to 1); the reduced quantity of 5 is allotted to the quality order work creation.
- Third step: Validate the 3rd quality order created, quantity 1. Quality order work is created for quantity 1.
  - The creation of quality order work is triggered by a change in the inventory blocking quantity. As the sum of quality orders quantity was 1, validating quantity 1 will result in the remaining quality order quantities to validate equaling 0. The inventory blocking is removed (from 1 to 0); the reduced quantity of 1 is allotted to the quality order work creation.

> [!NOTE]
> Creating quality order work depends on the inventory blocking quantity referenced against one or more quality orders. If the sum of the quality order quantities exceeds the referenced inventory blocking quantity, then the order in which the quality orders are validated determines the creation of quality order work.

## Cancelling quality item sampling work

It is possible to cancel the work created for _Quality item sampling_. The effect of the cancelling is conditioned by the parameter **Warehouse management > Setup > Warehouse management parameters > General > Work tab > Unregister receipt when cancelling work.** If the parameter is **Yes** and _Quality item sampling_ work is cancelled, then the associated quality order will be deleted, and the inventory will be unregistered. If this parameter is **No** and Q_uality item sampling_ work is cancelled, then the associated quality order will not be deleted, and the inventory will not be unregistered.

## Cross docking

It is possible to have a quality association setup which creates item sampling work. However, when cross docking exists in parallel with a quality association creating _quality__item sampling_ work, and there is only sufficient quantity to satisfy cross docking, then only item sampling work will be created. In a case where the receiving warehouse is setup to _Enable quality order for warehouse processes_ and a quality association is setup to use _Quality Management for warehouse processes only,_ thencreatingqualityitem sampling work _takes_ precedenceover cross docking work. No cross docking work will be created. In scenario where the quantity exceeds the requirement for cross docking, item sampling work will still only be created.

## Destructive test

It is possible to define a test group performing destructive tests. Destructive tests imply that regardless of the test result, the quantity of an item subjected to the test will be destroyed as part of the test. _Quality management for warehouse processes_ supports destructive testing in a similar way as quality management without _Quality management for warehouse processes_ enabled. Before the quality order can be validated, it is required to pick the quality order quantity. Picking will allow to specify the pick location. Picking can be registered from within the quality order form by navigating to **Inventory > Pick**. Once the pick for the quality order quantity is registered, then validation can be completed.

<a name="example-scenario"></a>

## Example scenario

### Prepare the scenario

To work through this scenario, you must prepare your system as follows:

- Work on a system with sample data installed and select the **USMF** legal entity.
- Enable the **Quality Management for Warehouse Processes** feature in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- Configure warehouse 51 to use the _Quality management for warehouse processes_ feature by doing the following:
    1. Go to **Warehouse management > Setup > Warehouse > Warehouses**.
    1. Select warehouse 51.
    1. Expand the **Warehouse** FastTab and set **Enable quality order for warehouse processes** to *Yes*.

### Quality in setup – move to QMS

<!-- KFM: I don't understand this heading. Also, what is "QMS"? We must spell it out at least once. -->

Now you must prepare a basic setup that will allow you system to support _Quality management for warehouse processes_ for warehouse 51. You will prepare the following elements, as described in the subsections of this section:

- Work class
- Work template
- Location directive
- Item sampling
- Quality association
- Mobile device menu items

<!-- KFM: It would be nice if each of the procedural subsections below had an introduction that very briefly explains why we are doing each of these things and what effects they will have. (The later ones already have this.)-->

#### Work class for quality in

1. Go to **Warehouse management > Setup > Work > Work classes**.
1. Create a new work class with the following settings:
    - **Work class ID** - _QualityIn_
    - **Description** - _Quality item sampling_
    - **Work order type** - _Quality item sampling_

#### Work template

1. Go to **Warehouse management > Setup > Work > Work templates**.
1. Set the **Work order type** to _Quality item sampling_.
1. Create a new work template with the following settings:
    - **Work template** - _51 Quality_
    - **Work template description** - _51 Quality_
1. Add a new line for the work template with the following settings:
    - **Work type** - _Pick_
    - **Work class ID** - _QualityIn_
1. Add a second line to the work template with the following settings:
    - **Work type** - _Put_
    - **Work class ID** - _QualityIn_

#### Location directive

1. Go to **Warehouse management > Setup > Location directives**.
1. Set the **Work order type** to _Quality item sampling_.
1. Create a new location directive with the following settings:
    - **Name** - _51 to quality_
    - **Work type** - _Put_
    - **Site** - 5
    - **Warehouse**: _51_
1. Add a new line for the location directive with the following settings: 
    - **From quantity** - _1_
    - **To quantity** - _1000000_
1. Create a new **Location Directive Action** with the following setting:
    - **Name** - _Quality_
1. On the new location directive action, open the **Edit** query and specify a **Range** record for the **Locations** table with the following values: <!-- This may need to be clarified. I'm not sure about the labels. -->
    - **Field** - _Location profile ID_
    - **Criteria** - **QMS**
1. Select **OK** to save the query and save this new location directive.

Next, you must change the sequence of the existing purchase order location directives for warehouse 51. The demo data includes the two location directives with a **Work order type** of _Purchase_: one named _51 QMS_ and one named _51 PO Direct_. To ensure that the *Quality management for warehouse processes* feature is applied for warehouse 51, you must make sure that the location directive named _51 QMS_ isn't applied. Rather than deleting that location directive (which you might want to use in the future), you can just change the sequence by doing the following:

1. Go to **Warehouse management > Setup > Location directives**.
1. Set the **Work order type** to _Purchase order_.
1. In the sequence list, select sequence number 5, with location directive _51 PO Direct_.
1. Move the selected sequence up to sequence number 4.
1. Check that as a result of this action, the location directive named _51 QMS_ now has a sequence number greater than or equal to 5.

#### Item sampling

_Quality management for warehouse processes_ adds a few new item sampling capabilities. **Sampling scope** can now be _Order_, _Shipment_, or _Load_, and **Sampling quantity** can now be _Full license plate_.

1. Go to **Inventory management > Setup > Quality control > Item sampling**.
1. Create a new item sampling record with the following settings:
    - **Item sampling** - _3rd LP_
    - **Description** - _Every third license plate_
    - **Sampling Scope** - _Order_
1. On the **Sampling quantity** FastTab, set the **Quantity specification** to _Full license plate_.
1. On the **Process** FastTab, set the **Per nth license plate** field value to _3_.
1. In the **Per storage dimension** section, enable both **Warehouse** and **Inventory status** .

#### Quality associations

Create a quality association that will use the new item sampling.

1. Go to **Inventory management > Setup > Quality control > Quality associations**.
1. Create a new quality associations record with the following settings:
    - **Reference type** - _Purchase_
    - **Item code** - _Table_
    - **Item** - _M9201_
    - **Site** - _5_
1. Set **Applicable warehouse type** to *Quality management for warehouse processes only*.
1. Expand the **Process** FastTab and set the **Event type**to *Registration*.
1. Expand the **Quality Order Process** FastTab and set **Quality Processing Policy** to _Create quality order_.
1. Expand the **Specifications FastTab** and set the **Test Group** to *View all* (right-click and select **View all**).
1. In the **Test groups** section, create a new test group with the following settings:
    - **Test Group** - _QMS_
    - **Description** - _QMS test_
    - **Acceptable quantity** - _100_
    - **Item Sampling** - _3rd LP_ (Select)
1. In the line Overview, add a record (one test) with the following settings: <!-- KFM: This step seems garbled. Please check against the UI and possibly clean up -->
    - **Sequence** - *1*
    - **Test** = *Enclosure measuring*
    - On the **Test tab**, set **Test variables** to *Pass/Fail*
    - **Default outcome** - *Pass*
1. Save the new Test Group and close the form.

**Back** in the Quality associations form, in the **Test group** field select **QMS**. Save the record.

#### Mobile device menu items for quality in

To complete the setup of moving goods to QMS, you must make the quality In Sampling work <!-- KFM: what do you mean by "quality In Sampling work"? Capitalization is strange; should some of this be bold or italic? --> available from a mobile device menu item. To set this up:

1. Go to  **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select the **Purchase Put-away** mobile device menu item.
1. On the **Work classes** FastTab, add the *QualityIn* work class ID.

#### Summary: Your move to QMS setup

You have now defined a quality association that triggers the creation of a quality order using the *Quality management for warehouse processes* feature. You have set up the work and location data for warehouse 51 to ensure that specific work is created upon purchase registration for item M9201. This ensures that every third license plate registered will be moved to a quality location (QMS) and a quality order will be created for the license plate quantity. Everything other than every third registered license plate will be directed to put-away instead of QMS.

### Process Quality Management Work to QMS

1. Go to **Procurement and sourcing > Purchase orders > All purchase orders**
1. Create a new purchase order with the following settings:
    - **Specify Vendor account** - *104*
    - **Warehouse** - *51*
1. Add a purchase order line with the following settings:
    - **Item** - *M9201*
    - **Quantity** - *20*
    - **UoM** - *ea*
    - **Warehouse** - *51*
1. Write down the purchase order number so you can use it later.
1. Go to a mobile device or emulator running the Warehouse mobile application (WMA) and sign into warehouse 51 by using **User ID** *51* and **Password** *1*.
1. Go to **Inbound > Purchase Receive** and enter the following values:
    - **PONum** - Enter the number for the purchase order that you just created.
    - **Qty** - *5*
    - **Unit** - *ea*
1. Continue receiving against the line, *5 ea* at a time, until the line is fully received (after creating a total of 4 LPs created).
1. Sign out of the WMA.
1. Back in the web client, go to **Procurement and sourcing > Purchase orders > All purchase orders**.
1. Find and open your purchase order.
1. In the **Purchase order lines** section, select the line for **Item number** *M9201* and then select **Purchase order lines > Work Details**.
1. Notice that the second and third work headers created are normal put-away work, while the first and the fourth are quality item sampling work. This is follows our item sampling setup, which is set to sample every third license plate.

#### Move to QMS

You will now move the license plates to their designated locations: the first and fourth license plates will go to QMS, while the second and third will go directly to storage. Do the following:

1. Go to a mobile device or emulator running the Warehouse mobile application (WMA) and sign into warehouse 51 by using **User ID** *51* and **Password** *1*.
1. Go to **Inbound > Purchase put away** and each of the license plates from the previous receiving procedure until you have closed all the work.

#### Summary: Process quality management work

You have now executed the quality item sampling work for the first and fourth license plates by moving them to the quality inspection location, while putting away the second and third license plates. The next step will be to do the quality order testing and control.

### Quality out setup: Move from QMS to storage or return

When workers report back on quality order results, the system will create work automatically.

You will now proceed with the required base setup of the work class, work template, and location directive to enable quality management for warehouse processes to create the required work to moved the quality order quantity from QMS to a designated warehouse location.

#### Work class for quality out

1. Go to **Warehouse management > Setup > Work > Work classes**.
1. Create a new work class with the following settings:
    - **Work class ID** - *QualityOut*
    - **Description** - *Quality Out*
    - **Work order type** - *Quality Order*

#### Work templates

1. Go to **Warehouse management > Setup > Work > Work templates**.
1. Change the **Work order type** to *Quality order*.
1. Create a new work template with the following settings:
    - **Work template** - *51 quality out*
    - **Work template description** - *51 quality out*
1. Add a new line with the following settings:
    - **Work type** - *Pick*
    - **Work class ID** - **QualityOut**
1. Add a second line with the following settings:
    - **Work type**: *Put*
    - **Work class ID**: *QualityOut*

#### Location directives

1. Go to **Warehouse management > Setup > Location directives**.
1. Change the **Work order type** to *Quality order*.
1. Create a new location directive with the following settings:
    - **Name** - *51 Pass*
    - **Work type** - *Put*
    - **Site** - *5*
    - **Warehouse** - *51*
1. On the action pane, select **Edit query** to open the query editor pane.
1. On the **Range** tab of the query editor, enter the following settings:
    - **Table** - *Quality orders*
    - **Field** - *Status*
    - **Criteria** - *Pass*
1. Select **OK** to save the query and close the pane.
1. On the **Lines** FastTab, add a new line with the following settings:
    - **From quantity** - *1*
    - **To quantity** - *1000000*
1. On the **Location Directive Actions** FastTab, add a row with the following settings:
    - **Name** - *Pass*
1. On the **Location Directive Actions** FastTab, select **Edit query** to open the query editor pane.
1. On the **Range** tab of the query editor, enter the following settings:
    - **Table** - *Locations*
    - **Field** - *Zone ID*
    - **Criteria** - *Bulk*
1. Select **OK** to save the query and close the pane.
1. On the action pane, select **Save** to save this new location directive.
1. Create a second location directive with the following settings:
    - **Name** - *51 Fail*
    - **Work type** - *Put*
    - **Site** - *5*
    - **Warehouse** - *51*
1. On the action pane, select **Edit query** to open the query editor pane.
1. On the **Range** tab of the query editor, enter the following settings:
    - **Table** - *Quality orders*
    - **Field** - *Status*
    - **Criteria** - *Fail*
1. Select **OK** to save the query and close the pane.
1. On the **Lines** FastTab, add a new line with the following settings:
    - **From quantity** - *1*
    - **To quantity** - *1000000*
1. On the **Location Directive Actions** FastTab, add a row with the following settings:
    - **Name** - *Fail*
1. On the **Location Directive Actions** FastTab, select **Edit query** to open the query editor pane.
1. On the **Range** tab of the query editor, enter the following settings:
    - **Table** - *Locations*
    - **Field** - *Zone ID*
    - **Criteria** - *Return*
1. Select **OK** to save the query and close the pane.
1. On the action pane, select **Save** to save this new location directive.

#### Mobile device menu items for quality out

1. Go to  **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select the **QMS put-away** mobile device menu item.
1. On the **Work classes** FastTab, add the *QualityPut* work class ID.

Warehouse workers will now be able to pick quality order work using the **QMS Put-away** menu item, both for the quality failed goods to the put at a return location, and the quality passed goods to be put in the bulk-001 location.

#### Summary: Your move from QMS setup

You set up the work and location data for warehouse 51 to ensure that work is automatically created upon quality order completion. This ensures that each quality-controlled license plate is moved to either a bulk or return location.

### Process quality management work from QMS

1. Go to  **Inventory management > Periodic tasks > Quality management > Quality orders**.
1. Select the first quality order for the quantities that were registered.
1. On the action bar, select **Validate**. The test updates to a **Status** of *Fail*.
1. Go to  **Warehouse management > All Work**.
1. Open the work that you just created and note that it shows a **Work order type** of *Quality order*. It includes a line with a put **Location** of *Return* and a **Status** of *Fail*. If the quality order **Status** were *Pass*, then the put **Location** would be *Bulk*.
1. Go back to **Inventory management > Periodic tasks > Quality management > Quality orders**.
1. Select the second quality order for the items that were registered.
1. Select **Results** in the lower grid action bar. Update the **Result quantity** to *5* and verify that the **Test result** changes to a check mark.
1. Select **Validate** and close the page.
1. Back in the **Quality Orders** page, select **Validate** on the action bar and validate. The **Status** updates to *Pass*.
    > [!NOTE]
    > The validation event triggers the creation of the quality order work to move the quantity from the quality control location to a new location.
1. Go to **Warehouse management > All Work**.
1. Select the work just created and note that a second quality order work header has been created with a put **Location** of *BULK-001*.
1. Go to a mobile device or emulator running the Warehouse mobile application (WMA) and sign into warehouse 51 by using **User ID** *51* and **Password** *1*.
1. Go to **Quality > Put Away from QMS** and enter the following values process each of the two license plates related to both pieces of work such that all work gets closed.

> [!NOTE]
> Consider adding the quality out entry to a mobile device menu item with the activity code **Display open work list**. You can find such an example in mobile device menu item named **Work list** in the demo data. First add the **Quality order** work class to a user-directed menu item, as this is a prerequisite for work to be displayed in the work list. Then add the **Quality order** work class to the **Work list** menu item. Doing this will enable users with access to the work list list to pick and process the auto-generated work that results from a quality order validation.
