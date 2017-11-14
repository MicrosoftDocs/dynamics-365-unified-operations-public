---
# required metadata

title: Synchronize sales order headers and lines directly between Sales and Finance and Operations
description: The topic discusses the templates and underlying tasks that are used to synchronize sales order headers and lines directly between Microsoft Dynamics 365 for Sales and Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: ChristianRytt
manager: AnnBe
ms.date: 11/14/2017
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

# Synchronize sales order headers and lines directly between Sales and Finance and Operations

[!include[banner](../includes/banner.md)]

The topic discusses the templates and underlying tasks that are used to synchronize sales order headers and lines directly between Microsoft Dynamics 365 for Sales and Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.

> [!NOTE]
> Before you can use the Prospect to cash solution, you should be familiar with [Dynamics 365 Data integration](/common-data-service/entity-reference/dynamics-365-integration).
 
## Templates and tasks

The following templates and underlying tasks are used to synchronize sales order headers and lines directly between Finance and Operations and Sales:

- **Names of the templates in Data integration:**

    - Sales Orders (Sales to Fin and Ops) - Direct
    - Sales Orders (Fin and Ops to Sales) - Direct

- **Names of the tasks in the Data integration project:**

    - OrderHeader
    - OrderLine

The following synchronization tasks are required before synchronization of sales order headers and lines can occur:

- Products (Fin and Ops to Sales) - Direct
- Accounts (Sales to Fin and Ops) - Direct (if used)
- Contacts to Customers (Sales to Fin and Ops) - Direct (if used)

## Entity set

| Finance and Operations  | Sales             |
|-------------------------|-------------------|
| CDS sales order headers | SalesOrders       |
| CDS sales order lines   | SalesOrderDetails |

## Entity flow

Sales orders are created in Sales and synchronized to Finance and Operations when the **Sales Orders (Sales to Fin and Ops) - Direct** template is activated. You can activate and synchronize sales orders from Sales only if the orders consist entirely of products that are externally maintained. Therefore, there can be no write-in products. The activated sales orders become read-only in the user interface (UI), and from that point onward, updates are processed from Finance and Operations. After a sales order has a status of **Confirmed**, the activated **Sales Orders (Fin and Ops to Sales) - Direct** template is used to synchronize any updates or the fulfillment status from Finance and Operations to Sales.

You don't have to create sales orders in Sales. You can create them in Finance and Operations instead. In this case, sales orders that have a status of **Confirmed** are synchronized to Sales as described earlier.

In Finance and Operations, filters in the template help guarantee that only relevant sales orders are included in the synchronization:

- If the ordering customer and the invoicing customer on the sales order originate from Sales, they are included in the synchronization. In Finance and Operations, the **OrderingCustomerIsExternallyMaintained** and **InvoiceCustomerIsExternallyMaintained** fields are used to track the synchronization in the data entities.
- The sales order in Finance and Operations must be confirmed. Only confirmed sales orders or sales orders that have a higher processing status, such as **Shipped** or **Invoiced**, are synchronized to Sales.
- After a sales order is created or modified, the **Calculate sales totals** batch job in Finance and Operations must be run. Only sales orders where sales totals have been calculated are synchronized to Sales.

### Freight tax

Sales doesn't support tax at the header level, because all tax is stored at the line level.

To support tax at the header level from Finance and Operations, such as tax on freight, the tax is synchronized to Sales as a write-in product. This write-in product is named **Freight Tax**, and it has the tax amount from Finance and Operations. In this way, the standard price calculation in Sales can be used to calculate totals, even when there is tax at the header level from Finance and Operations.

### Discount calculation and rounding

The discount calculation model in Sales differs from the model in Finance and Operations. In Finance and Operations, the final discount amount on a sales line can be the result of a combination of discount amounts and discount percentages. If the final discount amount is divided by the quantity on the line, rounding might occur. However, this rounding isn't considered if a **Per unit** discount amount that is rounded is synchronized to Sales. For the full discount amount from a sales line in Finance and Operations to be correctly synchronized to Sales, the full amount must be synchronized without being divided by line quantity. Therefore, Sales requires that the line discount be defined as a **Per line item** discount.

When a sales order line is synchronized in the other direction, from Sales to Finance and Operations, the full line discount amount is used. Because Finance and Operations has no field that can store the full discount amount for a line, the amount is divided by the quantity and stored in the **Line discount** field. Any rounding that occurs during this division is stored in the **Sales charges** field on the sales line.

