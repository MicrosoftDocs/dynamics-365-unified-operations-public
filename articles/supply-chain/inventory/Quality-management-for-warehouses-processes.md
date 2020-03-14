Quality management for warehouse processes
==========================================

*Quality management for warehouse processes* extends the capabilities of quality
management. It allows users to integrate item sampling controls into the
warehouse receiving process using advanced warehouse management. Warehouse work
can be automatically generated to take inventory to the quality area by
percentage, fixed quantity, or based on every nth license plate. Once a quality
order has been completed, work can automatically be created to take inventory to
the next location in the process depending on the quality results. Further to
this Quality management for warehouse processes extends the capabilities of
quality management by allowing for quality orders to optionally be created for
the inventory being sent to the quality area and quality orders are not always
required. This accommodates for a lightweight quality control process only
creating warehouse work.

Quality management for warehouse processes is enabled through feature
management.

Key benefits
------------

Quality management for warehouse processes automatically creates work as part of
the receiving process to move the inventory quantity required for quality
control to a quality control location. Any quantity received, which exceeds the
quantity required for quality control as per the item sampling, will move to an
inbound location as per the location directive setup. Once the quality order is
validated, work is automatically created to move the quantity for the quality
order to a new, inbound location as per the location directive setup. The
automatic creation of work with only the required quantity to move to and from
quality control provides an integrated process experience.

*Note: When Quality management for warehouse processes is enabled, then it is
still possible to leverage the manual process of using inventory movement and
movement by template to have a warehouse worker trigger the creation of
warehouse work to move inventory from a quality control location to a new
location. It is also still supported to setup an inbound location directive to
move inventory in its entirety, not considering the item sampling setup, from a
receiving location to a quality control location.*

Quality management and Quality management for warehouse processes
-----------------------------------------------------------------

Once *Quality management for warehouse management processes* is enabled through
feature management, changes are introduced to the setup of key warehouse
management and quality management entities. An overview of the entities that in
combination enable quality order for warehouse processes are the below. In
parenthesis is stated the suggested action, if quality management has been
applied prior to enabling *Quality management for warehouse management
processes*.

![](media/8d59ff5f679f18d9d9b98ce46b973815.png)

Enablers: Work order types Quality item sampling and Quality order
------------------------------------------------------------------

*Quality management for warehouse processes* introduces two work order types:
Quality item sampling and Quality order. These are used with the purpose of
enabling the work creation process for *Quality management for warehouse
processes*. *Quality item sampling* is the work order type used for work
creation to move registered inventory into quality control. Once quality control
has completed, *Quality order* is the work order type used for work creation to
move inventory from quality control to a new location based on location
directive setup.

### Work class, Location directive, and Work templates

Work order types *Quality item sampling* and *Quality order* are consumed by
location directives, work classes, and work templates. In order for warehouse
work to be automatically created to move inventory to a quality control, a work
class for *quality item sampling* and *quality order* respectively must be
created. This is needed to ensure that appropriate work can be created
automatically off of the two work order types and that this work subsequently
can be executed in the warehouse mobile application (WMA). Subsequently, It is
required to setup a work template for both work order types. In order to move
inventory registered to a quality control location automatically, a work
template must be setup using the *quality item sampling* work order type. In
order to move inventory from a quality location, once quality control is
completed, it is required to setup a work template using the *quality order*
work order type. Location directives for the two work order types must be setup
such that the correct quality control location to move the inventory to upon
registration is applied; once quality control is completed, the location
directive for *quality order* ensures that that a new destination location is
selected for moving the inventory out of the quality control location.

Lastly it is required to decide which mobile device menu item(s) should support
moving the received inventory to the quality control location and which mobile
device menu item(s) should support moving the inventory passing or failing
control from the quality control location to a new location.

For navigation and examples of *how-to* setup the enablers for quality
management for warehouse processes, see *simple demo*.

Quality management: Enable a warehouse
--------------------------------------

First the warehouse needs to be enabled before *quality management for warehouse
processes* can be applied for a specific warehouse. This is done by setting the
parameter under *Warehouse management-\>Setup-\>Warehouse-\> Warehouses-\>
Warehouse tab, Enable quality order for warehouse processes* to **Yes**. This
parameter can only be set to Yes, when the warehouse uses warehouse management
processes. When the parameter *Enable quality order for warehouse processes* is
set to Yes, whether quality order for warehouse management is actually applied
for this warehouse is controlled by the quality association setup. The parameter
can at any given point in time be switched back to No, whereby *quality
management for warehouse processes* will not be applicable for the warehouse
regardless of the setup in quality associations.

![](media/c70bd5d8139de4a686d83b74ba7bbcf0.png)

Quality management: Quality Control
-----------------------------------

*Quality management for warehouse processes* controls a number of key settings
for quality associations and item sampling.

### Quality management: Quality Associations

