---
# required metadata

title: Synchronize sales order headers and lines directly from Finance and Operations to Sales
description: This topic discusses the templates and underlying tasks that are used to synchronize sales order headers and lines directly from Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, to Microsoft Dynamics 365 for Sales. 
author: ChristianRytt
manager: AnnBe
ms.date: 10/25/2017
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

# Synchronize sales order headers and lines directly from Finance and Operations to Sales

[!include[banner](../includes/banner.md)]

This topic discusses the templates and underlying tasks that are used to synchronize sales order headers and lines directly from Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, to Microsoft Dynamics 365 for Sales.

## Data flow in Prospect to cash

The Prospect to cash solution uses the Data integration feature to synchronize data across instances of Finance and Operations and Sales. The Prospect to cash templates that are available with the Data integration feature enable the flow of data about accounts, contacts, products, sales quotations, sales orders, and sales invoices between Finance and Operations and Sales. The following illustration shows how the data is synchronized between Finance and Operations and Sales.

[![Data flow in Prospect to cash](./media/prospect-to-cash-data-flow.png)](./media/prospect-to-cash-data-flow.png)

## Templates and tasks

To access the available templates, open [PowerApps Admin Center](https://preview.admin.powerapps.com/dataintegration). Select **Projects**, and then, in the upper-right corner, select **New project** to select public templates.

The following template and underlying tasks are used to synchronize sales order headers and lines from Finance and Operations to Sales:

- **Name of the template in Data integration:** Sales Orders (Fin and Ops to Sales) - Direct
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

Sales orders are created in Finance and Operations and synchronized to Sales.

Filters in the template help guarantee that only relevant sales orders are included in the synchronization:

- On the sales order, both the ordering customer and the invoicing customer that originate from Sales will be included in the synchronization. In Finance and Operations, the **OrderingCustomerIsExternallyMaintained** and **InvoiceCustomerIsExternallyMaintained** fields are used to track the synchronization in the data entities.
- The sales order in Finance and Operations must be confirmed. Only confirmed sales orders or sales orders that have a higher processing status, such as **Shipped** or **Invoiced**, are synchronized to Sales.
- After a sales order is created or modified, the **Calculate sales totals** batch job in Finance and Operations must be run. Only sales orders where sales totals are calculated will be synchronized to Sales.

> [!NOTE]
> Currently, tax that is related to charges on the sales order header isn't included in the synchronization from Finance and Operations to Sales. Sales doesn't support tax information at the header level. However, tax that is related to charges at the line level is included in the synchronization.

## Prospect to cash solution for Sales

New fields have been added to the **Order** entity and appear on the page:

- **Is Maintained Externally** – Set this option to **Yes** when the order is coming from Finance and Operations.
- **Processing status** – This field shows the processing status of the order in Finance and Operations. The following values are available:

    - Active
    - Confirmed
    - Packing Slip
    - Invoiced
    - Picked
    - Partially Picked
    - Partially Packed
    - Shipped
    - Partially Shipped
    - Partially Invoiced
    - Cancelled

The **Has Externally Maintained Products Only** setting is used in other sales order scenarios (for example, synchronization from Sales to Finance and Operation) to consistently track whether a sales order consists entirely of externally maintained products. If a sales order consists entirely of externally maintained products, the products are maintained in Finance and Operations. This setting helps guarantee that you don't try to synchronize sales order lines that have products that are unknown to Finance and Operations.

The **Create Invoice**, **Cancel Order**, **Recalculate**, **Get Products**, and **Lookup Address** buttons on the **Sales order** page are hidden for externally maintained orders, because invoices will be created in Finance and Operations and synchronized to Sales. The order page can't be edited, because sales order information will be synchronized from Finance and Operations.

The status of a sales order will remain **Active** to help guarantee that changes from Finance and Operations can flow to the sales order in Sales. To control this behavior, set the default **Statecode \[Status\]** value to **Active** in the Data integration project.

## Preconditions and mapping setup

Before you synchronize sales orders, it's important that you update the following settings in the systems.

### Setup in Sales

- Make sure that permissions are set up for the team that the user from your Sales connection set is assigned to. If you're using demo data, the user usually has admin access, but the team doesn't have admin access. If the team doesn't also have admin access, when you run the project from Data integration, you will receive an error message that states that Principal team is missing.

    Go to **Settings** > **Security** > **Teams**, select the relevant team, select **Manage Roles**, and select a role that has the desired permissions, such as **System Administrator**.

- Go to **Settings** > **Administration** > **System settings** > **Sales**, and makes sure that the following settings are used:

    - The **Use system prizing calculation system** option is set to **Yes**.
    - The **Discount calculation method** field is set to **Line item**.

### Setup in Finance and Operations

Go to **Sales and marketing** > **Periodic tasks** > **Calculate sales totals**, and set the job to run as a batch job. Set the **Calculate totals for sales orders** option to **Yes**. This step is important, because only sales orders where sales totals are calculated will be synchronized to Sales. The frequency of the batch job should be aligned with the frequency of sales order synchronization.

### Setup in the Data integration project

#### SalesHeader task

- Make sure that the required mapping exists for **InvoiceCountryRegionId** to **BillingAddress\_Country** and for **DeliveryCountryRegionId** to **DeliveryAddress\_Country**.

    The template value is a value map where several countries or regions are mapped.

- A price list is required in order to create orders in Sales. Update the value map for **pricelevelid.name \[Price list name\]** to the price list that is used in Sales per currency. You can use the default price list for a single currency. Alternatively, if you have price lists in multiple currencies, you can use a value map.

    The default template value for **pricelevelid.name \[Price list name\]** is **CRM Service USA (sample)**.

#### SalesLine task

- Make sure that the required mapping exists for **DeliveryCountryRegionId** to **DeliveryAddress\_Country**.

    The template value is a value map where several countries or regions are mapped.

- Make sure that the required value map for **SalesUnitSymbol** in Finance and Operations exists.

    A template value that has a value map is defined for **SalesUnitSymbol** to **Quantity\_UOM**.

## Template mapping in Data integration

> [!NOTE]
> The **Payment terms**, **Freight terms**, **Delivery terms**, **Shipping method**, and **Delivery mode** fields aren't included in the default mappings. To map these fields, you must set up a value mapping that is specific to the data in the organizations that the entity is synchronized between.

The following illustrations show an example of a template mapping in Data integration. 

> [!NOTE]
> The mapping shows which field information will be synchronized from Sales to Finance and Operations.

### OrderHeader

![Template mapping in Data integrator](./media/sales-order-direct-template-mapping-data-integrator-1.png)

### OrderLine

![Template mapping in Data integrator](./media/sales-order-direct-template-mapping-data-integrator-2.png)



## Related topics

[Prospect to cash](prospect-to-cash.md)

[Synchronize accounts directly from Sales to customers in Finance and Operations](accounts-template-mapping-direct.md)

[Synchronize products directly from Finance and Operations to products in Sales](products-template-mapping-direct.md)

[Synchronize contacts directly from Sales to contacts or customers in Finance and Operations](contacts-template-mapping-direct.md)

[Synchronize sales invoice headers and lines directly from Finance and Operations to Sales](sales-invoice-template-mapping-direct.md)



