## CDS sales quotation header to quotes

This template synchronizes data between Finance and Operations apps and Common Data Service.

Reversed source filter: statecode eq 0

Finance and Operations apps | Map type | model-driven apps in Dynamics 365 | Default value
---|---|---|---
SALESQUOTATIONNUMBER | = | msdyn_quotenumber | 
REQUESTINGCUSTOMERACCOUNTNUMBER | = | customerid.Account(accountnumber).Contact(msdyn_contactpersonid) | 
CURRENCYCODE | = | transactioncurrencyid.isocurrencycode | 
CUSTOMERSREFERENCE | = | msdyn_customersreference | 
DELIVERYADDRESSCITY | = | shipto_city | 
DELIVERYADDRESSCOUNTRYREGIONISOCODE | >< | shipto_country | 
DELIVERYADDRESSSTREETNUMBER | = | shipto_line2 | 
DELIVERYADDRESSZIPCODE | = | shipto_postalcode | 
DELIVERYADDRESSSTREET | = | shipto_line1 | 
DELIVERYADDRESSSTATEID | = | shipto_stateorprovince | 
SALESQUOTATIONNAME | = | name | 
INVOICEADDRESSCITY | >> | billto_city | 
INVOICEADDRESSSTREET | >> | billto_line1 | 
INVOICEADDRESSSTREETNUMBER | >> | billto_line2 | 
INVOICEADDRESSCOUNTRYREGIONISOCODE | >> | billto_country | 
INVOICEADDRESSSTATEID | >> | billto_stateorprovince | 
INVOICEADDRESSZIPCODE | >> | billto_postalcode | 
QUOTATIONTOTALAMOUNT | >> | totalamount | 
TOTALDISCOUNTAMOUNT | >> | discountamount | 
QUOTATIONTOTALTAXAMOUNT | >> | totaltax | 
QUOTATIONTOTALCHARGESAMOUNT | >> | freightamount | 
AREPRICESINCLUDINGSALESTAX | >< | msdyn_arepricesincludingsalestax | 
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
FORMATTEDDELIVERYADDRESS | >> | msdyn_formatteddeliveryaddress | 
FORMATTEDINVOICEADDRESS | >> | msdyn_formattedinvoiceaddress | 
GENERATEDSALESORDERNUMBER | = | msdyn_generatedsalesordernumber.msdyn_salesordernumber | 
INVOICEADDRESSCOUNTRYREGIONID | > | msdyn_invoiceaddresscountryregionid | 
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
LANGUAGEID | >< | msdyn_language | 
PAYMENTTERMSNAME | = | msdyn_paymentterms.msdyn_name | 
PRICECUSTOMERGROUPCODE | = | msdyn_pricecustomergroup.msdyn_groupcode | 
RECEIPTDATEREQUESTED | = | msdyn_requestedreceiptdate | 
REQUESTEDSHIPPINGDATE | = | requestdeliveryby | 
SALESORDERPROMISINGMETHOD | >< | msdyn_salesorderpromisingmethod | 
SALESQUOTATIONCONFIRMATIONDATE | = | msdyn_salesquotationconfirmationdate | 
SALESQUOTATIONEXPIRYDATE | = | msdyn_salesquotationexpirydate | 
SALESQUOTATIONFOLLOWUPDATE | = | msdyn_salesquotationfollowupdate | 
SALESQUOTATIONSTATUS | >< | msdyn_salesquotationstatus | 
TOTALDISCOUNTPERCENTAGE | = | msdyn_totaldiscountpercentage | 
URL | = | msdyn_url | 
EMAIL | = | emailaddress | 
