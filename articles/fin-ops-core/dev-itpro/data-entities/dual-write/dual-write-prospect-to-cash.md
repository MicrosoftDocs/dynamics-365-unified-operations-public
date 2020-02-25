---
# required metadata

title: Prospect to cash in dual-write
description: 
author: RamaKrishnamoorthy
manager: AnnBe
ms.date: 01/27/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-01-27

---

# Prospect to cash in dual-write

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

Converting a prospect to a customer and maintaining an ongoing business relationship with the same customer is the goal for most businesses. In Dynamics 365 apps, the prospect-to-cache process takes place through quotations or order processing workflows, and the financials are reconciled and recognized. Integrated prospect-to-cash with dual-write creates a workflow takes a quotation and an order that originate in either Dynamics 365 Sales or Dynamics 365 Supply Chain Management and makes the quotation and order available in both apps.

You can access the processing states and invoice information in the app interface in real-time. This helps you handle functions like product stocking, inventory handling, and fulfillment using Dynamics 365 Supply Chain Management without recreating the quotation and order.

![dual-write data flow in prospect-to-cash diagram](../dual-write/media/dual-write-prospect-to-cash[1].png)

## Prerequisites and mapping setup

Before you can synchronize sales quotations, you must update the following settings.

### Setup in Dynamics 365 Sales

In Dynamics 365 Sales, go to **Settings > Administration > System settings > Sales**, and make sure that the following settings are used:
•	The **Use system prizing calculation** system option is set to **Yes**.
•	The **Discount calculation method** field is set to **Line item**.

### Site and warehouse

**Site** and **warehouse** are required fields for quotation and order lines in Supply Chain Management. So, in case each product is assigned to a site and warehouse on the “Default order settings” entity, then system has been configured to auto-populate them when a user tries to add the product to the quotation line or order line.

### Number Sequencing for quotation and Order

The number sequences for Supply Chain Management and Sales are not connected when syncing and creating a quotation and order in Sales and Supply Chain Management. If a sales order is created in Sales, it is synchronized to Supply Chain Management with the same sales order number. To ensure that the the sales order number isn't duplicated, you must use different number sequencing systems in the two environments.

For example, suppose that Supply Chain Management number sequence is **1,2,3,4,5...**, and the Sales number sequencing is **100,99,97,...**." The number sequencing will eventually overlap as sales orders are created in Supply Chain Management and Sales. If we create a 100 sales orders in Sales, then we eventually will generate a number that already exists in Supply Chain Management. Instead, Supply Chain Management  could use a number sequence like "F1, F2, F3..." and Sale could use a number sequence like "C1, C2, C3...". These sequences will not produce duplicate sales order numbers.

## Sales quotation

Sales quotations can be created in either Sales or Supply Chain Management. If you create the quotation in Sales, it is synced to Supply Chain Management in real time and vice versa. There are a few things to note:

+ You can add a discount to the quotation product and the discount will be synchronized to Supply Chain Management. The **Discount**, **Charges**, and **Tax** fields on the header are controlled by a setup in Supply Chain Management. This setup doesn't support integration mapping. Instead, the **Price**, **Discount**, **Charge**, and **Tax** fields are maintained and handled in Supply Chain Management.
+ These fields in the sales quotation header are read-only: **Discount %**, **Discount**, and **Freight Amount**.
+ The **Freight terms**, **Delivery terms**, **Shipping method**, and **Delivery mode** fields aren't part of the default mappings. To map these fields, you must set up a value mapping that is specific to the data in the organizations that the entity is synchronized between.

## Sales Order

You can create sales orders in either Sales or Supply Chain Management. If you create the sales order in Sales, it's synced to Supply Chain Management in real time and vice versa. There are a few things to note:

+ You can activate and synchronize orders from Sales only if all the Order Products consist of products coming from Finance and Operations apps. Therefore, there can be no write-in products.
+ Discount calculation and rounding:
    –	The discount calculation model in Sales differs from the discount calculation model in Supply Chain Management. In Supply Chain Management, the final discount amount on a sales line can be the result of a combination of discount amounts and discount percentages. If this final discount amount is divided by the quantity on the line, rounding can occur. However, this rounding isn't considered if a rounded per-unit discount amount is synchronized to Sales. To help guarantee that the full discount amount from a sales line in Supply Chain Management is correctly synchronized to Sales, the full amount must be synchronized without being divided by the line quantity. Therefore, you must define the **Discount calculation method** as **Line item** in Sales.
    –	When a sales order line is synchronized from Sales to Supply Chain Management, the full line discount amount is used. Because Supply Chain Management has no field that can store the full discount amount for a line, the amount is divided by the quantity and stored in the **Line discount** field. Any rounding that occurs in this division is stored in the **Sales charges** field on the sales line.

