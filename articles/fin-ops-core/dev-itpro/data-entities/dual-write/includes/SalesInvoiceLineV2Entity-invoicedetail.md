## Sales invoice lines V2 to invoicedetails

This template synchronizes data between Finance and Operations apps and Common Data Service.

Finance and Operations apps | Map type | model-driven apps in Dynamics 365 | Default value
---|---|---|---
CONFIRMEDSHIPPINGDATE | >> | msdyn_confirmedshippingdate | 
CURRENCYCODE | >> | transactioncurrencyid.isocurrencycode | 
INVENTORYSITEID | >> | msdyn_inventorysite.msdyn_siteid | 
INVENTORYWAREHOUSEID | >> | msdyn_inventorywarehouse.msdyn_warehouseidentifier | 
INVOICEDATE | >> | invoiceid.msdyn_invoicedate | 
INVOICEDQUANTITY | >> | quantity | 
INVOICENUMBER | >> | invoiceid.msdyn_invoicenumber | 
LEDGERVOUCHER | >> | invoiceid.msdyn_ledgervoucher | 
LINEAMOUNT | >> | extendedamount | 
LINECREATIONSEQUENCENUMBER | >> | sequencenumber | 
LINETOTALCHARGEAMOUNT | >> | msdyn_totalchargeamount | 
LINETOTALDISCOUNTAMOUNT | >> | manualdiscountamount | 
LINETOTALTAXAMOUNT | >> | tax | 
PRODUCTNAME | >> | description | 
PRODUCTNUMBER | >> | productid.msdyn_productnumber | 
SALESPRICE | >> | priceperunit | 
SALESPRODUCTCATEGORYHIERARCHYNAME | >> | msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name | 
SALESPRODUCTCATEGORYNAME | >> | msdyn_salesproductcategory.msdyn_name | 
SALESUNITSYMBOL | >> | uomid.msdyn_symbol | 
none | >> | producttypecode | 1
none | >> | propertyconfigurationstatus | 2
none | >> | ispriceoverridden | True
