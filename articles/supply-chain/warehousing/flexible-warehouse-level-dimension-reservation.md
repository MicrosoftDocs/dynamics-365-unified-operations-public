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

1. The business choses to rely on their warehouse operations to manage picking of quantities with batch/serial numbers after the said quantities have been located within the warehousing storage space. This model - referred to as "Batch-below[location]" - is common when product's batch/serial number identification is of no importance to the customers when placing the demand with the selling company.
2. When batch/serial numbers are part of the customer's order specification and are recorded on the demand order, the warehouse operations are constrained by the requested specific numbers when locating the quantities within the warehouse, and are not allowed to change them. This is a "Batch-above[location]" reservation hierarchy type.

The challenge with the above principle is that any given released product can have only one inventory reservation hierarchy assigned to it. This implies that in order for the warehouse management system to support handling of the tracked item, the decision on timing for when batch/serial number is reserved, i.e. at demand order taking or during the warehouse picking work, once taken by means of hierarchy assignment, cannot be changed ad-hoc.

## Flexible reservation for batch-tracked items

### Business scenario

Due to the nature of its manufactured products, a company employs an inventory strategy of tracking its finished goods by batch numbers. As the said company also uses the D365F&amp;O Warehouse Management System workload, that has a well-equipped logic for planning and executing warehouse pick and ship operations for batch-enabled items, most of the finished items are associated with a "Batch-below[Location]" inventory reservation hierarchy. The advantage behind such an operational setup is that decisions (that are effectively, reservation decisions) about which batches to pick and where to locate them within the warehouse are postponed until the warehouse picking operations start as opposed to when the customer's order is placed.

While the "Batch\_below[location]" inventory reservation hierarchy serves the company's business goals well, there are multiple of its established customers that when reordering products require the same batch as previously purchased. In essence, the company is looking for flexibility in handling the batch reservation rules, where depending on the customers' demand for the same item:

- a batch number can be recorded and reserved at the order taking time by the sales processor, with no possibility to be changed during warehouse operations and/or being taken by other demands, hence ensuring the ordered batch number is shipped to the customer
- when irrelevant to the customer, a batch number(s) can be decided beyond the sales order registration and reservation by the warehouse operations during picking work

### Allowing specific batch reservation on the sales order

To accommodate the desired flexibility in the batch reservation behaviour for items that are associated with a "Batch\_below[location]" inventory reservation hierarchy, inventory managers must enable the **Allow reservation on demand order** field for the Batch number level.

![Making inventory reservation hierarchy flexible](media/Flexible-inventory-reservation-hierarchy.png)

Be aware that when **Batch number** level in the hierarchy is selected, all other dimensions that are above and up to the location will be selected automatically (all dimensions placed above the **Location** level are pre-selected by default.) This behaviour is meant to convey the logic according to which, once you reserve a specific batch number on the order line, all dimensions in the range between the batch number and location are also automatically reserved (see more details in the sections below).

> [!NOTE]
> The **Allow reservation on demand order** option only applies to reservation hierarchy levels that are below the warehouse location dimension.
>
> In the current implementation, Batch number is the only level in the hierarchy that is open for flexible reservation policy. That means that you cannot set checkmark in the **Allow reservation on demand order** field for Location, License plate or Serial number.
>
> If your reservation hierarchy includes Serial number dimension (which must always be placed below the Batch number level) and you have enabled batch-specific reservation for the Batch number, the program will continue handling serial number reservation and picking operations based on rules applicable to "Serial\_below[location]" reservation policy.
 
You can allow batch-specific reservation for an existing "Batch\_below[location]" hierarchy at any point of time in your deployment. This will not affect any reservations or open warehouse work that have been created prior to this change. However, removal of the **Allow reservation on demand order** option is disallowed when there are existing inventory transactions of issue type Reserved ordered, Reserved physical, or Ordered for one or more items that are associated with that reservation hierarchy.

 > [!NOTE]
 > You can also change item's existing reservation hierarchy from the one that does not allow batch specification on the order to the one that does, provided the hierarchy level structure is identical in both hierarchies. Use the standard **Change reservation hierarchy for items** function to perform the desired reassignment. This may be relevant when you wish to disallow flexible batch reservation for a subset of batch-tracked items and allow it for the rest of the product portfolio.

Regardless of whether you have enabled the **Allow reservation on demand order** option, if you do not want to reserve a specific batch number for the item on an order line, default warehouse operations logic that is valid for a "Batch\_below[location]" reservation hierarchy will still apply.

### Reserve specific batch number for the customer order

Once the batch-tracked item's "Batch\_below[location]" reservation hierarchy is enabled to allow specific batch number reservation on the sales order, the sales order processors can take customer orders for the same item in one of the two ways, depending on the customer's request:

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
3. In the **Name** field, type a name, for example "BatchFlex".
4. In the **Description** field, type a name, for example "Batch below flexible".
5. Use the right arrow button to move **Owner** and **Serial number** dimensions from the Selected section to the Available.
6. Click Ok.
7. For the Batch number level, set checkmark in the **Allow reservation on demand order** column. Note that both License plate and Location dimension levels are checkmarked automatically and you cannot uncheck them.
8. Click **Save**.

