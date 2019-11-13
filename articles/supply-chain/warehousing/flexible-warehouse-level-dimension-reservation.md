---
# required metadata

title: Flexible warehouse-level dimension reservation 
description: This topic describes an enhancement to the inventory reservation policy that allows businesses, who sell batch-tracked products and run their logistics as WMS-enabled operations, to reserve specific batches for their customers’ sales orders even though the reservation hierarchy associated with such products disallows this (by being of a type that is commonly referred to as “Batch-below[location]”.)
author: omulvad
manager: AnnBe
ms.date: 11/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSReservationHierarchy 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2020-01-15
ms.dyn365.ops.version: 10.0.9

---

# Flexible warehouse-level dimension reservation

[!include [banner](../includes/banner.md)]

This topic describes an enhancement to the inventory reservation policy that allows businesses, who sell batch-tracked products and run their logistics as WMS-enabled operations, to reserve specific batches for their customers’ sales orders even though the reservation hierarchy associated with such products disallows this (by being of a type that is commonly referred to as “Batch-below[location]”.)

## Inventory reservation hierarchy

Below is a summary of the existing inventory reservation hierarchy with focus on handing the batch- and serial-tracked items. Inventory reservation hierarchy concept is described in more details [insert link].

Inventory reservation hierarchy dictates that as far as storage dimensions are concerned, it is the demand order that carries the mandatory dimensions of site, warehouse, and inventory status, while it is the warehouse logic that is responsible for assigning and reserving a location to the requested quantities. In other words, in the interactions between the demand order and the warehouse operations, the demand order is expected to say from where - site and warehouse - the order must be shipped, and the warehouse then relies on its logic to locate the required quantity within the warehouse premises.

Tracking dimensions - batch and/or serial numbers - are, however, a subject to more flexibility, that is meant to reflect the business's operational model. Here, an inventory reservation hierarchy can accommodate scenarios where:

1. The business choses to rely on their warehouse operations to manage picking of quantities with batch/serial numbers after the said quantities have been located within the warehousing storage space. This model - referred to as &quot;Batch-below[location]&quot; - is common when product's batch/serial number identification is of no importance to the customers when placing the demand with the selling company.
2. When batch/serial numbers are part of the customer&#39;s order specification and are recorded on the demand order, the warehouse operations are constrained by the requested specific numbers when locating the quantities within the warehouse, and are not allowed to change them. This is a &quot;Batch-above[location]&quot; reservation hierarchy type.

The challenge with the above principle is that any given released product can have only one inventory reservation hierarchy assigned to it. This implies that in order for the warehouse management system to support handling of the tracked item, the decision on timing for when batch/serial number is reserved, i.e. at demand order taking or during the warehouse picking work, once taken by means of hierarchy assignment, cannot be changed ad-hoc.

## Flexible reservation for batch-tracked items

### Business scenario

Due to the nature of its manufactured products, a company employs an inventory strategy of tracking its finished goods by batch numbers. As the said company also uses the D365F&amp;O Warehouse Management System workload, that has a well-equipped logic for planning and executing warehouse pick and ship operations for batch-enabled items, most of the finished items are associated with a &quot;Batch-below[Location]&quot; inventory reservation hierarchy. The advantage behind such an operational setup is that decisions (that are effectively, reservation decisions) about which batches to pick and where to locate them within the warehouse are postponed until the warehouse picking operations start as opposed to when the customer's order is placed.

While the &quot;Batch\_below[location]&quot; inventory reservation hierarchy serves the company's business goals well, there are multiple of its established customers that when reordering products require the same batch as previously purchased. In essence, the company is looking for flexibility in handling the batch reservation rules, where depending on the customers' demand for the same item:

- a batch number can be recorded and reserved at the order taking time by the sales processor, with no possibility to be changed during warehouse operations and/or being taken by other demands, hence ensuring the ordered batch number is shipped to the customer
- when irrelevant to the customer, a batch number(s) can be decided beyond the sales order registration and reservation by the warehouse operations during picking work

### Allowing specific batch reservation on the sales order

To accommodate the desired flexibility in the batch reservation behaviour for items that are associated with a &quot;Batch\_below[location]&quot; inventory reservation hierarchy, inventory managers must enable the **Allow reservation on demand order** field for the Batch number level.

Be aware that when **Batch number** level in the hierarchy is selected, all other dimensions that are above and up to the location will be selected automatically. This behaviour is meant to convey the logic according to which, once you reserve a specific batch number on the order line, all dimensions in the range between the batch number and location are also automatically reserved (see more details in the sections below).

 > [!NOTE]
 > The **Allow reservation on demand order** option only applies to reservation hierarchy levels that are below the warehouse location dimension.
 
 > In the current implementation, Batch number is the only level in the hierarchy that is open for flexible reservation policy. That means that you cannot set checkmark in the **Allow reservation on demand order** field for Location, License plate or Serial number.
 
 > If your reservation hierarchy includes Serial number dimension (which must always be placed below the Batch number level) and you have enabled batch-specific reservation for the Batch number, the program will continue handling serial number reservation and picking operations based on rules applicable to &quot;Serial\_below[location]&quot; reservation policy.
 
You can allow batch-specific reservation for an existing &quot;Batch\_below[location]&quot; hierarchy at any point of time in your deployment. This will not affect any reservations or open warehouse work that have been created prior to this change. However, removal of the **Allow reservation on demand order** option is disallowed when there are existing inventory transactions of issue type Reserved ordered, Reserved physical, or Ordered for one or more items that are associated with that reservation hierarchy.

 > [!NOTE]
 > You can also change item's existing reservation hierarchy from the one that does not allow batch specification on the order to the one that does, provided the hierarchy level structure is identical in both hierarchies. Use the standard **Change reservation hierarchy for items** function to perform the desired reassignment. This may be relevant when you wish to disallow flexible batch reservation for a subset of batch-tracked items and allow it for the rest of the product portfolio.

