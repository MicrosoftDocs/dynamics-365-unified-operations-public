## CDS sales order headers to salesorders

This template synchronizes data between Finance and Operations apps and Common Data Service.

Reversed source filter: msdyn_ordertype eq 192350000

Finance and Operations apps | Map type | model-driven apps in Dynamics 365 | Default value
---|---|---|---
SALESORDERNUMBER | >< | msdyn_salesordernumber | 
ORDERINGCUSTOMERACCOUNTNUMBER | >< | customerid.Account(accountnumber).Contact(msdyn_contactpersonid) | 
CURRENCYCODE | >< | transactioncurrencyid.isocurrencycode | 
DELIVERYADDRESSCITY | >< | shipto_city | 
DELIVERYADDRESSCOUNTRYREGIONISOCODE | >< | shipto_country | 
DELIVERYADDRESSSTREETNUMBER | >< | shipto_line2 | 
DELIVERYADDRESSZIPCODE | >< | shipto_postalcode | 
DELIVERYADDRESSSTREET | >< | shipto_line1 | 
DELIVERYADDRESSSTATEID | >< | shipto_stateorprovince | 
SALESORDERNAME | >> | name | 
INVOICEADDRESSCITY | >> | billto_city | 
INVOICEADDRESSSTREET | >> | billto_line1 | 
INVOICEADDRESSSTREETNUMBER | >> | billto_line2 | 
INVOICEADDRESSCOUNTRYREGIONISOCODE | >> | billto_country | 
INVOICEADDRESSSTATEID | >> | billto_stateorprovince | 
INVOICEADDRESSZIPCODE | >> | billto_postalcode | 
ORDERTOTALAMOUNT | >> | totalamount | 
TOTALDISCOUNTAMOUNT | >> | discountamount | 
ORDERTOTALTAXAMOUNT | >> | totaltax | 
ORDERTOTALCHARGESAMOUNT | >> | freightamount | 
AREPRICESINCLUDINGSALESTAX | >< | msdyn_arepricesincludingsalestax | 
CONFIRMEDRECEIPTDATE | = | msdyn_confirmedreceiptdate | 
CONFIRMEDSHIPPINGDATE | = | msdyn_confirmedshippingdate | 
CONTACTPERSONID | = | msdyn_contactperson.msdyn_contactpersonid | 
CUSTOMERREQUISITIONNUMBER | = | msdyn_customerrequisitionnumber | 
DEFAULTSHIPPINGSITEID | = | msdyn_defaultshippingsite.msdyn_siteid | 
DEFAULTSHIPPINGWAREHOUSEID | = | msdyn_defaultshippingwarehouse.msdyn_warehouseidentifier | 
DELIVERYADDRESSCOUNTYID | = | msdyn_deliveryaddresscountyid | 
DELIVERYADDRESSDESCRIPTION | = | msdyn_deliveryaddressdescription | 
DELIVERYADDRESSDISTRICTNAME | = | msdyn_deliveryaddressdistrictname | 
DELIVERYADDRESSDUNSNUMBER | = | msdyn_deliveryaddressdunsnumber | 
DELIVERYADDRESSLATITUDE | = | msdyn_deliveryaddresslatitude | 
DELIVERYADDRESSLOCATIONID | = | msdyn_deliveryaddresslocationid | 
DELIVERYADDRESSLONGITUDE | = | msdyn_deliveryaddresslongitude | 
DELIVERYADDRESSNAME | = | msdyn_deliveryaddressname | 
DELIVERYADDRESSPOSTBOX | = | msdyn_deliveryaddresspostbox | 
DELIVERYBUILDINGCOMPLIMENT | = | msdyn_deliverybuildingcompliment | 
FORMATTEDDELVERYADDRESS | >> | msdyn_formatteddeliveryaddress | 
EMAIL | = | emailaddress | 
FORMATTEDINVOICEADDRESS | >> | msdyn_formattedinvoiceaddress | 
INVOICEADDRESSCOUNTYID | >> | msdyn_invoiceaddresscountyid | 
INVOICEADDRESSDISTRICTNAME | >> | msdyn_invoiceaddressdistrictname | 
INVOICEADDRESSLATITUDE | >> | msdyn_invoiceaddresslatitude | 
INVOICEADDRESSLONGITUDE | >> | msdyn_invoiceaddresslongitude | 
INVOICEADDRESSPOSTBOX | >> | msdyn_invoiceaddresspostbox | 
INVOICEBUILDINGCOMPLIMENT | >> | msdyn_invoicebuildingcompliment | 
INVOICECUSTOMERACCOUNTNUMBER | = | msdyn_invoicecustomer.accountnumber | 
ISDELIVERYADDRESSORDERSPECIFIC | >< | msdyn_isdeliveryaddressorderspecific | 
ISDELIVERYADDRESSPRIVATE | >< | msdyn_isdeliveryaddressprivate | 
ISINVOICEADDRESSPRIVATE | >> | msdyn_isinvoiceaddressprivate | 
ISONETIMECUSTOMER | >< | msdyn_isonetimecustomer | 
ISSALESPROCESSINGSTOPPED | >< | msdyn_issalesprocessingstopped | 
PAYMENTTERMSBASEDATE | = | msdyn_paymenttermsbasedate | 
PAYMENTTERMSNAME | = | msdyn_paymentterms.msdyn_name | 
PRICECUSTOMERGROUPCODE | = | msdyn_pricecustomergroup.msdyn_groupcode | 
QUOTATIONNUMBER | = | msdyn_quotationnumber | 
REQUESTEDRECEIPTDATE | = | msdyn_requestedreceiptdate | 
REQUESTEDSHIPPINGDATE | = | requestdeliveryby | 
SALESORDERPROMISINGMETHOD | >< | msdyn_salesorderpromisingmethod | 
URL | = | msdyn_url | 
none | >> | statecode | 0
none | >> | statuscode | 1
SALESORDERPROCESSINGSTATUS | >< | msdyn_processingstatus | 
LANGUAGEID | >< | msdyn_language | 
CUSTOMERSORDERREFERENCE | >< | msdyn_customersorderreference | 
DELIVERYMODECODE | = | msdyn_deliverymode.msdyn_name | 
DELIVERYTERMSCODE | = | msdyn_deliveryterms.msdyn_termscode | 
SALESORDERORIGINCODE | = | msdyn_salesorderorigin.msdyn_origincode | 
