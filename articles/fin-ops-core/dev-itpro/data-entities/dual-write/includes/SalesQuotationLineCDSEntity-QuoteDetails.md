## CDS sales quotation lines to quotedetails

This template synchronizes data between Finance and Operations apps and Common Data Service.

Finance and Operations apps | Map type | model-driven apps in Dynamics 365 | Default value
---|---|---|---
ALLOWEDOVERDELIVERYPERCENTAGE | = | msdyn_allowedoverdeliverypercentage | 
ALLOWEDUNDERDELIVERYPERCENTAGE | = | msdyn_allowedunderdeliverypercentage | 
SALESQUOTATIONNUMBER | = | quoteid.msdyn_quotenumber | 
LINECREATIONSEQUENCENUMBER | = | sequencenumber | 
CURRENCYCODE | >> | transactioncurrencyid.isocurrencycode | 
DELIVERYADDRESSCITY | = | shipto_city | 
DELIVERYADDRESSCOUNTRYREGIONISOCODE | >< | shipto_country | 
DELIVERYADDRESSCOUNTYID | = | msdyn_deliveryaddresscountyid | 
DELIVERYADDRESSDESCRIPTION | = | msdyn_deliveryaddressdescription | 
DELIVERYADDRESSDISTRICTNAME | = | msdyn_deliveryaddressdistrictname | 
DELIVERYADDRESSDUNSNUMBER | = | msdyn_deliveryaddressdunsnumber | 
DELIVERYADDRESSLATITUDE | = | msdyn_deliveryaddresslatitude | 
DELIVERYADDRESSLOCATIONID | = | msdyn_deliveryaddresslocationid | 
DELIVERYADDRESSLONGITUDE | = | msdyn_deliveryaddresslongitude | 
DELIVERYADDRESSNAME | = | msdyn_deliveryaddressname | 
DELIVERYADDRESSPOSTBOX | = | msdyn_deliveryaddresspostbox | 
DELIVERYADDRESSSTATEID | = | shipto_stateorprovince | 
DELIVERYADDRESSSTREET | = | shipto_line1 | 
DELIVERYADDRESSSTREETNUMBER | = | shipto_line2 | 
DELIVERYADDRESSZIPCODE | = | shipto_postalcode | 
DELIVERYBUILDINGCOMPLIMENT | = | msdyn_deliverybuildingcompliment | 
EXTERNALITEMNUMBER | = | msdyn_externalitemnumber | 
FIXEDPRICECHARGES | = | msdyn_fixedpricecharges | 
FORMATTEDDELIVERYADDRESS | = | msdyn_formatteddeliveryaddress | 
ISDELIVERYADDRESSPRIVATE | >< | msdyn_isdeliveryaddressprivate | 
ISDELIVERYADDRESSORDERSPECIFIC | >< | msdyn_isdeliveryaddressspecific | 
LINEAMOUNT | >> | baseamount | 
LINEAMOUNT | >> | extendedamount | 
LINEDESCRIPTION | = | msdyn_linedescription2 | 
LINEDISCOUNTAMOUNT | = | msdyn_linediscountamount | 
LINEDISCOUNTPERCENTAGE | = | msdyn_linediscountpercentage | 
MULTILINEDISCOUNTAMOUNT | = | msdyn_multilinediscountamount | 
MULTILINEDISCOUNTPERCENTAGE | = | msdyn_multilinediscountpercentage | 
PRODUCTNAME | = | description | 
PRODUCTNUMBER | = | productid.msdyn_productnumber | 
REQUESTEDRECEIPTDATE | = | msdyn_requestedreceiptdate | 
REQUESTEDSALESQUANTITY | = | quantity | 
REQUESTEDSHIPPINGDATE | = | requestdeliveryby | 
SALESPRICE | = | priceperunit | 
SALESPRICEQUANTITY | = | msdyn_salespricequantity | 
SALESQUOTATIONPROMISINGMETHOD | >< | msdyn_salesquotationpromisingmethod | 
SALESQUOTATIONSTATUS | >< | msdyn_salesquotationstatus | 
SALESUNITSYMBOL | = | uomid.msdyn_symbol | 
SHIPPINGSITEID | = | msdyn_shippingsite.msdyn_siteid | 
SHIPPINGWAREHOUSEID | = | msdyn_shippingwarehouse.msdyn_warehouseidentifier | 
TOTALCHARGESAMOUNT | >> | msdyn_totalchargesamount | 
TOTALDISCOUNTAMOUNT | = | manualdiscountamount | 
TOTALTAXAMOUNT | >> | tax | 
SALESPRODUCTCATEGORYHIERARCHYNAME | > | msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name | 
SALESPRODUCTCATEGORYNAME | = | msdyn_salesproductcategory.msdyn_name | 
none | >> | ispriceoverridden | true
