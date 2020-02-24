---
# required metadata

title: Prospect to cash
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

# Prospect to cash

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

Converting a prospect to a customer over a successful business deal and continuous business with the same customer is the target for most of the businesses. In Dynamics 365 world, it takes place through quotations or order processing workflows, and the financials are reconciled and recognized. Integrated prospect to cash workflow helps the quotation and order to originate in either Sales or Supply Chain application but becomes available on both.

Dynamics 365 users can access the processing states and invoice information on their application interface in real-time. Also, this helps businesses to handle functions like product stocking, inventory handling and fulfillment inside Supply chain application without recreating the quote/order.

![dual-write data flow in prospect-to-cash diagram](../dual-write/media/dual-write-prospect-to-cash[1].png)

## Preconditions and mapping setup
Before sales quotations are synchronized, it's important that you update the following settings.
### Setup in Sales
Go to Settings > Administration > System settings > Sales, and make sure that the following settings are used:
•	The Use system prizing calculation system option is set to Yes.
•	The Discount calculation method field is set to Line item.
### Site & Warehouse
Site and warehouse are required fields for quote and order lines in Supply Chain Management. So, in case each product is assigned to a site and warehouse on the “Default order settings” entity, then system has been configured to auto-populate them when a user tries to add the product to the quote line or order line.
### Number Sequencing for Quote and Order
While syncing and creating sales quote/order in Sales and Supply Chain Management, please be aware that the number sequences for Supply Chain Management and Sales are not connected. If a sales order is created in Sales, it gets synchronized to Supply Chain Management application with the same sales order number. To ensure that there the sales order number does not get duplicated make sure to use different number sequencing systems in both environments.

To explain further,
Suppose Supply Chain Management’s number sequence is as follows – 1,2,3,4,5... 
Sales number sequencing is as following – 100,99,97, … 
As you can see the number sequencing will eventually overlap as sales orders are created in Supply Chain Management and Sales. If we create a 100 SOs in Sales eventually we will hit a number that already exists in Supply Chain Management.
Alternatively 
Supply Chain Management Number Sequencing – F1, F2, F3... 
Sales Number Sequencing – C1, C2, C3... 
These number sequences won’t overlap.


## Sales Quotation
Sales quotations can be created in either Sales or Supply Chain Management. If it is created in Sales, it gets synced to Supply Chain Management in real time and vice versa. Following are few things to note:

•	A discount can be added to the quote product and will be synchronized to Supply Chain Management. The Discount, Charges, and Tax fields on the header are controlled by a setup in Supply Chain Management. Currently, this setup doesn't support integration mapping. In the current design, the Price, Discount, Charge, and Tax fields are maintained and handled in Supply Chain Management.

•	Read-only fields on the sales quotation header: Discount %, Discount, and Freight Amount

•	The Freight terms, Delivery terms, Shipping method, and Delivery mode fields aren't part of the default mappings. To map these fields, you must set up a value mapping that is specific to the data in the organizations that the entity is synchronized between.

## Sales Order
Sales orders can be created in either Sales or Supply Chain Management. If it is created in Sales, it gets synced to Supply Chain Management in real time and vice versa. Following are few things to note:

•	You can only activate and synchronize orders from Sales if all the Order Products consist of products coming from F&O. Therefore, there can be no write-in products.

•	Discount calculation and rounding:

–	The discount calculation model in Sales differs from the discount calculation model in Supply Chain Management. In Supply Chain Management, the final discount amount on a sales line can be the result of a combination of discount amounts and discount percentages. If this final discount amount is divided by the quantity on the line, rounding can occur. However, this rounding isn't considered if a rounded per-unit discount amount is synchronized to Sales. To help guarantee that the full discount amount from a sales line in Supply Chain Management is correctly synchronized to Sales, the full amount must be synchronized without being divided by the line quantity. Therefore, you must define the Discount calculation method as Line item in Sales.

