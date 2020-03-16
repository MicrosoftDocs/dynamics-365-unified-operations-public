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

**Quality management for warehouse processes** extends the capabilities of quality management. It allows users to integrate item sampling controls into the warehouse receiving process using advanced warehouse management. Warehouse work can be automatically generated to take inventory to the quality area by percentage, fixed quantity, or based on every nth license plate.  Once a quality order has been completed, work can automatically be created to take inventory to the next location in the process depending on the quality results. Further to this Quality management for warehouse processes extends the capabilities of quality management by allowing for quality orders to optionally be created for the inventory being sent to the quality area and quality orders are not always required. This accommodates for a lightweight quality control process only creating warehouse work.

Quality management for warehouse processes is enabled through feature management.

## Key benefits

Quality management for warehouse processes automatically creates work as part of the receiving process to move the inventory quantity required for quality control to a quality control location. Any quantity received, which exceeds the quantity required for quality control as per the item sampling, will move to an inbound location as per the location directive setup. Once the quality order is validated, work is automatically created to move the quantity for the quality order to a new, inbound location as per the location directive setup. The automatic creation of work with only the required quantity to move to and from quality control provides an integrated process experience.

> [!NOTE]
> When **Quality management for warehouse processes** is enabled, then it is still possible to leverage the manual process of using inventory movement and movement by template to have a warehouse worker trigger the creation of warehouse work to move inventory from a quality control location to a new location. It is also still supported to setup an inbound location directive to move inventory in its entirety, not considering the item sampling setup, from a receiving location to a quality control location.

## Quality management and Quality management for warehouse processes

Once **Quality management for warehouse management processes** is enabled through feature management, changes are introduced to the setup of key warehouse management and quality management entities. An overview of the entities that in combination enable quality order for warehouse processes are the below. In parenthesis is stated the suggested action, if quality management has been applied prior to enabling _Quality management for warehouse management processes_.

## Enablers: Work order types "Quality item sampling" and "Quality order"

_Quality management for warehouse processes_ introduces two work order types: Quality item sampling and Quality order. These are used with the purpose of enabling the work creation process for _Quality management for warehouse processes_. **Quality item sampling** is the work order type used for work creation to move registered inventory into quality control. Once quality control has completed, **Quality order** is the work order type used for work creation to move inventory from quality control to a new location based on location directive setup.

### Work class, Location directive, and Work templates

Work order types _Quality item sampling_ and _Quality order_ are consumed by location directives, work classes, and work templates. In order for warehouse work to be automatically created to move inventory to a quality control, a work class for _quality item sampling_ and _quality order_ respectively must be created. This is needed to ensure that appropriate work can be created automatically off of the two work order types and that this work subsequently can be executed in the warehouse mobile application (WMA). Subsequently, It is required to setup a work template for both work order types. In order to move inventory registered to a quality control location automatically, a work template must be setup using the _quality item sampling_ work order type. In order to move inventory from a quality location, once quality control is completed, it is required to setup a work template using the _quality order_ work order type. Location directives for the two work order types must be setup such that the correct quality control location to move the inventory to upon registration is applied; once quality control is completed, the location directive for _quality order_ ensures that that a new destination location is selected for moving the inventory out of the quality control location.

Lastly it is required to decide which mobile device menu item(s) should support moving the received inventory to the quality control location and which mobile device menu item(s) should support moving the inventory passing or failing control from the quality control location to a new location.

For navigation and examples of _how-to_ setup the enablers for quality management for warehouse processes, see _simple demo_.

## Quality management: Enable a warehouse

First the warehouse needs to be enabled before _quality management for warehouse processes_ can be applied for a specific warehouse. This is done by setting the parameter under _Warehouse management > Setup > Warehouse > Warehouses > Warehouse tab,_ **Enable quality order for warehouse processes** to **Yes**. This parameter can only be set to Yes, when the warehouse uses warehouse management processes. When the parameter _Enable quality order for warehouse processes_ is set to Yes, whether quality order for warehouse management is actually applied for this warehouse is controlled by the quality association setup. The parameter can at any given point in time be switched back to No, whereby _quality management for warehouse processes_ will not be applicable for the warehouse regardless of the setup in quality associations.

