---
title: Field Service integration documentation
---

The Dynamics 365 Data integration provides support for scenarios where field
service activities are done outside of Dynamics 365 for Finance and Operations.

The first phase focuses on enabling invoicing of Dynamics 365 for Field Service
work orders and agreements in Finance and Operations. The supported flow starts
in Field Service, where information from work orders will sync to Finance and
Operations as sales orders. In Finance and Operations, the sales orders can be
invoiced to generate the invoice documents. In addition, the information from
Field Service agreement invoices will sync to Finance and Operations.

The Dynamics 365 Data Integration synchronizes data using customizable projects.
Standard templates can be used to create custom integration projects, where
additional standard and custom fields as well as entities can be mapped to
adjust integration and fit into specific needs.

The first phase for integration between Field Service and Finance and Operations
enables synchronization of:

-   Finance and Operations Products to Field Service Products with Field Service
    Product Type

-   Field Service Work order to Finance and Operations Sales order

-   Field Service Invoice to Finance and Operations Free text invoice

![](media/7477cbf17827210318e1a83d4276c69e.png)

Synchronization of Field Service Work orders to Finance and Operations Sales orders
===================================================================================

This topic discusses the templates and underlying tasks that are used for
synchronization of Work orders from Microsoft Dynamics 365 for Field Service to
Sales orders in Microsoft Dynamics 365 for Finance and Operations, Enterprise
edition.

Templates and tasks

The following templates and underlying tasks are used to run synchronization of
Work order from Field Service to Sales order in Microsoft Dynamics 365 for
Finance and Operations:

1.  **Names of the templates in Data integration:**

    -   Work Orders to Sales orders (Field Service to Fin and Ops)

2.  **Names of the tasks in the Data integration project:**

    -   WorkOrderHeader

    -   WorkOrderServiceLineEstimate

    -   WorkOrderServiceLineUsed

    -   WorkOrderProductLineEstimate

    -   WorkOrderProductLineUsed

The following synchronization tasks are required before synchronization of sales
order headers and lines can occur:

-   Field Service Products (Fin and Ops to Field Service)

-   Accounts (Sales to Fin and Ops) – Direct

Entity set

**Field Service Finance and Operations**

msdyn_workorders CDS sales order headers

msdyn_workorderservices CDS sales order lines

msdyn_workorderproducts CDS sales order lines

Entity flow

Work orders are created in Field Service and can synchronize to Finance and
Operations, via a CDS Data Integration project, when they only include
externally maintained products and work order status differs from
**Open-Unscheduled** and **Closed – Cancelled**. Updates on the work order will
sync to the sales order, including origin type and status information.

Expected versus Used

The Field Service Work order products and services holds both **Estimated** and
**Used** values for quantity and amount. Finance and Operations Sales orders
don’t have the same concept of Estimated and Used. To support product allocation
with expected quantity on the Sales order in Finance and Operations, while at
the same time ensuring that the used quantity is consumed and invoiced, there
are two sets of tasks to synchronize the Work Order Products and Work Order
Services; One for estimated and one for used values.

This enables scenarios where estimated values are used for
allocation/reservation in Finance and Operations while the used values are used
for consumption and invoicing.

### Estimated:

The estimated values are used for synchronization of **Product lines** when:

**Line Status** is **Estimated,** and **Allocated** is **Yes,** and **System
status** is not **Closed – Posted**.

The estimated values are used for synchronization of **Service lines** when:

**Line Status** is **Estimated,** and **System status** is not **Closed –
Posted**.

### Used:

In other cases, the used values are synchronized.

#### The following table shows an overview of the various combinations

| **Line type** | **System Status**  | **Line Status** | **Allocated** |     | **Fin and Ops value** |
|---------------|--------------------|-----------------|---------------|-----|-----------------------|
| Products      | Open - Scheduled   | Estimated       | Yes           | =\> | Estimated             |
| Products      | Open - Scheduled   | Estimated       | No            | =\> | Used                  |
| Products      | Open - Scheduled   | Used            | Yes           | =\> | Used                  |
| Products      | Open - Scheduled   | Used            | No            | =\> | Used                  |
| Products      | Open - In Progress | Estimated       | Yes           | =\> | Estimated             |
| Products      | Open - In Progress | Estimated       | No            | =\> | Used                  |
| Products      | Open - In Progress | Used            | Yes           | =\> | Used                  |
| Products      | Open - In Progress | Used            | No            | =\> | Used                  |
| Products      | Open - Completed   | Estimated       | Yes           | =\> | Estimated             |
| Products      | Open - Completed   | Estimated       | No            | =\> | Used                  |
| Products      | Open - Completed   | Used            | Yes           | =\> | Used                  |
| Products      | Open - Completed   | Used            | No            | =\> | Used                  |
| Products      | Closed - Posted    | Estimated       | Yes           | =\> | Used                  |
| Products      | Closed - Posted    | Estimated       | No            | =\> | Used                  |
| Products      | Closed - Posted    | Used            | Yes           | =\> | Used                  |
| Products      | Closed - Posted    | Used            | No            | =\> | Used                  |
|               |                    |                 |               |     |                       |
| Services      | Open - Scheduled   | Estimated       | \-            | =\> | Estimated             |
| Services      | Open - Scheduled   | Used            | \-            | =\> | Used                  |
| Services      | Open - In Progress | Estimated       | \-            | =\> | Estimated             |
| Services      | Open - In Progress | Used            | \-            | =\> | Used                  |
| Services      | Open - Completed   | Estimated       | \-            | =\> | Estimated             |
| Services      | Open - Completed   | Used            | \-            | =\> | Used                  |
| Services      | Closed - Posted    | Estimated       | \-            | =\> | Used                  |
| Services      | Closed - Posted    | Used            | \-            | =\> | Used                  |