–	When a sales order line is synchronized from Sales to Supply Chain Management, the full line discount amount is used. Because Supply Chain Management has no field that can store the full discount amount for a line, the amount is divided by the quantity and stored in the Line discount field. Any rounding that occurs in this division is stored in the Sales charges field on the sales line.

Example
Synchronization from Sales to Supply Chain Management

Sales: Quantity = 3, per-line discount = $10.00

Supply Chain Management: Quantity = 3, line discount amount = $3.33, sales charge = -$0.01

Synchronization from Supply Chain Management to Sales

Supply Chain Management: Quantity = 3, line discount amount = $3.33, sales charge = -$0.01

Sales: Quantity = 3, per-line discount = (3 × $3.33) + $0.01 = $10.00

•	Dual Write solution for Sales

  New fields have been added to the Order entity and appear on the page. Most of these fields are in the Integration tab in Sales. There  are a few special fields we would like to call attention to:

  1) Processing status – This field shows the processing status of the order in Supply Chain Management. This field is locked and only   shows the status of the order from Supply Chain Management. The following values are available:

    –	Active – The status after the order is activated in Sales by using the Activate button.

    –	Confirmed

    –	Delivered

    –	Invoiced

    –	Partially Delivered

    –	Partially Invoiced

    –	Picked

    –	Cancelled


This table shows how the processing status is mapped to the CRM status code:

Processing Status |	CRM Statuscode 
------------------|----------------
Active |	New/Pending/Onhold
Confirmed/Picked |	In Progress
Partially Delivered |	Partial
Delivered |	Complete
Invoiced/Partially |	Invoiced	Invoiced
Canceled |	No Money

  2) The Create Invoice and Cancel Order buttons on the Sales order page are hidden on Sales.

  3) The sales order status will remain Active to help guarantee that changes from Supply Chain Management can flow to the sales order in Sales. To control this behavior, set the default Statecode [Status] value to Active
  
## Invoice
Sales invoices are created in Supply Chain Management and synchronized to Sales. Following are few things to note:

•	An Invoice number field has been added to the Invoice entity and appears on the page.

•	The Create invoice button on the Sales order page is hidden, because invoices will be created in Supply Chain Management and synchronized to Sales. The Invoice page can't be edited, because invoices will be synchronized from Supply Chain Management.

•	The Sales order status value is automatically changed to Invoiced when the related invoice from Supply Chain Management has been synchronized to Sales. Additionally, the owner of the sales order that the invoice was created from is assigned as the owner of the invoice. Therefore, the owner of the sales order can view the invoice.

•	The Freight terms, Delivery terms and Delivery mode fields aren't included in the default mappings. To map these fields, you must set up a value mapping that is specific to the data in the organizations that the entity is synchronized between.

## Templates

For information about **Account** and **Contact**, see [Integrated customer master](customer-mapping.md).

For information about **Product** and **Pricelist**, see [Unified product mastering experience](product-mapping.md).

Other templates:

Finance and Operations | Other Dynamics 365 apps | Description
-----------------------|--------------------------------|---
CDS sales quotation header | Quotes |
CDS sales quotation lines | Quote Details |
CDS sales order headers | SalesOrders |
CDS sales order lines | SalesOrderDetails |
Invoice Header | Invoices |
Invoice Lines | InvoiceDetails |