Create a new released product and:
1. set the following product's three master data parameters to the below values:
    - Storage dimension group=*Ware*
    - Tracking dimension group=*Batch-Phy*
    - Reservation hierarchy=*BatchFlex*
2. create two batch numbers, for example "B11" and "B22"
3. add item quantity to on-hand stock as per below:

    | Warehouse | Batch number | Location | License plate | Quantity |
    | --- | --- | --- | --- | --- |
    | 24 | B11 | BULK-001 |   | 10 |
    | 24 | B11 | FL-001 | LP11 | 10 |
    | 24 | B22 | FL-002 | LP22 | 10 |

Enter sales order details:
1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**
2. Click **New**.
3. For the sales order header, select customer account **US-003**.
4. Add a line for your new item and enter quantity "10". Make sure the **Warehouse** field is set to **24**.
5. From the **Sales order lines** action bar, click **Inventory** \> **[Maintain] Batch reservation**. The **Batch reservation** page displays a list of batches available for order line quantity reservation, in our case quantity 20 of batch "B11" and quantity 10 of batch "B22".

    Note that in contrast to the regular behaviour where **Batch reservation** page is inaccessible from the line with an item whose associated reservation hierarchy is not enabled for batch-specific reservation, the user is able to open the page.

    > [!NOTE]
    > If you want to reserve a specific batch for the sales order you must use the **Batch reservation** page.
    >
    > If you enter the batch number directly on the sales order line, the system will regard this as if you entered a specific batch value for an item that is subject to the "Batch-below[location]" reservation policy. If on the warning message that appears upon line saving you confirm your decision to have the batch number specified directly on the order line, the line in question will not be handled by the regular warehouse management logic.
    >
    > If you open the **Reservation** page and reserve the quantity from there, no specific batch will be reserved and the execution of the warehouse operations for this line will follow the rules applicable under the "Batch-below[location]" reservation policy.

    The general working of and interactions with this page are the same as for items whose associated reservation hierarchy is of type "Batch-above[location]", except:

    -  a new **Batch numbers committed to source line** tab displays the batch numbers that are reserved for the order line. The batch values in the tab's grid will be shown throughout the entire fulfilment cycle of the order line, including the warehouse processing stages. This is in contrast to the existing behaviour of the records displayed in the **Overview** tab, where a regular order line reservation, as done for the dimensions above location level, is shown in the grid up to a point when warehouse work is created, after which the line reservation is taken over by the work entity and is no longer displayed on this page. The introduction of the new tab ensures that the sales order processor can view the batch number(s) that were committed to the customer's order at any point in its lifecycle, up to invoicing.
    -  The user can decide whether, in addition to reserving a specific batch, they also want to manually select that very batch's specific location and license plate, instead of letting the system make the selection automatically. Relevance of such a decision is related to the design of the order-committed batch reservation mechanism. As was pointed out earlier, when reserving a batch number for item under "Batch-below[location]" reservation policy, the system must reserve all dimensions up to and including location. As a result, warehouse work will carry the same storage dimensions as were reserved by the users working with the orders, and may not always represent the item storage placement that is convenient, or even possible, for picking operations. In cases where order processors are aware of the warehouse constraints, they may be interested in making manual selections of the specific locations and license plates when reserving a batch. To do so, the user must make use of the standard &quot;Display dimensions&quot; facility on the page header and add the Location and License plate to the **Overview** tab's grid.

6. In the **Batch reservation** page, select the line for batch "B11" and click **Reserve line**. There is no designated logic as to how location(s) and license plate(s) are assigned during the automatic reservation. Optionally, you can enter the quantity in the **Reservation** field manually. Note that in the **Batch numbers committed to source line** tab, batch "B11" is shown as **Committed**:

    ![Committing specific batch number to a sales order line on the Batch reservation page](media/Batch-reservation-form-with-order-committed-reservation.png)

    > [!NOTE]
    > Reservation of the sales order line quantity can be done across multiple batches. Likewise, reservation of the same batch can be done against multiple locations and license plates, if enabled for location.
    >
    > Reservation of a specific batch for the quantity on a sales order line can also be partial. For example, the total quantity of 100 units can be reserved so that a specific batch is committed to 20 units, while 80 units are reserved at the site and warehouse level for any available batch. In this case, the warehouse management system will handle picking operations by two separate work lines.

7. Go to **Product information management** \> **Products** \> **Released products**. Select your item and click **Manage inventory** Action Pane \> **View** \> **Transactions**:

    ![Order-committed reservation as an inventory transaction type](media/Inventory-transactions-for-order-committed-reservation.png)

    Review the item's inventory transactions related to the sales order line reservation:

    - transaction with **Reference** type **Sales order** and **Issue** type **Reserved physical** represents the order line reservation for the inventory dimensions above location, which according to the item's reservation hierarchy are "Site", "Warehouse" and "Inventory status".
    - transaction with **Reference** type **Order-committed reservation** and **Issue** type **Reserved physical** represents the order line reservation for the specific batch and all other inventory dimensions above it. In our example, those dimensions are "Batch number" and "Location". The latter happened to be "Bulk-001".