Synchronization of **Estimated** versus **Used** is controlled with the two sets
of tasks for Product lines and Services lines where predefined filters trigger
the correct task, and the underlying mapping ensures that the correct values for
**Expected** versus **Used** are synchronized.

#### Example

1.  A work order is created and scheduled in Field Service

    System Status: **Open – Scheduled**

    -   Product line Estimated Qty = 5ea, Used Qty = 0ea, Line Status =
        Estimated, Allocated = No

    -   Service line Estimated Qty = 2h, Used Qty = 0h, Line Status = Estimated

>   Here the Product Used Quantity of 0 and Service Estimated Quantity of 2h
>   sync to Finance and Operations

1.  Products are allocated in Field service

    System Status: **Open – Scheduled**

    -   Product line Estimated Qty = 5ea, Used Qty = 0ea, Line Status =
        Estimated, Allocated = Yes

    -   Service line Estimated Qty = 2h, Used Qty = 0h, Line Status = Estimated

>   Here the Product Estimated Quantity of 5ea and Service Estimated Quantity of
>   2h sync to Finance and Operations

1.  The service technician starts working on the Work order and registers
    material usage (6)

    System Status: **Open – In Progress**

    -   Product line Estimated Qty = 5ea, Used Qty = 6ea, Line Status = Used,
        Allocated = Yes

    -   Service line Estimated Qty = 2h, Used Qty = 0h, Line Status = Estimated

>   Here the Product Used Quantity of 6 and Service Estimated Quantity of 2h
>   sync to Finance and Operations

1.  The service technician completes the Work order and registers used time
    (1.5h)

    System Status: **Open – Completed**

    -   Product line Estimated Qty = 5ea, Used Qty = 6ea, Line Status = Used,
        Allocated = Yes

    -   Service line Estimated Qty = 2h, Used Qty = 1.5h, Line Status = Used

>   Here the Product Used Quantity of 6 and Service Estimated Quantity of 1.5h
>   sync to Finance and Operations

Sales order Origin and Status

Sales origin
------------

To keep track of sales orders in Finance and Operations, which originate work
orders it is possible to create a **Sales origin** with **Origin type
assignment** = **Yes** and **Sales origin type** = **Work order integration**.

The mapping defaulting will set sales origin of all sales orders created from
work orders to this sales origin. This can be useful when working with the sales
order in Finance and Operations and it is essential to ensure that these sales
orders originating from work orders do not synchronize back to Sales as sales
orders.

See Preconditions and Mapping setup for details on creating the correct sales
origin setup in Finance and Operations.

Status
------

The field **External work order status** is shown on the Sales order header
**Setup** tab when the sales order originates from a work order. The **External
work order status** shows the System status from the Field Service Work order,
to keep track of the synchronized work order status in the Finance and
Operations Sales order. This also provides insight to the Finance and Operations
user about when to ship or invoice the sales order.

The External work order status field can have the following values:

-   Open - Scheduled

-   Open - In Progress

-   Open - Completed

-   Closed - Posted

Field Service CRM solution

To support the field service integration between Field service and Finance and
Operations additional functionality from the Field Service CRM solution is
needed. The solution includes the following changes:

Work Order entity
-----------------

-   The field **Has Externally Maintained Products Only** have been added to the
    Work order entity and appears on the page.

>   The **Has Externally Maintained Products Only** setting is used to
>   consistently track whether a work order consists entirely of externally
>   maintained products. A work order consists entirely of externally maintained
>   products when all the related products are maintained in Finance and
>   Operations. This setting helps guarantee that you don't try to synchronize
>   work orders that have products that are unknown to Finance and Operations.

Work Order Product entity
-------------------------