## Quality management: Quality Control

_Quality management for warehouse processes_ controls a number of key settings for quality associations and item sampling.

### Quality management: Quality Associations

Navigate to _Inventory Management > Setup > Quality Control > Quality Associations_.

In **Quality Association** under Conditions fast tab, the **Applicable warehouse type** can be set to either **All** or **Quality Management for warehouse processes only**.

Only when set to **Quality Management for warehouse processes only** does the _quality management for warehouse processes_ take effect. It is only possible to select the option, _Quality Management for warehouse processes only,_ when the reference type is either **Purchase** or **Production**. For all other reference types, the _Applicable warehouse type_ value can only be _All_. The _All_ value is similar as quality management without _Quality management for warehouse processes_ being enabled. Features part of _Quality management for warehouse processes_ do not take effect when the _Applicable warehouse type_ is _All_.

> [!NOTE]
> Quality Management for warehouse processes only takes effect when the item on the source document line uses advanced warehouse management processes and the warehouse parameter **Enable quality order for warehouse processes** is set to **Yes** for the warehouse on the source document line.

When _Quality management for warehouse processes_ is enabled, then the applicable warehouse type is logically inserted into the 4th level of the quality association search hierarchy. The below is a logical representation of the search hierarchy.

| Level | Description |
| --- | --- |
| Level&nbsp;1 | **Reference type**, **Event type**, and **Execution match**. If there is a match against the source document line, then proceed to level 2. |
| Level 2 | **Item code** : **Table**, **Group**, **All**. Table is more specific than group, group is more specific than All. If there is a match for Table (specific item), then proceed to level 3. If no match for Table, then search for Group match. If not match for Group, then All applies. If match, proceed to level 3. |
| Level 3 | **Account code** / **Resource code**. Similar search as applied for Item code. |
| Level 4 | **Applicable warehouse type** : **Quality order for warehouse processes only**, **All**. If the warehouse on the source document has _Enable quality order for warehouse processes_ set to _Yes_ **,** and the item on the source document line is setup to _Use warehouse management processes_, then both an association with _quality management for warehouse processes only_ and _All_ will be applicable in parallel if both exist. If the warehouse on the source document has _Enable quality order for warehouse processes_ set to _No_ **,** and the item on the source document line is setup to _Use warehouse management processes_, then only quality management will be applicable. |

Consider that you have defined a warehouse with **Enable quality order for warehouse processes** to **Yes** , and you have two quality associations defined for reference type purchase, All items, Event type Registration. The only difference between the two quality associations is the **Applicable warehouse type** : One is **All** , the other is **Quality management for warehouse processes only**. In such a case they are both equally specific and both quality association will be applicable. However, if the test group is the same for both of the associations, then only one quality order will be created. The quality order will be created for the quality association where the **Applicable warehouse type** equals **Quality order for warehouse processes only**.

If the test group is not the same both of the associations, then two quality orders will be created. The first quality order will be created for the quality association where the **Applicable warehouse type** equals **Quality order for warehouse processes only**. The second quality order will be created for the quality association where the **Applicable warehouse type** equals **All**.

> [!NOTE]
> The applicable warehouse type **Quality management for warehouse processes only**, is considered more specific than **All** in cases where the criteria for the quality associations for level 1 and 2 are the same and the test group is the same. Two quality orders will only be created when the test groups differ.

#### Reference types

When the _reference type_ is _purchase_ and the Applicable warehouse type is _Quality management for warehouse processes only_ then the _event type_ (Process tab) must be _registration_. Only _registration_ is a supported event for _purchase_ when using _quality order for warehouse processes_.

When the _reference type_ is _production_ and the _Applicable warehouse type_ is _Quality management for warehouse processes only,_ then the event type (Process tab) must be _Report as finished_ and the _execution_ (Process tab) must be _After_. Only _report as finished_ with _execution After_ is a supported event for production when using _quality order for warehouse processes_.

