---
# required metadata

title: Synchronization of sales orders directly between Sales and Finance and Operations
description: The topic discusses the templates and underlying tasks that are used to run synchronization of sales orders directly between Microsoft Dynamics 365 for Sales and Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: ChristianRytt
manager: AnnBe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: yuyus
ms.search.scope: Core, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: crytt
ms.dyn365.ops.intro: July 2017 update 
ms.search.validFrom: 2017-07-8

---

# Synchronization of sales orders directly between Sales and Finance and Operations

[!include[banner](../includes/banner.md)]

The topic discusses the templates and underlying tasks that are used to run synchronization of sales orders directly between Microsoft Dynamics 365 for Sales and Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.

## Templates and tasks

To access the available templates, open [PowerApps Admin Center](https://preview.admin.powerapps.com/dataintegration). Select **Projects**, and then, in the upper-right corner, select **New project** to select public templates.

The following templates and underlying tasks are used to run synchronization of sales orders directly between Sales and Finance and Operations:

- **Names of the templates in Data integration:** 

    - Sales Orders (Sales to Fin and Ops) - Direct
    - Sales Orders (Fin and Ops to Sales) - Direct

- **Names of the tasks in the Data integration project:**

    - OrderHeader
    - OrderLine

The following synchronization tasks are required before synchronization of sales invoice headers and lines can occur:

- Products (Fin and Ops to Sales) - Direct
- Accounts (Sales to Fin and Ops) - Direct (if used)
- Contacts to Customers (Sales to Fin and Ops) - Direct (if used)

## Entity set

| Finance and Operations  | Sales             |
|-------------------------|-------------------|
| CDS sales order headers | SalesOrders       |
| CDS sales order lines   | SalesOrderDetails |

## Entity flow

Sales orders are created in Sales and synchronized to Finance and Operations when **Run project** is triggered for a project based on the **Sales Orders (Sales to Fin and Ops) - Direct** template. You can only activate and synchronize orders from Sales if all **Order Products** consist of products that are externally maintained. Therefore, there can be no write-in products. After the order is activated, the sales order becomes read-only in the user interface (UI). At that point, the updates are made from Finance and Operations. After the sales order has a status of **Confirmed**, the a project based on the **Sales Orders (Fin and Ops to Sales) - Direct** template can be used to synchronize updates or fulfillment status from Finance and Operations to Sales.

You don't have to create orders in Sales. You can create new sales orders in Finance and Operations instead. After a sales order has a status of **Confirmed**, it's synchronized to Sales as described in the previous paragraph.

In Finance and operations, filters in the template help guarantee that only the relevant sales orders are included in the synchronization:

- On the sales order, both the ordering customer and the invoicing customer have to originate from Sales to be included in the synchronization. In Finance and Operations, the **OrderingCustomerIsExternallyMaintained** and **InvoiceCustomerIsExternallyMaintained** fields are used to filter sales orders from the data entities.
- The sales order in Finance and Operations must be confirmed. Only confirmed sales orders or sales orders that have a higher processing status, such as **Shipped** or **Invoiced**, are synchronized to Sales.
- After a sales order is created or modified, the **Calculate sales totals** batch job in Finance and Operations must be run. Only sales orders where sales totals are calculated will be synchronized to Sales.

## Freight tax

Sales doesn't support tax at the header level, because tax is stored at the line level. To support tax at the header level from Finance and Operations, such as tax on freight, the system synchronizes tax to Sales as a write-in product that is named **Freight Tax**, and that has the tax amount from Finance and Operations. In this way, the standard price calculation in Sales can be used for totals, even when there is tax at the header level from Finance and Operations.

## Discount calculation and rounding

The discount calculation model in Sales differs from the discount calculation model in Finance and Operations. In Finance and Operations, the final discount amount on a sales line can be the result of a combination of discount amounts and discount percentages. If this final discount amount is divided by the quantity on the line, rounding can occur. However, this rounding isn't considered if a rounded per-unit discount amount is synchronized to Sales. To help guarantee that the full discount amount from a sales line in Finance and Operations is correctly synchronized to Sales, the full amount must be synchronized without being divided by the line quantity. Therefore, you must define the **Discount calculation method** as **Line item** in Sales.

When a sales order line is synchronized from Sales to Finance and Operations, the full line discount amount is used. Because Finance and Operations has no field that can store the full discount amount for a line, the amount is divided by the quantity and stored in the **Line discount** field. Any rounding that occurs in this division is stored in the **Sales charges** field on the sales line.

### Example

**Synchronization from Sales to Finance and Operations**

- **Sales:** Quantity = 3, per-line discount = $10.00
- **Finance and Operations:** Quantity = 3, line discount amount = $3.33, sales charge = -$0.01 

**Synchronization from Finance and Operations to Sales**

- **Finance and Operations:** Quantity = 3, line discount amount = $3.33, sales charge = -$0.01
- **Sales:** Quantity = 3, per-line discount = (3 × $3.33) + $0.01 = $10.00

## Prospect to cash solution for Sales

New fields have been added to the **Order** entity and appear on the page:

- **Is Maintained Externally** – Set this option to **Yes** when the order is coming from Finance and Operations.
- **Processing status** – This field shows the processing status of the order in Finance and Operations. The following values are available:

    - **Draft** – The initial status when an order is created in Sales. In Sales, only orders with this processing status can be edited.
    - **Active** – The status after the order is activated in Sales by using the **Activate** button.
    - **Confirmed**
    - **Packing Slip**
    - **Invoiced**
    - **Picked**
    - **Partially Picked**
    - **Partially Packed**
    - **Shipped**
    - **Partially Shipped**
    - **Partially Invoiced**
    - **Cancelled**

The **Has Externally Maintained Products Only** setting is used during order activation to consistently track whether a sales order consists entirely of externally maintained products. If a sales order consists entirely of externally maintained products, the products are maintained in Finance and Operations. This setting helps guarantee that you don't activate and try to synchronize sales order lines that have products that are unknown to Finance and Operations.

The **Create Invoice**, **Cancel Order**, **Recalculate**, **Get Products**, and **Lookup Address** buttons on the **Sales order** page are hidden for externally maintained orders, because invoices will be created in Finance and Operations and synchronized to Sales. These orders can't be edited, because sales order information will be synchronized from Finance and Operations after activation.

The sales order status will remain **Active** to help guarantee that changes from Finance and Operations can flow to the sales order in Sales. To control this behavior, set the default **Statecode \[Status\]** value to **Active** in the Data integration project.

## Preconditions and mapping setup

Before you synchronize sales orders, it's important that you update the following settings in the systems.

### Setup in Sales

- Make sure that permissions are set up for the team that the user from your Sales connection set is assigned to. If you're using demo data, the user usually has admin access, but the team doesn't have admin access. If the team doesn't have admin access, when you run the project from Data integration, you will receive an error message that states that the Principal team is missing.

    Go to **Settings** &gt; **Security** &gt; **Teams**, select the relevant team, select **Manage Roles**, and select a role that has the desired permissions, such as **System Administrator**.

- Go to **Settings** &gt; **Administration** &gt; **System settings** &gt; **Sales**, and make sure that the following settings are used:

    - The **Use system prizing calculation system** option is set to **Yes**.
    - The **Discount calculation method** field is set to **Line item**.

### Setup in Finance and Operations

- Go to **Sales and marketing** &gt; **Periodic tasks** &gt; **Calculate sales totals**, and set the job to run as a batch job. Set the **Calculate totals for sales orders** option to **Yes**. This step is important, because only sales orders where sales totals are calculated will be synchronized to Sales. The frequency of the batch job should be aligned with the frequency of sales order synchronization.

### Setup in the Sales Orders (Sales to Fin and Ops) - Direct Data integration project

- Make sure that the required mapping exists for **Shipto\_country** to **DeliveryAddressCountryRegionISOCode**. You can make blank a default value in the value map to avoid having to type country for national orders. Set the left side to 'Blank', and set the right side to the desired country or region.

    The template value is a value map where several countries or regions are mapped, and where 'Blank' = US.

### Setup in the Sales Orders (Fin and Ops to Sales) - Direct Data integration project

#### SalesHeader task

- A price list is required in order to create orders in Sales. Update the value map for **pricelevelid.name \[Price List Name\]** to the price list that is used in Sales per currency. You can use the default price list for a single currency. Alternatively, if you have price lists in multiple currencies, you can use a value map.

    The default template value for **pricelevelid.name \[Price List Name\]** is **CRM Service USA (sample)**.

#### SalesLine task

- Make sure that the required value map for **SalesUnitSymbol** in Finance and Operations exists.
- Make sure that the required units are defined in Sales.

    A template value that has a value map is defined for **SalesUnitSymbol** to **oumid.name**.

## Template mapping in Data integration

> [!NOTE]
> The **Payment terms**, **Freight terms**, **Delivery terms**, **Shipping method**, and **Delivery mode** fields aren't part of the default mappings. To map these fields, you must set up a value mapping that is specific to the data in the organizations that the entity is synchronized between.

The following illustrations show an example of a template mapping in Data integration.

> [!NOTE]
> The mapping shows which field information will be synchronized from Sales to Finance and Operations, or from Finance and Operations to Sales.

### Sales Orders (Fin and Ops to Sales) - Direct: OrderHeader

[![Template mapping in Data integration](./media/sales-order-direct-template-mapping-data-integrator-1.png)](./media/sales-order-direct-template-mapping-data-integrator-1.png)

### Sales Orders (Fin and Ops to Sales) - Direct: OrderLine

[![Template mapping in Data integration](./media/sales-order-direct-template-mapping-data-integrator-2.png)](./media/sales-order-direct-template-mapping-data-integrator-2.png)

### Sales Orders (Sales to Fin and Ops) - Direct: OrderHeader

[![Template mapping in Data integration](./media/sales-order-direct-template-mapping-data-integrator-3.png)](./media/sales-order-direct-template-mapping-data-integrator-3.png)

### Sales Orders (Sales to Fin and Ops) - Direct: OrderLine

[![Template mapping in Data integration](./media/sales-order-direct-template-mapping-data-integrator-4.png)](./media/sales-order-direct-template-mapping-data-integrator-4.png)

## Related topics

[Prospect to cash](prospect-to-cash.md)