-   The field **Order Has Externally Maintained Products Only** has been added
    to the Work Order Product entity and appears on the page. It is used to
    consistently track whether the work order product is maintained in Finance
    and Operations. This setting helps guarantee that you don't try to
    synchronize work order products that are unknown to Finance and Operations.

-   The field **Header System Status** has been added to the Work Order Product
    entity and appears on the page. It is used to consistently track the work
    order system status and ensure correct filtering when synchronizing work
    order products to Finance and Operations. With filters on the integration
    tasks, **Header System Status** information is also used to determine
    whether the estimated or used values should be synchronized.

-   **Invoiced Unit Amount** shows the Amount invoiced per actual unit used.
    **Invoiced Unit Amount** = **Total Amount** / **Actual Quantity**. The field
    is used for integration to systems that don’t support different values for
    used and billed quantity. The field is not shown in the UI.

-   **Invoiced Discount Amount** is calculated as the **Discount Amount** plus
    rounding from the calculation of the **Invoiced Unit Amount**. The field is
    used for integration and not shown in the UI.

-   **Decimal Quantity** stores the value from **Quantity** as a Decimal Number.
    The field is used for integration and not shown in the UI.

-   The value in **Used** fields is set back to zero in case the work order
    product **Line Status** for some reason is changed from **Used** to
    **Estimated**. This is done to avoid situations where mistakenly entered
    used quantity is used for synchronizing when **Line Status** is
    **Estimated** and **Allocated** = **No.**

Work Order Service entity
-------------------------

-   The field **Order Has Externally Maintained Products Only** has been added
    to the Work Order Service entity and appears on the page. It is used to
    consistently track whether the work order service is maintained in Finance
    and Operations. This setting helps guarantee that you don't try to
    synchronize work order service that are unknown to Finance and Operations.

-   The field **Header System Status** has been added to the Work Order Service
    entity and appears on the page. It is used to consistently track the work
    order system status and ensure correct filtering when synchronizing work
    order service to Finance and Operations. With filters on the integration
    tasks, **Header System Status** information is also used to determine
    whether the estimated or used values should be synchronized.

-   The field **Duration In Hours** stores the minute value from **Duration**
    converted to hours. The field is used for integration and not shown in the
    UI.

-   The field **Estimated Duration In Hours** stores the minute value from
    **Estimated Duration** converted to hours. The field is used for integration
    and not shown in the UI.

-   The field **Invoiced Unit Amount** stores the Amount invoiced per actual
    unit used. **Invoiced Unit Amount** = **Total Amount** / **Actual
    Quantity**. The field is used for integration to systems that don’t support
    different values for used and billed quantity. The field is not shown in the
    UI.

-   The field **Invoiced Discount Amount** is calculated as the **Discount
    Amount** plus rounding from the calculation of the **Invoiced Unit Amount**.
    The field is used for integration and not shown in the UI.

-   The field **External Line Order** is a calculated negative line order number
    for use in external systems where work order product and service lines are
    combined. This way work order products are inserted with positive line
    numbers and services with negative line numbers. **External Line Order** =
    **Line Order** \* -1. The field is not shown in the UI.

-   The value in **Used** fields is set back to zero in case the work order
    service **Line Status** for some reason is changed from **Used** to
    **Estimated**. This is done to avoid situations where mistakenly entered
    used quantity is used for synchronizing when **Line Status** = **Estimated**
    and **Header System Status** = **Closed – Posted**.

Preconditions and mapping setup

Before you synchronize work orders, it's important that you update the following
settings in the systems.

Setup in Field Service
----------------------

-   Ensure that you don’t have overlapping number series for Work orders and
    Sales order cross both Sales and Finance and Operations, as this could lead
    to incorrect update of existing sales orders in Sales or Finance and
    Operations.

-   Set **Work Order Invoice Creation** to **Never**, as the invoicing will be
    done from Finance and Operations

>   Go to Field Service \> Settings \> Administration \> Field Service Settings,
>   and make sure that the following setting is used:

-   The **Work Order Invoice Creation** option is set to **Never**.

Setup in Finance and Operations
-------------------------------

Setup of sales origin for Work order integration is needed to distinguish the
Finance and Operations sales orders created from Field Service Work Orders. When
the sales origin on a sales order has sales origin type Work order integration
the field **External work order status** is shown.

Besides having the information on the sales order header, it can be used to
ensure that sales orders created from Field Service Work Orders are filtered out
during sales order synchronization from Finance and Operations to Sales.

Go to Sales and marketing \> Setup \> Sales orders \> Sales origin, click
**New** to create a new **Sales origin**

-   Enter the **Sales origin** e.g. WorkOrder

-   Enter the **Description** e.g. Field Service Work Order

-   Checkmark **Origin type assignment**

-   Set **Sales origin type** to **Work order integration**

-   Click **Save**

Template mapping in Data integration

*Will insert screenshots of the final mapping for the 5 tasks, once finalized.*