#### Quality processing policy

The _Quality processing policy_ is located in the tab _Quality order process_. It can have the value _Create quality order_ or _Create work only_. The default value is _Create quality order_.

If the _conditions_ of the _quality association_ are met for a _reference type_, then a quality order is created.

_Quality management for warehouse processes_ introduces the ability to create work based on item sampling only. This to allow for a lightweight process. This supports scenarios such as where only work is desired to be automatically created to move part of the registered quantity related to a purchase order line or production report as finished to a quality control location without creating a quality order upfront. The inventory for which work is created is based on the _item sampling_ associated with the quality association. Once the quantity is put at the quality control location, the quality department can manually create a quality order if needed.

> [!NOTE]
> If the Quality processing policy is **Create work only**, then only **Quality item sampling** work to move inventory to the quality control location is automatically created. The automatic creation of quality order work from a quality control location happens upon quality order validation. Therefore, if it is desired to have work automatically created to move the inventory from the quality location to a new location upon quality order validation, a quality order must be manually created. The validation of the quality order will trigger the automatic creation of **Quality order** work to move inventory from the quality control location.

The creation of quality order work is unrelated to the quality association setup. If a work template exists for the work order type **Quality order** and the query criteria are met for the work template **,** then the creation of quality order work is triggered upon quality order validation.

#### Referenced item sampling

It is mandatory for a _quality association_ to reference an _item sampling_. The item sampling defines what quantity is submitted to quality control. The _item sampling_ can be setup in such a manner that it only applies to _quality associations_ where the _Applicable warehouse__type_ is _Quality management for warehouse processes only_. _Item sampling_ where the _scope_ is either _load_ or _shipment_, or where the quantity specification is _Full license plate,_ can only be referenced against _quality associations_ where the _Applicable warehouse type_ is _Quality management for warehouse processes only_.

If an _item sampling_ is defined such that is can only be used in _Quality management for warehouse processes only_, then an error is thrown when it is attempted to be referenced from a _quality association_ which does not use _quality order for warehouse processes_.

> [!NOTE]
> Item sampling setup to use **full blocking** is not supported for a quality association with Applicable warehouse type equal Quality management for warehouse processes only.

### Quality management: Item Sampling

_Quality management for warehouse processes_ introduces the concept of _item sampling scope_. _Item sampling scope_ is used when evaluating if and how quality orders and/ or _quality item sampling_ work will be created. The base item sampling scope is **Order** which is the scope when _Quality management for warehouse processes_ is not enabled. When the scope is _Order_, then the source document line will be the basis for evaluating if and how quality orders and/ or _quality item sampling_ and _quality order_ work is created. Sampling scope **Load** and **Shipment** are only available when _Quality management for warehouse processes_ is enabled.

- Sampling scope = **Load**. The load will be used to as basis for evaluating if and how a quality order and/or work is created.
- Sampling scope = **Shipment**. The shipment will be used to as basis for evaluating if and how a quality order and/or work is created.

> [!NOTE]
> When the scope is set to Shipment or Load, those entities will be used if available. If not, then the order will be used.

In addition to _scope_, _Quality management for warehouse processes_ introduces the quantity specification **Full license plate**. **Full license plate** supports the creation of quality order and _quality item sampling_ work based on license plates.

When the quantity specification F_ull license plate_ is selected in **Inventory management > Setup > Quality Control > Item Sampling, fast tab Sampling quantity** , then the **Break count by item** and **Per nth license plate** options in the **Process** FastTab become active and the value field in _Sampling quantity_ becomes inactive. _Per updated quantity_, _Location_, and _License plate_ are automatically set to Yes and cannot be changed.

**Break count by item** controls if the license plate count is evaluated per item, or if the count is across all items within the sampling scope. Product variants are treated as the same item. _Break count by item_ controls if the license plate count is reset for each different item.