Navigate to *Inventory Management-\>Setup-\>Quality Control-\>Quality
Associations*.

In *Quality Association* under Conditions fast tab, the *Applicable warehouse
type* can be set to either *All* or *Quality Management for warehouse processes
only*.

![](media/8afa893038d6dee47f4daea18a74a52c.png)

Only when set to *Quality Management for warehouse processes only* does the
*quality management for warehouse processes* take effect. It is only possible to
select the option, *Quality Management for warehouse processes only,* when the
reference type is either **Purchase** or **Production**. For all other reference
types, the *Applicable warehouse type* value can only be *All*. The *All* value
is similar as quality management without *Quality management for warehouse
processes* being enabled. Features part of *Quality management for warehouse
processes* do not take effect when the *Applicable warehouse type* is *All*.

>   *Note: Quality Management for warehouse processes only takes effect when the
>   item on the source document line uses advanced warehouse management
>   processes and the warehouse parameter Enable quality order for warehouse
>   processes is set to Yes for the warehouse on the source document line.*

When *Quality management for warehouse processes* is enabled, then the
applicable warehouse type is logically inserted into the 4th level of the
quality association search hierarchy. The below is a logical representation of
the search hierarchy.

#### 1. Level **Reference type**, E**vent type**, and **Execution match**. If there is a match against the source document line, then proceed to level 2. 

2. Level **Item code**: **Table**, **Group**, **All**. Table is more specific
than group, group is more specific than All. If there is a match for Table
(specific item), then proceed to level 3. If no match for Table, then search for
Group match. If not match for Group, then All applies. If match, proceed to
level 3.

3. Level **Account code**/ **Resource code**. Similar search as applied for Item
code.

4. Level **Applicable warehouse type**: **Quality order for warehouse processes
only**, **All**. If the warehouse on the source document has *Enable quality
order for warehouse processes* set to *Yes***,** and the item on the source
document line is setup to *Use warehouse management processes*, then both an
association with *quality management for warehouse processes only* and *All*
will be applicable in parallel if both exist. If the warehouse on the source
document has *Enable quality order for warehouse processes* set to *No***,** and
the item on the source document line is setup to *Use warehouse management
processes*, then only quality management will be applicable.

Consider that you have defined a warehouse with *Enable quality order for
warehouse processes* to *Yes*, and you have two quality associations defined for
reference type purchase, All items, Event type Registration. The only difference
between the two quality associations is the *Applicable warehouse type*: One is
*All*, the other is *Quality management for warehouse processes only*. In such a
case they are both equally specific and both quality association will be
applicable. However, if the test group is the same for both of the associations,
then only one quality order will be created. The quality order will be created
for the quality association where the **Applicable warehouse type** equals
**Quality order for warehouse processes only**.

If the test group is not the same both of the associations, then two quality
orders will be created. The first quality order will be created for the quality
association where the **Applicable warehouse type** equals **Quality order for
warehouse processes only**. The second quality order will be created for the
quality association where the **Applicable warehouse type** equals **All**.

>   *Note: The applicable warehouse type Quality management for warehouse
>   processes only, is considered more specific than All in cases where the
>   criteria for the quality associations for level 1 and 2 are the same and the
>   test group is the same. Two quality orders will only be created when the
>   test groups differ.*

#### Reference types

When the *reference type* is *purchase* and the Applicable warehouse type is
*Quality management for warehouse processes only* then the *event type* (Process
tab) must be *registration*. Only *registration* is a supported event for
*purchase* when using *quality order for warehouse processes*.

When the *reference type* is *production* and the *Applicable warehouse type* is
*Quality management for warehouse processes only,* then the event type (Process
tab) must be *Report as finished* and the *execution* (Process tab) must be
*After*. Only *report as finished* with *execution After* is a supported event
for production when using *quality order for warehouse processes*.

#### Quality processing policy

The *Quality processing policy* is located in the tab *Quality order process*.
It can have the value *Create quality order* or *Create work only*. The default
value is *Create quality order*.

![](media/d600f2b56da08a286a5c73707f441b76.png)

If the *conditions* of the *quality association* are met for a *reference type*,
then a quality order is created.

*Quality management for warehouse processes* introduces the ability to create
work based on item sampling only. This to allow for a lightweight process. This
supports scenarios such as where only work is desired to be automatically
created to move part of the registered quantity related to a purchase order line
or production report as finished to a quality control location without creating
a quality order upfront. The inventory for which work is created is based on the
*item sampling* associated with the quality association. Once the quantity is
put at the quality control location, the quality department can manually create
a quality order if needed.

*Note: If the Quality processing policy is Create work only, then only Quality
item sampling work to move inventory to the quality control location is
automatically created. The automatic creation of quality order work from a
quality control location happens upon quality order validation. Therefore, if it
is desired to have work automatically created to move the inventory from the
quality location to a new location upon quality order validation, a quality
order must be manually created. The validation of the quality order will trigger
the automatic creation of Quality order work to move inventory from the quality
control location.*