### FO.SalesQuotationHeaderCDSEntity to CDS.quote
Source field | Map type | Destination field
---|---|---
SALESQUOTATIONNUMBER | = | msdyn_quotenumber
REQUESTINGCUSTOMERACCOUNTNUMBER | = | customerid.Account(accountnumber).Contact(msdyn_contactpersonid)
CURRENCYCODE | = | transactioncurrencyid.isocurrencycode
CUSTOMERSREFERENCE | = | msdyn_customersreference
DELIVERYADDRESSCITY | = | shipto_city
DELIVERYADDRESSCOUNTRYREGIONISOCODE | >< | shipto_country
DELIVERYADDRESSSTREETNUMBER | = | shipto_line2
DELIVERYADDRESSZIPCODE | = | shipto_postalcode
DELIVERYADDRESSSTREET | = | shipto_line1
DELIVERYADDRESSSTATEID | = | shipto_stateorprovince
SALESQUOTATIONNAME | = | name
INVOICEADDRESSCITY | >> | billto_city
INVOICEADDRESSSTREET | >> | billto_line1
INVOICEADDRESSSTREETNUMBER | >> | billto_line2
INVOICEADDRESSCOUNTRYREGIONISOCODE | >> | billto_country
INVOICEADDRESSSTATEID | >> | billto_stateorprovince
INVOICEADDRESSZIPCODE | >> | billto_postalcode
QUOTATIONTOTALAMOUNT | >> | totalamount
TOTALDISCOUNTAMOUNT | >> | discountamount
QUOTATIONTOTALTAXAMOUNT | >> | totaltax
QUOTATIONTOTALCHARGESAMOUNT | >> | freightamount
AREPRICESINCLUDINGSALESTAX | >< | msdyn_arepricesincludingsalestax
CONTACTPERSONID | = | msdyn_contactperson.msdyn_contactpersonid
CUSTOMERREQUISITIONNUMBER | = | msdyn_customerrequisitionnumber
DEFAULTSHIPPINGSITEID | = | msdyn_defaultshippingsite.msdyn_siteid
DEFAULTSHIPPINGWAREHOUSEID | = | msdyn_defaultshippingwarehouse.msdyn_warehouseidentifier
DELIVERYADDRESSCOUNTYID | = | msdyn_deliveryaddresscountyid
DELIVERYADDRESSDESCRIPTION | = | msdyn_deliveryaddressdescription
DELIVERYADDRESSDISTRICTNAME | = | msdyn_deliveryaddressdistrictname
DELIVERYADDRESSDUNSNUMBER | = | msdyn_deliveryaddressdunsnumber
DELIVERYADDRESSLATITUDE | = | msdyn_deliveryaddresslatitude
DELIVERYADDRESSLOCATIONID | = | msdyn_deliveryaddresslocationid
DELIVERYADDRESSLONGITUDE | = | msdyn_deliveryaddresslongitude
DELIVERYADDRESSNAME | = | msdyn_deliveryaddressname
DELIVERYADDRESSPOSTBOX | = | msdyn_deliveryaddresspostbox
DELIVERYBUILDINGCOMPLIMENT | = | msdyn_deliverybuildingcompliment
FORMATTEDDELIVERYADDRESS | >> | msdyn_formatteddeliveryaddress
FORMATTEDINVOICEADDRESS | >> | msdyn_formattedinvoiceaddress
GENERATEDSALESORDERNUMBER | = | msdyn_generatedsalesordernumber.msdyn_salesordernumber
INVOICEADDRESSCOUNTRYREGIONID | > | msdyn_invoiceaddresscountryregionid
INVOICEADDRESSCOUNTYID | >> | msdyn_invoiceaddresscountyid
INVOICEADDRESSDISTRICTNAME | >> | msdyn_invoiceaddressdistrictname
INVOICEADDRESSLATITUDE | >> | msdyn_invoiceaddresslatitude
INVOICEADDRESSLONGITUDE | >> | msdyn_invoiceaddresslongitude
INVOICEADDRESSPOSTBOX | >> | msdyn_invoiceaddresspostbox
INVOICEBUILDINGCOMPLIMENT | >> | msdyn_invoicebuildingcompliment
INVOICECUSTOMERACCOUNTNUMBER | = | msdyn_invoicecustomer.accountnumber
ISDELIVERYADDRESSORDERSPECIFIC | >< | msdyn_isdeliveryaddressorderspecific
ISDELIVERYADDRESSPRIVATE | >< | msdyn_isdeliveryaddressprivate
ISINVOICEADDRESSPRIVATE | >> | msdyn_isinvoiceaddressprivate
LANGUAGEID | >< | msdyn_language
PAYMENTTERMSNAME | = | msdyn_paymentterms.msdyn_name
PRICECUSTOMERGROUPCODE | = | msdyn_pricecustomergroup.msdyn_groupcode
RECEIPTDATEREQUESTED | = | msdyn_requestedreceiptdate
REQUESTEDSHIPPINGDATE | = | requestdeliveryby
SALESORDERPROMISINGMETHOD | >< | msdyn_salesorderpromisingmethod
SALESQUOTATIONCONFIRMATIONDATE | = | msdyn_salesquotationconfirmationdate
SALESQUOTATIONEXPIRYDATE | = | msdyn_salesquotationexpirydate
SALESQUOTATIONFOLLOWUPDATE | = | msdyn_salesquotationfollowupdate
SALESQUOTATIONSTATUS | >< | msdyn_salesquotationstatus
TOTALDISCOUNTPERCENTAGE | = | msdyn_totaldiscountpercentage
URL | = | msdyn_url
EMAIL | = | emailaddress