The value in_Per nth license plate_ creates quality orders per every nth license plate that is receipt registered. _Per nth license plate_ requires a value greater than 0.

When receiving in the warehouse mobile application (WMA) and the item being received matches a _quality association_ then the referenced _item sampling_ will be used to control the creation of quality orders and what combination of _quality item sampling_ and _purchase order_ work is created.

> [!NOTE]
> When receipt registering in the client using the small registration form or item arrival journal for purchase order lines, if the item being registered matches a quality association, then the referenced item sampling will be used to control the creation of quality orders only. No quality item sampling work nor Purchase order work will be created regardless of the setup of the applicable warehouse type on the quality association.

## Quality order auto generation – examples when the Applicable warehouse type is Quality management for warehouse processes only

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

## Simple demo

### Prepare the demo

Pre-condition: Demo data, Company USMF

#### Feature Management

This step is required if you have not auto enabled the feature.

Navigate to the Feature Management Workspace. Select the tab page &quot;Not enabled&quot; Select the feature **Quality Management For Warehouse Processes.** Choose to Enable now.

#### Warehouse

You will start by enabling warehouse 51 to use the quality management for warehouse processes feature.

Navigate to _Warehouse management > Setup > Warehouse > Warehouses_ and select warehouse 51. Expand the Warehouse FastTab and set &#39;Enable quality order for warehouse processes&quot; to Yes

### Quality In Setup – move to QMS

Then you proceed with the required base setup of the work class, work template, location directive, item sampling, and quality association to enable quality management for warehouse processes to run for warehouse 51.

#### Work class

Navigate to _Warehouse management > Setup > Work > Work classes._ Create a new work class.

- Work class ID: QualityIn
- Description: Quality Item Sampling
- Work order type: Quality Item Sampling

#### Work template

Navigate to _Warehouse management > Setup > Work > Work templates_. Select Work order type = **Quality Item Sampling**. Create a new work template:

- Work template: 51 Quality
- Work template description: 51 Quality

Create a new line for the work template:

- Work type: Pick
- Work class ID: QualityIn

Create a second line the work template:

- Work type: Put
- Work class ID: QualityIn

#### Location directive

Navigate to _Warehouse management > Setup > Location directives_ and select Work order type = **Quality Item Sampling**. Create a new location directive:

- Name: 51 To Quality
- Work type: Put
- Site: 5
- Warehouse: 51

Create a new **line** :

- From quantity: 1
- To quantity: 1000000

Create a new **Location Directive Action** :

- Name: Quality

On the new location directive action, open the Edit query and specify a Range record for table Locations. Field =  Location Profile ID, Criteria = QMS. Click OK to save the query and save this new location directive.

Next, you will change the sequence of the existing purchase order location directives for warehouse 51. The demo data includes two location directives for work order type = Purchase named &quot; **51 QMS**&quot; and &quot; **51 PO Direct**&quot;. To ensure that the quality management fore warehouse processes feature is applied for warehouse 51, it is important that the location directive named &quot; **51 QMS**&quot; is not applied. In order to allow you to change back, rather than deleting the location directive, you re-sequence.

In the Location Directives form, do the following:

Select work order type = Purchase Order. In the sequence list, select sequence number 5 with location directive &quot; **51 PO Direct**&quot;. Move this sequence up, such that it gets sequence 4. Check that as a result of this action, the location directive named &quot; **51 QMS**&quot; now has a sequence equal to or higher than 5.

#### Item sampling

Quality management for warehouse processes enables a few additional item sampling capabilities. Sampling scope can now be order, shipment, or load, and sampling quantity can now be full license plate.

Navigate to _Inventory management > Setup > Quality control > Item sampling_ and create a new record.

- Item sampling = 3rd LP
- Description: Every third license plate
- Sampling Scope: **Order**

In the Sampling quantity FastTab, set the Quantity specification to **Full license plate**.

In the Process FastTab, set the Per nth License Plate field value to **3**.

Enable both **Warehouse** and **Inventory status** in the per storage dimension section.

#### Quality associations