Regardless of whether you have enabled the **Allow reservation on demand order** option, if you do not want to reserve a specific batch number for the item on an order line, default warehouse operations logic that is valid for a &quot;Batch\_below[location]&quot; reservation hierarchy will still apply.

### Reserve specific batch number for the customer order

Once the batch-tracked item's &quot;Batch\_below[location]&quot; reservation hierarchy is enabled to allow specific batch number reservation on the sales order, the sales order processors can take customer orders for the same item in one of the two ways, depending on the customer's request:

- enter order details without batch number - when the product's batch specification is of no importance to the customer. All existing processes associated with handling such an order in the system remain unchanged and will require no additional considerations from the users.
- enter order details and reserve a specific batch number – when the customer requests a specific batch, typically when reordering the previously purchased product. Such specific batch reservation is referred to as order-committed reservation.

The following set of rules are valid when processing quantities with batch number committed to a specific order:

- to allow reservation of a specific batch number for the item under &quot;Batch-below[location]&quot; reservation policy, the system must reserve all dimensions up to and including location. In the standard application, this range will typically include license plate dimension.
- location directives are not used when creating pick work for a sales line with order-committed batch reservation.
- during warehouse processing, including exception handling, of work for order-committed batches, neither the users nor the system are allowed to change that very batch number.

The following example will illustrate the end-to-end flow.

## Example scenario

For this scenario, you must have demo data installed, and you must use the **USMF** demo data company.

Enable an inventory reservation hierarchy to allow batch-specific reservation:

1. Go to **Warehouse management** \> **Setup** \> **Inventory \> Reservation hierarchy**
2. Click **New**
3. In the **Name** field, type a name, for example `BatchFlex`.
4. In the **Description** field, type a name, for example `Batch below flexible`
5. Use the right arrow button to move **Owner** and **Serial number** dimensions from the Selected section to the Available.
6. Click Ok.
7. For the Batch number level, set checkmark in the **Allow reservation on demand order** column. Note that both License plate and Location dimension levels are checkmarked automatically and you cannot uncheck them.
8. Click **Save**.

Create a new released product and:
1. set the following product's three master data parameters to the below values:
    - Storage dimension group=*Ware*
    - Tracking dimension group=*Batch-Phy*
    - Reservation hierarchy=*BatchFlex*
2. create two batch numbers, for example `B11` and `B22`
3. add item quantity to on-hand stock as per below:

    | Warehouse | Batch number | Location | License plate | Quantity |
    | --- | --- | --- | --- | --- |
    | 24 | B11 | BULK-001 |   | 100 |
    | 24 | B11 | FL-001 | LP11 | 10 |
    | 24 | B22 | FL-002 | LP22 | 10 |

Enter sales order details:
1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**
2. Click **New**.
3. For the sales order header, select customer account **US-003**.
4. Add a line for your new item and enter quantity `10`.
5. From the Sales order lines action bar, click **Inventory** \> **[Maintain] Batch reservation**. The **Batch reservation** page displays a list of batches available for order line quantity reservation, in our case quantity 110 of batch *B1* and quantity 10 of batch *B2*.

    Note that in contrast to the regular behaviour where **Batch reservation** page is inaccessible from the line with an item whose associated reservation hierarchy is not enabled for batch-specific reservation, the user is able to open the page.

    > [!NOTE]
    > If you want to reserve a specific batch for the sales order you must use the **Batch reservation** page.

    > If you enter the batch number directly on the sales order line, the system will regard this as if you entered a specific batch value for an item that is subject to the &quot;Batch-below[location]&quot; reservation policy. If on the warning message that appears upon line saving you confirm your decision to have the batch number specified directly on the order line, the line in question will not be handled by the regular warehouse management logic.

    > If you open the **Reservation** page and reserve the quantity from there, no specific batch will be reserved and the execution of the warehouse operations for this line will follow the rules applicable under the &quot;Batch-below[location]&quot; reservation policy.

    The general working of and interactions with this page are the same as for items whose associated reservation hierarchy is of type "Batch-above[location]", except:

    -  a new **Batch numbers committed to source line** tab displays the batch numbers that are reserved for the order line. The batch values in the tab's grid will be shown throughout the entire fulfilment cycle of the order line, including the warehouse processing stages. This is in contrast to the existing behaviour of the records displayed in the **Overview** tab, where a regular order line reservation, as done for the dimensions above location level, is shown in the grid up to a point when warehouse work is created, after which the line reservation is taken over by the work entity and is no longer displayed on this page. The introduction of the new tab ensures that the sales order processor can view the batch number(s) that were committed to the customer's order at any point in its lifecycle, up to invoicing.
    -  The user can decide whether, in addition to reserving a specific batch, they also want to manually select that very batch's specific location and license plate, instead of letting the system make the selection automatically. Relevance of such a decision is related to the design of the order-committed batch reservation mechanism. As was pointed out earlier, when reserving a batch number for item under &quot;Batch-below[location]&quot; reservation policy, the system must reserve all dimensions up to and including location. As a result, warehouse work will carry the same storage dimensions as were reserved by the users working with the orders, and may not always represent the item storage placement that is convenient, or even possible, for picking operations. In cases where order processors are aware of the warehouse constraints, they may be interested in making manual selections of the specific locations and license plates when reserving a batch. To do so, the user must make use of the standard &quot;Display dimensions&quot; facility on the page header and add the Location and License plate to the **Overview** tab's grid.