The creation of quality order work is unrelated to the quality association
setup. If a work template exists for the work order type *Quality order* and the
query criteria are met for the work template**,** then the creation of quality
order work is triggered upon quality order validation.

#### Referenced item sampling

It is mandatory for a *quality association* to reference an *item sampling*. The
item sampling defines what quantity is submitted to quality control. The *item
sampling* can be setup in such a manner that it only applies to *quality
associations* where the *Applicable warehouse type* is *Quality management for
warehouse processes only*. *Item sampling* where the *scope* is either *load* or
*shipment*, or where the quantity specification is *Full license plate,* can
only be referenced against *quality associations* where the *Applicable
warehouse type* is *Quality management for warehouse processes only*.

If an *item sampling* is defined such that is can only be used in *Quality
management for warehouse processes only*, then an error is thrown when it is
attempted to be referenced from a *quality association* which does not use
*quality order for warehouse processes*.

*Note: Item sampling setup to use full blocking is not supported for a quality
association with Applicable warehouse type equal Quality management for
warehouse processes only*

### Quality management: Item Sampling

*Quality management for warehouse processes* introduces the concept of *item
sampling scope*. *Item sampling scope* is used when evaluating if and how
quality orders and/ or *quality item sampling* work will be created. The base
item sampling scope is *Order* which is the scope when *Quality management for
warehouse processes* is not enabled. When the scope is *Order*, then the source
document line will be the basis for evaluating if and how quality orders and/ or
*quality item sampling* and *quality order* work is created. Sampling scope
*Load* and *Shipment* are only available when *Quality management for warehouse
processes* is enabled.

-   Sampling scope = *Load*. The load will be used to as basis for evaluating if
    and how a quality order and/or work is created.

-   Sampling scope = *Shipment*. The shipment will be used to as basis for
    evaluating if and how a quality order and/or work is created.

>   *Note: When the scope is set to Shipment or Load, those entities will be
>   used if available. If not, then the order will be used.*

In addition to *scope*, *Quality management for warehouse processes* introduces
the quantity specification *Full license plate*. *Full license plate* supports
the creation of quality order and *quality item sampling* work based on license
plates.

When the quantity specification F*ull license plate* is selected in *Inventory
management-\>Setup-\>Quality Control-\>Item Sampling, fast tab Sampling
quantity*, then the *Break count by item* and *Per nth license plate* options in
the *Process* FastTab become active and the value field in *Sampling quantity*
becomes inactive. *Per updated quantity*, *Location*, and *License plate* are
automatically set to Yes and cannot be changed.

*Break count by item* controls if the license plate count is evaluated per item,
or if the count is across all items within the sampling scope. Product variants
are treated as the same item. *Break count by item* controls if the license
plate count is reset for each different item.

The value in *Per nth license plate* creates quality orders per every nth
license plate that is receipt registered. *Per nth license plate* requires a
value greater than 0.

When receiving in the warehouse mobile application (WMA) and the item being
received matches a *quality association* then the referenced *item sampling*
will be used to control the creation of quality orders and what combination of
*quality item sampling* and *purchase order* work is created.

>   *Note: When receipt registering in the client using the small registration
>   form or item arrival journal for purchase order lines, if the item being
>   registered matches a quality association, then the referenced item sampling
>   will be used to control the creation of quality orders only. No quality item
>   sampling work nor Purchase order work will be created regardless of the
>   setup of the applicable warehouse type on the quality association.*

Quality order auto generation – examples when the Applicable warehouse type is Quality management for warehouse processes only
------------------------------------------------------------------------------------------------------------------------------

The following examples illustrate how the setup of a *quality association* and
associated *item sampling* impacts the quality order generation when *Quality
management for warehouse processes* only is applied.

When the *quantity specification* is *Full License Plate*, then the *Per nth
license plate* controls for which license plates *quality item sampling* work is
created. The first license plate will always go to quality, then the nth after
that as controlled by this value.

The *Reference type* for the examples below is *Purchase*, and the *Event type
Registration*.