### FO.SalesQuotationLineCDSEntity to CDS.QuoteDetails
Source field | Map type | Destination field
---|---|---
ALLOWEDOVERDELIVERYPERCENTAGE | = | msdyn_allowedoverdeliverypercentage
ALLOWEDUNDERDELIVERYPERCENTAGE | = | msdyn_allowedunderdeliverypercentage
SALESQUOTATIONNUMBER | = | quoteid.msdyn_quotenumber
LINECREATIONSEQUENCENUMBER | = | sequencenumber
CURRENCYCODE | >> | transactioncurrencyid.isocurrencycode
DELIVERYADDRESSCITY | = | shipto_city
DELIVERYADDRESSCOUNTRYREGIONISOCODE | >< | shipto_country
DELIVERYADDRESSCOUNTYID | = | msdyn_deliveryaddresscountyid
DELIVERYADDRESSDESCRIPTION | = | msdyn_deliveryaddressdescription
DELIVERYADDRESSDISTRICTNAME | = | msdyn_deliveryaddressdistrictname
DELIVERYADDRESSDUNSNUMBER | = | msdyn_deliveryaddressdunsnumber
DELIVERYADDRESSLATITUDE | = | msdyn_deliveryaddresslatitude
DELIVERYADDRESSLOCATIONID | = | msdyn_deliveryaddresslocationid
DELIVERYADDRESSLONGITUDE | = | msdyn_deliveryaddresslongitude
DELIVERYADDRESSNAME | = | msdyn_deliveryaddressname
DELIVERYADDRESSPOSTBOX | = | msdyn_deliveryaddresspostbox
DELIVERYADDRESSSTATEID | = | shipto_stateorprovince
DELIVERYADDRESSSTREET | = | shipto_line1
DELIVERYADDRESSSTREETNUMBER | = | shipto_line2
DELIVERYADDRESSZIPCODE | = | shipto_postalcode
DELIVERYBUILDINGCOMPLIMENT | = | msdyn_deliverybuildingcompliment
EXTERNALITEMNUMBER | = | msdyn_externalitemnumber
FIXEDPRICECHARGES | = | msdyn_fixedpricecharges
FORMATTEDDELIVERYADDRESS | = | msdyn_formatteddeliveryaddress
ISDELIVERYADDRESSPRIVATE | >< | msdyn_isdeliveryaddressprivate
ISDELIVERYADDRESSORDERSPECIFIC | >< | msdyn_isdeliveryaddressspecific
LINEAMOUNT | >> | baseamount
LINEAMOUNT | >> | extendedamount
LINEDESCRIPTION | = | msdyn_linedescription2
LINEDISCOUNTAMOUNT | = | msdyn_linediscountamount
LINEDISCOUNTPERCENTAGE | = | msdyn_linediscountpercentage
MULTILINEDISCOUNTAMOUNT | = | msdyn_multilinediscountamount
MULTILINEDISCOUNTPERCENTAGE | = | msdyn_multilinediscountpercentage
PRODUCTNAME | = | description
PRODUCTNUMBER | = | productid.msdyn_productnumber
REQUESTEDRECEIPTDATE | = | msdyn_requestedreceiptdate
REQUESTEDSALESQUANTITY | = | quantity
REQUESTEDSHIPPINGDATE | = | requestdeliveryby
SALESPRICE | = | priceperunit
SALESPRICEQUANTITY | = | msdyn_salespricequantity
SALESQUOTATIONPROMISINGMETHOD | >< | msdyn_salesquotationpromisingmethod
SALESQUOTATIONSTATUS | >< | msdyn_salesquotationstatus
SALESUNITSYMBOL | = | uomid.msdyn_symbol
SHIPPINGSITEID | = | msdyn_shippingsite.msdyn_siteid
SHIPPINGWAREHOUSEID | = | msdyn_shippingwarehouse.msdyn_warehouseidentifier
TOTALCHARGESAMOUNT | >> | msdyn_totalchargesamount
TOTALDISCOUNTAMOUNT | = | manualdiscountamount
TOTALTAXAMOUNT | >> | tax
SALESPRODUCTCATEGORYHIERARCHYNAME | > | msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name
SALESPRODUCTCATEGORYNAME | = | msdyn_salesproductcategory.msdyn_name
none | >> | ispriceoverridden