Now you create a quality association that will use the new item sampling.

Navigate to _Inventory management > Setup > Quality control > Quality associations_ and create a new record: Reference Type = **Purchase** , Item code = Table, Item = **M9201** , Site = **5**.

Set &quot; **Applicable warehouse type**&quot; to &quot; **Quality management for warehouse processes only**&quot;.

Expand the **Process** FastTab **and Set the event type = &quot;** Registration**&quot;.

Expand the **Quality Order Process** FastTab **and set Quality Processing Policy** = &#39; Create Quality Order&#39; .

Expand the **Specifications FastTab** , and on the Test Group select to View All (Right click – View All).

When you are in the Test Groups form, create a new test group as below:

- Test Group = QMS
- Description = QMS Test
- Acceptable quantity = 100
- Item Sampling = 3rd LP (Select)

In the line Overview, add a record (one test):

- Sequence = 1
- Test = Enclosure measuring
- In the **Test tab** , select **Test variables** = Pass/Fail
- Choose **Default outcome** = Pass

Save the new Test Group and close the form.

**Back** in the Quality associations form, in the **Test group** field select **QMS**. Save the record.

#### Mobile device menu items

In order to complete the setup of moving goods to QMS, you need the quality In Sampling work to be available from a mobile device menu item.

Navigate to _Warehouse management > Setup > Mobile device > Mobile device menu items_ and select **Purchase Put-away** mobile device menu item. In the Work classes FastTab, add the &#39; **QualityIn&#39;** work class ID.

#### Setup summery – move to QMS

You have now defined the quality association triggering the creation of a quality order using the quality management for warehouse processes feature. You have setup the work and location data for warehouse 51 to ensure that specific work is created upon purchase registration for M9201 to ensure that each 3rd license plate registered is moved to a quality location (QMS) and a quality order is created for the license plate quantity. Everything but every 3rd license plate registered will be directed to put-away instead of QMS.

### Processing Quality Management Work to QMS

**Navigate to** _Procurement and sourcing > Purchase orders > All purchase orders_ and create a new order. Specify Vendor account = 104 and Warehouse = 51.

Create on Purchase order line with the following data:

- Item = M9201
- Quantity = 20
- UoM = ea
- Warehouse = 51

Write down the purchase order number.

Open the **warehouse mobile application** (WMA). Login with User ID = 51 and demo Password = 1. Navigate to _Inbound > Purchase Receive_.

Enter your purchase order number as PONum.

Ensure to enter 5 ea as the quantity. Continue receiving against the line, 5 ea at a time, until the line is fully received (4 total LPs created). Logout from the warehouse mobile application (WMA).

**Navigate back** to _Procurement and sourcing > Purchase orders > All purchase orders_ and find your purchase order. Select the purchase order line for item M9201, and in the Purchase Order Lines ribbon click on **Work Details**.

Notice that the second and third work headers created are normal put-away work, while the first and the fourth created Quality Item Sampling work. This is according to our item sampling setup, each 3rd license plate.

#### Move to QMS

You are now going to move the license plates to their designated locations: 1st and 4th LP to QMS, and 2nd and 3rd LP to storage.

Open the **warehouse mobile application** (WMA). Login with User ID = 51 and demo Password = 1. Navigate to _Inbound > Purchase put away_ and enter each of the license plates from the previous receiving such that all work is closed.

#### Summary – Processing quality management work

You have now executed the quality item sampling work for the 1st and 4th license plates moving them to the quality inspection location (QMS), while you have put away the 2nd and 3rd license plate received. Next step will be to do the quality order related testing and control.

### Quality Out Setup – move from QMS to storage or return

When reporting back on quality order results and the process is using quality management for warehouse processes, work will be automatically created.

You will now proceed with the required base setup of the work class, work template, and location directive to enable quality management for warehouse processes to create the required work to moved the quality order quantity from QMS to a designated warehouse location.

#### Work class

Navigate to _Warehouse management > Setup > Work > Work classes_ and create a new work class.