### Example: synchronization from Sales to Supply Chain Management

Suppose you have this sales order:

+ Sales: Quantity = 3, per-line discount = $10.00
+ Supply Chain Management: Quantity = 3, line discount amount = $3.33, sales charge = -$0.01

If you cynchronization from Supply Chain Management to Sales, then:

+ Supply Chain Management: Quantity = 3, line discount amount = $3.33, sales charge = -$0.01
+ Sales: Quantity = 3, per-line discount = (3 × $3.33) + $0.01 = $10.00

## Dual-write solution for Sales

New fields have been added to the **Order** entity and appear on the page. Most of these fields are in the **Integration** tab in Sales. There are a few special fields:

+ **Processing status**: This field shows the processing status of the order in Supply Chain Management. This field is locked and only shows the status of the order from Supply Chain Management. The following values are available:

    + Active – The status after the order is activated in Sales by using the Activate button.
    + Confirmed
    + Delivered
    + Invoiced
    + Partially Delivered
    + Partially Invoiced
    + Picked
    + Cancelled
    
    This table shows how the processing status is mapped to the CRM status code:
    
    Processing Status   | CRM Statuscode 
    --------------------|----------------
    Active              | New/Pending/Onhold
    Confirmed/Picked    | In Progress
    Partially Delivered | Partial
    Delivered           | Complete
    Invoiced/Partially  | Invoiced	Invoiced
    Canceled            | No Money
    
+ The **Create Invoice** and **Cancel Order** buttons on the Sales order page are hidden on Sales.
+ The **Sales order status** will remain **Active** to help guarantee that changes from Supply Chain Management can flow to the sales order in Sales. To control this behavior, set the default **Statecode [Status]** value to **Active**.
  
## Invoice
Sales invoices are created in Supply Chain Management and synchronized to Sales. There are a few things to note:

+ An **Invoice** number field has been added to the **Invoice** entity and appears on the page.
+ The **Create invoice** button on the Sales order page is hidden, because invoices will be created in Supply Chain Management and synchronized to Sales. The **Invoice** page can't be edited, because invoices will be synchronized from Supply Chain Management.
+ The **Sales order status** value is automatically changed to **Invoiced** when the related invoice from Supply Chain Management has been synchronized to Sales. Additionally, the owner of the sales order that the invoice was created from is assigned as the owner of the invoice. Therefore, the owner of the sales order can view the invoice.
+ The **Freight terms**, **Delivery terms**, and **Delivery mode** fields aren't included in the default mappings. To map these fields, you must set up a value mapping that is specific to the data in the organizations that the entity is synchronized between.

## Templates

Prospect-to-cash includes a collection of core entity maps that work together during data interaction, as shown in the following table.

Finance and Operations apps      | Model-driven app in Dynamics 365 | Description
---------------------------------|----------------------------------|------------
Sales invoice headers V2         | invoices                         |
Sales invoice lines V2           | invoicedetails                   |
CDS sales order headers          | salesorders                      |
CDS sales order lines            | salesorderdetails                |
Sales order origin codes         | msdyn_salesorderorigins          |
CDS sales quotation header       | quotes                           |
CDS sales quotation lines        | quotedetails                     |

Related core entity maps for prospect-to-cash are:
+ [Customers V3 to accounts](customer-mapping.md#customers-v3-to-accounts)
+ [CDS Contacts V2 to contacts](customer-mapping.md#cds-contacts-v2-to-contacts)
+ [Customers V3 to contacts](customer-mapping.md#customers-v3-to-contacts)
+ [Released products V2 to msdyn_sharedproductdetails](product-mapping.md#released-products-v2-to-msdyn_sharedproductdetails)
+ [All products to msdyn_globalproducts](product-mapping.md#all-products-to-msdyn_globalproducts)
+ [Pricelist]()

[!include [banner](../../includes/dual-write-symbols.md)]

[!include [sales invoice](includes/SalesInvoiceHeaderV2Entity-invoice.md)]

[!include [sales invoice line](includes/SalesInvoiceLineV2Entity-invoicedetail.md)]

[!include [sales order header](includes/SalesOrderHeaderCDSEntity-salesorder.md)]

[!include [sales order line](includes/SalesOrderLineCDSEntity-salesorderdetails.md)]

[!include [sales order origin](includes/SalesOrderOriginEntity-msdyn-salesorderorigin.md)]

[!include [sales quotation header](includes/SalesQuotationHeaderCDSEntity-quote.md)]

[!include [sales quotation line](includes/SalesQuotationLineCDSEntity-QuoteDetails.md)]