### FO.SalesOrderHeaderCDSEntity to CDS.salesorder
Source field | Map type | Destination field
---|---|---
SALESORDERNUMBER | >< | msdyn_salesordernumber
ORDERINGCUSTOMERACCOUNTNUMBER | >< | customerid.Account(accountnumber).Contact(msdyn_contactpersonid)
CURRENCYCODE | >< | transactioncurrencyid.isocurrencycode
DELIVERYADDRESSCITY | >< | shipto_city
DELIVERYADDRESSCOUNTRYREGIONISOCODE | >< | shipto_country
DELIVERYADDRESSSTREETNUMBER | >< | shipto_line2
DELIVERYADDRESSZIPCODE | >< | shipto_postalcode
DELIVERYADDRESSSTREET | >< | shipto_line1
DELIVERYADDRESSSTATEID | >< | shipto_stateorprovince
SALESORDERNAME | >> | name
INVOICEADDRESSCITY | >> | billto_city
INVOICEADDRESSSTREET | >> | billto_line1
INVOICEADDRESSSTREETNUMBER | >> | billto_line2
INVOICEADDRESSCOUNTRYREGIONISOCODE | >> | billto_country
INVOICEADDRESSSTATEID | >> | billto_stateorprovince
INVOICEADDRESSZIPCODE | >> | billto_postalcode
ORDERTOTALAMOUNT | >> | totalamount
TOTALDISCOUNTAMOUNT | >> | discountamount
ORDERTOTALTAXAMOUNT | >> | totaltax
ORDERTOTALCHARGESAMOUNT | >> | freightamount
AREPRICESINCLUDINGSALESTAX | >< | msdyn_arepricesincludingsalestax
CONFIRMEDRECEIPTDATE | = | msdyn_confirmedreceiptdate
CONFIRMEDSHIPPINGDATE | = | msdyn_confirmedshippingdate
CONTACTPERSONID | = | msdyn_contactperson.msdyn_contactpersonid
CUSTOMERREQUISITIONNUMBER | = | msdyn_customerrequisitionnumber
DEFAULTSHIPPINGSITEID | = | msdyn_defaultshippingsite.msdyn_siteid
DEFAULTSHIPPINGWAREHOUSEID | = | msdyn_defaultshippingwarehouse.msdyn_warehouseidentifier
DELIVERYADDRESSCOUNTYID | = | msdyn_deliveryaddresscountyid
DELIVERYADDRESSDESCRIPTION | = | msdyn_deliveryaddressdescription
DELIVERYADDRESSDISTRICTNAME | = | msdyn_deliveryaddressdistrictname
DELIVERYADDRESSDUNSNUMBER | = | msdyn_deliveryaddressdunsnumber
DELIVERYADDRESSLATITUDE | = | msdyn_deliveryaddresslatitude
DELIVERYADDRESSLOCATIONID | = | msdyn_deliveryaddresslocationid
DELIVERYADDRESSLONGITUDE | = | msdyn_deliveryaddresslongitude
DELIVERYADDRESSNAME | = | msdyn_deliveryaddressname
DELIVERYADDRESSPOSTBOX | = | msdyn_deliveryaddresspostbox
DELIVERYBUILDINGCOMPLIMENT | = | msdyn_deliverybuildingcompliment
FORMATTEDDELVERYADDRESS | >> | msdyn_formatteddeliveryaddress
EMAIL | = | emailaddress
FORMATTEDINVOICEADDRESS | >> | msdyn_formattedinvoiceaddress
INVOICEADDRESSCOUNTYID | >> | msdyn_invoiceaddresscountyid
INVOICEADDRESSDISTRICTNAME | >> | msdyn_invoiceaddressdistrictname
INVOICEADDRESSLATITUDE | >> | msdyn_invoiceaddresslatitude
INVOICEADDRESSLONGITUDE | >> | msdyn_invoiceaddresslongitude
INVOICEADDRESSPOSTBOX | >> | msdyn_invoiceaddresspostbox
INVOICEBUILDINGCOMPLIMENT | >> | msdyn_invoicebuildingcompliment
INVOICECUSTOMERACCOUNTNUMBER | = | msdyn_invoicecustomer.accountnumber
ISDELIVERYADDRESSORDERSPECIFIC | >< | msdyn_isdeliveryaddressorderspecific
ISDELIVERYADDRESSPRIVATE | >< | msdyn_isdeliveryaddressprivate
ISINVOICEADDRESSPRIVATE | >> | msdyn_isinvoiceaddressprivate
ISONETIMECUSTOMER | >< | msdyn_isonetimecustomer
ISSALESPROCESSINGSTOPPED | >< | msdyn_issalesprocessingstopped
PAYMENTTERMSBASEDATE | = | msdyn_paymenttermsbasedate
PAYMENTTERMSNAME | = | msdyn_paymentterms.msdyn_name
PRICECUSTOMERGROUPCODE | = | msdyn_pricecustomergroup.msdyn_groupcode
QUOTATIONNUMBER | = | msdyn_quotationnumber
REQUESTEDRECEIPTDATE | = | msdyn_requestedreceiptdate
REQUESTEDSHIPPINGDATE | = | requestdeliveryby
SALESORDERPROMISINGMETHOD | >< | msdyn_salesorderpromisingmethod
URL | = | msdyn_url
none | >> | statecode
none | >> | statuscode
SALESORDERPROCESSINGSTATUS | >< | msdyn_processingstatus
LANGUAGEID | >< | msdyn_language
CUSTOMERSORDERREFERENCE | >< | msdyn_customersorderreference
DELIVERYMODECODE | = | msdyn_deliverymode.msdyn_name
DELIVERYTERMSCODE | = | msdyn_deliveryterms.msdyn_termscode
SALESORDERORIGINCODE | = | msdyn_salesorderorigin.msdyn_origincode