| **Sampling Scope** | **Quantity Specification** | **Per updated quantity**    | **Per storage dimension**                               | **Break count By item** | **Per nth license plate** | **Result**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|--------------------|----------------------------|-----------------------------|---------------------------------------------------------|-------------------------|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Order              | Full license plate         | Yes *Locked (not editable)* | Location:Yes License Plate: Yes *Locked (not editable)* | No                      | 3                         | Order line quantity: 100 EA 1. Register receipt on WMA for 20 EA, LP1 Quality Item sampling work for 20 EA Quality order \#1 for 20 EA 2. Register receipt on WMA for 20 EA, LP2 Purchase order work for 20 EA (put away) 3. Register receipt on WMA for 20 EA, LP3 Purchase order work for 20 EA (put away) 4. Register receipt on WMA for 20 EA, LP4 Quality Item sampling work for 20 EA 5. Register receipt on WMA for 20 EA, LP5 Purchase order work for 20 EA (put away)                                                                                                                                                                                                                                                                                                                                                                                          |
| Order              | Fixed quantity = 1         | Yes                         | Location:Yes License Plate: Yes                         | No                      |                           | Order line quantity: 100 1. Register receipt on WMA for 20 EA, LP1 Quality Item sampling work for 1 EA Quality order \#1 for 1 EA Purchase order work for 19 EA (put away) 2. Register receipt on WMA for 20 EA, LP2 Quality Item sampling work for 1 EA Quality order \#1 for 1 EA Purchase order work for 19 (put away) 3. Register receipt on WMA for 20 EA, LP3 Quality Item sampling work for 1 EA Quality order \#1 for 1 EA Purchase order work for 19 EA (put away) 4. Register receipt on WMA for 20 EA, LP4 Quality Item sampling work for 1 EA Quality order \#1 for 1 EA Purchase order work for 19 EA (put away) 5. Register receipt on WMA for 20 EA, LP5 Quality Item sampling work for 1 EA Quality order \#1 for 1 EA Purchase order work for 19 EA (put away)                                                                                         |
| Order              | Percent=10                 | No                          | Location:No License Plate:No                            | No                      |                           | Order line quantity: 100 EA 1. Register receipt on WMA for 50 EA, LP1 Quality Item sampling work for 10 EA Quality order \#1 for 10 EA Purchase order work for 40 EA (put away) 2. Register receipt on WMA for 50 EA, LP2 Purchase order work for 50 EA (put away)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Load               | Percent=5                  | Yes *Locked (not editable)* | Location:No License Plate:No                            | No                      |                           | Order line quantity: 500 EA Two Loads: 1st load 200 EA, 2nd load 300 EA 1. Register receipt on WMA 1st load for 100 EA Quality Item sampling work for 5 EA Quality order \#1 for 5 EA Purchase order work for 95 EA (put away) 2. Register receipt on WMA 1st load for 100 EA Quality Item sampling work for 5 EA Quality order \#1 for 5 EA Purchase order work for 95 EA (put away) 3.Register receipt on WMA 2nd load for 300 EA Quality Item sampling work for 15 EA Quality order \#1 for 15 EA Purchase order work for 285 EA (put away)                                                                                                                                                                                                                                                                                                                          |
| Order              | Percent=10                 | No                          | Location:Yes License Plate:Yes                          | No                      |                           | Order line quantity: 100 1. Register receipt on WMA for 50 EA, LP1 Quality Item sampling work for 5 EA Quality order \#1 for 5 EA Purchase order work for 45 EA (put away) 2. Register receipt on WMA for 50 EA, LP2 Quality Item sampling work for 5 EA Quality order \#1 for 5 EA Purchase order work for 45 (put away)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Load               | Full license plate         | Yes *Locked (not editable)* | Location:Yes License Plate: Yes *Locked (not editable)* | No                      | 3                         | Two items: Order line quantity Item A: 120 EA (4 pallets) Order line quantity Item B: 90 EA (3 pallets) One Load, two load lines with each of the order lines. 1. Register receipt on WMA Item A, 30 EA, LP1 Quality Item sampling work for 30 EA Quality order \#1 for 30 EA 2. Register receipt on WMA Item A, 30 EA, LP2 Purchase order work for 30 EA (put away) 3. Register receipt on WMA Item A, 30 EA, LP3 Purchase order work for 30 EA (put away) 4. Register receipt on WMA Item A, 30 EA, LP4 Quality Item sampling work for 30 EA Quality order \#1 for 30 EA 5. Register receipt on WMA Item B, 30 EA, LP5 Purchase order work for 30 EA (put away) 6. Register receipt on WMA Item B, 30 EA, LP6 Purchase order work for 30 EA (put away) 7. Register receipt on WMA Item A, 30 EA, LP7 Quality Item sampling work for 30 EA Quality order \#1 for 30 EA |
| Load               | Full license plate         | Yes *Locked (not editable)* | Location:Yes License Plate: Yes *Locked (not editable)* | Yes                     | 3                         | Two items: Order line quantity Item A: 120 EA (4 pallets) Order line quantity Item B: 90 EA (3 pallets) One Load, two load lines with each of the order lines. 1. Register receipt on WMA Item A, 30 EA, LP1 Quality Item sampling work for 30 EA Quality order \#1 for 30 EA 2. Register receipt on WMA Item A, 30 EA, LP2 Purchase order work for 30 EA (put away) 3. Register receipt on WMA Item A, 30 EA, LP3 Purchase order work for 30 EA (put away) 4. Register receipt on WMA Item A, 30 EA, LP4 Quality Item sampling work for 30 EA Quality order \#1 for 30 EA 5. Register receipt on WMA Item B, 30 EA, LP5 Quality Item sampling work for 30 EA Quality order \#1 for 30 EA 6. Register receipt on WMA Item B, 30 EA, LP6 Purchase order work for 30 EA (put away) 7. Register receipt on WMA Item A, 30 EA, LP7 Purchase order work for 30 EA (put away) |
| Load               | Percent=10                 | Yes *Locked (not editable)* | Location:No License Plate:No                            | No                      |                           | Order line quantity: 100 EA No load(s) created. Order scope is applied. 1. Register receipt on WMA for 50 EA, LP1 Quality Item sampling work for 5 EA Quality order \#1 for 5 EA Purchase order work for 45 EA (put away) 2. Register receipt on WMA for 50 EA, LP2 Quality Item sampling work for 5 EA Quality order \#1 for 5 EA Purchase order work for 45 EA (put away)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

