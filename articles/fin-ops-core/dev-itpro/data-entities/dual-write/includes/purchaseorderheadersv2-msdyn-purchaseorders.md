---
author: robinarh
ms.service: dynamics-ax-applications
ms.topic: include
ms.date: 11/17/2020
ms.author: rhaertle
---

### Purchase order headers V2 to msdyn_purchaseorders

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement field | Default value
---|---|---|---
DELIVERYADDRESSNAME |  | `msdyn_addressname` | 
REQUESTEDDELIVERYDATE |  | `msdyn_dateexpected` | 
PURCHASEORDERNUMBER |  | `msdyn_name` | 
PAYMENTTERMSNAME |  | `msdyn_paymentterm.msdyn_name` | 
DEFAULTRECEIVINGWAREHOUSEID |  | `msdyn_receivetowarehouse.msdyn_warehouseidentifier` | 
ACCOUNTINGDATE |  | `msdyn_accountingdate` | 
AREPRICESINCLUDINGSALESTAX |  | `msdyn_arepriceincludingsalestax` | 
ATTENTIONINFORMATION |  | `msdyn_attentioninformation` | 
CASHDISCOUNTCODE |  | `msdyn_cashdiscountcode` | 
CASHDISCOUNTPERCENTAGE |  | `msdyn_cashdiscountpercentage` | 
CONTACTPERSONID |  | `msdyn_contactpersonid.msdyn_contactpersonid` | 
CURRENCYCODE |  | `transactioncurrencyid.isocurrencycode` | 
DEFAULTRECEIVINGSITEID |  | `msdyn_defaultreceivingsiteid.msdyn_siteid` | 
DELIVERYTERMSID |  | `msdyn_deliveryterm.msdyn_termscode` | 
EMAIL |  | `msdyn_email` | 
ISCHANGEMANAGEMENTACTIVE |  | `msdyn_ischangemanagementactive` | 
ISDELIVEREDDIRECTLY |  | `msdyn_isdeliverydirectly` | 
LANGUAGEID |  | `msdyn_language` | 
ORDERERPERSONNELNUMBER |  | `msdyn_ordererpersonnelnumber.cdm_workernumber` | 
REASONCODE |  | `msdyn_reasoncode` | 
REASONCOMMENT |  | `msdyn_reasoncomment` | 
TOTALDISCOUNTPERCENTAGE |  | `msdyn_totaldiscountpercentage` | 
URL |  | `msdyn_url` | 
VENDORORDERREFERENCE |  | `msdyn_vendororderreference` | 
VENDORPAYMENTMETHODNAME |  | `msdyn_vendorpaymentmethod.msdyn_name` | 
VENDORPAYMENTMETHODSPECIFICATIONNAME |  | `msdyn_vendorpaymentmethodspecificationname` | 
ORDERVENDORACCOUNTNUMBER |  | `msdyn_vendor.accountnumber` | 
DELIVERYMODEID |  | `msdyn_shipvia.msdyn_name` | 
INVOICEVENDORACCOUNTNUMBER |  | `msdyn_invoicevendoraccount.accountnumber` | 
DOCUMENTAPPROVALSTATUS |  | `msdyn_documentapprovalstatus` | 
PURCHASEORDERSTATUS |  | `msdyn_purchaseorderstatus` | 
DELIVERYADDRESSCITY |  | `msdyn_city` | 
DELIVERYADDRESSCOUNTRYREGIONISOCODE |  | `msdyn_country` | 
DELIVERYADDRESSSTATEID |  | `msdyn_stateorprovince` | 
DELIVERYADDRESSZIPCODE |  | `msdyn_postalcode` | 
DELIVERYADDRESSSTREET |  | `msdyn_address1` | 
INVOICEADDRESSSTREETNUMBER |  | `msdyn_invoiceaddressstreetnumber` | 
CONFIRMEDDELIVERYDATE |  | `msdyn_confirmeddeliverydate` | 
DELIVERYADDRESSLONGITUDE |  | `msdyn_longitude` | 
DELIVERYADDRESSLATITUDE |  | `msdyn_latitude` | 
DELIVERYADDRESSCOUNTRYREGIONID |  | `msdyn_deliveryaddresscountryregionid` | 
DELIVERYADDRESSCOUNTYID |  | `msdyn_deliveryaddresscountyid` | 
DELIVERYADDRESSDESCRIPTION |  | `msdyn_deliveryaddressdescription` | 
DELIVERYADDRESSDISTRICTNAME |  | `msdyn_deliveryaddressdistrictname` | 
DELIVERYADDRESSDUNSNUMBER |  | `msdyn_deliveryaddressdunsnumber` | 
DELIVERYADDRESSLOCATIONID |  | `msdyn_deliveryaddresslocationid` | 
DELIVERYADDRESSPOSTBOX |  | `msdyn_deliveryaddresspostbox` | 
DELIVERYADDRESSTIMEZONE |  | `msdyn_deliveryaddresstimezone` | 
DELIVERYBUILDINGCOMPLIMENT |  | `msdyn_deliverybuildingcompliment` | 
FORMATTEDDELIVERYADDRESS |  | `msdyn_formatteddeliveryaddress` | 
FORMATTEDINVOICEADDRESS |  | `msdyn_formattedinvoiceaddress` | 
INVOICEADDRESSCITY |  | `msdyn_invoiceaddresscity` | 
INVOICEADDRESSCOUNTRYREGIONID |  | `msdyn_invoiceaddresscountryregionid` | 
INVOICEADDRESSCOUNTY |  | `msdyn_invoiceaddresscounty` | 
INVOICEADDRESSSTATE |  | `msdyn_invoiceaddressstate` | 
INVOICEADDRESSSTREET |  | `msdyn_invoiceaddressstreet` | 
DELIVERYADDRESSSTREETNUMBER |  | `msdyn_address2` | 
INVOICEADDRESSZIPCODE |  | `msdyn_invoiceaddresszipcode` | 