### FO.SalesOrderLineCDSEntity to CDS.salesorderdetails
Source field | Map type | Destination field
---|---|---
CURRENCYCODE | >> | transactioncurrencyid.isocurrencycode
DELIVERYADDRESSCITY | >< | shipto_city
DELIVERYADDRESSCOUNTRYREGIONISOCODE | >< | shipto_country
DELIVERYADDRESSZIPCODE | >< | shipto_postalcode
DELIVERYADDRESSSTATEID | >< | shipto_stateorprovince
DELIVERYADDRESSSTREET | >< | shipto_line1
DELIVERYADDRESSSTREETNUMBER | >< | shipto_line2
LINEAMOUNT | >> | extendedamount
LINECREATIONSEQUENCENUMBER | >< | sequencenumber
ORDEREDSALESQUANTITY | >< | quantity
PRODUCTNAME | >< | description
PRODUCTNUMBER | >< | productid.msdyn_productnumber
SALESORDERNUMBER | >< | salesorderid.msdyn_salesordernumber
SALESUNITSYMBOL | >< | uomid.msdyn_symbol
LINEDISCOUNTAMOUNT | >< | manualdiscountamount
TOTALTAXAMOUNT | >> | tax
SALESPRICE | >< | priceperunit
LINEAMOUNT | >> | baseamount
SALESPRODUCTCATEGORYNAME | = | msdyn_salesproductcategory.msdyn_name
SALESPRODUCTCATEGORYHIERARCHYNAME | >> | msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name
ISDELIVERYADDRESSORDERSPECIFIC | >< | msdyn_isdeliveryaddressspecific
ISDELIVERYADDRESSPRIVATE | >< | msdyn_isdeliveryaddressprivate
ISLINESTOPPED | >< | msdyn_islinestopped
ALLOWEDOVERDELIVERYPERCENTAGE | = | msdyn_allowedoverdeliverypercentage
ALLOWEDUNDERDELIVERYPERCENTAGE | = | msdyn_allowedunderdeliverypercentage
CONFIRMEDSHIPPINGDATE | = | msdyn_confirmedshippingdate
CONFIRMEDRECEIPTDATE | = | msdyn_confirmedreceiptdate
DELIVERYADDRESSCOUNTYID | = | msdyn_deliveryaddresscountyid
DELIVERYADDRESSDESCRIPTION | = | msdyn_deliveryaddressdescription
DELIVERYADDRESSDISTRICTNAME | = | msdyn_deliveryaddressdistrictname
DELIVERYADDRESSDUNSNUMBER | = | msdyn_deliveryaddressdunsnumber
DELIVERYADDRESSLATITUDE | = | msdyn_deliveryaddresslatitude
DELIVERYADDRESSLOCATIONID | = | msdyn_deliveryaddresslocationid
DELIVERYADDRESSLONGITUDE | = | msdyn_deliveryaddresslongitude
DELIVERYADDRESSNAME | = | msdyn_deliveryaddressname
DELIVERYADDRESSPOSTBOX | = | msdyn_deliveryaddresspostbox
DELIVERYBUILDINGCOMPLIMENT | = | msdyn_deliverybuildingcompliment
EXTERNALITEMNUMBER | = | msdyn_externalitemnumber
FIXEDPRICECHARGES | = | msdyn_fixedpricecharges
FORMATTEDDELIVERYADDRESS | = | msdyn_formatteddeliveryaddress
LINEDESCRIPTION | = | msdyn_linedescription
LINEDISCOUNTAMOUNT | >< | msdyn_linediscountamount
LINEDISCOUNTPERCENTAGE | >< | msdyn_linediscountpercentage
MULTILINEDISCOUNTAMOUNT | >< | msdyn_multilinediscountamount
MULTILINEDISCOUNTPERCENTAGE | >< | msdyn_multilinediscountpercentage
REQUESTEDRECEIPTDATE | = | msdyn_requestedreceiptdate
REQUESTEDSHIPPINGDATE | = | requestdeliveryby
SALESORDERLINESTATUS | >> | msdyn_linestatus
SALESORDERPROMISINGMETHOD | >< | msdyn_salesorderpromisingmethod
SALESPRICEQUANTITY | = | msdyn_salespricequantity
SHIPPINGSITEID | = | msdyn_shippingsite.msdyn_siteid
SHIPPINGWAREHOUSEID | = | msdyn_shippingwarehouse.msdyn_warehouseidentifier
none | >> | ispriceoverridden
TOTALCHARGESAMOUNT | >> | msdyn_totalchargesamount
DELIVERYMODECODE | = | msdyn_deliverymode.msdyn_name
DELIVERYTERMSID | = | msdyn_deliveryterms.msdyn_termscode