The validation of the quality orders in above examples trigger the creation of
*quality order* work to move inventory from the quality location to a location
as defined in the location directive for the *quality order* work order type.
This can be setup to be any location such as a return or storage location
depending on the test result for the quality order. See the simple demo for an
example of such setup.

It is possible to re-open a quality order already validated. However, when
*Quality order* work related to moving the inventory from the quality location
is in status closed or in progress, then the quality order cannot be re-opened.

Process insights when multiple quality associations co-exist
------------------------------------------------------------

It is possible to have more quality associations defined and applied for the
same source document line where both the applicable warehouse type equal
**Quality management for warehouse processes only** and **All.**

Consider the following scenario for reference type *purchase*:

1.  First quality association defined: *Applicable warehouse type* equal
    **Quality management for warehouse processes only**, **Item code** equal
    A0001, **Account code** equal All, **Test group** equal Enclosure. **Item
    sampling** is 5 pcs.

2.  Second quality association defined: *Applicable warehouse type* equal All,
    **Item code** equal All, **Account code** equal All, **Test group** equal
    Enclosure. **Item sampling** is 1 pcs.

3.  Third quality association defined: *Applicable warehouse type* equal
    **Quality management for warehouse processes only**, **Item code** equal
    All, **Account code** equal 104, **Test group** equal Impedance. **Item
    sampling** is every 2nd license plate. This implies that 1st license plate
    received, 3rd license plate received, 5th license plate received, etc. will
    create a quality order.

4.  Fourth quality association defined: *Applicable warehouse type* equal All,
    **Item code** equal All, **Account code** equal All, **Test group** equal
    Impedance. **Item sampling** is 5 pcs.

5.  Fifth quality association defined: *Applicable warehouse type* equal All,
    **Item code** equal All, **Account code** equal All, **Test group** equal
    Cone. **Item sampling** is 10%.

A purchase order is created for vendor 104, item A0001 with quantity 10.

Purchase order line quantity 10 is registered as received on one license plate
using the warehouse mobile application.

The result will be the following:

-   One quality order from the first quality association for test group
    Enclosure. Quantity 5. No quality order from the second quality association,
    as the criteria for the first quality association is more specific relative
    to the test group Enclosure.

-   One quality order for the third quality association for test group
    Impedance. Quantity 10. No quality order from the fourth quality
    association, as the criteria for the first quality association is more
    specific relative to the test group Impedance.

-   One quality order for the fifth quality association for test group Cone.
    Quantity 1.

In relation to creating one quality order for each of the 3 quality
associations, quality item sampling work is also created. As the quantity
registered is only 10, and the sum of the quality order quantities created for
**Quality management for warehouse processes only** is 16 per the item sampling
setup and thereby exceeding the physical quantity registered of 10, work will
not be created for the entire quality order quantities; the 16. Only 10 are
physically available to be moved to the quality control location. The priority
in which quality item sampling work creation is performed, follows the order of
the quality order creation:

-   1st Quality order, quantity 5. Quality Item sampling work created for 5. Now
    quantity 5 (10-5) remains for subsequent quality item sampling work
    creation.

-   2nd Quality order, quantity 10. Quality Item sampling work created for 5.
    Now quantity 0 remains for subsequent quality item sampling work creation.

-   3rd Quality order, quantity 1. No quality item sampling work created.

As part of creating the quality orders, an inventory blocking of quantity 10 is
created. This inventory blocking is referenced against each of the three quality
orders. Sum of the quality order quantities is 16.

Upon **quality order validation**, quality order work will be attempted to be
created for each quality order validated. As the sum of the quality order
quantities exceeds what is actually blocked and hence available for work
creation, quality order work cannot be created for the entire quality order
quantities. This is exemplified by continuing with the example.