#### Example

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

    - **Draft** – The status when an order is first created in Sales. **Draft** is the only processing status in Sales that can be edited.
    - **Active** – The status after the order is activated by using the **Activate** button in Sales.
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

The **Has Externally Maintained Products Only** setting is used during activation to consistently track whether a sales order consists entirely of externally maintained products. If a sale order has only externally maintained products, the products are maintained in Finance and Operations. This behavior helps guarantee that you don't activate and try to synchronize sales order lines that have products that are unknown to Finance and Operations.
 
For externally maintained orders, the **Create Invoice**, **Cancel Order**, **Recalculate**, **Get Products**, and **Lookup Address** buttons on the **Sales order** page are hidden, because invoices will be created in Finance and Operations and synchronized to Sales. The order page can't be edited, because sales order information will be synchronized from Finance and Operations.
 
The value of the **Sales order status** field will remain **Active** to help guarantee that changes from Finance and Operations can flow to the sales order in Sales. To control this behavior, set the default **Statecode \[Status\]** value to **Active** in the Data integration project.

## Preconditions and mapping setup 

Before sales orders are synchronized, it's important that you update the following settings.

### Setup in Sales

- Make sure that permissions are set up for the team that the user from your connection set in Sales is assigned to. If you're using demo data, the user usually has admin access, but the team doesn't have admin access. If the team doesn't have admin access when you run the project from data integrator, you will receive an error message that states that the Principal team is missing.

    To set up permissions for the team, go to **Settings** &gt; **Security** &gt; **Teams**, and select the relevant team. Select **Manage Roles**, and then select a role that has the desired permissions, such as **System Administrator**.

- Go to **Settings** &gt; **Administration** &gt; **System settings** &gt; **Sales**, and make sure that the following settings are used:

    - The **Use system prizing calculation system** option is set to **Yes**.
    - The **Discount calculation method** field is set to **Line item**.

### Setup in Finance and Operations

Go to **Sales and marketing** &gt; **Periodic tasks** &gt; **Calculate sales totals**, and set up the task so that it runs as a batch job. Make sure that you set the **Calculate totals for sales orders** option to **Yes**. This setting is important, because only sales orders where sales totals have been calculated are synchronized to Sales. The frequency of the batch job should be aligned with the frequency of sales order synchronization.

### Setup in the Sales Orders (Sales to Fin and Ops) - Direct Data integration project

- Make sure that the required mapping exists for **Shipto\_country** to **DeliveryAddressCountryRegionISOCode**. In the value map, you can define a default value that is used if the value is left blank. Just leave the left side blank, and set the right side to the desired country or region.

    The template value is a value map where several countries or regions are mapped, and where a blank value equals a value of **US**.

### Setup in the Sales Orders (Fin and Ops to Sales) - Direct Data integration project

#### SalesHeader task

- A price list is required in order to create orders in Sales. Update the value map for **pricelevelid.name \[Price List Name\]** to the price list that is used in Sales per currency. You can use the default price list for a single currency. Alternatively, if you have price lists in multiple currencies, you can use a value map.

    The default template value for **pricelevelid.name \[Price List Name\]** is **CRM Service USA (sample)**.

#### SalesLine task

- Make sure that the required value map exists for **SalesUnitSymbol** in Finance and Operations, and that the required units are defined in Sales.

    A template value that has a value map is defined for **SalesUnitSymbol** to **oumid.name**.

## Template mapping in data integrator

> [!NOTE]
> The **Payment terms**, **Freight terms**, **Delivery terms**, **Shipping method**, and **Delivery mode** fields aren't part of the default mappings. To map these fields, you must set up a value mapping that is specific to the data in the organizations that the entity is synchronized between.

The following illustrations show an example of a template mapping in data integrator.

### Sales Orders (Fin and Ops to Sales) - Direct: OrderHeader

![Template mapping in data integrator](./media/sales-order-direct-template-mapping-data-integrator-1.png)

### Sales Orders (Fin and Ops to Sales) - Direct: OrderLine

![Template mapping in data integrator](./media/sales-order-direct-template-mapping-data-integrator-2.png)

### Sales Orders (Sales to Fin and Ops) - Direct: OrderHeader

![Template mapping in data integrator](./media/sales-order-direct-template-mapping-data-integrator-3.png)

### Sales Orders (Sales to Fin and Ops) - Direct: OrderLine

![Template mapping in data integrator](./media/sales-order-direct-template-mapping-data-integrator-4.png)

## Related topics

[Prospect to cash](prospect-to-cash.md)