## FO.SalesInvoiceHeaderV2Entity to CDS.invoice
Source field | Map type | Destination field
---|---|---
none | >> | ispricelocked
none | >> | statuscode
CONTACTPERSONID | >> | msdyn_contactperson.msdyn_contactpersonid
CURRENCYCODE | >> | transactioncurrencyid.isocurrencycode
CUSTOMERSORDERREFERENCE | >> | description
INVOICEADDRESSCITY | >> | billto_city
INVOICEADDRESSCOUNTRYREGIONISOCODE | >> | billto_country
INVOICEADDRESSSTATE | >> | billto_stateorprovince
INVOICEADDRESSSTREET | >> | billto_line1
INVOICEADDRESSSTREETNUMBER | >> | billto_line2
INVOICEADDRESSZIPCODE | >> | billto_postalcode
INVOICECUSTOMERACCOUNTNUMBER | >> | customerid.Account(accountnumber).Contact(msdyn_contactpersonid)
INVOICEDATE | >> | msdyn_invoicedate
INVOICENUMBER | >> | msdyn_invoicenumber
LEDGERVOUCHER | >> | msdyn_ledgervoucher
PAYMENTTERMSNAME | >> | msdyn_paymentterms.msdyn_name
SALESORDERNUMBER | >> | salesorderid.msdyn_salesordernumber
TOTALCHARGEAMOUNT | >> | freightamount
TOTALDISCOUNTAMOUNT | >> | totaldiscountamount
TOTALDISCOUNTCUSTOMERGROUPCODE | >> | discountamount
TOTALINVOICEAMOUNT | >> | totalamount
TOTALTAXAMOUNT | >> | totaltax

