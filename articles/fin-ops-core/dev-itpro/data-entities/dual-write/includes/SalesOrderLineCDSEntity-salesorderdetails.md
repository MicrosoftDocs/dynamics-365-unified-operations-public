## CDS sales order lines to salesorderdetails

This template synchronizes data between Finance and Operations apps and Common Data Service.

Finance and Operations apps | Map type | model-driven apps in Dynamics 365 | Default value
---|---|---|---
CURRENCYCODE | >> | transactioncurrencyid.isocurrencycode | 
DELIVERYADDRESSCITY | >< | shipto_city | 
DELIVERYADDRESSCOUNTRYREGIONISOCODE | >< | shipto_country | 
DELIVERYADDRESSZIPCODE | >< | shipto_postalcode | 
DELIVERYADDRESSSTATEID | >< | shipto_stateorprovince | 
DELIVERYADDRESSSTREET | >< | shipto_line1 | 
DELIVERYADDRESSSTREETNUMBER | >< | shipto_line2 | 
LINEAMOUNT | >> | extendedamount | 
LINECREATIONSEQUENCENUMBER | >< | sequencenumber | 
ORDEREDSALESQUANTITY | >< | quantity | 
PRODUCTNAME | >< | description | 
PRODUCTNUMBER | >< | productid.msdyn_productnumber | 
SALESORDERNUMBER | >< | salesorderid.msdyn_salesordernumber | 
SALESUNITSYMBOL | >< | uomid.msdyn_symbol | 
LINEDISCOUNTAMOUNT | >< | manualdiscountamount | 
TOTALTAXAMOUNT | >> | tax | 
SALESPRICE | >< | priceperunit | 
LINEAMOUNT | >> | baseamount | 
SALESPRODUCTCATEGORYNAME | = | msdyn_salesproductcategory.msdyn_name | 
SALESPRODUCTCATEGORYHIERARCHYNAME | >> | msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name | 
ISDELIVERYADDRESSORDERSPECIFIC | >< | msdyn_isdeliveryaddressspecific | 
ISDELIVERYADDRESSPRIVATE | >< | msdyn_isdeliveryaddressprivate | 
ISLINESTOPPED | >< | msdyn_islinestopped | 
ALLOWEDOVERDELIVERYPERCENTAGE | = | msdyn_allowedoverdeliverypercentage | 
ALLOWEDUNDERDELIVERYPERCENTAGE | = | msdyn_allowedunderdeliverypercentage | 
CONFIRMEDSHIPPINGDATE | = | msdyn_confirmedshippingdate | 
CONFIRMEDRECEIPTDATE | = | msdyn_confirmedreceiptdate | 
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
EXTERNALITEMNUMBER | = | msdyn_externalitemnumber | 
FIXEDPRICECHARGES | = | msdyn_fixedpricecharges | 
FORMATTEDDELIVERYADDRESS | = | msdyn_formatteddeliveryaddress | 
LINEDESCRIPTION | = | msdyn_linedescription | 
LINEDISCOUNTAMOUNT | >< | msdyn_linediscountamount | 
LINEDISCOUNTPERCENTAGE | >< | msdyn_linediscountpercentage | 
MULTILINEDISCOUNTAMOUNT | >< | msdyn_multilinediscountamount | 
MULTILINEDISCOUNTPERCENTAGE | >< | msdyn_multilinediscountpercentage | 
REQUESTEDRECEIPTDATE | = | msdyn_requestedreceiptdate | 
REQUESTEDSHIPPINGDATE | = | requestdeliveryby | 
SALESORDERLINESTATUS | >> | msdyn_linestatus | 
SALESORDERPROMISINGMETHOD | >< | msdyn_salesorderpromisingmethod | 
SALESPRICEQUANTITY | = | msdyn_salespricequantity | 
SHIPPINGSITEID | = | msdyn_shippingsite.msdyn_siteid | 
SHIPPINGWAREHOUSEID | = | msdyn_shippingwarehouse.msdyn_warehouseidentifier | 
none | >> | ispriceoverridden | true
TOTALCHARGESAMOUNT | >> | msdyn_totalchargesamount | 
DELIVERYMODECODE | = | msdyn_deliverymode.msdyn_name | 
DELIVERYTERMSID | = | msdyn_deliveryterms.msdyn_termscode | 