- Work class ID: QualityOut
- Description: Quality Out
- Work order type: Quality Order

#### Work templates

Navigate to _Warehouse management > Setup > Work > Work templates_ and change the Work order type to **Quality Order**. Create a new work template:

- Work template: 51 Quality Out
- Work template description: 51 Quality Out

Create a new line for the work template:

- Work type: Pick
- Work class ID: QualityOut

Create a second line for the work template:

- Work type: Put
- Work class ID: QualityOut

#### Location directives

Navigate to _Warehouse management > Setup > Location directives._ Change the **Work order type** to **Quality Order**. Create a new location directive:

- Name: 51 Pass
- Work type: Put
- Site: 5
- Warehouse: 51

On the new location directive header, open the Edit query and specify a Range record for table Quality Orders. Field = Status, Criteria = Pass. Click OK to save the query.

Create a new **line** :

- From quantity: 1
- To quantity: 1000000

Create a second and new **Location Directive Action** :

- Name: Pass

On the new location directive action, open the Edit query and specify a Range record for table Locations. Field = Zone ID, Criteria = Bulk. Click OK to save the query and save this new location directive.

**Create** a second location directive.

- Name: 51 Fail
- Work type: Put
- Site: 5
- Warehouse: 51

On the new location directive header, open the Edit query and specify a Range record for table Quality Orders. Field = Status, Criteria = Fail. Click OK to save the query.

Create a **new** line:

- From quantity: 1
- To quantity: 10000000

Create a **new** Location Directive Action:

- Name: Fail

On the new location directive action, open the Edit query and specify a Range record for table Locations. Field = Zone ID, Criteria = Return. Click OK to save the query and save this new location directive.

#### Mobile device menu items

Navigate to _Warehouse management > Setup > Mobile device > Mobile device menu items_ and select QMS Put-away. In the Work classes FastTab add the &#39;QualityOut&#39; work class ID.

The warehouse worker will now be able to pick the Quality order work using the QMS Put-away menu item, both for the quality failed goods to the put at a return location, and the quality passed goods to be put in the bulk-001 location.

#### Setup summery – move from QMS

You have setup the work and location data for warehouse 51 to ensure that work is automatically created upon quality order completion. This ensures that each license plate quality controlled is moved to either to a bulk or a return location.

### Processing Quality Management Work from QMS

Navigate to _Inventory management > Periodic tasks > Quality management > Quality orders_ and select the first quality order for the quantities that were registered.

Click on &#39;Validate&#39; in the action bar and validate. The test will be updated to a Status of Fail.

Navigate to _Warehouse management > All Work._ Select the work just created and view that a new piece of work was created for Work order type = Quality Order, with a put to the Return location, when the quality order status is Fail. If the quality order status were Pass, then the put location would be Bulk.

Navigate back to _Inventory management > Periodic tasks > Quality management > Quality orders_ and select the second quality order for the items that were registered. Click on Results in the lower grid action bar. Update the Result quantity to 5 and verify that the Test result changes to a checkmark. Click Validate and close the form.

Back in the Quality Orders form,Click on Validate in the header action bar and validate. The status will be updated to Pass.

> [!NOTE]
> The creation of the quality order work to move the quantity from the quality control location to a new location is triggered from the validation event.

Navigate to _Warehouse management > All Work._ Select the work just created and see that a second Quality Order work header has been created, with a put location of BULK-001.

Open the **warehouse mobile application** (WMA). Login with User ID = 51 and demo Password = 1. Navigate to _Quality > Put Away from QMS_ and process each of the two license plates related to both pieces of work such that all work gets closed.

> [!NOTE]
> Consider adding the quality out to a mobile device menu item with the activity code Display open work list. You can find such an example in mobile device menu item named **Worklist** part of demo data. First you add the Quality order work class to a User-Directed menu item, as this is a prerequisite for work to be displayed in the worklist. Then you add Quality order work class to the **Worklist** menu item. Doing such will enable users with access to the worklist list to pick and process the autogenerated work resulting from a quality order validation.