## FO.SalesInvoiceLineV2Entity to CDS.invoicedetail
Source field | Map type | Destination field
---|---|---
CONFIRMEDSHIPPINGDATE | >> | msdyn_confirmedshippingdate
CURRENCYCODE | >> | transactioncurrencyid.isocurrencycode
INVENTORYSITEID | >> | msdyn_inventorysite.msdyn_siteid
INVENTORYWAREHOUSEID | >> | msdyn_inventorywarehouse.msdyn_warehouseidentifier
INVOICEDATE | >> | invoiceid.msdyn_invoicedate
INVOICEDQUANTITY | >> | quantity
INVOICENUMBER | >> | invoiceid.msdyn_invoicenumber
LEDGERVOUCHER | >> | invoiceid.msdyn_ledgervoucher
LINEAMOUNT | >> | extendedamount
LINECREATIONSEQUENCENUMBER | >> | sequencenumber
LINETOTALCHARGEAMOUNT | >> | msdyn_totalchargeamount
LINETOTALDISCOUNTAMOUNT | >> | manualdiscountamount
LINETOTALTAXAMOUNT | >> | tax
PRODUCTNAME | >> | description
PRODUCTNUMBER | >> | productid.msdyn_productnumber
SALESPRICE | >> | priceperunit
SALESPRODUCTCATEGORYHIERARCHYNAME | >> | msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name
SALESPRODUCTCATEGORYNAME | >> | msdyn_salesproductcategory.msdyn_name
SALESUNITSYMBOL | >> | uomid.msdyn_symbol
none | >> | producttypecode
none | >> | propertyconfigurationstatus
none | >> | ispriceoverridden