-   First step: Validate the 2nd quality order created, quantity 10. Quality
    order work is created for quantity 4.

    -   The creation of quality order work is triggered by a change in the
        inventory blocking quantity. As the sum of quality orders quantity was
        16, validating quantity 10 will result in the remaining quality order
        quantities to validate equaling 6. The inventory blocking quantity is
        reduced to 6 (from 10 to 6); the reduced quantity of 4 is allotted to
        the quality order work creation.

-   Second step: Validate the 1st quality order created, quantity 5. Quality
    order work is created for quantity 5.

    -   The creation of quality order work is triggered by a change in the
        inventory blocking quantity. As the sum of quality orders quantity was
        6, validating quantity 5 will result in the remaining quality order
        quantities to validate equaling 1. The inventory blocking quantity is
        reduced to 1 (from 6 to 1); the reduced quantity of 5 is allotted to the
        quality order work creation.

-   Third step: Validate the 3rd quality order created, quantity 1. Quality
    order work is created for quantity 1.

    -   The creation of quality order work is triggered by a change in the
        inventory blocking quantity. As the sum of quality orders quantity was
        1, validating quantity 1 will result in the remaining quality order
        quantities to validate equaling 0. The inventory blocking is removed
        (from 1 to 0); the reduced quantity of 1 is allotted to the quality
        order work creation.

        *Note: Creating quality order work depends on the inventory blocking
        quantity referenced against one or more quality orders. If the sum of
        the quality order quantities exceeds the referenced inventory blocking
        quantity, then the order in which the quality orders are validated
        determines the creation of quality order work.*

Cancelling quality item sampling work
-------------------------------------

It is possible to cancel the work created for *Quality item sampling*. The
effect of the cancelling is conditioned by the parameter *Warehouse
management-\> Setup-\>Warehouse management parameters-\>General-\>Work
tab-\>Unregister receipt when cancelling work.* If the parameter is *Yes* and
*Quality item sampling* work is cancelled, then the associated quality order
will be deleted, and the inventory will be unregistered. If this parameter is
*No* and Q*uality item sampling* work is cancelled, then the associated quality
order will not be deleted, and the inventory will not be unregistered.

Cross docking
-------------

It is possible to have a quality association setup which creates item sampling
work. However, when cross docking exists in parallel with a quality association
creating *quality item sampling* work, and there is only sufficient quantity to
satisfy cross docking, then only item sampling work will be created. In a case
where the receiving warehouse is setup to *Enable quality order for warehouse
processes* and a quality association is setup to use *Quality Management for
warehouse processes only,* then creating quality item sampling work *takes*
precedence over cross docking work. No cross docking work will be created. In
scenario where the quantity exceeds the requirement for cross docking, item
sampling work will still only be created.

Destructive test
----------------

It is possible to define a test group performing destructive tests. Destructive
tests imply that regardless of the test result, the quantity of an item
subjected to the test will be destroyed as part of the test. *Quality management
for warehouse processes* supports destructive testing in a similar way as
quality management without *Quality management for warehouse processes* enabled.
Before the quality order can be validated, it is required to pick the quality
order quantity. Picking will allow to specify the pick location. Picking can be
registered from within the quality order form by navigating to
*Inventory-\>Pick*. Once the pick for the quality order quantity is registered,
then validation can be completed.

Simple demo
===========

Pre-condition: Demo data, Company USMF

Feature Management
------------------

This step is required if you have not auto enabled the feature.

Navigate to the Feature Management Workspace. Select the tab page “Not enabled”
Select the feature **Quality Management For Warehouse Processes.** Choose to
Enable now.

Warehouse
---------

You will start by enabling warehouse 51 to use the quality management for
warehouse processes feature.

Navigate to *Warehouse management Setup Warehouse Warehouses* and select
warehouse 51. Expand the Warehouse FastTab and set ‘Enable quality order for
warehouse processes” to Yes

Quality In Setup – move to QMS
==============================

Then you proceed with the required base setup of the work class, work template,
location directive, item sampling, and quality association to enable quality
management for warehouse processes to run for warehouse 51.

Work class
----------

Navigate to *Warehouse management Setup Work Work classes.* Create a new work
class.

-   Work class ID: QualityIn

-   Description: Quality Item Sampling

-   Work order type: Quality Item Sampling

Work template
-------------

Navigate to *Warehouse management Setup Work Work templates*. Select Work order
type = **Quality Item Sampling**. Create a new work template:

-   Work template: 51 Quality

-   Work template description: 51 Quality

Create a new line for the work template:

-   Work type: Pick

-   Work class ID: QualityIn

Create a second line the work template:

-   Work type: Put

-   Work class ID: QualityIn

Location directive
------------------

Navigate to *Warehouse management Setup Location directives* and select Work
order type = **Quality Item Sampling**. Create a new location directive:

-   Name: 51 To Quality

-   Work type: Put

-   Site: 5

-   Warehouse: 51

Create a new **line**:

-   From quantity: 1

-   To quantity: 1000000

Create a new **Location Directive Action**:

-   Name: Quality

On the new location directive action, open the Edit query and specify a Range
record for table Locations. Field = Location Profile ID, Criteria = QMS. Click
OK to save the query and save this new location directive.

Next, you will change the sequence of the existing purchase order location
directives for warehouse 51. The demo data includes two location directives for
work order type = Purchase named “**51 QMS**” and “**51 PO Direct**”. To ensure
that the quality management fore warehouse processes feature is applied for
warehouse 51, it is important that the location directive named “**51 QMS**” is
not applied. In order to allow you to change back, rather than deleting the
location directive, you re-sequence.

In the Location Directives form, do the following:

Select work order type = Purchase Order. In the sequence list, select sequence
number 5 with location directive “**51 PO Direct**”. Move this sequence up, such
that it gets sequence 4. Check that as a result of this action, the location
directive named “**51 QMS**” now has a sequence equal to or higher than 5.

Item sampling
-------------

Quality management for warehouse processes enables a few additional item
sampling capabilities. Sampling scope can now be order, shipment, or load, and
sampling quantity can now be full license plate.

Navigate to *Inventory management Setup Quality control Item sampling* and
create a new record.

-   Item sampling = 3rd LP

-   Description: Every third license plate

-   Sampling Scope: **Order**

In the Sampling quantity FastTab, set the Quantity specification to ‘**Full
license plate**.’

In the Process FastTab, set the Per nth License Plate field value to **3**.

Enable both **Warehouse** and **Inventory status** in the per storage dimension
section.

Quality associations
--------------------

Now you create a quality association that will use the new item sampling.

Navigate to *Inventory management Setup Quality control Quality associations*
and create a new record: Reference Type = **Purchase**, Item code = Table, Item
= **M9201**, Site = **5**.

Set “**Applicable warehouse type**” to “**Quality management for warehouse
processes only**”.

Expand the **Process FastTab** and Set the event type = “**Registration**”.

Expand the **Quality Order Process FastTab** and set Quality Processing Policy =
‘**Create Quality Order’**.

Expand the **Specifications FastTab**, and on the Test Group select to View All
(Right click – View All).

When you are in the Test Groups form, create a new test group as below:

-   Test Group = QMS

-   Description = QMS Test

-   Acceptable quantity = 100

-   Item Sampling = 3rd LP (Select)

In the line Overview, add a record (one test):

-   Sequence = 1

-   Test = Enclosure measuring

-   In the **Test tab**, select **Test variables**= Pass/Fail

-   Choose **Default outcome** = Pass

Save the new Test Group and close the form.

**Back** in the Quality associations form, in the **Test group** field select
**QMS**. Save the record.

Mobile device menu items
------------------------

In order to complete the setup of moving goods to QMS, you need the quality In
Sampling work to be available from a mobile device menu item.

Navigate to *Warehouse management Setup Mobile device Mobile device menu items*
and select **Purchase Put-away** mobile device menu item. In the Work classes
FastTab, add the ‘**QualityIn’** work class ID.

Setup summery – move to QMS
---------------------------

You have now defined the quality association triggering the creation of a
quality order using the quality management for warehouse processes feature. You
have setup the work and location data for warehouse 51 to ensure that specific
work is created upon purchase registration for M9201 to ensure that each 3rd
license plate registered is moved to a quality location (QMS) and a quality
order is created for the license plate quantity. Everything but every 3rd
license plate registered will be directed to put-away instead of QMS.

Processing Quality Management Work to QMS
=========================================

**Navigate to** *Procurement and sourcing Purchase orders All purchase orders*
and create a new order. Specify Vendor account = 104 and Warehouse = 51.

Create on Purchase order line with the following data:

-   Item = M9201

-   Quantity = 20

-   UoM = ea

-   Warehouse = 51

Write down the purchase order number.

Open the **warehouse mobile application** (WMA). Login with User ID = 51 and
demo Password = 1. Navigate to *Inbound Purchase Receive*.

Enter your purchase order number as PONum.

Ensure to enter 5 ea as the quantity. Continue receiving against the line, 5 ea
at a time, until the line is fully received (4 total LPs created). Logout from
the warehouse mobile application (WMA).

**Navigate back** to *Procurement and sourcing Purchase orders All purchase
orders* and find your purchase order. Select the purchase order line for item
M9201, and in the Purchase Order Lines ribbon click on **Work Details**.

Notice that the second and third work headers created are normal put-away work,
while the first and the fourth created Quality Item Sampling work. This is
according to our item sampling setup, each 3rd license plate.

Move to QMS
-----------

You are now going to move the license plates to their designated locations: 1st
and 4th LP to QMS, and 2nd and 3rd LP to storage.

Open the **warehouse mobile application** (WMA). Login with User ID = 51 and
demo Password = 1. Navigate to *Inbound Purchase put away* and enter each of the
license plates from the previous receiving such that all work is closed.

