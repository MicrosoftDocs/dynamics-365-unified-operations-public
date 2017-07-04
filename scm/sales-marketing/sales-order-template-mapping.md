---
# required metadata

title: Sales order headers and lines
description: The topic discusses the templates and underlying tasks that are used to synchronize sales order headers and lines from Microsoft Dynamics 365 for Sales to Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. 
author: ChristianRytt
manager: AnnBe
ms.date: 07/3/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.search.scope: Core, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ChristianRytt
ms.dyn365.ops.intro: July 2017 update 
ms.search.validFrom: 2017-07-8

---

# Sales order headers and lines

[!include[banner](../includes/banner.md)]

The topic discusses the templates and underlying tasks that are used to synchronize sales order headers and lines from Microsoft Dynamics 365 for Sales to Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. 

## Template and tasks

The following templates and underlying tasks are used to synchronize sales order headers and lines from Sales to Finance and Operations:

- **Name of the template:** Sales Orders (Sales to Fin and Ops)
- **Names of the tasks in the project:**

    - OrderHeader
    - OrderLine

The following synchronization tasks are required before synchronization of sales order headers and lines can occur:

- Products
- Accounts (if used)
- Contacts (if used)

## Entity set

| Sales             | CDS            | Finance and Operations |
|-------------------|----------------|------------------------|
| SalesOrders       | SalesOrder     | Sales order headers V2 |
| SalesOrderDetails | SalesOrderLine | CDS sales order lines  |

## Entity flow

Sales orders are created in Sales and synchronized to Finance and Operations.

Sales orders from Sales are synchronized only if the following conditions are met:

- All products on the sales order lines are externally maintained.
- The sales order has been submitted.

## Prospect to cash solution for Sales

The **Has Externally Maintained Products Only** field has been added to the order header to consistently track whether the sales order consists entirely of externally maintained products. If a sales order has only externally maintained products, the products are maintained in Finance and Operations. This behavior helps guarantee that you don't try to synchronize sales order lines with products that are unknown to Finance and Operations.

All products and lines on the order are updated with the **Has Externally Maintained Products Only** information from the sales order header. This information can be found in the **Order Has Externally Maintained Products Only** field on the Order line entity.

To submit orders where **Has Externally Maintained Products Only** is set to **Yes**, click the **Submit Order** button. Only submitted orders and products/lines on the orders are synchronized to Common Data Service (CDS) and Finance and Operations.

The **Order status** field is automatically set to **Invoiced** when the related invoice from Finance and Operations has been synchronized to Sales. Additionally, the owner of the sales order that the invoice was created from is assigned as the owner of the invoice. Therefore, the owner of the sales order can view the invoice.

The **Discount**, **Charges**, and **Tax** fields are controlled by a complex setup in Finance and Operations. This setup doesn't currently support integration mapping. In the current design, the **Price**, **Discount**, **Charge**, and **Tax** fields are mastered and handled by Finance and Operations.

In Sales, the solution makes the following fields read-only, because the values aren't synchronized to Finance and Operations:

- **Read-only fields on the sales order header:** Discount %, Discount, Freight Amount
- **Read-only fields on sales order lines:** Tax

## Preconditions and mapping setup

- Before you synchronize sales orders, in Sales, go to **Settings** &gt; **Administration** &gt; **System settings** &gt; **Sales**, and make sure that the **Discount calculation method** field is set to **Per unit**. This setting helps guarantee that the line item discount from Sales matches the setting in Finance and Operations. Otherwise, the discount won't be correct in Finance and Operations, because Finance and Operations will read the discount as a per-unit discount even if it was a per-line discount in Sales.
- In Finance and Operations, go to **Account receivable** &gt; **Setup** &gt; **Accounts receivable parameters**. On the **Number sequence** tab, select the number sequence for sales orders, and then click **View details**. Then, under **General Setup**, set the **Manual** field to **Yes**.
- In Finance and Operations, go to **Accounts receivable** &gt; **Setup** &gt; **Accounts receivable parameters**. Then, on the **Shipments** tab, set the **Delivery date control** field to **None**. This setting helps prevent synchronization from failing for sales orders.

### SalesHeader

- The **Requested delivery date** field is required in Finance and Operations, and synchronization will fail if the field is left blank. To prevent this issue, if the field is blank, a default date is taken from **Source &gt; CDS**. The date should be updated to a preferred value. Currently, you can't enter a value such as **[today]** to represent today's date. You must enter a specific date. The default template value for **Requested delivery date** is **1/1/2020**.
- The **Order date** field is required in CDS, and synchronization will fail if the field is left blank. To prevent this issue, if the field is blank, a default date is taken from **Source &gt; CDS**. The date should be updated to a preferred value. Currently, you can't enter a value such as **[today]** to represent today's date. You must enter a specific date. The default template value for **Order date** is **1/1/2020**.
- The **Address Country region code** field is required in Finance and Operations. To help prevent synchronization errors, you can specify a default value that is used if the field is left blank in Sales. The default template value for **DeliveryAddressCountryRegionISOCode** is **USA**.
- Update the mapping for **CDS Organization ID Organization_OrganizationId** in **Source &gt; CDS**:

    - The default template value for **SalesOrder_Organization_OrganizationId** is **ORG001**.
    - The default template value for **Product_Organization_OrganizationId** is **ORG001**.

### SalesLine

- You can add the following mappings from **CDS &gt; Destination** to help guarantee that sales lines are imported into Finance and Operations if there is no default information from either the customer or the product:

    - **SiteId** – A site is required in order to generate quotations and sales orders in Finance and Operations. The default template value for **SiteId** is **1**.
    - **WarehouseId** – A warehouse is required in order to process quotations and sales orders in Finance and Operations. The default template value for **WarehouseId** is **13**.

- Make sure that the required value map for the selling unit of measure (UOM) in Finance and Operations exists in the **CDS &gt; Destination** mapping for **Quantity_UOM** to **SALESUNITSYMBOL**.

## Template mapping in data integrator

> [!NOTE]
> The **Payment terms**, **Freight terms**, **Delivery terms**, **Shipping method**, and **Delivery mode** fields aren't part of the default mappings. To map these fields, you must set up a value mapping that is specific to the data in the organizations that the entity is synchronized between.

The following illustrations show an example of a template mapping in data integrator.

### OrderHeader

![Template mapping in data integrator](./media/sales-order-template-mapping-data-integrator-1.png)

![Template mapping in data integrator](./media/sales-order-template-mapping-data-integrator-2.png)

### OrderLine

![Template mapping in data integrator](./media/sales-order-template-mapping-data-integrator-3.png)

![Template mapping in data integrator](./media/sales-order-template-mapping-data-integrator-4.png)