8. On the sales order header, click **Warehouse** Action Pane \> **Actions** \> **Release to warehouse**. The order line has now been waved, and load and work have been created.

Review and process warehouse work with order-committed batch number:

1. From the sales order lines action bar, click **Warehouse** \> **Work details**.

    The work that handles pick operation of batch quantities committed to sales order line has the following 3 characteristics:
    
    1. To create work, the system uses work templates but not location directives. This means that all the standard settings that are defined for work template, such as a maximum number of pick lines or a specific unit of measure, will be applied to determine when a new work should be created. However, the rules that are associated with location directives for identifying pick and put locations are not considered. This is because the order-committed reservation already specifies all the inventory dimensions, including those at the warehouse storage level, so that the work inherits them without consulting location directives.
    2. The batch number is not displayed on the pick line (as is the case for the work line created for an item with "Batch-above[location]" hierarchy). Instead, specifications of the "from" batch number as well as all other storage dimensions are shown on the work line's Work inventory transaction, that are referenced from the associated inventory transactions:
    
    ![Warehouse inventory transaction for work originating from order-committed reservation](media/Work-inventory-transactions-for-order-committed-reservation.png)
    
    3. Once work is created, the item's inventory transaction of Reference type **Order-committed reservation** is removed, with the inventory transaction of **Reference** type **Work** now holding the physical reservation on all the quantity's inventory dimensions.

    Once work is created, warehouse operations can proceed with handling its execution in a regular fashion, except that the instructions on the mobile device will prescribe the worker what specific batch number to pick. In the warehouse environments where locations are license plate-controlled, once at the location storing the same batch on multiple license plates, the worker can pick from/any license plate, provided it is not already reserved, for example, by another order-committed reservation or work that originates from such a reservation.

    To address the potential challenge where picking from the location as specified on the work line may turn out to be impractical, the warehouse operators can make use of:
    - the standard **Override location** action on a mobile device (provided the warehouse worker's **Allow pick location override** setting is enabled), or
    - the **Change location** action on the **Work list details** page
    to direct picking of the specific batch from a more convenient location.

2. From the mobile device, complete picking and putting the work.

    The quantity 10 of batch number "B11" has now been picked for the sales order line and is placed in the "Baydoor" location, ready to be loaded onto the trick and dispatched to the customer's address.
    
## Exception handling of warehouse work with order-committed batch number

Warehouse work for picking order-committed batch number is subject to the same standard warehouse exception handling and actions as any other regular work. Generally, the open work and/or work line can be cancelled, interrupted due to Full user location situation, short-picked, and get updated due to a movement. Likewise, the picked quantity of the already completed work can be reduced or the work can be reversed. The key rule that is applied to all of these exception handling actions is that the batch number that was reserved for the customer can never be replaced with a different one, while its storage dimension – location and license plate – may change due to manual update by the user or automatic update by the system. The latter is based on the same random storage dimension assignment as applied when automatically reserving a specific batch without specifying storage dimensions.

For example, let's review the scenario where the previously completed work is being unpicked by means of using the Reduce pick quantity function.

1. \[Continue from the previous example] Go to **Warehouse management** \> **Loads** \> **Active loads**.
2. Select the load that was created in connection with shipping your sales order.
3. From the Load order lines action bar, click **Reduce picked quantity**.
4. On the **Reduce picked quantity** page, in the **Move to location** field select **FL-001**, in the **Move to license plate** field select **LP33**.
5. In the grid, in the **Inventory quantity to unpick** field, enter "10".
6. Click OK.

Review the results of the unpicking action:

- the previously closed work has been set to status **Cancelled**.
- a new work of type **Inventory movement** for the unpicked quantity of 10 for batch number "B11" has been created to represent movement from location "Baydoor" to location "FL-001", license plate "LP33", and is set to status **Closed**.
- on the **Batch reservation** page, batch "B11" is shown as physically reserved in the **Batch numbers committed to source line** tab, and the **Reservation** field contains quantity 10 for batch number "B11". The **Location** and **License plate** fields (add it to the grid, if not displayed) contains "FL-001" and "LP11" respectively. This is a result of the system re-reserving the originally ordered batch number and assigning the location and license plate IDs where the said batch is available for reservation (which is equivalent to the user running the **Reserve line** function for the order line for a given batch number).

An overview of how order-committed batch reservation is handled by the system with regards to a given warehouse flow is provided here (insert link).

## Functionality not supported together with Flexible warehouse-level dimension reservation feature:

- Catch weight management
- Physical negative inventory
- Reservation against ordered supply
- Transfer orders and material consumption

## Other limitations

**Container consolidation rule of packing by directive unit**. Container build templates, where **Pack by directive unit** field is enabled, are not recommended for use together with order-committed reservations. This is due to the current design where location directives are not utilized in warehouse work creation, and so only the lowest unit in unit sequence group (inventory unit) is applied during containerization wave step.