Summery – Processing quality management work
--------------------------------------------

You have now executed the quality item sampling work for the 1st and 4th license
plates moving them to the quality inspection location (QMS), while you have put
away the 2nd and 3rd license plate received. Next step will be to do the quality
order related testing and control.

Quality Out Setup – move from QMS to storage or return
======================================================

When reporting back on quality order results and the process is using quality
management for warehouse processes, work will be automatically created.

You will now proceed with the required base setup of the work class, work
template, and location directive to enable quality management for warehouse
processes to create the required work to moved the quality order quantity from
QMS to a designated warehouse location.

Work class
----------

Navigate to *Warehouse management Setup Work Work classes* and create a new work
class.

-   Work class ID: QualityOut

-   Description: Quality Out

-   Work order type: Quality Order

Work templates
--------------

Navigate to *Warehouse management Setup Work Work templates* and change the Work
order type to **Quality Order**. Create a new work template:

-   Work template: 51 Quality Out

-   Work template description: 51 Quality Out

Create a new line for the work template:

-   Work type: Pick

-   Work class ID: QualityOut

Create a second line for the work template:

-   Work type: Put

-   Work class ID: QualityOut

Location directives
-------------------

Navigate to *Warehouse management Setup Location directives.* Change the **Work
order type** to **Quality Order**. Create a new location directive:

-   Name: 51 Pass

-   Work type: Put

-   Site: 5

-   Warehouse: 51

On the new location directive header, open the Edit query and specify a Range
record for table Quality Orders. Field = Status, Criteria = Pass. Click OK to
save the query.

Create a new **line**:

-   From quantity: 1

-   To quantity: 1000000

Create a second and new **Location Directive Action**:

-   Name: Pass

On the new location directive action, open the Edit query and specify a Range
record for table Locations. Field = Zone ID, Criteria = Bulk. Click OK to save
the query and save this new location directive.

**Create** a second location directive.

-   Name: 51 Fail

-   Work type: Put

-   Site: 5

-   Warehouse: 51

On the new location directive header, open the Edit query and specify a Range
record for table Quality Orders. Field = Status, Criteria = Fail. Click OK to
save the query.

Create a **new** line:

-   From quantity: 1

-   To quantity: 10000000

Create a **new** Location Directive Action:

-   Name: Fail

On the new location directive action, open the Edit query and specify a Range
record for table Locations. Field = Zone ID, Criteria = Return. Click OK to save
the query and save this new location directive.

Mobile device menu items
------------------------

Navigate to *Warehouse management Setup Mobile device Mobile device menu items*
and select QMS Put-away. In the Work classes FastTab add the ‘QualityOut’ work
class ID.

The warehouse worker will now be able to pick the Quality order work using the
QMS Put-away menu item, both for the quality failed goods to the put at a return
location, and the quality passed goods to be put in the bulk-001 location.

Setup summery – move from QMS
-----------------------------

You have setup the work and location data for warehouse 51 to ensure that work
is automatically created upon quality order completion. This ensures that each
license plate quality controlled is moved to either to a bulk or a return
location.

Processing Quality Management Work from QMS
===========================================

Navigate to *Inventory management Periodic tasks Quality management Quality
orders* and select the first quality order for the quantities that were
registered.

Click on ‘Validate’ in the action bar and validate. The test will be updated to
a Status of Fail.

Navigate to *Warehouse management All Work.* Select the work just created and
view that a new piece of work was created for Work order type = Quality Order,
with a put to the Return location, when the quality order status is Fail. If the
quality order status were Pass, then the put location would be Bulk.

Navigate back to *Inventory management Periodic tasks Quality management Quality
orders* and select the second quality order for the items that were registered.
Click on Results in the lower grid action bar. Update the Result quantity to 5
and verify that the Test result changes to a checkmark. Click Validate and close
the form.

Back in the Quality Orders form, Click on Validate in the header action bar and
validate. The status will be updated to Pass.

*Note: The creation of the quality order work to move the quantity from the
quality control location to a new location is triggered from the validation
event.*

Navigate to *Warehouse management  All Work.* Select the work just created and
see that a second Quality Order work header has been created, with a put
location of BULK-001.

Open the **warehouse mobile application** (WMA). Login with User ID = 51 and
demo Password = 1. Navigate to *Quality Put Away from QMS* and process each of
the two license plates related to both pieces of work such that all work gets
closed.

>   *Note: Consider adding the quality out to a mobile device menu item with the
>   activity code Display open work list. You can find such an example in mobile
>   device menu item named “Worklist” part of demo data. First you add the
>   Quality order work class to a User-Directed menu item, as this is a
>   prerequisite for work to be displayed in the worklist. Then you add Quality
>   order work class to the “Worklist” menu item. Doing such will enable users
>   with access to the worklist list to pick and process the autogenerated work
>   resulting from a quality order validation.*
