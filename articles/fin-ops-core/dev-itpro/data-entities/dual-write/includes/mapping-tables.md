---
author: robinarh
ms.topic: include
ms.date: 3/4/2021
ms.author: rhaertle
---

###  <a name="138"></a>All products (msdyn_globalproducts)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PRODUCTNAME` | > | `msdyn_productname` |
`PRODUCTNUMBER` | > | `msdyn_productnumber` |

###  <a name="119"></a>Asset management asset lifecycle models (msdyn_assetlifecyclemodels)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`ACTIVELIFECYCLESTATEID` | = | `msdyn_activelifecyclestate.msdyn_assetlifecyclestate_id` |
`INBOUNDLIFECYCLESTATEID` | = | `msdyn_inboundlifecyclestate.msdyn_assetlifecyclestate_id` |
`INSTORAGELIFECYCLESTATEID` | = | `msdyn_instoragelifecyclestate.msdyn_assetlifecyclestate_id` |
`LIFECYCLEMODELID` | = | `msdyn_assetlifecyclemodel_id` |
`NAME` | = | `msdyn_name` |
`ONLOANLIFECYCLESTATEID` | = | `msdyn_onloanlifecyclestate.msdyn_assetlifecyclestate_id` |
`OUTBOUNDLIFECYCLESTATEID` | = | `msdyn_outboundlifecyclestate.msdyn_assetlifecyclestate_id` |
`RECEIVEDLIFECYCLESTATEID` | = | `msdyn_receivedlifecyclestate.msdyn_assetlifecyclestate_id` |

###  <a name="120"></a>Asset management asset lifecycle states (msdyn_assetlifecyclestates)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DELETEOPENCALENDARLINES` | >< | `msdyn_deleteopencalendarlines` |
`LIFECYCLESTATEID` | = | `msdyn_assetlifecyclestate_id` |
`LINE` | = | `msdyn_line` |
`MAINTENANCEASSETACTIVE` | >< | `msdyn_maintenanceassetactive` |
`NAME` | = | `msdyn_name` |

###  <a name="124"></a>Asset management asset types (msdyn_customerassetcategories)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`LIFECYCLEMODELID` | = | `msdyn_lifecyclemodel.msdyn_assetlifecyclemodel_id` |
`MAINTENANCEASSETTYPEID` | = | `msdyn_maintenanceassettypeid` |
`NAME` | = | `msdyn_name` |
`CALCULATEKPITOTAL` | >< | `msdyn_calculatekpitotal` |

###  <a name="125"></a>Asset management assets (msdyn_customerassets)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`ACQUISITIONCOST` | = | `msdyn_acquisitioncost` |
`ACQUISITIONDATE` | = | `msdyn_acquisitiondate` |
`ACTIVEFROM` | = | `msdyn_activefrom` |
`ACTIVETO` | = | `msdyn_activeto` |
`FUNCTIONALLOCATIONID` | = | `msdyn_functionallocation.msdyn_functionallocation_id` |
`MAINTENANCEASSETLIFECYCLESTATEID` | = | `msdyn_assetlifecyclestate.msdyn_assetlifecyclestate_id` |
`MODELID` | = | `msdyn_model.msdyn_model_id` |
`MODELPRODUCTID` | = | `msdyn_model.msdyn_manufacturer.msdyn_manufacturer_id` |
`MODELYEAR` | = | `msdyn_modelyear` |
`NAME` | = | `msdyn_name` |
`NOTES` | = | `msdyn_notes` |
`PURCHASEORDERID` | = | `msdyn_purchaseorderid` |
`REPLACEMENTDATE` | >< | `msdyn_replacementdate` |
`REPLACEMENTVALUE` | = | `msdyn_replacementvalue` |
`SERIALID` | = | `msdyn_serialid` |
`VENDACCOUNT` | = | `msdyn_vendaccount` |
`WARRANTYDATEFROMVEND` | = | `msdyn_warrantydatefromvend` |
`WARRANTYID` | = | `msdyn_warranty.msdyn_warranty_id` |
`WRKCTRID` | = | `msdyn_wrkctrid` |
`FIXEDASSETID` | = | `msdyn_fixedassetid` |
`MAINTENANCEASSETID` | = | `msdyn_maintenanceassetid` |
`PARENTMAINTENANCEASSETID` | = | `msdyn_parentasset.msdyn_maintenanceassetid` |
`MAINTENANCEASSETTYPEID` | = | `msdyn_customerassetcategory.msdyn_maintenanceassettypeid` |
`PRODUCTID` | = | `msdyn_manufacturer.msdyn_manufacturer_id` |

###  <a name="134"></a>Asset management functional location lifecycle models (msdyn_functionallocationlifecyclemodels)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`LIFECYCLEMODELID` | = | `msdyn_functionallocationlifecyclemodel_id` |
`NAME` | = | `msdyn_name` |

###  <a name="135"></a>Asset management functional location lifecycle states (msdyn_functionallocationlifecyclestates)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`ALLOWDELETELOCATION` | >< | `msdyn_allowdeletelocation` |
`ALLOWNEWSUBLOCATIONS` | >< | `msdyn_allownewsublocations` |
`ALLOWRENAMELOCATION` | >< | `msdyn_allowrenamelocation` |
`FUNCTIONALLOCATIONACTIVE` | >< | `msdyn_functionallocationactive` |
`LIFECYCLESTATEID` | = | `msdyn_functionallocationlifecyclestate_id` |
`NAME` | = | `msdyn_name` |
`ALLOWINSTALLMAINTENANCEASSETS` | >< | `msdyn_allowinstallmaintenanceassets` |
`CREATELOCATIONMAINTENANCEASSET` | >< | `msdyn_createlocationmaintenanceasset` |
`MAINTENANCEASSETLIFECYCLESTATEID` | = | `msdyn_assetlifecyclestate.msdyn_assetlifecyclestate_id` |

###  <a name="137"></a>Asset management functional location types (msdyn_functionallocationtypes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`ALLOWMULTIPLEINSTALLEDASSETS` | >< | `msdyn_allowmultipleinstalledassets` |
`FUNCTIONALLOCATIONTYPEID` | = | `msdyn_functionallocationtype_id` |
`NAME` | = | `msdyn_name` |
`UPDATEASSETDIMENSION` | >< | `msdyn_updateassetdimension` |
`LIFECYCLEMODELID` | = | `msdyn_lifecyclemodelid.msdyn_functionallocationlifecyclemodel_id` |
`MAINTENANCEASSETTYPEID` | = | `msdyn_maintenanceassettype.msdyn_maintenanceassettypeid` |

###  <a name="136"></a>Asset management functional locations (msdyn_functionallocations)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`FUNCTIONALLOCATIONID` | = | `msdyn_functionallocation_id` |
`INVENTORYLOCATIONID` | = | `msdyn_inventorylocationid` |
`INVENTORYSITEID` | = | `msdyn_inventorysiteid` |
`NAME` | = | `msdyn_name` |
`NOTES` | = | `msdyn_notes` |
`PARENTFUNCTIONALLOCATIONID` | = | `msdyn_parentfunctionallocation.msdyn_functionallocation_id` |
`FUNCTIONALLOCATIONLIFECYCLESTATEID` | = | `msdyn_functionallocationlifecyclestate.msdyn_functionallocationlifecyclestate_id` |
`FUNCTIONALLOCATIONTYPEID` | = | `msdyn_functionallocationtype.msdyn_functionallocationtype_id` |

###  <a name="153"></a>Asset management manufacturers (msdyn_manufacturers)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DESCRIPTION` | = | `msdyn_description` |
`PRODUCTID` | = | `msdyn_manufacturer_id` |

###  <a name="154"></a>Asset management models (msdyn_models)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DESCRIPTION` | = | `msdyn_description` |
`MODELID` | = | `msdyn_model_id` |
`PRODUCTID` | = | `msdyn_manufacturer.msdyn_manufacturer_id` |
`MAINTENANCEASSETTYPEID` | = | `msdyn_maintenanceassettype.msdyn_maintenanceassettypeid` |

###  <a name="209"></a>Asset management warranty (msdyn_warranties)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`NAME` | = | `msdyn_name` |
`WARRANTYID` | = | `msdyn_warranty_id` |

###  <a name="115"></a>CDS Contacts V2 (contacts)

This template synchronizes data between Finance and Operations apps and Dataverse.

Source filter: `(AssociatedContactType = 1)`

Reversed source filter: `msdyn_contactforvendor eq true and msdyn_sellable eq false and msdyn_contactpersonid ne null`

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CONTACTPERSONPARTYNUMBER` | = | `msdyn_partyid.msdyn_partynumber` |
`ASSOCIATEDCONTACTTYPE` | << | `none` | Vendor
`ASSOCIATEDCONTACTNUMBER` | = | `msdyn_vendorcontactid.msdyn_vendoraccountnumber` |
`EMPLOYMENTDEPARTMENT` | = | `department` |
`NOTES` | = | `description` |
`GOVERNMENTIDENTIFICATIONNUMBER` | = | `governmentid` |
`ISRECEIVINGDIRECTMAIL` | >< | `donotemail` |
`SPOUSENAME` | = | `spousesname` |
`none` | >> | `msdyn_contactforvendor` | True
`CONTACTPERSONID` | = | `msdyn_contactpersonid` |

###  <a name="123"></a>CDS Exchange Rates (msdyn_currencyexchangerates)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`EXCHANGERATETYPENAME` | > | `msdyn_currencyexchangeratepair.msdyn_currencyexchangeratetypeid.msdyn_name` |
`FROMCURRENCYCODE` | > | `msdyn_currencyexchangeratepair.msdyn_fromtransactioncurrencyid.isocurrencycode` |
`TOCURRENCYCODE` | > | `msdyn_currencyexchangeratepair.msdyn_totransactioncurrencyid.isocurrencycode` |
`RATE` | > | `msdyn_exchangerate` |
`VALIDFROM` | > | `msdyn_validfrom` |
`VALIDTO` | > | `msdyn_validto` |

###  <a name="220"></a>CDS Parties (msdyn_parties)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PARTYNUMBER` | = | `msdyn_partynumber` |
`PARTYTYPE` | >< | `msdyn_partytype` |
`NAMEALIAS` | = | `msdyn_namealias` |
`KNOWNAS` | = | `msdyn_nickname` |
`LANGUAGEID` | >< | `msdyn_language` |
`ORGANIZATIONNAME` | = | `msdyn_organizationname` |
`ORGANIZATIONABCCODE` | >< | `msdyn_organizationabccode` |
`ORGANIZATIONNUMOFEMPLOYEES` | = | `msdyn_numberofemployees` |
`ORGANIZATIONNUMBER` | = | `msdyn_organizationnumber` |
`ORGANIZATIONPHONETICNAME` | = | `msdyn_organizationphoneticname` |
`PERSONFIRSTNAME` | = | `msdyn_firstname` |
`PERSONMIDDLENAME` | = | `msdyn_middlename` |
`PERSONLASTNAME` | = | `msdyn_lastname` |
`PERSONLASTNAMEPREFIX` | = | `msdyn_lastnameprefix` |
`PERSONINITIALS` | = | `msdyn_initials` |
`PERSONPROFESSIONALTITLE` | = | `msdyn_professionaltitle` |
`PERSONPROFESSIONALSUFFIX` | = | `msdyn_professionalsuffix` |
`PERSONPHONETICFIRSTNAME` | = | `msdyn_phoneticfirstname` |
`PERSONPHONETICLASTNAME` | = | `msdyn_phoneticlastname` |
`PERSONPHONETICMIDDLENAME` | = | `msdyn_phoneticmiddlename` |
`PERSONGENDER` | >< | `msdyn_gender` |
`PERSONMARITALSTATUS` | >< | `msdyn_maritalstatus` |
`PERSONHOBBIES` | = | `msdyn_hobbies` |
`PERSONCHILDRENNAMES` | = | `msdyn_childrennames` |
`PERSONANNIVERSARYDAY` | = | `msdyn_anniversaryday` |
`PERSONANNIVERSARYYEAR` | = | `msdyn_anniversaryyear` |
`PERSONBIRTHDAY` | = | `msdyn_birthday` |
`PERSONBIRTHYEAR` | = | `msdyn_birthyear` |
`PERSONANNIVERSARYMONTH` | >< | `msdyn_anniversarymonth` |
`PERSONBIRTHMONTH` | >< | `msdyn_birthmonth` |

###  <a name="233"></a>CDS Party postal address locations (msdyn_partypostaladdresses)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`ISPRIMARY` | >< | `msdyn_isprimary` |
`LOCATIONID` | = | `msdyn_postaladdresscollectionid.msdyn_location` |
`PARTYNUMBER` | = | `msdyn_partyid.msdyn_partynumber` |
`PURPOSE` | = | `msdyn_postaladdresspurposenames` |
`ISLOCATIONOWNER` | >> | `msdyn_islocationowner` |

###  <a name="145"></a>CDS inventory on-hand entries (msdyn_inventoryonhandentries)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`REQUESTID` | = | `msdyn_request.msdyn_requestid` |
`INVENTORYSITEID` | = | `msdyn_inventorysite.msdyn_siteid` |
`INVENTORYWAREHOUSEID` | = | `msdyn_inventorywarehouse.msdyn_warehouseidentifier` |
`AVAILABLEONHANDQUANTITY` | > | `msdyn_availableonhandquantity` |
`AVAILABLEORDEREDQUANTITY` | > | `msdyn_availableorderedquantity` |
`ONHANDQUANTITY` | > | `msdyn_onhandquantity` |
`ONORDERQUANTITY` | > | `msdyn_onorderquantity` |
`ORDEREDQUANTITY` | > | `msdyn_orderedquantity` |
`RESERVEDONHANDQUANTITY` | > | `msdyn_reservedonhandquantity` |
`RESERVEDORDEREDQUANTITY` | > | `msdyn_reservedorderedquantity` |
`TOTALAVAILABLEQUANTITY` | > | `msdyn_totalavailablequantity` |
`ATPDATE` | = | `msdyn_atpdate` |
`ATPQUANTITY` | > | `msdyn_atpquantity` |
`PROJECTEDISSUEQUANTITY` | > | `msdyn_projectedissuequantity` |
`PROJECTEDONHANDQUANTITY` | > | `msdyn_projectedonhandquantity` |
`PROJECTEDRECEIPTQUANTITY` | > | `msdyn_projectedreceiptquantity` |
`ORDERQUANTITY` | > | `msdyn_orderquantity` |
`UNAVAILABLEONHANDQUANTITY` | > | `msdyn_unavailableonhandquantity` |

###  <a name="147"></a>CDS inventory on-hand requests (msdyn_inventoryonhandrequests)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`REQUESTID` | = | `msdyn_requestid` |
`PRODUCTNUMBER` | < | `msdyn_product.msdyn_productnumber` |
`ISATPCALCULATION` | << | `msdyn_isatpcalculation` |
`ORDERQUANTITY` | < | `msdyn_orderquantity` |
`INVENTORYSITEID` | < | `msdyn_inventorysite.msdyn_siteid` |
`INVENTORYWAREHOUSEID` | < | `msdyn_inventorywarehouse.msdyn_warehouseidentifier` |
`REFERENCENUMBER` | < | `msdyn_referencenumber` |
`LINECREATIONSEQUENCENUMBER` | < | `msdyn_linecreationsequencenumber` |

###  <a name="235"></a>CDS postal address history V2 (msdyn_postaladdresses)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`LOCATIONID` | = | `msdyn_postaladdresscollectionid.msdyn_location` |
`VALIDFROM` | = | `msdyn_validfrom` |
`VALIDTO` | = | `msdyn_validto` |
`DESCRIPTION` | = | `msdyn_name` |
`STREET` | = | `msdyn_street` |
`STREETNUMBER` | = | `msdyn_streetnumber` |
`CITY` | = | `msdyn_city` |
`STATE` | = | `msdyn_state` |
`COUNTRYREGIONID` | = | `msdyn_countryregionid` |
`ZIPCODE` | = | `msdyn_zipcode` |
`COUNTY` | = | `msdyn_county` |
`DISTRICTNAME` | = | `msdyn_district` |
`BUILDINGCOMPLIMENT` | = | `msdyn_buildingcompliment` |
`POSTBOX` | = | `msdyn_postbox` |

###  <a name="234"></a>CDS postal address locations (msdyn_postaladdresscollections)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DESCRIPTION` | = | `msdyn_description` |
`LOCATIONID` | = | `msdyn_location` |

###  <a name="181"></a>CDS purchase order line entity (msdyn_purchaseorderproducts)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`REQUESTEDDELIVERYDATE` | = | `msdyn_dateexpected` |
`LINEDESCRIPTION` | = | `msdyn_description` |
`LINENUMBER` | = | `msdyn_lineorder` |
`PRODUCTNUMBER` | = | `msdyn_product.msdyn_productnumber` |
`PURCHASEORDERNUMBER` | = | `msdyn_purchaseorder.msdyn_name` |
`ORDEREDPURCHASEQUANTITY` | = | `msdyn_quantity` |
`LINEAMOUNT` | > | `msdyn_lineamount` |
`PURCHASEPRICE` | > | `msdyn_unitcost` |
`BARCODE` | = | `msdyn_barcode` |
`CATCHWEIGHTUNITSYMBOL` | = | `msdyn_catchweightunitsymbol.msdyn_symbol` |
`CONFIRMEDSHIPPINGDATE` | = | `msdyn_confirmedshippingdate` |
`CUSTOMERREFERENCE` | = | `msdyn_customerreference` |
`CUSTOMERREQUISITIONNUMBER` | = | `msdyn_customerrequisitionnumber` |
`EXTERNALITEMNUMBER` | = | `msdyn_externalitemnumber` |
`ISPARTIALDELIVERYPREVENTED` | >< | `msdyn_ispartialdeliveryprevented` |
`LINEDISCOUNTAMOUNT` | > | `msdyn_linediscountamount` |
`LINEDISCOUNTPERCENTAGE` | > | `msdyn_linediscountpercentage` |
`ORDEREDCATCHWEIGHTQUANTITY` | = | `msdyn_orderedcatchweightquantity` |
`PURCHASEORDERLINESTATUS` | >> | `msdyn_purchaseorderlinestatus` |
`PURCHASEPRICEQUANTITY` | = | `msdyn_purchasepricequantity` |
`RECEIVINGSITEID` | = | `msdyn_receivingsiteid.msdyn_siteid` |
`REQUESTEDSHIPPINGDATE` | = | `msdyn_requestedshippingdate` |
`REQUESTERPERSONNELNUMBER` | = | `msdyn_requesterpersonnelnumber.cdm_workernumber` |
`PROCUREMENTPRODUCTCATEGORYNAME` | > | `msdyn_procurementproductcategory.msdyn_name` |
`PROCUREMENTPRODUCTCATEGORYHIERACHYNAME` | > | `msdyn_procurementproductcategory.msdyn_hierarchy.msdyn_name` |
`CURRENCYCODE` | > | `transactioncurrencyid.isocurrencycode` |
`CONFIRMEDDELIVERYDATE` | = | `msdyn_confirmeddeliverydate` |
`DELIVERYADDRESSCITY` | > | `msdyn_deliveryaddresscity` |
`DELIVERYADDRESSCOUNTRYREGIONID` | > | `msdyn_deliveryaddresscountryregionid` |
`DELIVERYADDRESSSTATEID` | > | `msdyn_deliveryaddressstate` |
`DELIVERYADDRESSSTREET` | > | `msdyn_deliveryaddressstreet` |
`DELIVERYADDRESSSTREETNUMBER` | > | `msdyn_deliveryaddressstreetnumber` |
`DELIVERYADDRESSZIPCODE` | > | `msdyn_deliveryaddresszipcode` |
`FORMATTEDDELVERYADDRESS` | > | `msdyn_formatteddeliveryaddress` |
`PURCHASEUNITSYMBOL` | = | `msdyn_unit.msdyn_symbol` |
`RECEIVINGWAREHOUSEID` | = | `msdyn_associatetowarehouse.msdyn_warehouseidentifier` |
`DELIVERYADDRESSDESCRIPTION` | > | `msdyn_deliveryaddressdescription` |
`DELIVERYADDRESSNAME` | > | `msdyn_deliveryaddressname` |

###  <a name="182"></a>CDS purchase order line soft deleted entity (msdyn_purchaseorderproducts)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`LINENUMBER` | > | `msdyn_lineorder` |
`PURCHASEORDERNUMBER` | > | `msdyn_purchaseorder.msdyn_name` |
`ISDELETED` | >> | `msdyn_issoftdeletedinscm` |

###  <a name="213"></a>CDS released distinct products (products)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PRODUCTNUMBER` | > | `msdyn_productnumber` |
`PRODUCTNAME` | > | `name` |
`PRODUCTDESCRIPTION` | > | `description` |
`ITEMNUMBER` | > | `msdyn_itemnumber` |
`CURRENCYCODE` | > | `transactioncurrencyid.isocurrencycode` |
`SALESUNITSYMBOL` | > | `defaultuomid.msdyn_symbol` |
`SALESPRICE` | > | `price` |
`UNITCOST` | > | `currentcost` |
`PRODUCTTYPE` | >> | `producttypecode` |
`SALESUNITDECIMALPRECISION` | >> | `quantitydecimal` | 0
`ISCATCHWEIGHTPRODUCT` | >> | `msdyn_iscatchweight` |
`ISSTOCKEDPRODUCT` | >> | `msdyn_isstockedproduct` |
`PRODUCTCOLORID` | > | `msdyn_productcolor.msdyn_productcolorname` |
`PRODUCTCONFIGURATIONID` | > | `msdyn_productconfiguration.msdyn_productconfiguration` |
`PRODUCTSIZEID` | > | `msdyn_productsize.msdyn_productsize` |
`PRODUCTSTYLEID` | > | `msdyn_productstyle.msdyn_productstyle` |
`FIELDSERVICEPRODUCTTYPE` | >> | `msdyn_fieldserviceproducttype` |

###  <a name="217"></a>CDS sales order headers (salesorders)

This template synchronizes data between Finance and Operations apps and Dataverse.

Reversed source filter: `msdyn_ordertype eq 192350000`

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`SALESORDERNUMBER` | = | `msdyn_salesordernumber` |
`ORDERINGCUSTOMERACCOUNTNUMBER` | = | `customerid.Account(accountnumber).Contact(msdyn_contactpersonid)` |
`CURRENCYCODE` | = | `transactioncurrencyid.isocurrencycode` |
`DELIVERYADDRESSCITY` | = | `shipto_city` |
`DELIVERYADDRESSCOUNTRYREGIONISOCODE` | >< | `shipto_country` |
`DELIVERYADDRESSSTREETNUMBER` | = | `shipto_line2` |
`DELIVERYADDRESSZIPCODE` | = | `shipto_postalcode` |
`DELIVERYADDRESSSTREET` | = | `shipto_line1` |
`DELIVERYADDRESSSTATEID` | = | `shipto_stateorprovince` |
`SALESORDERNAME` | > | `name` |
`INVOICEADDRESSCITY` | > | `billto_city` |
`INVOICEADDRESSSTREET` | > | `billto_line1` |
`INVOICEADDRESSSTREETNUMBER` | > | `billto_line2` |
`INVOICEADDRESSCOUNTRYREGIONISOCODE` | > | `billto_country` |
`INVOICEADDRESSSTATEID` | > | `billto_stateorprovince` |
`INVOICEADDRESSZIPCODE` | > | `billto_postalcode` |
`ORDERTOTALAMOUNT` | > | `totalamount` |
`TOTALDISCOUNTAMOUNT` | > | `discountamount` |
`ORDERTOTALTAXAMOUNT` | > | `totaltax` |
`ORDERTOTALCHARGESAMOUNT` | > | `freightamount` |
`AREPRICESINCLUDINGSALESTAX` | >< | `msdyn_arepricesincludingsalestax` |
`CONFIRMEDRECEIPTDATE` | = | `msdyn_confirmedreceiptdate` |
`CONFIRMEDSHIPPINGDATE` | = | `msdyn_confirmedshippingdate` |
`CONTACTPERSONID` | = | `msdyn_associatedcontact.msdyn_contactforpartynumber` |
`CUSTOMERREQUISITIONNUMBER` | = | `msdyn_customerrequisitionnumber` |
`DEFAULTSHIPPINGSITEID` | = | `msdyn_defaultshippingsite.msdyn_siteid` |
`DEFAULTSHIPPINGWAREHOUSEID` | = | `msdyn_defaultshippingwarehouse.msdyn_warehouseidentifier` |
`DELIVERYADDRESSCOUNTYID` | = | `msdyn_deliveryaddresscountyid` |
`DELIVERYADDRESSDESCRIPTION` | = | `msdyn_deliveryaddressdescription` |
`DELIVERYADDRESSDISTRICTNAME` | = | `msdyn_deliveryaddressdistrictname` |
`DELIVERYADDRESSDUNSNUMBER` | = | `msdyn_deliveryaddressdunsnumber` |
`DELIVERYADDRESSLATITUDE` | = | `msdyn_deliveryaddresslatitude` |
`DELIVERYADDRESSLOCATIONID` | = | `msdyn_deliveryaddresslocationid` |
`DELIVERYADDRESSLONGITUDE` | = | `msdyn_deliveryaddresslongitude` |
`DELIVERYADDRESSNAME` | = | `msdyn_deliveryaddressname` |
`DELIVERYADDRESSPOSTBOX` | = | `msdyn_deliveryaddresspostbox` |
`DELIVERYBUILDINGCOMPLIMENT` | = | `msdyn_deliverybuildingcompliment` |
`FORMATTEDDELVERYADDRESS` | > | `msdyn_formatteddeliveryaddress` |
`EMAIL` | = | `emailaddress` |
`FORMATTEDINVOICEADDRESS` | > | `msdyn_formattedinvoiceaddress` |
`INVOICEADDRESSCOUNTYID` | > | `msdyn_invoiceaddresscountyid` |
`INVOICEADDRESSDISTRICTNAME` | > | `msdyn_invoiceaddressdistrictname` |
`INVOICEADDRESSLATITUDE` | > | `msdyn_invoiceaddresslatitude` |
`INVOICEADDRESSLONGITUDE` | > | `msdyn_invoiceaddresslongitude` |
`INVOICEADDRESSPOSTBOX` | > | `msdyn_invoiceaddresspostbox` |
`INVOICEBUILDINGCOMPLIMENT` | > | `msdyn_invoicebuildingcompliment` |
`INVOICECUSTOMERACCOUNTNUMBER` | = | `msdyn_invoicecustomerid.Account(accountnumber).Contact(msdyn_contactpersonid)` |
`ISDELIVERYADDRESSORDERSPECIFIC` | >< | `msdyn_isdeliveryaddressorderspecific` |
`ISDELIVERYADDRESSPRIVATE` | >< | `msdyn_isdeliveryaddressprivate` |
`ISINVOICEADDRESSPRIVATE` | >> | `msdyn_isinvoiceaddressprivate` |
`ISONETIMECUSTOMER` | >< | `msdyn_isonetimecustomer` |
`ISSALESPROCESSINGSTOPPED` | >< | `msdyn_issalesprocessingstopped` |
`PAYMENTTERMSBASEDATE` | = | `msdyn_paymenttermsbasedate` |
`PAYMENTTERMSNAME` | = | `msdyn_paymentterms.msdyn_name` |
`PRICECUSTOMERGROUPCODE` | = | `msdyn_pricecustomergroup.msdyn_groupcode` |
`QUOTATIONNUMBER` | = | `msdyn_quotationnumber` |
`REQUESTEDRECEIPTDATE` | = | `msdyn_requestedreceiptdate` |
`REQUESTEDSHIPPINGDATE` | = | `requestdeliveryby` |
`SALESORDERPROMISINGMETHOD` | >< | `msdyn_salesorderpromisingmethod` |
`URL` | = | `msdyn_url` |
`SALESORDERPROCESSINGSTATUS` | >< | `msdyn_processingstatus` |
`LANGUAGEID` | >< | `msdyn_language` |
`CUSTOMERSORDERREFERENCE` | = | `msdyn_customersorderreference` |
`DELIVERYMODECODE` | = | `msdyn_deliverymode.msdyn_name` |
`DELIVERYTERMSCODE` | = | `msdyn_deliveryterms.msdyn_termscode` |
`SALESORDERORIGINCODE` | = | `msdyn_salesorderorigin.msdyn_origincode` |
`none` | >> | `msdyn_ordertype` | 192350000
`CURRENCYCODE` | > | `msdyn_isocurrencycode` |

###  <a name="216"></a>CDS sales order lines (salesorderdetails)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CURRENCYCODE` | > | `transactioncurrencyid.isocurrencycode` |
`DELIVERYADDRESSCITY` | = | `shipto_city` |
`DELIVERYADDRESSCOUNTRYREGIONISOCODE` | >< | `shipto_country` |
`DELIVERYADDRESSZIPCODE` | = | `shipto_postalcode` |
`DELIVERYADDRESSSTATEID` | = | `shipto_stateorprovince` |
`DELIVERYADDRESSSTREET` | = | `shipto_line1` |
`DELIVERYADDRESSSTREETNUMBER` | = | `shipto_line2` |
`LINEAMOUNT` | > | `extendedamount` |
`LINECREATIONSEQUENCENUMBER` | = | `sequencenumber` |
`ORDEREDSALESQUANTITY` | = | `quantity` |
`PRODUCTNAME` | = | `description` |
`PRODUCTNUMBER` | = | `productid.msdyn_productnumber` |
`SALESORDERNUMBER` | = | `salesorderid.msdyn_salesordernumber` |
`SALESUNITSYMBOL` | = | `uomid.msdyn_symbol` |
`TOTALDISCOUNTAMOUNT` | = | `manualdiscountamount` |
`TOTALTAXAMOUNT` | > | `tax` |
`SALESPRICE` | = | `priceperunit` |
`LINEAMOUNT` | > | `baseamount` |
`SALESPRODUCTCATEGORYNAME` | = | `msdyn_salesproductcategory.msdyn_name` |
`SALESPRODUCTCATEGORYHIERARCHYNAME` | > | `msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name` |
`ISDELIVERYADDRESSORDERSPECIFIC` | >< | `msdyn_isdeliveryaddressspecific` |
`ISDELIVERYADDRESSPRIVATE` | >< | `msdyn_isdeliveryaddressprivate` |
`ISLINESTOPPED` | >< | `msdyn_islinestopped` |
`ALLOWEDOVERDELIVERYPERCENTAGE` | = | `msdyn_allowedoverdeliverypercentage` |
`ALLOWEDUNDERDELIVERYPERCENTAGE` | = | `msdyn_allowedunderdeliverypercentage` |
`CONFIRMEDSHIPPINGDATE` | = | `msdyn_confirmedshippingdate` |
`CONFIRMEDRECEIPTDATE` | = | `msdyn_confirmedreceiptdate` |
`DELIVERYADDRESSCOUNTYID` | = | `msdyn_deliveryaddresscountyid` |
`DELIVERYADDRESSDESCRIPTION` | = | `msdyn_deliveryaddressdescription` |
`DELIVERYADDRESSDISTRICTNAME` | = | `msdyn_deliveryaddressdistrictname` |
`DELIVERYADDRESSDUNSNUMBER` | = | `msdyn_deliveryaddressdunsnumber` |
`DELIVERYADDRESSLATITUDE` | = | `msdyn_deliveryaddresslatitude` |
`DELIVERYADDRESSLOCATIONID` | = | `msdyn_deliveryaddresslocationid` |
`DELIVERYADDRESSLONGITUDE` | = | `msdyn_deliveryaddresslongitude` |
`DELIVERYADDRESSNAME` | = | `msdyn_deliveryaddressname` |
`DELIVERYADDRESSPOSTBOX` | = | `msdyn_deliveryaddresspostbox` |
`DELIVERYBUILDINGCOMPLIMENT` | = | `msdyn_deliverybuildingcompliment` |
`EXTERNALITEMNUMBER` | = | `msdyn_externalitemnumber` |
`FIXEDPRICECHARGES` | = | `msdyn_fixedpricecharges` |
`FORMATTEDDELIVERYADDRESS` | = | `msdyn_formatteddeliveryaddress` |
`LINEDESCRIPTION` | = | `msdyn_linedescription` |
`LINEDISCOUNTAMOUNT` | = | `msdyn_linediscountamount` |
`LINEDISCOUNTPERCENTAGE` | = | `msdyn_linediscountpercentage` |
`MULTILINEDISCOUNTAMOUNT` | = | `msdyn_multilinediscountamount` |
`MULTILINEDISCOUNTPERCENTAGE` | = | `msdyn_multilinediscountpercentage` |
`REQUESTEDRECEIPTDATE` | = | `msdyn_requestedreceiptdate` |
`REQUESTEDSHIPPINGDATE` | = | `requestdeliveryby` |
`SALESORDERLINESTATUS` | >> | `msdyn_linestatus` |
`SALESORDERPROMISINGMETHOD` | >< | `msdyn_salesorderpromisingmethod` |
`SALESPRICEQUANTITY` | = | `msdyn_salespricequantity` |
`SHIPPINGSITEID` | = | `msdyn_shippingsite.msdyn_siteid` |
`SHIPPINGWAREHOUSEID` | = | `msdyn_shippingwarehouse.msdyn_warehouseidentifier` |
`none` | >> | `ispriceoverridden` | true
`TOTALCHARGESAMOUNT` | > | `msdyn_totalchargesamount` |
`DELIVERYMODECODE` | = | `msdyn_deliverymode.msdyn_name` |
`DELIVERYTERMSID` | = | `msdyn_deliveryterms.msdyn_termscode` |

###  <a name="215"></a>CDS sales quotation header (quotes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Reversed source filter: `msdyn_ordertype eq 192350000 and statecode eq 0`

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`SALESQUOTATIONNUMBER` | = | `msdyn_quotenumber` |
`REQUESTINGCUSTOMERACCOUNTNUMBER` | = | `customerid.Account(accountnumber).Contact(msdyn_contactpersonid)` |
`CURRENCYCODE` | = | `transactioncurrencyid.isocurrencycode` |
`CUSTOMERSREFERENCE` | = | `msdyn_customersreference` |
`DELIVERYADDRESSCITY` | = | `shipto_city` |
`DELIVERYADDRESSCOUNTRYREGIONISOCODE` | >< | `shipto_country` |
`DELIVERYADDRESSSTREETNUMBER` | = | `shipto_line2` |
`DELIVERYADDRESSZIPCODE` | = | `shipto_postalcode` |
`DELIVERYADDRESSSTREET` | = | `shipto_line1` |
`DELIVERYADDRESSSTATEID` | = | `shipto_stateorprovince` |
`SALESQUOTATIONNAME` | = | `name` |
`INVOICEADDRESSCITY` | > | `billto_city` |
`INVOICEADDRESSSTREET` | > | `billto_line1` |
`INVOICEADDRESSSTREETNUMBER` | > | `billto_line2` |
`INVOICEADDRESSCOUNTRYREGIONISOCODE` | > | `billto_country` |
`INVOICEADDRESSSTATEID` | > | `billto_stateorprovince` |
`INVOICEADDRESSZIPCODE` | > | `billto_postalcode` |
`QUOTATIONTOTALAMOUNT` | > | `totalamount` |
`TOTALDISCOUNTAMOUNT` | > | `discountamount` |
`QUOTATIONTOTALTAXAMOUNT` | > | `totaltax` |
`QUOTATIONTOTALCHARGESAMOUNT` | > | `freightamount` |
`AREPRICESINCLUDINGSALESTAX` | >< | `msdyn_arepricesincludingsalestax` |
`CONTACTPERSONID` | = | `msdyn_associatedcontact.msdyn_contactforpartynumber` |
`CUSTOMERREQUISITIONNUMBER` | = | `msdyn_customerrequisitionnumber` |
`DEFAULTSHIPPINGSITEID` | = | `msdyn_defaultshippingsite.msdyn_siteid` |
`DEFAULTSHIPPINGWAREHOUSEID` | = | `msdyn_defaultshippingwarehouse.msdyn_warehouseidentifier` |
`DELIVERYADDRESSCOUNTYID` | = | `msdyn_deliveryaddresscountyid` |
`DELIVERYADDRESSDESCRIPTION` | = | `msdyn_deliveryaddressdescription` |
`DELIVERYADDRESSDISTRICTNAME` | = | `msdyn_deliveryaddressdistrictname` |
`DELIVERYADDRESSDUNSNUMBER` | = | `msdyn_deliveryaddressdunsnumber` |
`DELIVERYADDRESSLATITUDE` | = | `msdyn_deliveryaddresslatitude` |
`DELIVERYADDRESSLOCATIONID` | = | `msdyn_deliveryaddresslocationid` |
`DELIVERYADDRESSLONGITUDE` | = | `msdyn_deliveryaddresslongitude` |
`DELIVERYADDRESSNAME` | = | `msdyn_deliveryaddressname` |
`DELIVERYADDRESSPOSTBOX` | = | `msdyn_deliveryaddresspostbox` |
`DELIVERYBUILDINGCOMPLIMENT` | = | `msdyn_deliverybuildingcompliment` |
`FORMATTEDDELIVERYADDRESS` | > | `msdyn_formatteddeliveryaddress` |
`FORMATTEDINVOICEADDRESS` | > | `msdyn_formattedinvoiceaddress` |
`GENERATEDSALESORDERNUMBER` | = | `msdyn_generatedsalesordernumber.msdyn_salesordernumber` |
`INVOICEADDRESSCOUNTRYREGIONID` | > | `msdyn_invoiceaddresscountryregionid` |
`INVOICEADDRESSCOUNTYID` | > | `msdyn_invoiceaddresscountyid` |
`INVOICEADDRESSDISTRICTNAME` | > | `msdyn_invoiceaddressdistrictname` |
`INVOICEADDRESSLATITUDE` | > | `msdyn_invoiceaddresslatitude` |
`INVOICEADDRESSLONGITUDE` | > | `msdyn_invoiceaddresslongitude` |
`INVOICEADDRESSPOSTBOX` | > | `msdyn_invoiceaddresspostbox` |
`INVOICEBUILDINGCOMPLIMENT` | > | `msdyn_invoicebuildingcompliment` |
`INVOICECUSTOMERACCOUNTNUMBER` | = | `msdyn_invoicecustomerid.Account(accountnumber).Contact(msdyn_contactpersonid)` |
`ISDELIVERYADDRESSORDERSPECIFIC` | >< | `msdyn_isdeliveryaddressorderspecific` |
`ISDELIVERYADDRESSPRIVATE` | >< | `msdyn_isdeliveryaddressprivate` |
`ISINVOICEADDRESSPRIVATE` | >> | `msdyn_isinvoiceaddressprivate` |
`LANGUAGEID` | >< | `msdyn_language` |
`PAYMENTTERMSNAME` | = | `msdyn_paymentterms.msdyn_name` |
`PRICECUSTOMERGROUPCODE` | = | `msdyn_pricecustomergroup.msdyn_groupcode` |
`RECEIPTDATEREQUESTED` | = | `msdyn_requestedreceiptdate` |
`REQUESTEDSHIPPINGDATE` | = | `requestdeliveryby` |
`SALESORDERPROMISINGMETHOD` | >< | `msdyn_salesorderpromisingmethod` |
`SALESQUOTATIONCONFIRMATIONDATE` | = | `msdyn_salesquotationconfirmationdate` |
`SALESQUOTATIONEXPIRYDATE` | = | `msdyn_salesquotationexpirydate` |
`SALESQUOTATIONFOLLOWUPDATE` | = | `msdyn_salesquotationfollowupdate` |
`SALESQUOTATIONSTATUS` | >< | `msdyn_salesquotationstatus` |
`TOTALDISCOUNTPERCENTAGE` | = | `msdyn_totaldiscountpercentage` |
`URL` | = | `msdyn_url` |
`EMAIL` | = | `emailaddress` |
`none` | >> | `msdyn_ordertype` | 192350000
`CURRENCYCODE` | > | `msdyn_isocurrencycode` |
`OPERATINGUNITPARTYNUMBER` | = | `msdyn_operatingunit.msdyn_partynumber` |

###  <a name="214"></a>CDS sales quotation lines (quotedetails)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`ALLOWEDOVERDELIVERYPERCENTAGE` | = | `msdyn_allowedoverdeliverypercentage` |
`ALLOWEDUNDERDELIVERYPERCENTAGE` | = | `msdyn_allowedunderdeliverypercentage` |
`SALESQUOTATIONNUMBER` | = | `quoteid.msdyn_quotenumber` |
`LINECREATIONSEQUENCENUMBER` | = | `sequencenumber` |
`CURRENCYCODE` | > | `transactioncurrencyid.isocurrencycode` |
`DELIVERYADDRESSCITY` | = | `shipto_city` |
`DELIVERYADDRESSCOUNTRYREGIONISOCODE` | >< | `shipto_country` |
`DELIVERYADDRESSCOUNTYID` | = | `msdyn_deliveryaddresscountyid` |
`DELIVERYADDRESSDESCRIPTION` | = | `msdyn_deliveryaddressdescription` |
`DELIVERYADDRESSDISTRICTNAME` | = | `msdyn_deliveryaddressdistrictname` |
`DELIVERYADDRESSDUNSNUMBER` | = | `msdyn_deliveryaddressdunsnumber` |
`DELIVERYADDRESSLATITUDE` | = | `msdyn_deliveryaddresslatitude` |
`DELIVERYADDRESSLOCATIONID` | = | `msdyn_deliveryaddresslocationid` |
`DELIVERYADDRESSLONGITUDE` | = | `msdyn_deliveryaddresslongitude` |
`DELIVERYADDRESSNAME` | = | `msdyn_deliveryaddressname` |
`DELIVERYADDRESSPOSTBOX` | = | `msdyn_deliveryaddresspostbox` |
`DELIVERYADDRESSSTATEID` | = | `shipto_stateorprovince` |
`DELIVERYADDRESSSTREET` | = | `shipto_line1` |
`DELIVERYADDRESSSTREETNUMBER` | = | `shipto_line2` |
`DELIVERYADDRESSZIPCODE` | = | `shipto_postalcode` |
`DELIVERYBUILDINGCOMPLIMENT` | = | `msdyn_deliverybuildingcompliment` |
`EXTERNALITEMNUMBER` | = | `msdyn_externalitemnumber` |
`FIXEDPRICECHARGES` | = | `msdyn_fixedpricecharges` |
`FORMATTEDDELIVERYADDRESS` | = | `msdyn_formatteddeliveryaddress` |
`ISDELIVERYADDRESSPRIVATE` | >< | `msdyn_isdeliveryaddressprivate` |
`ISDELIVERYADDRESSORDERSPECIFIC` | >< | `msdyn_isdeliveryaddressspecific` |
`LINEAMOUNT` | > | `baseamount` |
`LINEAMOUNT` | > | `extendedamount` |
`LINEDESCRIPTION` | = | `msdyn_linedescription2` |
`LINEDISCOUNTAMOUNT` | = | `msdyn_linediscountamount` |
`LINEDISCOUNTPERCENTAGE` | = | `msdyn_linediscountpercentage` |
`MULTILINEDISCOUNTAMOUNT` | = | `msdyn_multilinediscountamount` |
`MULTILINEDISCOUNTPERCENTAGE` | = | `msdyn_multilinediscountpercentage` |
`PRODUCTNAME` | = | `description` |
`PRODUCTNUMBER` | = | `productid.msdyn_productnumber` |
`REQUESTEDRECEIPTDATE` | = | `msdyn_requestedreceiptdate` |
`REQUESTEDSALESQUANTITY` | = | `quantity` |
`REQUESTEDSHIPPINGDATE` | = | `requestdeliveryby` |
`SALESPRICE` | = | `priceperunit` |
`SALESPRICEQUANTITY` | = | `msdyn_salespricequantity` |
`SALESQUOTATIONPROMISINGMETHOD` | >< | `msdyn_salesquotationpromisingmethod` |
`SALESQUOTATIONSTATUS` | >< | `msdyn_salesquotationstatus` |
`SALESUNITSYMBOL` | = | `uomid.msdyn_symbol` |
`SHIPPINGSITEID` | = | `msdyn_shippingsite.msdyn_siteid` |
`SHIPPINGWAREHOUSEID` | = | `msdyn_shippingwarehouse.msdyn_warehouseidentifier` |
`TOTALCHARGESAMOUNT` | > | `msdyn_totalchargesamount` |
`TOTALDISCOUNTAMOUNT` | = | `manualdiscountamount` |
`TOTALTAXAMOUNT` | > | `tax` |
`SALESPRODUCTCATEGORYHIERARCHYNAME` | > | `msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name` |
`SALESPRODUCTCATEGORYNAME` | = | `msdyn_salesproductcategory.msdyn_name` |
`none` | >> | `ispriceoverridden` | true

###  <a name="121"></a>Chart of accounts (msdyn_chartofaccountses)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DESCRIPTION` | = | `msdyn_description` |
`MAINACCOUNTMASK` | = | `msdyn_mainaccountmask` |
`CHARTOFACCOUNTS` | = | `msdyn_name` |

###  <a name="170"></a>Colors (msdyn_productcolors)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`COLORID` | > | `msdyn_productcolorname` |

###  <a name="105"></a>Compensation job function (cdm_jobfunctions)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`JOBFUNCTIONID` | = | `cdm_name` |
`DESCRIPTION` | = | `cdm_description` |

###  <a name="108"></a>Compensation job type (cdm_jobtypes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`JOBTYPEID` | = | `cdm_name` |
`DESCRIPTION` | = | `cdm_description` |
`EXEMPTSTATUS` | >< | `cdm_exemptstatus` |

###  <a name="222"></a>Complimentary closings (msdyn_complimentaryclosings)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CLOSINGPHRASE` | = | `msdyn_closingphrase` |

###  <a name="171"></a>Configurations (msdyn_productconfigurations)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CONFIGURATIONID` | > | `msdyn_productconfiguration` |

###  <a name="223"></a>Contact person titles (msdyn_salescontactpersontitles)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`JOBTITLE` | = | `msdyn_jobtitle` |
`JOBTITLEALIAS` | = | `msdyn_jobtitlealias` |

###  <a name="221"></a>Contacts V2 (msdyn_contactforparties)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CONTACTPERSONID` | = | `msdyn_contactforpartynumber` |
`CONTACTPERSONPARTYNUMBER` | = | `msdyn_contactpartyid.msdyn_partynumber` |
`ASSOCIATEDPARTYNUMBER` | = | `msdyn_associatedpartyid.msdyn_partynumber` |
`EMPLOYMENTPROFESSION` | = | `msdyn_employmentprofession` |
`EMPLOYMENTDEPARTMENT` | = | `msdyn_employmentdepartment` |
`PRIMARYSALUTATIONPHRASE` | = | `msdyn_primarysalutationphrase.msdyn_salutationphrase` |
`ASSISTANTNAME` | = | `msdyn_assistantname` |
`ASSISTANTPHONENUMBER` | = | `msdyn_assistantphonenumber` |
`AVAILABLEFROMTIME` | = | `msdyn_availablefromtime` |
`AVAILABLETOTIME` | = | `msdyn_availabletotime` |
`CONTACTACTIVITYSENSITIVITYLEVEL` | >< | `msdyn_contactactivitysensitivitylevel` |
`CONTACTPERSONRESPONSIBLEPERSONNELNUMBER` | = | `msdyn_employeeresponsible.cdm_workernumber` |
`DECISIONMAKINGROLECODE` | = | `msdyn_decisionmakingrole.msdyn_rolename` |
`EMPLOYMENTCOMPUTERNETWORKNAME` | = | `msdyn_employmentcomputernetworkname` |
`EMPLOYMENTJOBFUNCTIONNAME` | = | `msdyn_employmentjobfunctionname` |
`EMPLOYMENTJOBTITLE` | = | `msdyn_jobtitle.msdyn_jobtitlealias` |
`EMPLOYMENTOFFICELOCATION` | = | `msdyn_employmentofficelocation` |
`GOVERNMENTIDENTIFICATIONNUMBER` | = | `msdyn_governmentidentificationnumber` |
`HASREQUESTEDINTERNETACCESS` | >< | `msdyn_hasrequestedinternetaccess` |
`IDENTITYCARDNUMBER` | = | `msdyn_identitycardnumber` |
`ISRECEIVINGDIRECTMAIL` | >< | `msdyn_isreceivingdirectmail` |
`ISVIP` | >< | `msdyn_isvip` |
`LOYALTYLEVELPHRASE` | = | `msdyn_loyaltylevelphrase.msdyn_levelphrase` |
`MANAGERCONTACTPERSONID` | = | `msdyn_parentcontactforpartyid.msdyn_contactforpartynumber` |
`MICROSOFTOUTLOOKCATEGORIES` | = | `msdyn_microsoftoutlookcategories` |
`MILEAGEDISTANCE` | = | `msdyn_mileagedistance` |
`NOTES` | = | `msdyn_notes` |
`ORGANIZATIONIDENTIFICATIONNUMBER` | = | `msdyn_organizationidentificationnumber` |
`PERSONALCHARACTERTYPECODE` | = | `msdyn_personalcharactertypecode.msdyn_typename` |
`PRIMARYCOMPLIMENTARYCLOSINGPHRASE` | = | `msdyn_primarycomplimentaryclosingphrase.msdyn_closingphrase` |
`CONTACTINFORMATIONLANGUAGEID` | >< | `msdyn_nativelanguage` |
`SPOUSENAME` | = | `msdyn_spousename` |

###  <a name="218"></a>Currencies (transactioncurrencies)

This template synchronizes data between Finance and Operations apps and Dataverse.

Source filter: `((CURRENCYCODE != "999"))`

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CURRENCYCODE` | = | `isocurrencycode` |
`NAME` | = | `currencyname` |
`SYMBOL` | = | `currencysymbol` |
`none` | >> | `exchangerate` | 1.0000000000

###  <a name="230"></a>Customer Attachments (annotations)

This template synchronizes data between Finance and Operations apps and Dataverse.

Source filter: `((TypeId == "Note") || (TypeId == "URL"))`

Reversed source filter: `(objecttypecode eq 'account' or objecttypecode eq 'contact') and msdyn_relatedentityid ne null`

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DOCUMENTID` | = | `msdyn_notesid` |
`NAME` | = | `subject` |
`none` | >> | `objecttypecode` | account
`CUSTOMERACCOUNTNUMBER` | = | `msdyn_relatedentityid` |
`TYPEID` | << | `none` | Note
`NOTES` | = | `notetext` |
`RESTRICTION` | >< | `msdyn_restriction` |

###  <a name="126"></a>Customer groups (msdyn_customergroups)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CUSTOMERGROUPID` | = | `msdyn_groupid` |
`DESCRIPTION` | = | `msdyn_description` |
`ISSALESTAXINCLUDEDINPRICE` | >< | `msdyn_issalestaxincludedinprice` |
`PAYMENTTERMID` | = | `msdyn_paymenttermid.msdyn_name` |
`CLEARINGPERIODPAYMENTTERMNAME` | = | `msdyn_clearingperiodpaymenttermname.msdyn_name` |

###  <a name="146"></a>Customer hierarchies (msdyn_customerhierarchies)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CUSTOMERHIERARCHYID` | = | `msdyn_customerhierarchynumber` |
`NAME` | = | `msdyn_name` |
`ORGANIZATIONPARTYNUMBER` | = | `msdyn_organizationpartynumber.msdyn_partynumber` |
`PURPOSE` | >< | `msdyn_purpose` |

###  <a name="163"></a>Customer hierarchy nodes (msdyn_customerhierarchynodes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CUSTOMERHIERARCHYID` | = | `msdyn_customerhierarchynumber.msdyn_customerhierarchynumber` |
`NODEPARTYNUMBER` | = | `msdyn_nodepartynumber.msdyn_partynumber` |
`NODETYPE` | >< | `msdyn_nodetype` |
`ROLE` | >< | `msdyn_role` |

###  <a name="127"></a>Customer payment method (msdyn_customerpaymentmethods)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`NAME` | = | `msdyn_name` |
`ACCOUNTTYPE` | >< | `msdyn_accounttype` |
`DISCOUNTGRACEPERIODDAYS` | = | `msdyn_discountgraceperioddays` |
`BRIDGINGPOSTINGENABLED` | >< | `msdyn_bridgingpostingenabled` |
`ISSEPA` | >< | `msdyn_issepa` |
`LASTFILENUMBER` | = | `msdyn_lastfilenumber` |
`LASTFILENUMBERTODAY` | = | `msdyn_lastfilenumbertoday` |
`DESCRIPTION` | = | `msdyn_description` |
`PAYMENTTYPE` | >< | `msdyn_paymenttype` |
`CREATEANDDRAWBILLOFEXCHANGEDURINGINVOICEPOSTING` | >< | `msdyn_invoiceupdate` |
`PAYMENTSTATUS` | >< | `msdyn_paymentstatus` |
`SUMBYPERIOD` | >< | `msdyn_sumbyperiod` |
`ENABLEPOSTDATEDCHECKCLEARINGPOSTING` | >< | `msdyn_enablepostdatescheckclearingposting` |
`BILLOFEXCHANGEDRAFTTYPE` | >< | `msdyn_billofexchangedrafttype` |
`DIRECTDEBIT` | >< | `msdyn_directdebit` |

###  <a name="101"></a>Customers V3 (accounts)

This template synchronizes data between Finance and Operations apps and Dataverse.

Source filter: `((PartyType == "Organization"))`

Reversed source filter: `customertypecode eq 3`

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CUSTOMERACCOUNT` | = | `accountnumber` |
`CREDITLIMIT` | = | `creditlimit` |
`SALESCURRENCYCODE` | = | `transactioncurrencyid.isocurrencycode` |
`SALESMEMO` | = | `description` |
`CREDITLIMITISMANDATORY` | >< | `msdyn_creditlimitismandatory` |
`CREDITRATING` | = | `msdyn_creditrating` |
`CUSTOMERGROUPID` | = | `msdyn_customergroupid.msdyn_groupid` |
`IDENTIFICATIONNUMBER` | = | `msdyn_identificationnumber` |
`INVOICEACCOUNT` | = | `msdyn_billingaccount.accountnumber` |
`ISONETIMECUSTOMER` | >< | `msdyn_onetimecustomer` |
`ONHOLDSTATUS` | >< | `msdyn_onholdstatus` |
`PARTYCOUNTRY` | = | `msdyn_partycountry` |
`PARTYSTATE` | = | `msdyn_partystateprovince` |
`PAYMENTDAY` | = | `msdyn_paymentday.msdyn_name` |
`PAYMENTMETHOD` | = | `msdyn_customerpaymentmethod.msdyn_name` |
`PAYMENTSCHEDULE` | = | `msdyn_paymentschedule.msdyn_name` |
`PAYMENTTERMS` | = | `msdyn_paymentterm.msdyn_name` |
`PAYMENTTERMSBASEDAYS` | = | `msdyn_paymenttermsbasedays` |
`TAXEXEMPTNUMBER` | = | `msdyn_taxexemptnumber` |
`VENDORACCOUNT` | = | `msdyn_vendor.msdyn_vendoraccountnumber` |
`none` | >> | `customertypecode` | 3
`PARTYTYPE` | << | `none` | Organization
`PARTYNUMBER` | = | `msdyn_partyid.msdyn_partynumber` |
`CONTACTPERSONID` | = | `msdyn_primarycontact.msdyn_contactforpartynumber` |
`SALESTAXGROUP` | = | `msdyn_salestaxgroup.msdyn_name` |

###  <a name="116"></a>Customers V3 (contacts)

This template synchronizes data between Finance and Operations apps and Dataverse.

Source filter: `((PartyType == "Person"))`

Reversed source filter: `msdyn_sellable eq true  and msdyn_contactpersonid ne null`

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`none` | >> | `msdyn_sellable` | True
`PARTYTYPE` | << | `none` | Person
`PARTYNUMBER` | = | `msdyn_partyid.msdyn_partynumber` |
`CUSTOMERACCOUNT` | = | `msdyn_contactpersonid` |
`CUSTOMERGROUPID` | = | `msdyn_customergroupid.msdyn_groupid` |
`IDENTIFICATIONNUMBER` | = | `msdyn_identificationnumber` |
`PARTYCOUNTRY` | = | `msdyn_partycountry` |
`PARTYSTATE` | = | `msdyn_partystateprovince` |
`SALESCURRENCYCODE` | = | `transactioncurrencyid.isocurrencycode` |
`SALESMEMO` | = | `description` |
`PAYMENTDAY` | = | `msdyn_paymentday.msdyn_name` |
`PAYMENTSCHEDULE` | = | `msdyn_paymentschedule.msdyn_name` |
`PAYMENTMETHOD` | = | `msdyn_customerpaymentmethod.msdyn_name` |
`SALESTAXGROUP` | = | `msdyn_salestaxgroup.msdyn_name` |
`PAYMENTTERMS` | = | `msdyn_paymentterms.msdyn_name` |
`CONTACTPERSONID` | = | `msdyn_primarycontact.msdyn_contactforpartynumber` |

###  <a name="224"></a>Decision making roles (msdyn_decisionmakingroles)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`ROLEDESCRIPTION` | = | `msdyn_roledescription` |
`ROLENAME` | = | `msdyn_rolename` |

###  <a name="172"></a>Default order settings (msdyn_productdefaultordersettings)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`INVENTWAREHOUSEID` | = | `msdyn_inventorywarehouse.msdyn_warehouseidentifier` |
`INVENTORYSITEID` | = | `msdyn_inventorysite.msdyn_siteid` |
`INVENTORYATPDELAYEDDEMANDOFFSETDAYS` | = | `msdyn_inventoryatpdelayeddemandoffsetdays` |
`INVENTORYATPDELAYEDSUPPLYOFFSETDAYS` | = | `msdyn_inventoryatpdelayedsupplyoffsetdays` |
`ITEMNUMBER` | = | `msdyn_itemnumber.msdyn_itemnumber` |
`INVENTORYATPBACKWARDDEMANDTIMEFENCEDAYS` | = | `msdyn_inventoryatpbackwarddemandtimefencedays` |
`INVENTORYATPBACKWARDSUPPLYTIMEFENCEDAYS` | = | `msdyn_inventoryatpbackwardsupplytimefencedays` |
`INVENTORYATPTIMEFENCEDAYS` | = | `msdyn_inventoryatptimefencedays` |
`MAXIMUMINVENTORYORDERQUANTITY` | = | `msdyn_maximuminventoryorderquantity` |
`MAXIMUMPROCUREMENTORDERQUANTITY` | = | `msdyn_maximumprocurementorderquantity` |
`MAXIMUMSALESORDERQUANTITY` | = | `msdyn_maximumsalesorderquantity` |
`MINIMUMINVENTORYORDERQUANTITY` | = | `msdyn_minimuminventoryorderquantity` |
`MINIMUMPROCUREMENTORDERQUANTITY` | = | `msdyn_minimumprocurementorderquantity` |
`MINIMUMSALESORDERQUANTITY` | = | `msdyn_minimumsalesorderquantity` |
`STANDARDINVENTORYORDERQUANTITY` | = | `msdyn_standardinventoryorderquantity` |
`STANDARDPROCUREMENTORDERQUANTITY` | = | `msdyn_standardprocurementorderquantity` |
`STANDARDSALESORDERQUANTITY` | = | `msdyn_standardsalesorderquantity` |
`INVENTORYLEADTIMEDAYS` | = | `msdyn_inventoryleadtimedays` |
`INVENTORYQUANTITYMULTIPLES` | = | `msdyn_inventoryquantitymultiples` |
`PROCUREMENTQUANTITYMULTIPLES` | = | `msdyn_procurementquantitymultiples` |
`SALESQUANTITYMULTIPLES` | = | `msdyn_salesquantitymultiples` |
`PROCUREMENTSITEID` | = | `msdyn_procurementsite.msdyn_siteid` |
`PROCUREMENTLEADTIMEDAYS` | = | `msdyn_procurementleadtimedays` |
`SALESSITEID` | = | `msdyn_salessite.msdyn_siteid` |
`SALESATPDELAYEDDEMANDOFFSETDAYS` | = | `msdyn_salesatpdelayeddemandoffsetdays` |
`SALESATPDELAYEDSUPPLYOFFSETDAYS` | = | `msdyn_salesatpdelayedsupplyoffsetdays` |
`SALESATPBACKWARDDEMANDTIMEFENCEDAYS` | = | `msdyn_salesatpbackwarddemandtimefencedays` |
`SALESATPBACKWARDSUPPLYTIMEFENCEDAYS` | = | `msdyn_salesatpbackwardsupplytimefencedays` |
`SALESATPTIMEFENCEDAYS` | = | `msdyn_salesatptimefencedays` |
`SALESLEADTIMEDAYS` | = | `msdyn_salesleadtimedays` |
`PROCUREMENTWAREHOUSEID` | = | `msdyn_procurementwarehouse.msdyn_warehouseidentifier` |
`SALESWAREHOUSEID` | = | `msdyn_saleswarehouse.msdyn_warehouseidentifier` |
`AREINVENTORYORDERPROMISINGDEFAULTSOVERRIDDEN` | >< | `msdyn_areinventoryorderdefaultsoverridden` |
`INVENTORYORDERPROMISINGMETHOD` | >< | `msdyn_inventoryorderpromisingmethod` |
`ISINVENTORYATPINCLUDINGPLANNEDORDERS` | >< | `msdyn_isinventoryatpincludingplannedorders` |
`ISINVENTORYUSINGWORKINGDAYS` | >< | `msdyn_isinventoryusingworkingdays` |
`ISINVENTORYSITEMANDATORY` | >< | `msdyn_isinventorysitemandatory` |
`ISINVENTORYPROCESSINGSTOPPED` | >< | `msdyn_isinventoryprocessingstopped` |
`ISPROCUREMENTUSINGWORKINGDAYS` | >< | `msdyn_isprocurementusingworkingdays` |
`ISPROCUREMENTSITEMANDATORY` | >< | `msdyn_isprocurementsitemandatory` |
`ISPROCUREMENTPROCESSINGSTOPPED` | >< | `msdyn_isprocurementprocessingstopped` |
`ARESALESORDERPROMISINGDEFAULTSOVERRIDDEN` | >< | `msdyn_aresalesorderdefaultsoverridden` |
`SALESORDERPROMISINGMETHOD` | >< | `msdyn_salesorderpromisingmethod` |
`ISSALESATPINCLUDINGPLANNEDORDERS` | >< | `msdyn_issalesatpincludingplannedorders` |
`ISSALESSITEMANDATORY` | >< | `msdyn_issalessitemandatory` |
`ISSALESLEADTIMEOVERRIDDEN` | >< | `msdyn_issalesleadtimeoverridden` |
`ISSALESPROCESSINGSTOPPED` | >< | `msdyn_issalesprocessingstopped` |
`ISINVENTORYWAREHOUSEMANDATORY` | >< | `msdyn_isinventorywarehousemandatory` |
`ISPROCUREMENTWAREHOUSEMANDATORY` | >< | `msdyn_isprocurementwarehousemandatory` |
`ISSALESWAREHOUSEMANDATORY` | >< | `msdyn_issaleswarehousemandatory` |

###  <a name="225"></a>Employment job functions (msdyn_employmentjobfunctions)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`FUNCTIONDESCRIPTION` | = | `msdyn_functiondescription` |
`FUNCTIONNAME` | = | `msdyn_functionname` |

###  <a name="104"></a>Employment per company (cdm_employments)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`EMPLOYMENTENDDATE` | = | `cdm_employmentenddate` |
`PERSONNELNUMBER` | = | `cdm_workerid.cdm_workernumber` |
`EMPLOYMENTSTARTDATE` | = | `cdm_employmentstartdate` |
`WORKERTYPE` | >> | `cdm_workertype` |

###  <a name="103"></a>Ethnic origins (cdm_ethnicorigins)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`ETHNICORIGINID` | = | `cdm_name` |
`DESCRIPTION` | = | `cdm_description` |

###  <a name="122"></a>Exchange rate currency pair (msdyn_currencyexchangeratepairs)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`EXCHANGERATEDISPLAYFACTOR` | >< | `msdyn_displayfactor` |
`EXCHANGERATETYPENAME` | = | `msdyn_currencyexchangeratetypeid.msdyn_name` |
`FROMCURRENCYCODE` | = | `msdyn_fromtransactioncurrencyid.isocurrencycode` |
`TOCURRENCYCODE` | = | `msdyn_totransactioncurrencyid.isocurrencycode` |

###  <a name="129"></a>Exchange rate type (msdyn_exchangeratetypes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`NAME` | = | `msdyn_name` |
`DESCRIPTION` | = | `msdyn_description` |

###  <a name="130"></a>Financial dimension format (msdyn_financialdimensionformats)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DIMENSIONFORMATNAME` | = | `msdyn_dimensionformatname` |
`DIMENSIONFORMATTYPE` | >< | `msdyn_dimensionformattype` |
`FINANCIALDIMENSIONFORMAT` | = | `msdyn_financialdimensionformat` |
`ISACTIVE` | >< | `msdyn_isactive` |

###  <a name="128"></a>Financial dimensions (msdyn_dimensionattributes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DIMENSIONNAME` | = | `msdyn_dimensionname` |
`COPYVALUESONCREATE` | >< | `msdyn_copyvaluesoncreate` |
`REPORTCOLUMNNAME` | = | `msdyn_reportcolumnname` |
`GIVEDERIVEDDIMENSIONSPRECEDENCE` | >< | `msdyn_givederiveddimensionsprecedence` |
`UseValuesFrom` | = | `msdyn_usevaluesfrom` |
`DimensionValueMask` | = | `msdyn_dimensionvaluemask` |

###  <a name="132"></a>Fiscal calendar integration entity (msdyn_fiscalcalendars)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CALENDARID` | = | `msdyn_calendar` |
`DESCRIPTION` | = | `msdyn_description` |

###  <a name="131"></a>Fiscal calendar period (msdyn_fiscalcalendarperiods)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`COMMENTS` | = | `msdyn_comments` |
`ENDDATE` | = | `msdyn_enddate` |
`MONTH` | >< | `msdyn_month` |
`CALENDAR` | = | `msdyn_fiscalcalendar.msdyn_calendar` |
`QUARTER` | >< | `msdyn_quarter` |
`SHORTNAME` | = | `msdyn_shortname` |
`STARTDATE` | = | `msdyn_startdate` |
`TYPE` | >< | `msdyn_fiscalperiodtype` |
`PERIODNAME` | = | `msdyn_periodname` |
`FISCALYEAR` | = | `msdyn_fiscalcalendaryear.msdyn_name` |
`CALENDAR` | = | `msdyn_fiscalcalendaryear.msdyn_fiscalcalendarname` |

###  <a name="133"></a>Fiscal calendar year integration entity (msdyn_fiscalcalendaryears)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`FISCALCALENDAR_CALENDARID` | = | `msdyn_fiscalcalendarname` |
`NAME` | = | `msdyn_name` |
`STARTDATE` | = | `msdyn_startdate` |
`ENDDATE` | = | `msdyn_enddate` |
`FISCALCALENDAR_CALENDARID` | = | `msdyn_calendar.msdyn_calendar` |

###  <a name="203"></a>Inventory aisle (msdyn_warehouseaisles)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`AISLEID` | = | `msdyn_aisleid` |
`AISLENUMBER` | = | `msdyn_aislenumber` |
`WAREHOUSEID` | = | `msdyn_warehouse.msdyn_warehouseidentifier` |
`AISLENAME` | = | `msdyn_aislename` |
`MANUALSTARTINGSORTORDERCODE` | = | `msdyn_manualstartingsortordercode` |
`ISSORTORDERCODEASSIGNEDDESCENDING` | >< | `msdyn_issortordercodeassigneddescending` |

###  <a name="196"></a>Item sales tax group (msdyn_taxitemgroups)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`TAXITEMGROUP` | = | `msdyn_name` |
`NAME` | = | `msdyn_description` |

###  <a name="107"></a>Jobs (cdm_jobs)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`JOBID` | = | `cdm_name` |
`MAXIMUMNUMBEROFPOSITIONS` | = | `cdm_maximumnumberofpositions` |
`ALLOWUNLIMITEDPOSITIONS` | >< | `cdm_allowunlimitedpositions` |
`DESCRIPTION` | = | `cdm_description` |
`JOBDESCRIPTION` | = | `cdm_jobdescription` |
`JOBTYPEID` | = | `cdm_jobtypeid.cdm_name` |
`FUNCTIONID` | = | `cdm_jobfunctionid.cdm_name` |
`EFFECTIVE` | = | `cdm_validfrom` |
`EXPIRATION` | = | `cdm_validto` |
`FULLTIMEEQUIVALENT` | = | `cdm_defaultfulltimeequivalent` |

###  <a name="109"></a>Language codes (cdm_languages)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`LANGUAGECODEID` | = | `cdm_name` |
`DESCRIPTION` | = | `cdm_description` |

###  <a name="148"></a>Ledger (msdyn_ledgers)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`LEGALENTITYID` | > | `msdyn_company.cdm_companycode` |
`DESCRIPTION` | > | `msdyn_description` |
`ACCOUNTINGCURRENCY` | > | `msdyn_accountingcurrency.isocurrencycode` |
`ISBUDGETCONTROLENABLED` | >> | `msdyn_isbudgetcontrolenabled` |
`NAME` | > | `msdyn_name` |
`REPORTINGCURRENCY` | > | `msdyn_reportingcurrency.isocurrencycode` |
`BUDGETEXCHANGERATETYPE` | > | `msdyn_budgetexchangeratetype.msdyn_name` |
`CHARTOFACCOUNTS` | > | `msdyn_chartofaccounts.msdyn_name` |
`EXCHANGERATETYPE` | > | `msdyn_exchangeratetype.msdyn_name` |
`FISCALCALENDAR` | > | `msdyn_fiscalcalendar.msdyn_calendar` |
`REPORTINGCURRENCYEXCHANGERATETYPE` | > | `msdyn_reportingcurrencyexchangeratetype.msdyn_name` |

###  <a name="102"></a>Legal entities (cdm_companies)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`NAME` | > | `cdm_name` |
`LEGALENTITYID` | > | `cdm_companycode` |

###  <a name="142"></a>Legal entities (msdyn_internalorganizations)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`NAMEALIAS` | > | `msdyn_namealias` |
`LANGUAGEID` | > | `msdyn_languageid` |
`NAME` | > | `msdyn_name` |
`PARTYNUMBER` | > | `msdyn_partynumber` |
`none` | >> | `msdyn_type` | 806380000
`LEGALENTITYID` | > | `msdyn_companycode` |

###  <a name="149"></a>Loyalty card (msdyn_loyaltycards)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CARDNUMBER` | = | `msdyn_cardnumber` |
`CARDTENDERTYPE` | >< | `msdyn_cardtendertype` |
`PARTYNUMBER` | = | `msdyn_partynumber` |
`REPLACEMENTCARDNUMBER` | > | `msdyn_replacementcardnumber` |
`OMOPERATINGUNITNUMBER` | = | `msdyn_operatingunitnumber` |
`LOYALTYENROLLMENTDATE` | = | `msdyn_enrollmentdate` |
`LOYALTYENROLLMENTDATELOCAL` | = | `msdyn_effectivedate` |

###  <a name="226"></a>Loyalty levels (msdyn_loyaltylevels)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`LEVELPHRASE` | = | `msdyn_levelphrase` |
`LEVELDESCRIPTION` | = | `msdyn_description` |

###  <a name="150"></a>Loyalty reward points (msdyn_loyaltyrewardpoints)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`EXPIRATIONTIMEUNIT` | >< | `msdyn_expirationtimeunit` |
`EXPIRATIONTIMEVALUE` | = | `msdyn_expirationtimevalue` |
`REDEEMABLE` | >< | `msdyn_redeemable` |
`REDEEMRANKING` | = | `msdyn_redeemranking` |
`REWARDPOINTCURRENCY` | = | `msdyn_rewardpointcurrency.isocurrencycode` |
`REWARDPOINTID` | = | `msdyn_rewardpointid` |
`REWARDPOINTTYPE` | >< | `msdyn_rewardpointtype` |
`MAXIMUMLOYALTYREWARDPOINTS` | = | `msdyn_maximumloyaltyrewardpoints` |
`VESTINGTIMEUNIT` | >< | `msdyn_vestingtimeunit` |
`VESTINGTIMEVALUE` | = | `msdyn_vestingtimevalue` |

###  <a name="152"></a>Main account (msdyn_mainaccounts)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`MAINACCOUNTID` | = | `msdyn_accountnumber` |
`CHARTOFACCOUNTS` | = | `msdyn_chartofaccounts.msdyn_name` |
`NAME` | = | `msdyn_name` |
`BALANCECONTROL` | >< | `msdyn_balancecontrol` |
`EXCHANGEADJUSTMENTRATETYPE` | = | `msdyn_exchangeadjustmentratetype.msdyn_name` |
`CLOSING` | >< | `msdyn_closing` |
`REPORTINGEXCHANGEADJUSTMENTRATETYPE` | = | `msdyn_reportingexchangeadjustmentratetype.msdyn_name` |
`DEBITCREDITREQUIREMENT` | >< | `msdyn_debitcreditrequirement` |
`FINANCIALREPORTINGEXCHANGERATETYPE` | = | `msdyn_financialreportingexchangeratetype.msdyn_name` |
`FOREIGNCURRENCYREVALUATION` | >< | `msdyn_foreigncurrencyrevaluation` |
`MAINACCOUNTCATEGORY` | = | `msdyn_mainaccountcategoryname` |
`MANDATORYPAYMENTREFERENCE` | >< | `msdyn_mandatorypaymentreference` |
`MONETARY` | >< | `msdyn_monetary` |
`OFFSETACCOUNTDISPLAYVALUE` | = | `msdyn_offsetaccount` |
`POSTINGTYPE` | >< | `msdyn_postingtype` |
`SRUCODE` | = | `msdyn_srucode` |
`VALIDATECURRENCY` | >< | `msdyn_validatecurrencycode` |
`VALIDATEUSER` | >< | `msdyn_validateuser` |
`DEBITCREDITDEFAULT` | >< | `msdyn_debitcreditdefault` |
`DEFAULTCURRENCY` | = | `msdyn_defaultcurrency.isocurrencycode` |
`MAINACCOUNTTYPE` | >< | `msdyn_mainaccounttype` |
`FINANCIALREPORTINGCURRENCYTRANSLATIONTYPE` | >< | `msdyn_financialreportingcurrencytrantype` |
`USER` | = | `msdyn_user` |
`VALIDATEPOSTINGTYPE` | >< | `msdyn_validateposting` |

###  <a name="151"></a>Main account categories (msdyn_mainaccountcategories)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`MAINACCOUNTCATEGORY` | = | `msdyn_mainaccountcategory` |
`REFERENCEID` | = | `msdyn_referenceid` |
`DESCRIPTION` | = | `msdyn_description` |
`DISPLAYORDER` | = | `msdyn_displayorder` |
`CLOSED` | >< | `msdyn_closed` |
`MAINACCOUNTTYPE` | >< | `msdyn_mainaccounttypevalue` |

###  <a name="212"></a>Mixed reality guides entity (msmrw_guides)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`INTEGRATIONKEY` | < | `msmrw_integrationkey` |
`NAME` | < | `msmrw_name` |
`SCHEMAVERSION` | < | `msmrw_schemaversion` |
`GUIDEID` | < | `msmrw_guideid` |
`CREATEDON` | < | `createdon` |
`LASTMODIFIEDON` | < | `modifiedon` |

###  <a name="192"></a>Modes of delivery (msdyn_shipvias)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`MODECODE` | = | `msdyn_name` |
`MODEDESCRIPTION` | = | `msdyn_description` |

###  <a name="155"></a>Name affixes (msdyn_nameaffixes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`AFFIX` | = | `msdyn_affix` |
`TYPE` | >< | `msdyn_affixtype` |
`DESCRIPTION` | = | `msdyn_description` |

###  <a name="143"></a>Operating unit (msdyn_internalorganizations)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`LANGUAGEID` | > | `msdyn_languageid` |
`NAMEALIAS` | > | `msdyn_namealias` |
`NAME` | > | `msdyn_name` |
`PARTYNUMBER` | > | `msdyn_partynumber` |
`OPERATINGUNITTYPE` | >> | `msdyn_type` |

###  <a name="139"></a>Organization hierarchy - published (msdyn_internalorganizationhierarchies)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`VALIDTO` | > | `msdyn_validto` |
`VALIDFROM` | > | `msdyn_validfrom` |
`HIERARCHYTYPE` | > | `msdyn_hierarchytypename` |
`PARENTORGANIZATIONPARTYNUMBER` | > | `msdyn_parentpartyid` |
`CHILDORGANIZATIONPARTYNUMBER` | > | `msdyn_childpartyid` |
`HIERARCHYTYPE` | > | `msdyn_hierarchytypeid.msdyn_name` |
`CHILDORGANIZATIONPARTYNUMBER` | > | `msdyn_childid.msdyn_partynumber` |
`PARENTORGANIZATIONPARTYNUMBER` | > | `msdyn_parentid.msdyn_partynumber` |

###  <a name="140"></a>Organization hierarchy purposes (msdyn_internalorganizationhierarchypurposes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`HIERARCHYTYPE` | > | `msdyn_hierarchypurposetypename` |
`HIERARCHYTYPE` | > | `msdyn_hierarchytype.msdyn_name` |
`HIERARCHYPURPOSE` | >> | `msdyn_hierarchypurpose` |
`IMMUTABLE` | >> | `msdyn_immutable` |
`SETASDEFAULT` | >> | `msdyn_setasdefault` |

###  <a name="141"></a>Organization hierarchy type (msdyn_internalorganizationhierarchytypes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`NAME` | > | `msdyn_name` |

###  <a name="236"></a>Party contacts V3 (msdyn_partyelectronicaddresses)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`COUNTRYREGIONCODE` | = | `msdyn_internationalcallingcode` |
`DESCRIPTION` | = | `msdyn_description` |
`ELECTRONICADDRESSID` | = | `msdyn_electronicaddressnumber` |
`PARTYNUMBER` | = | `msdyn_partyid.msdyn_partynumber` |
`LOCATOR` | = | `msdyn_locator` |
`LOCATOREXTENSION` | = | `msdyn_locatorextension` |
`ISINSTANTMESSAGE` | >< | `msdyn_isinstantmessage` |
`ISMOBILEPHONE` | >< | `msdyn_ismobile` |
`ISPRIMARY` | >< | `msdyn_isprimary` |
`ISPRIVATE` | >< | `msdyn_isprivate` |
`PURPOSE` | = | `msdyn_purpose` |
`TYPE` | >< | `msdyn_type` |

###  <a name="157"></a>Payment day lines CDS V2 (msdyn_paymentdaylines)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`NAME` | = | `msdyn_paymentday.msdyn_name` |
`LINENUMBER` | = | `msdyn_linenumber` |
`FREQUENCY` | >< | `msdyn_frequency` |
`DAYOFWEEK` | >< | `msdyn_dayofweek` |
`DAYOFMONTH` | = | `msdyn_dayofmonth` |

###  <a name="158"></a>Payment days CDS (msdyn_paymentdays)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`NAME` | = | `msdyn_name` |
`DESCRIPTION` | = | `msdyn_description` |

###  <a name="160"></a>Payment schedule (msdyn_paymentschedules)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`NAME` | = | `msdyn_name` |
`DESCRIPTION` | = | `msdyn_description` |
`ALLOCATIONMETHOD` | >< | `msdyn_allocationmethod` |
`PAYMENTFREQUENCYUNITS` | >< | `msdyn_paymentfrequencyunit` |
`PAYMENTFREQUENCY` | = | `msdyn_paymentfrequency` |
`NUMBEROFPAYMENTS` | = | `msdyn_numberofpayments` |
`FIXEDPAYMENTAMOUNT` | = | `msdyn_fixedpaymentamount` |
`MINIMUMPAYMENTAMOUNT` | = | `msdyn_minimumpaymentamount` |
`SALESTAXALLOCATIONMETHOD` | >< | `msdyn_salestaxallocationmethod` |
`NOTES` | = | `msdyn_note` |

###  <a name="159"></a>Payment schedule lines (msdyn_paymentschedulelines)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PAYMENTSCHEDULENAME` | = | `msdyn_paymentschedule.msdyn_name` |
`LINENUMBER` | = | `msdyn_linenumber` |
`PERIODSAFTERDUEDATE` | = | `msdyn_periodsafterduedate` |
`PERCENTORAMOUNT` | >< | `msdyn_percentoramount` |
`PERCENTORAMOUNTVALUE` | = | `msdyn_percentoramountvalue` |

###  <a name="227"></a>Personal character types (msdyn_personalcharactertypes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`TYPEDESCRIPTION` | = | `msdyn_typedescription` |
`TYPENAME` | = | `msdyn_typename` |

###  <a name="110"></a>Position type (cdm_positiontypes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`POSITIONTYPEID` | = | `cdm_name` |
`DESCRIPTION` | = | `cdm_description` |
`CLASSIFICATION` | >< | `cdm_classification` |

###  <a name="111"></a>Position worker assignments (cdm_positionworkerassignmentmaps)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PERSONNELNUMBER` | = | `cdm_workerid.cdm_workernumber` |
`POSITIONID` | = | `cdm_jobpositionid.cdm_jobpositionnumber` |
`VALIDFROM` | = | `cdm_validfrom` |
`VALIDTO` | = | `cdm_validto` |

###  <a name="106"></a>Positions V2 (cdm_jobpositions)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`POSITIONID` | = | `cdm_jobpositionnumber` |
`DESCRIPTION` | = | `cdm_description` |
`ACTIVATION` | = | `cdm_activation` |
`AVAILABLEFORASSIGNMENT` | = | `cdm_availableforassignment` |
`FULLTIMEEQUIVALENT` | = | `cdm_fulltimeequivalent` |
`DETAILEFFECTIVE` | = | `cdm_validfrom` |
`DETAILEXPIRATION` | = | `cdm_validto` |
`RETIREMENT` | = | `cdm_retirement` |
`POSITIONTYPEID` | = | `cdm_positiontypeid.cdm_name` |
`JOBID` | = | `cdm_jobid.cdm_name` |

###  <a name="162"></a>Price customer groups (msdyn_pricecustomergroups)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`GROUPCODE` | = | `msdyn_groupcode` |
`GROUPNAME` | = | `msdyn_groupname` |

###  <a name="164"></a>Product Number Identified Barcode (msdyn_productbarcodes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PRODUCTNUMBER` | > | `msdyn_productnumberid.msdyn_productnumber` |
`BARCODE` | > | `msdyn_name` |
`BARCODE` | > | `msdyn_barcode` |
`PRODUCTQUANTITY` | > | `msdyn_productquantity` |
`PRODUCTDESCRIPTION` | > | `msdyn_productdescription` |
`BARCODESETUPID` | > | `msdyn_barcodesetupid` |
`PRODUCTQUANTITYUNITSYMBOL` | > | `msdyn_unitofmeasureid.msdyn_symbol` |
`ISDEFAULTSCANNEDBARCODE` | >> | `msdyn_isdefaultscannedbarcode` |
`ISDEFAULTPRINTEDBARCODE` | >> | `msdyn_isdefaultprintedbarcode` |
`ISDEFAULTDISPLAYEDBARCODE` | >> | `msdyn_isdefaultdisplayedbarcode` |

###  <a name="166"></a>Product categories (msdyn_productcategories)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PRODUCTCATEGORYHIERARCHYNAME` | = | `msdyn_hierarchy.msdyn_name` |
`ISCATEGORYINHERITINGPARENTPRODUCTATTRIBUTES` | >< | `msdyn_isinheritingparentproductattributes` |
`PROJECTCATEGORYNAME` | = | `msdyn_projectcategoryname` |
`ISTANGIBLEPRODUCT` | >< | `msdyn_istangibleproduct` |
`ISCATEGORYINHERITINGPARENTCATEGORYATTRIBUTES` | >< | `msdyn_isinheritingparentcategoryattributes` |
`CATEGORYCODE` | = | `msdyn_code` |
`CATEGORYDESCRIPTION` | = | `msdyn_description` |
`CATEGORYKEYWORDS` | = | `msdyn_keywords` |
`CATEGORYNAME` | = | `msdyn_name` |
`FRIENDLYCATEGORYNAME` | = | `msdyn_friendlycategoryname` |
`PARENTPRODUCTCATEGORYNAME` | = | `msdyn_parentproductcategory.msdyn_name` |
`PARENTPRODUCTCATEGORYHIERARCHYNAME` | > | `msdyn_parentproductcategory.msdyn_hierarchy.msdyn_name` |
`CATEGORYRECORDID` | > | `msdyn_externalproductcategoryid` |
`EXTERNALID` | = | `msdyn_integrationid` |

###  <a name="167"></a>Product category assignments (msdyn_productcategoryassignments)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PRODUCTNUMBER` | = | `msdyn_globalproduct.msdyn_productnumber` |
`PRODUCTCATEGORYNAME` | = | `msdyn_productcategory.msdyn_name` |
`PRODUCTCATEGORYHIERARCHYNAME` | = | `msdyn_productcategory.msdyn_hierarchy.msdyn_name` |
`PRODUCTNUMBER` | > | `msdyn_name` |

###  <a name="168"></a>Product category hierarchies (msdyn_productcategoryhierarchies)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`HIERARCHYNAME` | = | `msdyn_name` |
`HIERARCHYDESCRIPTION` | = | `msdyn_description` |

###  <a name="169"></a>Product category hierarchy roles (msdyn_productcategoryhierarchyroles)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PRODUCTCATEGORYHIERARCHYNAME` | = | `msdyn_hierarchy.msdyn_name` |
`HIERARCHYROLE` | >< | `msdyn_hierarchyrole` |

###  <a name="175"></a>Product default order settings V2 (msdyn_productspecificdefaultordersettings)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`INVENTORYWAREHOUSEID` | = | `msdyn_inventorywarehouse.msdyn_warehouseidentifier` |
`INVENTORYSITEID` | = | `msdyn_inventorysite.msdyn_siteid` |
`INVENTORYATPDELAYEDDEMANDOFFSETDAYS` | = | `msdyn_inventoryatpdelayeddemandoffsetdays` |
`INVENTORYATPDELAYEDSUPPLYOFFSETDAYS` | = | `msdyn_inventoryatpdelayedsupplyoffsetdays` |
`ITEMNUMBER` | = | `msdyn_itemnumber.msdyn_itemnumber` |
`INVENTORYATPBACKWARDDEMANDTIMEFENCEDAYS` | = | `msdyn_inventoryatpbackwarddemandtimefencedays` |
`INVENTORYATPBACKWARDSUPPLYTIMEFENCEDAYS` | = | `msdyn_inventoryatpbackwardsupplytimefencedays` |
`INVENTORYATPTIMEFENCEDAYS` | = | `msdyn_inventoryatptimefencedays` |
`MAXIMUMINVENTORYORDERQUANTITY` | = | `msdyn_maximuminventoryorderquantity` |
`MAXIMUMPROCUREMENTORDERQUANTITY` | = | `msdyn_maximumprocurementorderquantity` |
`MAXIMUMSALESORDERQUANTITY` | = | `msdyn_maximumsalesorderquantity` |
`MINIMUMINVENTORYORDERQUANTITY` | = | `msdyn_minimuminventoryorderquantity` |
`MINIMUMPROCUREMENTORDERQUANTITY` | = | `msdyn_minimumprocurementorderquantity` |
`MINIMUMSALESORDERQUANTITY` | = | `msdyn_minimumsalesorderquantity` |
`STANDARDINVENTORYORDERQUANTITY` | = | `msdyn_standardinventoryorderquantity` |
`STANDARDPROCUREMENTORDERQUANTITY` | = | `msdyn_standardprocurementorderquantity` |
`STANDARDSALESORDERQUANTITY` | = | `msdyn_standardsalesorderquantity` |
`INVENTORYLEADTIMEDAYS` | = | `msdyn_inventoryleadtimedays` |
`INVENTORYQUANTITYMULTIPLES` | = | `msdyn_inventoryquantitymultiples` |
`PROCUREMENTQUANTITYMULTIPLES` | = | `msdyn_procurementquantitymultiples` |
`SALESQUANTITYMULTIPLES` | = | `msdyn_salesquantitymultiples` |
`PROCUREMENTSITEID` | = | `msdyn_procurementsite.msdyn_siteid` |
`PROCUREMENTLEADTIMEDAYS` | = | `msdyn_procurementleadtimedays` |
`SALESSITEID` | = | `msdyn_salessite.msdyn_siteid` |
`SALESATPDELAYEDDEMANDOFFSETDAYS` | = | `msdyn_salesatpdelayeddemandoffsetdays` |
`SALESATPDELAYEDSUPPLYOFFSETDAYS` | = | `msdyn_salesatpdelayedsupplyoffsetdays` |
`SALESATPBACKWARDDEMANDTIMEFENCEDAYS` | = | `msdyn_salesatpbackwarddemandtimefencedays` |
`SALESATPBACKWARDSUPPLYTIMEFENCEDAYS` | = | `msdyn_salesatpbackwardsupplytimefencedays` |
`SALESATPTIMEFENCEDAYS` | = | `msdyn_salesatptimefencedays` |
`SALESLEADTIMEDAYS` | = | `msdyn_salesleadtimedays` |
`PROCUREMENTWAREHOUSEID` | = | `msdyn_procurementwarehouse.msdyn_warehouseidentifier` |
`SALESWAREHOUSEID` | = | `msdyn_saleswarehouse.msdyn_warehouseidentifier` |
`AREINVENTORYDEFAULTORDERSETTINGSOVERRIDDEN` | >< | `msdyn_areinventoryorderdefaultsoverridden` |
`INVENTORYORDERPROMISINGMETHOD` | >< | `msdyn_inventoryorderpromisingmethod` |
`ISINVENTORYATPINCLUDINGPLANNEDORDERS` | >< | `msdyn_isinventoryatpincludingplannedorders` |
`ISINVENTORYUSINGWORKINGDAYS` | >< | `msdyn_isinventoryusingworkingdays` |
`ISINVENTORYSITEMANDATORY` | >< | `msdyn_isinventorysitemandatory` |
`ISINVENTORYPROCESSINGSTOPPED` | >< | `msdyn_isinventoryprocessingstopped` |
`ISPROCUREMENTUSINGWORKINGDAYS` | >< | `msdyn_isprocurementusingworkingdays` |
`ISPROCUREMENTSITEMANDATORY` | >< | `msdyn_isprocurementsitemandatory` |
`ISPROCUREMENTPROCESSINGSTOPPED` | >< | `msdyn_isprocurementprocessingstopped` |
`ARESALESDEFAULTORDERSETTINGSOVERRIDDEN` | >< | `msdyn_aresalesorderdefaultsoverridden` |
`SALESORDERPROMISINGMETHOD` | >< | `msdyn_salesorderpromisingmethod` |
`ISSALESATPINCLUDINGPLANNEDORDERS` | >< | `msdyn_issalesatpincludingplannedorders` |
`ISSALESSITEMANDATORY` | >< | `msdyn_issalessitemandatory` |
`ISSALESLEADTIMEOVERRIDDEN` | >< | `msdyn_issalesleadtimeoverridden` |
`ISSALESPROCESSINGSTOPPED` | >< | `msdyn_issalesprocessingstopped` |
`ISINVENTORYWAREHOUSEMANDATORY` | >< | `msdyn_isinventorywarehousemandatory` |
`ISPROCUREMENTWAREHOUSEMANDATORY` | >< | `msdyn_isprocurementwarehousemandatory` |
`ISSALESWAREHOUSEMANDATORY` | >< | `msdyn_issaleswarehousemandatory` |
`OPERATIONALSITEID` | = | `msdyn_operationalsite.msdyn_siteid` |
`PRODUCTCOLORID` | = | `msdyn_productcolor.msdyn_productcolorname` |
`PRODUCTCONFIGURATIONID` | = | `msdyn_productconfiguration.msdyn_productconfiguration` |
`PRODUCTSIZEID` | = | `msdyn_productsize.msdyn_productsize` |
`PRODUCTSTYLEID` | = | `msdyn_productstyle.msdyn_productstyle` |

###  <a name="173"></a>Product dimension groups (msdyn_productdimensiongroups)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`WILLSALESPRICESEARCHUSEPRODUCTSTYLE` | >< | `msdyn_willsalespricesearchuseproductstyle` |
`WILLPURCHASEPRICESEARCHUSEPRODUCTSIZE` | >< | `msdyn_willpurchasepricesearchuseproductsize` |
`WILLSALESPRICESEARCHUSEPRODUCTCONFIGURATION` | >< | `msdyn_willsalespricesearchuseprodconfig` |
`WILLSALESPRICESEARCHUSEPRODUCTCOLOR` | >< | `msdyn_willsalespricesearchuseproductcolor` |
`WILLPURCHASEPRICESEARCHUSEPRODUCTSTYLE` | >< | `msdyn_willpurchasepricesearchuseproductstyle` |
`WILLPURCHASEPRICESEARCHUSEPRODUCTCONFIGURATION` | >< | `msdyn_willpurchpricesearchuseprodconfig` |
`WILLPURCHASEPRICESEARCHUSEPRODUCTCOLOR` | >< | `msdyn_willpurchpricesearchuseproductcolor` |
`ISPRODUCTSTYLEACTIVE` | >< | `msdyn_isproductstyleactive` |
`ISPRODUCTSIZEACTIVE` | >< | `msdyn_isproductsizeactive` |
`ISPRODUCTCONFIGURATIONACTIVE` | >< | `msdyn_isproductconfigurationactive` |
`ISPRODUCTCOLORACTIVE` | >< | `msdyn_isproductcoloractive` |
`GROUPNAME` | = | `msdyn_groupname` |
`GROUPDESCRIPTION` | = | `msdyn_groupdescription` |
`PRODUCTVARIANTNOMENCLATURENAME` | = | `msdyn_productvariantnomenclaturename` |
`WILLSALESPRICESEARCHUSEPRODUCTSIZE` | >< | `msdyn_willsalespricesearchuseproductsize` |

###  <a name="187"></a>Product master colors (msdyn_sharedproductcolors)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PRODUCTCOLORID` | > | `msdyn_productcolor.msdyn_productcolorname` |
`PRODUCTMASTERNUMBER` | > | `msdyn_globalproduct.msdyn_productnumber` |
`REPLENISHMENTWEIGHT` | > | `msdyn_replenishmentweight` |
`DISPLAYSEQUENCENUMBER` | > | `msdyn_displaysequencenumber` |

###  <a name="188"></a>Product master configurations (msdyn_sharedproductconfigurations)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CONTAINERUNITSYMBOL` | > | `msdyn_containerunit.msdyn_symbol` |
`PRODUCTCONFIGURATIONID` | > | `msdyn_productconfiguration.msdyn_productconfiguration` |
`PRODUCTMASTERNUMBER` | > | `msdyn_globalproduct.msdyn_productnumber` |
`REPLENISHMENTWEIGHT` | > | `msdyn_replenishmentweight` |
`DISPLAYSEQUENCENUMBER` | > | `msdyn_displaysequencenumber` |

###  <a name="190"></a>Product master sizes (msdyn_sharedproductsizes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PRODUCTMASTERNUMBER` | > | `msdyn_globalproduct.msdyn_productnumber` |
`PRODUCTSIZEID` | > | `msdyn_productsize.msdyn_productsize` |
`REPLENISHMENTWEIGHT` | > | `msdyn_replenishmentweight` |
`DISPLAYSEQUENCENUMBER` | > | `msdyn_displaysequencenumber` |

###  <a name="191"></a>Product master styles (msdyn_sharedproductstyles)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PRODUCTMASTERNUMBER` | > | `msdyn_globalproduct.msdyn_productnumber` |
`PRODUCTSTYLEID` | > | `msdyn_productstyle.msdyn_productstyle` |
`REPLENISHMENTWEIGHT` | > | `msdyn_replenishmentweight` |
`DISPLAYSEQUENCENUMBER` | > | `msdyn_displaysequencenumber` |

###  <a name="185"></a>Product receipt header (msdyn_purchaseorderreceipts)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`RECORDID` | > | `msdyn_recordid` |
`PRODUCTRECEIPTDATE` | > | `msdyn_datereceived` |
`DELIVERYADDRESSLATITUDE` | > | `msdyn_deliveryaddresslatitude` |
`DELIVERYADDRESSLONGITUDE` | > | `msdyn_deliveryaddresslongitude` |
`PURCHASEORDERNUMBER` | > | `msdyn_purchaseorder.msdyn_name` |
`DELIVERYMODEID` | > | `msdyn_shipvia.msdyn_name` |
`DELIVERYTERMSID` | > | `msdyn_deliveryterm.msdyn_termscode` |
`ORDERVENDORACCOUNTNUMBER` | > | `msdyn_ordervendor.msdyn_vendoraccountnumber` |
`REQUESTERPERSONNELNUMBER` | > | `msdyn_requesterpersonnel.cdm_workernumber` |
`ISDELIVERYADDRESSPRIVATE` | >> | `msdyn_isdeliveryaddressprivate` |
`DELIVERYADDRESSCOUNTRYREGIONID` | > | `msdyn_deliveryaddresscountryregionid` |
`DELIVERYADDRESSCOUNTYID` | > | `msdyn_deliveryaddresscountyid` |
`DELIVERYADDRESSSTATEID` | > | `msdyn_deliveryaddressstateid` |
`DELIVERYADDRESSZIPCODE` | > | `msdyn_deliveryaddresszipcode` |
`DELIVERYADDRESSNAME` | > | `msdyn_deliveryaddressname` |
`DELIVERYADDRESSTIMEZONE` | > | `msdyn_deliveryaddresstimezone` |
`DELIVERYADDRESSPOSTBOX` | > | `msdyn_deliveryaddresspostbox` |
`DELIVERYADDRESSSTREETNUMBER` | > | `msdyn_deliveryaddressstreetnumber` |
`DELIVERYADDRESSSTREET` | > | `msdyn_deliveryaddressstreet` |
`PRODUCTRECEIPTNUMBER` | > | `msdyn_name` |
`ATTENTIONINFORMATION` | > | `msdyn_note` |
`DELIVERYCITYINKANA` | > | `msdyn_deliverycityinkana` |
`DELIVERYSTREETINKANA` | > | `msdyn_deliverystreetinkana` |
`FORMATTEDDELIVERYADDRESS` | > | `msdyn_formatteddeliveryaddress` |
`DELIVERYADDRESSLOCATIONID` | > | `msdyn_deliveryaddresslocationid` |
`DELIVERYADDRESSCITY` | > | `msdyn_deliveryaddresscity` |
`DELIVERYADDRESSDESCRIPTION` | > | `msdyn_deliveryaddressdescription` |
`DELIVERYADDRESSDISTRICTNAME` | > | `msdyn_deliveryaddressdistrictname` |
`DELIVERYBUILDINGCOMPLIMENT` | > | `msdyn_deliverybuildingcompliment` |
`DELIVERYADDRESSDUNSNUMBER` | > | `msdyn_deliveryaddressdunsnumber` |

###  <a name="184"></a>Product receipt line (msdyn_purchaseorderreceiptproducts)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`RECORDID` | > | `msdyn_recordid` |
`DELIVERYADDRESSCOUNTRYREGIONID` | > | `msdyn_deliveryaddresscountryregionid` |
`DELIVERYADDRESSCOUNTYID` | > | `msdyn_deliveryaddresscountyid` |
`DELIVERYADDRESSSTATEID` | > | `msdyn_deliveryaddressstateid` |
`EXPECTEDDELIVERYDATE` | > | `msdyn_expecteddeliverydate` |
`EXTERNALITEMNUMBER` | > | `msdyn_externalitemnumber` |
`ITEMBATCHNUMBER` | > | `msdyn_itembatchnumber` |
`ITEMSERIALNUMBER` | > | `msdyn_itemserialnumber` |
`LINEDESCRIPTION` | > | `msdyn_linedescription` |
`ORDEREDPURCHASEQUANTITY` | > | `msdyn_orderedpurchasequantity` |
`PROCUREMENTPRODUCTCATEGORYNAME` | > | `msdyn_procurementproductcategory.msdyn_name` |
`PROCUREMENTPRODUCTCATEGORYHIERARCHYNAME` | > | `msdyn_procurementproductcategory.msdyn_hierarchy.msdyn_name` |
`PRODUCTRECEIPTDATE` | > | `msdyn_productreceiptdate` |
`PRODUCTRECEIPTHEADERRECORDID` | > | `msdyn_purchaseorderreceipt.msdyn_recordid` |
`PRODUCTRECEIPTNUMBER` | > | `msdyn_productreceiptnumber` |
`PURCHASEORDERLINENUMBER` | > | `msdyn_purchaseorderproduct.msdyn_lineorder` |
`PURCHASEORDERNUMBER` | > | `msdyn_purchaseorderproduct.msdyn_purchaseorder.msdyn_name` |
`PURCHASEORDERNUMBER` | > | `msdyn_purchaseorder.msdyn_name` |
`PURCHASEUNITSYMBOL` | > | `msdyn_purchaseunitsymbol.msdyn_symbol` |
`RECEIVEDINVENTORYQUANTITY` | > | `msdyn_receivedinventoryquantity` |
`RECEIVEDINVENTORYSTATUSID` | > | `msdyn_receivedinventorystatusid` |
`RECEIVEDPURCHASEQUANTITY` | > | `msdyn_quantity` |
`RECEIVINGSITEID` | > | `msdyn_receivingsiteid.msdyn_siteid` |
`RECEIVINGWAREHOUSEID` | > | `msdyn_associatetowarehouse.msdyn_warehouseidentifier` |
`RECEIVINGWAREHOUSELOCATIONID` | > | `msdyn_receivingwarehouselocation.msdyn_warehouselocationid` |
`RECEIVINGWAREHOUSEID` | > | `msdyn_receivingwarehouselocation.msdyn_warehouse.msdyn_warehouseidentifier` |
`REMAININGINVENTORYQUANTITY` | > | `msdyn_remaininginventoryquantity` |
`REMAININGPURCHASEQUANTITY` | > | `msdyn_remainingpurchasequantity` |
`PRODUCTNUMBER` | > | `msdyn_product.msdyn_productnumber` |

###  <a name="176"></a>Product specific unit conversions (msdyn_productspecificunitofmeasureconversions)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DENOMINATOR` | = | `msdyn_denominator` |
`NUMERATOR` | = | `msdyn_numerator` |
`FACTOR` | = | `msdyn_factor` |
`FROMUNITSYMBOL` | = | `msdyn_fromunit.msdyn_symbol` |
`TOUNITSYMBOL` | = | `msdyn_tounit.msdyn_symbol` |
`PRODUCTNUMBER` | = | `msdyn_globalproduct.msdyn_productnumber` |
`INNEROFFSET` | = | `msdyn_inneroffset` |
`OUTEROFFSET` | = | `msdyn_outeroffset` |
`ROUNDING` | >< | `msdyn_rounding` |

###  <a name="180"></a>Prospects (leads)

This template synchronizes data between Finance and Operations apps and Dataverse.

Source filter: `(IsB2BProspect == 1)`

Reversed source filter: `(msdyn_b2bcommerceprospect eq true)`

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PROSPECTNAME` | = | `fullname` |
`PROSPECTPARTYNUMBER` | = | `msdyn_partyid.msdyn_partynumber` |
`PROSPECTID` | = | `msdyn_prospectid` |
`PRIMARYPHONENUMBER` | = | `telephone1` |
`PRIMARYPHONENUMBEREXTENSION` | = | `msdyn_telephone1extension` |
`PRIMARYPHONENUMBERDESCRIPTION` | = | `description` |
`PRIMARYEMAILADDRESS` | = | `emailaddress1` |
`PRIMARYEMAILADDRESSDESCRIPTION` | = | `msdyn_emailaddress1description` |
`PRIMARYURL` | = | `websiteurl` |
`PRIMARYURLDESCRIPTION` | = | `msdyn_websiteurldescription` |
`ADDRESSCITY` | = | `address1_city` |
`ADDRESSCOUNTRYREGIONISOCODE` | = | `address1_country` |
`ADDRESSCOUNTYID` | = | `address1_county` |
`ADDRESSSTATEID` | = | `address1_stateorprovince` |
`ADDRESSSTREET` | = | `address1_line1` |
`ADDRESSZIPCODE` | = | `address1_postalcode` |
`ADDRESSPOSTBOX` | = | `address1_postofficebox` |
`ADDRESSLOCATIONROLES` | << | `none` | Business
`none` | >> | `address1_addresstypecode` | 1
`COMPANYNAME` | = | `companyname` |
`COMPANYSIZE` | = | `numberofemployees` |
`ADDRESSLATITUDE` | = | `address1_latitude` |
`ADDRESSLONGITUDE` | = | `address1_longitude` |
`CURRENCYCODE` | = | `transactioncurrencyid.isocurrencycode` |
`CUSTOMERGROUPID` | = | `msdyn_customergroupid.msdyn_groupid` |
`SALESTAXGROUPCODE` | = | `msdyn_salestaxgroup.msdyn_name` |
`PRIMARYFAXNUMBER` | = | `fax` |
`PRIMARYFAXNUMBERDESCRIPTION` | = | `msdyn_faxdescription` |
`PRIMARYFAXNUMBEREXTENSION` | = | `msdyn_faxextension` |
`RETAILCHANNELOPERATINGUNITPARTYNUMBER` | = | `msdyn_retailchannel.msdyn_partynumber` |
`ISB2BPROSPECT` | >< | `msdyn_b2bcommerceprospect` |
`B2BPROSPECTSTATUS` | >< | `msdyn_b2bprospectstatus` |

###  <a name="232"></a>Purchase order header document attachments (annotations)

This template synchronizes data between Finance and Operations apps and Dataverse.

Source filter: `((DocumentAttachmentTypeCode == "Note") || (DocumentAttachmentTypeCode == "URL"))`

Reversed source filter: `objecttypecode eq 'msdyn_purchaseorder'`

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DOCUMENTID` | = | `msdyn_notesid` |
`NOTES` | = | `notetext` |
`ATTACHMENTDESCRIPTION` | = | `subject` |
`PURCHASEORDERNUMBER` | = | `msdyn_relatedentityid` |
`DOCUMENTATTACHMENTTYPECODE` | << | `none` | Note
`none` | >> | `objecttypecode` | msdyn_purchaseorder
`ACCESSRESTRICTION` | >< | `msdyn_restriction` |

###  <a name="183"></a>Purchase order headers V2 (msdyn_purchaseorders)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DELIVERYADDRESSNAME` | > | `msdyn_addressname` |
`REQUESTEDDELIVERYDATE` | = | `msdyn_dateexpected` |
`PURCHASEORDERNUMBER` | = | `msdyn_name` |
`PAYMENTTERMSNAME` | = | `msdyn_paymentterm.msdyn_name` |
`DEFAULTRECEIVINGWAREHOUSEID` | = | `msdyn_receivetowarehouse.msdyn_warehouseidentifier` |
`ACCOUNTINGDATE` | = | `msdyn_accountingdate` |
`AREPRICESINCLUDINGSALESTAX` | >< | `msdyn_arepriceincludingsalestax` |
`ATTENTIONINFORMATION` | > | `msdyn_attentioninformation` |
`CASHDISCOUNTCODE` | = | `msdyn_cashdiscountcode` |
`CASHDISCOUNTPERCENTAGE` | = | `msdyn_cashdiscountpercentage` |
`CONTACTPERSONID` | = | `msdyn_contactpersonid.msdyn_contactpersonid` |
`CURRENCYCODE` | = | `transactioncurrencyid.isocurrencycode` |
`DEFAULTRECEIVINGSITEID` | = | `msdyn_defaultreceivingsiteid.msdyn_siteid` |
`DELIVERYTERMSID` | = | `msdyn_deliveryterm.msdyn_termscode` |
`EMAIL` | = | `msdyn_email` |
`ISCHANGEMANAGEMENTACTIVE` | >> | `msdyn_ischangemanagementactive` |
`ISDELIVEREDDIRECTLY` | >> | `msdyn_isdeliverydirectly` |
`LANGUAGEID` | >< | `msdyn_language` |
`ORDERERPERSONNELNUMBER` | = | `msdyn_ordererpersonnelnumber.cdm_workernumber` |
`REASONCODE` | = | `msdyn_reasoncode` |
`REASONCOMMENT` | = | `msdyn_reasoncomment` |
`TOTALDISCOUNTPERCENTAGE` | = | `msdyn_totaldiscountpercentage` |
`URL` | = | `msdyn_url` |
`VENDORORDERREFERENCE` | = | `msdyn_vendororderreference` |
`VENDORPAYMENTMETHODNAME` | = | `msdyn_vendorpaymentmethod.msdyn_name` |
`VENDORPAYMENTMETHODSPECIFICATIONNAME` | > | `msdyn_vendorpaymentmethodspecificationname` |
`ORDERVENDORACCOUNTNUMBER` | = | `msdyn_vendor.accountnumber` |
`DELIVERYMODEID` | = | `msdyn_shipvia.msdyn_name` |
`INVOICEVENDORACCOUNTNUMBER` | = | `msdyn_invoicevendoraccount.accountnumber` |
`DOCUMENTAPPROVALSTATUS` | >> | `msdyn_documentapprovalstatus` |
`PURCHASEORDERSTATUS` | >> | `msdyn_purchaseorderstatus` |
`DELIVERYADDRESSCITY` | > | `msdyn_city` |
`DELIVERYADDRESSCOUNTRYREGIONISOCODE` | > | `msdyn_country` |
`DELIVERYADDRESSSTATEID` | > | `msdyn_stateorprovince` |
`DELIVERYADDRESSZIPCODE` | > | `msdyn_postalcode` |
`DELIVERYADDRESSSTREET` | > | `msdyn_address1` |
`INVOICEADDRESSSTREETNUMBER` | > | `msdyn_invoiceaddressstreetnumber` |
`CONFIRMEDDELIVERYDATE` | = | `msdyn_confirmeddeliverydate` |
`DELIVERYADDRESSLONGITUDE` | > | `msdyn_longitude` |
`DELIVERYADDRESSLATITUDE` | > | `msdyn_latitude` |
`DELIVERYADDRESSCOUNTRYREGIONID` | > | `msdyn_deliveryaddresscountryregionid` |
`DELIVERYADDRESSCOUNTYID` | > | `msdyn_deliveryaddresscountyid` |
`DELIVERYADDRESSDESCRIPTION` | > | `msdyn_deliveryaddressdescription` |
`DELIVERYADDRESSDISTRICTNAME` | > | `msdyn_deliveryaddressdistrictname` |
`DELIVERYADDRESSDUNSNUMBER` | > | `msdyn_deliveryaddressdunsnumber` |
`DELIVERYADDRESSLOCATIONID` | > | `msdyn_deliveryaddresslocationid` |
`DELIVERYADDRESSPOSTBOX` | > | `msdyn_deliveryaddresspostbox` |
`DELIVERYADDRESSTIMEZONE` | > | `msdyn_deliveryaddresstimezone` |
`DELIVERYBUILDINGCOMPLIMENT` | > | `msdyn_deliverybuildingcompliment` |
`FORMATTEDDELIVERYADDRESS` | > | `msdyn_formatteddeliveryaddress` |
`FORMATTEDINVOICEADDRESS` | > | `msdyn_formattedinvoiceaddress` |
`INVOICEADDRESSCITY` | > | `msdyn_invoiceaddresscity` |
`INVOICEADDRESSCOUNTRYREGIONID` | > | `msdyn_invoiceaddresscountryregionid` |
`INVOICEADDRESSCOUNTY` | > | `msdyn_invoiceaddresscounty` |
`INVOICEADDRESSSTATE` | > | `msdyn_invoiceaddressstate` |
`INVOICEADDRESSSTREET` | > | `msdyn_invoiceaddressstreet` |
`DELIVERYADDRESSSTREETNUMBER` | > | `msdyn_address2` |
`INVOICEADDRESSZIPCODE` | > | `msdyn_invoiceaddresszipcode` |

###  <a name="189"></a>Released products V2 (msdyn_sharedproductdetails)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PRODUCTNUMBER` | > | `msdyn_globalproduct.msdyn_productnumber` |
`INTRASTATCHARGEPERCENTAGE` | > | `msdyn_intrastatchargepercentage` |
`ITEMNUMBER` | > | `msdyn_itemnumber` |
`APPROXIMATESALESTAXPERCENTAGE` | > | `msdyn_approximatesalestaxpercentage` |
`BESTBEFOREPERIODDAYS` | > | `msdyn_bestbeforeperioddays` |
`CARRYINGCOSTABCCODE` | >> | `msdyn_carryingcostabccode` |
`CONSTANTSCRAPQUANTITY` | > | `msdyn_constantscrapquantity` |
`COSTCHARGESQUANTITY` | > | `msdyn_costchargesquantity` |
`DEFAULTRECEIVINGQUANTITY` | > | `msdyn_defaultreceivingquantity` |
`FIXEDPURCHASEPRICECHARGES` | > | `msdyn_fixedpurchasepricecharges` |
`FIXEDSALESPRICECHARGES` | > | `msdyn_fixedsalespricecharges` |
`GROSSDEPTH` | > | `msdyn_grossdepth` |
`GROSSPRODUCTHEIGHT` | > | `msdyn_grossproductheight` |
`GROSSPRODUCTWIDTH` | > | `msdyn_grossproductwidth` |
`INVENTORYUNITSYMBOL` | > | `msdyn_inventoryunitsymbol.msdyn_symbol` |
`ISDISCOUNTPOSREGISTRATIONPROHIBITED` | >> | `msdyn_isdiscountposregistrationprohibited` |
`ISEXEMPTFROMAUTOMATICNOTIFICATIONANDCANCELLATION` | >> | `msdyn_exemptautomaticnotificationcancel` |
`ISINSTALLMENTELIGIBLE` | >> | `msdyn_isinstallmenteligible` |
`ISINTERCOMPANYPURCHASEUSAGEBLOCKED` | >> | `msdyn_isintercompanypurchaseusageblocked` |
`ISINTERCOMPANYSALESUSAGEBLOCKED` | >> | `msdyn_isintercompanysalesusageblocked` |
`ISMANUALDISCOUNTPOSREGISTRATIONPROHIBITED` | >> | `msdyn_ismanualdiscposregistrationprohibited` |
`ISPHANTOM` | >> | `msdyn_isphantom` |
`ISPOSREGISTRATIONBLOCKED` | >> | `msdyn_isposregistrationblocked` |
`ISPOSREGISTRATIONQUANTITYNEGATIVE` | >> | `msdyn_isposregistrationquantitynegative` |
`ISPURCHASEPRICEAUTOMATICALLYUPDATED` | >> | `msdyn_ispurchasepriceautomaticallyupdated` |
`ISPURCHASEPRICEINCLUDINGCHARGES` | >> | `msdyn_ispurchasepriceincludingcharges` |
`ISSALESWITHHOLDINGTAXCALCULATED` | >> | `msdyn_issaleswithholdingtaxcalculated` |
`ISRESTRICTEDFORCOUPONS` | >> | `msdyn_isrestrictedforcoupons` |
`ISSALESPRICEADJUSTMENTALLOWED` | >> | `msdyn_issalespriceadjustmentallowed` |
`ISSALESPRICEINCLUDINGCHARGES` | >> | `msdyn_issalespriceincludingcharges` |
`ISSCALEPRODUCT` | >> | `msdyn_isscaleproduct` |
`ISSHIPALONEENABLED` | >> | `msdyn_isshipaloneenabled` |
`ISUNITCOSTPRODUCTVARIANTSPECIFIC` | >> | `msdyn_isunitcostproductvariantspecific` |
`ISVARIANTSHELFLABELSPRINTINGENABLED` | >> | `msdyn_isvariantshelflabelsprintingenabled` |
`ISZEROPRICEPOSREGISTRATIONALLOWED` | >> | `msdyn_iszeropriceposregistrationallowed` |
`KEYINPRICEREQUIREMENTSATPOSREGISTER` | >> | `msdyn_keyinpricerequirementsatposregister` |
`KEYINQUANTITYREQUIREMENTSATPOSREGISTER` | >> | `msdyn_keyinquantityrequirementsatposregister` |
`MARGINABCCODE` | >> | `msdyn_marginabccode` |
`MAXIMUMPICKQUANTITY` | > | `msdyn_maximumpickquantity` |
`MUSTKEYINCOMMENTATPOSREGISTER` | >> | `msdyn_mustkeyincommentatposregister` |
`NECESSARYPRODUCTIONWORKINGTIMESCHEDULINGPROPERTYID` | > | `msdyn_necessaryproductionworkingtimeschedulingp` |
`NETPRODUCTWEIGHT` | > | `msdyn_netproductweight` |
`PACKINGDUTYQUANTITY` | > | `msdyn_packingdutyquantity` |
`POSREGISTRATIONACTIVATIONDATE` | > | `msdyn_posregistrationactivationdate` |
`POSREGISTRATIONBLOCKEDDATE` | > | `msdyn_posregistrationblockeddate` |
`POSREGISTRATIONPLANNEDBLOCKEDDATE` | > | `msdyn_posregistrationplannedblockeddate` |
`POTENCYBASEATTIBUTETARGETVALUE` | > | `msdyn_potencybaseattibutetargetvalue` |
`POTENCYBASEATTRIBUTEVALUEENTRYEVENT` | >> | `msdyn_potencybaseattributevalueentryevent` |
`PRODUCTTYPE` | >> | `msdyn_producttype` |
`PRODUCTIONCONSUMPTIONDENSITYCONVERSIONFACTOR` | > | `msdyn_productionconsumptiondensityconversion` |
`PRODUCTIONCONSUMPTIONDEPTHCONVERSIONFACTOR` | > | `msdyn_productionconsumptiondepthconversion` |
`PRODUCTIONCONSUMPTIONHEIGHTCONVERSIONFACTOR` | > | `msdyn_productionconsumptionheightconversion` |
`PRODUCTIONCONSUMPTIONWIDTHCONVERSIONFACTOR` | > | `msdyn_productionconsumptionwidthconversion` |
`PRODUCTVOLUME` | > | `msdyn_productvolume` |
`PURCHASECHARGESQUANTITY` | > | `msdyn_purchasechargesquantity` |
`PURCHASEOVERDELIVERYPERCENTAGE` | > | `msdyn_purchaseoverdeliverypercentage` |
`PURCHASEPRICE` | > | `msdyn_purchaseprice` |
`PURCHASEPRICEDATE` | > | `msdyn_purchasepricedate` |
`PURCHASEPRICINGPRECISION` | > | `msdyn_purchasepricingprecision` |
`PURCHASEUNDERDELIVERYPERCENTAGE` | > | `msdyn_purchaseunderdeliverypercentage` |
`RAWMATERIALPICKINGPRINCIPLE` | >> | `msdyn_rawmaterialpickingprinciple` |
`SALESCHARGESQUANTITY` | > | `msdyn_saleschargesquantity` |
`SALESOVERDELIVERYPERCENTAGE` | > | `msdyn_salesoverdeliverypercentage` |
`SALESPRICE` | > | `msdyn_salesprice` |
`SALESPRICECALCULATIONCHARGESPERCENTAGE` | > | `msdyn_salespricecalculationchargespercentage` |
`SALESPRICECALCULATIONCONTRIBUTIONRATIO` | > | `msdyn_salespricecalculationcontributionratio` |
`SALESPRICECALCULATIONMODEL` | >> | `msdyn_salespricecalculationmodel` |
`SALESPRICEDATE` | > | `msdyn_salespricedate` |
`SALESPRICINGPRECISION` | > | `msdyn_salespricingprecision` |
`SALESUNDERDELIVERYPERCENTAGE` | > | `msdyn_salesunderdeliverypercentage` |
`SALESUNITSYMBOL` | > | `msdyn_salesunitsymbol.msdyn_symbol` |
`SCALEINDICATOR` | >> | `msdyn_scaleindicator` |
`SELLSTARTDATE` | > | `msdyn_sellstartdate` |
`SHELFADVICEPERIODDAYS` | > | `msdyn_shelfadviceperioddays` |
`SHELFLIFEPERIODDAYS` | > | `msdyn_shelflifeperioddays` |
`SHIPSTARTDATE` | > | `msdyn_shipstartdate` |
`TAREPRODUCTWEIGHT` | > | `msdyn_tareproductweight` |
`TRANSFERORDEROVERDELIVERYPERCENTAGE` | > | `msdyn_transferorderoverdeliverypercentage` |
`TRANSFERORDERUNDERDELIVERYPERCENTAGE` | > | `msdyn_transferorderunderdeliverypercentage` |
`UNITCOST` | > | `msdyn_unitcost` |
`UNITCOSTDATE` | > | `msdyn_unitcostdate` |
`UNITCOSTQUANTITY` | > | `msdyn_unitcostquantity` |
`VARIABLESCRAPPERCENTAGE` | > | `msdyn_variablescrappercentage` |
`WAREHOUSEMOBILEDEVICEDESCRIPTIONLINE1` | > | `msdyn_warehousemobiledevicedescriptionline1` |
`WAREHOUSEMOBILEDEVICEDESCRIPTIONLINE2` | > | `msdyn_warehousemobiledevicedescriptionline2` |
`WILLINVENTORYISSUEAUTOMATICALLYREPORTASFINISHED` | >> | `msdyn_willinventoryissueautoreportasfinished` |
`WILLINVENTORYRECEIPTIGNOREFLUSHINGPRINCIPLE` | >> | `msdyn_willinventoryreceiptignoreflushing` |
`WILLPICKINGWORKBENCHAPPLYBOXINGLOGIC` | >> | `msdyn_willpickingworkbenchapplyboxinglogic` |
`WILLTOTALPURCHASEDISCOUNTCALCULATIONINCLUDEPRODUCT` | >> | `msdyn_willtotalpurchdiscountcalcincludeproduct` |
`WILLTOTALSALESDISCOUNTCALCULATIONINCLUDEPRODUCT` | >> | `msdyn_willtotalsalesdiscountcalcincludeproduct` |
`WILLWORKCENTERPICKINGALLOWNEGATIVEINVENTORY` | >> | `msdyn_willworkcenterpickingallownegativeinvent` |
`YIELDPERCENTAGE` | > | `msdyn_yieldpercentage` |
`ISUNITCOSTAUTOMATICALLYUPDATED` | >> | `msdyn_isunitcostautomaticallyupdated` |
`PURCHASEUNITSYMBOL` | > | `msdyn_purchaseunitsymbol.msdyn_symbol` |
`PURCHASEPRICEQUANTITY` | > | `msdyn_purchasepricequantity` |
`ISUNITCOSTINCLUDINGCHARGES` | >> | `msdyn_isunitcostincludingcharges` |
`FIXEDCOSTCHARGES` | > | `msdyn_fixedcostcharges` |
`MINIMUMCATCHWEIGHTQUANTITY` | > | `msdyn_minimumcatchweightquantity` |
`MAXIMUMCATCHWEIGHTQUANTITY` | > | `msdyn_maximumcatchweightquantity` |
`ALTERNATIVEITEMNUMBER` | > | `msdyn_alternativeitemnumber.msdyn_itemnumber` |
`BOMUNITSYMBOL` | > | `msdyn_bomunitsymbol.msdyn_symbol` |
`CATCHWEIGHTUNITSYMBOL` | > | `msdyn_catchweightunitsymbol.msdyn_symbol` |
`COMPARISONPRICEBASEUNITSYMBOL` | > | `msdyn_comparisonpricebaseunitsymbol.msdyn_symbol` |
`PRIMARYVENDORACCOUNTNUMBER` | > | `msdyn_vendorid.msdyn_vendoraccountnumber` |
`ISCATCHWEIGHTPRODUCT` | >> | `msdyn_iscatchweight` |
`PRODUCTDIMENSIONGROUPNAME` | > | `msdyn_productdimensiongroupid.msdyn_groupname` |

###  <a name="118"></a>Sales invoice headers V2 (invoices)

This template synchronizes data between Finance and Operations apps and Dataverse.

Source filter: `(SalesOrderNumber != "")`

Reversed source filter: `msdyn_ordertype eq 192350000`

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`none` | >> | `ispricelocked` | False
`none` | >> | `statuscode` | 4
`CONTACTPERSONID` | > | `msdyn_associatedcontact.msdyn_contactforpartynumber` |
`CURRENCYCODE` | > | `transactioncurrencyid.isocurrencycode` |
`CUSTOMERSORDERREFERENCE` | > | `description` |
`INVOICEADDRESSCITY` | > | `billto_city` |
`INVOICEADDRESSCOUNTRYREGIONISOCODE` | > | `billto_country` |
`INVOICEADDRESSSTATE` | > | `billto_stateorprovince` |
`INVOICEADDRESSSTREET` | > | `billto_line1` |
`INVOICEADDRESSSTREETNUMBER` | > | `billto_line2` |
`INVOICEADDRESSZIPCODE` | > | `billto_postalcode` |
`INVOICECUSTOMERACCOUNTNUMBER` | > | `customerid.Account(accountnumber).Contact(msdyn_contactpersonid)` |
`INVOICEDATE` | > | `msdyn_invoicedate` |
`INVOICENUMBER` | > | `msdyn_invoicenumber` |
`LEDGERVOUCHER` | > | `msdyn_ledgervoucher` |
`PAYMENTTERMSNAME` | > | `msdyn_paymentterms.msdyn_name` |
`SALESORDERNUMBER` | > | `salesorderid.msdyn_salesordernumber` |
`TOTALCHARGEAMOUNT` | > | `freightamount` |
`TOTALDISCOUNTAMOUNT` | > | `msdyn_totaldiscountamount` |
`TOTALDISCOUNTCUSTOMERGROUPCODE` | > | `discountamount` |
`TOTALINVOICEAMOUNT` | > | `msdyn_totalamount` |
`TOTALTAXAMOUNT` | > | `msdyn_totaltax` |
`none` | >> | `msdyn_ordertype` | 192350000

###  <a name="117"></a>Sales invoice lines V2 (invoicedetails)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`CONFIRMEDSHIPPINGDATE` | > | `msdyn_confirmedshippingdate` |
`CURRENCYCODE` | > | `transactioncurrencyid.isocurrencycode` |
`INVENTORYSITEID` | > | `msdyn_inventorysite.msdyn_siteid` |
`INVENTORYWAREHOUSEID` | > | `msdyn_inventorywarehouse.msdyn_warehouseidentifier` |
`INVOICEDATE` | > | `invoiceid.msdyn_invoicedate` |
`INVOICEDQUANTITY` | > | `quantity` |
`INVOICENUMBER` | > | `invoiceid.msdyn_invoicenumber` |
`LEDGERVOUCHER` | > | `invoiceid.msdyn_ledgervoucher` |
`LINEAMOUNT` | > | `extendedamount` |
`LINECREATIONSEQUENCENUMBER` | > | `sequencenumber` |
`LINETOTALCHARGEAMOUNT` | > | `msdyn_totalchargeamount` |
`LINETOTALDISCOUNTAMOUNT` | > | `manualdiscountamount` |
`LINETOTALTAXAMOUNT` | > | `tax` |
`PRODUCTNAME` | > | `description` |
`PRODUCTNUMBER` | > | `productid.msdyn_productnumber` |
`SALESPRICE` | > | `priceperunit` |
`SALESPRODUCTCATEGORYHIERARCHYNAME` | > | `msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name` |
`SALESPRODUCTCATEGORYNAME` | > | `msdyn_salesproductcategory.msdyn_name` |
`SALESUNITSYMBOL` | > | `uomid.msdyn_symbol` |
`none` | >> | `producttypecode` | 1
`none` | >> | `propertyconfigurationstatus` | 2
`none` | >> | `ispriceoverridden` | True

###  <a name="229"></a>Sales order header document attachments (annotations)

This template synchronizes data between Finance and Operations apps and Dataverse.

Source filter: `((DocumentAttachmentTypeCode == "Note") || (DocumentAttachmentTypeCode == "URL"))`

Reversed source filter: `objecttypecode eq 'salesorder'`

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DOCUMENTID` | = | `msdyn_notesid` |
`NOTES` | = | `notetext` |
`ATTACHMENTDESCRIPTION` | = | `subject` |
`SALESORDERNUMBER` | = | `msdyn_relatedentityid` |
`DOCUMENTATTACHMENTTYPECODE` | << | `none` | Note
`none` | >> | `objecttypecode` | salesorder
`ACCESSRESTRICTION` | >< | `msdyn_restriction` |

###  <a name="186"></a>Sales order origin codes (msdyn_salesorderorigins)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`ORIGINCODE` | = | `msdyn_origincode` |
`ORIGINDESCRIPTION` | = | `msdyn_origindescription` |

###  <a name="193"></a>Sales tax authorities (msdyn_taxauthorities)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`TAXAUTHORITYCODE` | = | `msdyn_taxauthoritycode` |
`TAXAUTHORITYIDENTIFICATION` | = | `msdyn_taxauthorityidentificator` |
`DESCRIPTION` | = | `msdyn_description` |
`REPORTLAYOUT` | >< | `msdyn_taxreportlayout` |
`ROUNDOFFTYPE` | >< | `msdyn_roundofftype` |
`ROUNDOFF` | = | `msdyn_roundoff` |
`EMAIL` | = | `msdyn_email` |
`PHONE` | = | `msdyn_phone` |
`URL` | = | `msdyn_url` |

###  <a name="194"></a>Sales tax exempt code entity CDS (msdyn_taxexemptcodes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`NAME` | = | `msdyn_name` |
`DESCRIPTION` | = | `msdyn_description` |

###  <a name="195"></a>Sales tax groups (msdyn_taxgroups)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`TAXGROUPCODE` | = | `msdyn_name` |
`DESCRIPTION` | = | `msdyn_description` |

###  <a name="197"></a>Sales tax ledger posting groups V2 (msdyn_taxpostinggroups)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`TAXPOSTINGGROUPCODE` | = | `msdyn_name` |
`DESCRIPTION` | = | `msdyn_description` |

###  <a name="228"></a>Salutations (msdyn_salutations)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`SALUTATIONPHRASE` | = | `msdyn_salutationphrase` |

###  <a name="156"></a>Sites (msdyn_operationalsites)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DEFAULTFINANCIALDIMENSIONVALUE` | = | `msdyn_defaultfinancialdimensionvalue` |
`DEFAULTINVENTORYSTATUSID` | = | `msdyn_defaultinventorystatusid` |
`ISRECEIVINGWAREHOUSEOVERRIDEALLOWED` | >< | `msdyn_isreceivingwarehouseoverrideallowed` |
`SITEID` | = | `msdyn_siteid` |
`SITENAME` | = | `msdyn_sitename` |
`TAXBRANCHCODE` | = | `msdyn_taxbranchcode` |
`FISCALESTABLISHMENTID` | = | `msdyn_fiscalestablishmentid` |
`ISPRIMARYADDRESSASSIGNED` | >< | `msdyn_isprimaryaddressassigned` |
`PRIMARYADDRESSCITY` | = | `msdyn_primaryaddresscity` |
`PRIMARYADDRESSCOUNTRYREGIONID` | = | `msdyn_primaryaddresscountryregionid` |
`PRIMARYADDRESSCOUNTYID` | = | `msdyn_primaryaddresscountyid` |
`PRIMARYADDRESSDISTRICTNAME` | = | `msdyn_primaryaddressdistrictname` |
`PRIMARYADDRESSLATITUDE` | = | `msdyn_primaryaddresslatitude` |
`PRIMARYADDRESSLOCATIONROLES` | = | `msdyn_primaryaddresslocationrole` |
`PRIMARYADDRESSLOCATIONSALESTAXGROUPCODE` | = | `msdyn_primaryaddresslocationsalestaxgroupcode` |
`PRIMARYADDRESSLONGITUDE` | = | `msdyn_primaryaddresslongitude` |
`PRIMARYADDRESSSTATEID` | = | `msdyn_primaryaddressstateid` |
`PRIMARYADDRESSSTREET` | = | `msdyn_primaryaddressstreet` |
`PRIMARYADDRESSZIPCODE` | = | `msdyn_primaryaddresszipcode` |
`PRIMARYADDRESSBUILDINGCOMPLIMENT` | = | `msdyn_primaryaddressbuildingcompliment` |
`PRIMARYADDRESSCITYINKANA` | = | `msdyn_primaryaddresscityinkana` |
`PRIMARYADDRESSSTREETINKANA` | = | `msdyn_primaryaddressstreetinkana` |
`PRIMARYADDRESSDESCRIPTION` | = | `msdyn_primaryaddressdescription` |
`FORMATTEDPRIMARYADDRESS` | = | `msdyn_formattedprimaryaddress` |
`WILLMASTERPLANNEDINTRASITEMOVEMENTSUSETRANSFERJOURNALS` | >< | `msdyn_masterplannedusestransferjournal` |
`PRIMARYADDRESSPOSTBOX` | = | `msdyn_primaryaddresspostbox` |
`PRIMARYADDRESSSTREETNUMBER` | = | `msdyn_primaryaddressstreetnumber` |

###  <a name="174"></a>Sizes (msdyn_productsizes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`SIZEID` | > | `msdyn_productsize` |

###  <a name="177"></a>Storage dimension groups (msdyn_productstoragedimensiongroups)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`WILLSALESPRICESEARCHUSEWAREHOUSE` | >< | `msdyn_willsalespricesearchusewarehouse` |
`WILLSALESPRICESEARCHUSESITE` | >< | `msdyn_willsalespricesearchusesite` |
`WILLSALESPRICESEARCHUSEINVENTORYSTATUS` | >< | `msdyn_willsalespricesearchuseinventorystatus` |
`WILLPURCHASEPRICESEARCHUSEWAREHOUSE` | >< | `msdyn_willpurchasepricesearchusewarehouse` |
`WILLPURCHASEPRICESEARCHUSESITE` | >< | `msdyn_willpurchasepricesearchusesite` |
`WILLPURCHASEPRICESEARCHUSEINVENTORYSTATUS` | >< | `msdyn_willpurchpricesearchuseinventstatus` |
`WILLCOVERAGEPLANNINGUSEWAREHOUSE` | >< | `msdyn_willcoverageplanusewarehouse` |
`WILLCOVERAGEPLANNINGUSELOCATION` | >< | `msdyn_iscoverageplanenabledforlocation` |
`WILLCOVERAGEPLANNINGUSEINVENTORYSTATUS` | >< | `msdyn_willcoverageplanuseinventorystatus` |
`AREADVANCEDWAREHOUSEMANAGEMENTPROCESSESENABLED` | >< | `msdyn_areadvancedwmprocessesenabled` |
`ISWAREHOUSEPRIMARYSTORAGEDIMENSION` | >< | `msdyn_iswarehouseprimarystoragedimension` |
`ISWAREHOUSEMANDATORY` | >< | `msdyn_iswarehousemandatory` |
`ISPHYSICALINVENTORYENABLEDFORWAREHOUSE` | >< | `msdyn_isphysicalinventoryenabledforwarehouse` |
`ISPHYSICALINVENTORYENABLEDFORLOCATION` | >< | `msdyn_isphysicalinventoryenabledforlocation` |
`ISLOCATIONACTIVE` | >< | `msdyn_islocationactive` |
`ISFINANCIALINVENTORYENABLEDFORWAREHOUSE` | >< | `msdyn_isfinancialinventoryenabledforwarehouse` |
`GROUPNAME` | = | `msdyn_groupname` |
`GROUPDESCRIPTION` | = | `msdyn_groupdescription` |
`ISBLANKRECEIPTALLOWEDFORLOCATION` | >< | `msdyn_isblankreceiptallowedforlocation` |
`ISBLANKISSUEALLOWEDFORLOCATION` | >< | `msdyn_isblankissueallowedforlocation` |

###  <a name="178"></a>Styles (msdyn_productstyles)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`STYLEID` | > | `msdyn_productstyle` |

###  <a name="198"></a>Terms of delivery (msdyn_termsofdeliveries)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`TERMSCODE` | = | `msdyn_termscode` |
`INTRASTATCODE` | = | `msdyn_intrastatcode` |
`SALESTAXLOCATIONROLE` | >< | `msdyn_salestaxlocationrole` |
`TERMSDESCRIPTION` | = | `msdyn_termsdescription` |
`FREIGHTCHARGETERMS` | >< | `msdyn_freightchargeterms` |
`DORETAILSALESORDERSGETTRANSPORTATIONCHARGESADDED` | >< | `msdyn_doretailsogettransportationchargesadded` |
`ISCASHONDELIVERY` | >< | `msdyn_iscashondelivery` |
`WILLSHIPMENTCONFIRMATIONTRANSFERCHARGES` | >< | `msdyn_willshipmentconfirmationtransfercharges` |

###  <a name="161"></a>Terms of payment (msdyn_paymentterms)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DESCRIPTION` | = | `msdyn_description` |
`NAME` | = | `msdyn_name` |
`NUMBEROFMONTHS` | = | `msdyn_numberofmonth` |
`CUTOFFDAYOFMONTH` | = | `msdyn_cutoffdayofmonth` |
`ISCASHPAYMENT` | >< | `msdyn_iscashpayment` |
`NUMBEROFDAYS` | = | `msdyn_days` |
`ISCERTIFIEDCOMPANYCHECK` | >< | `msdyn_iscertifiedcompanycheck` |
`ISDEFAULTPAYMENTTERM` | >< | `msdyn_isdefaultpaymentterm` |
`CREDITCARDPAYMENTTYPE` | >< | `msdyn_creditcardpaymenttype` |
`CREDITCARDCREDITCHECKTYPE` | >< | `msdyn_creditcardcreditchecktype` |
`PAYMENTDAYNAME` | = | `msdyn_paymentdayname.msdyn_name` |
`PAYMENTMETHODTYPE` | >< | `msdyn_paymentmethodtype` |
`PAYMENTSCHEDULENAME` | = | `msdyn_paymentschedulename.msdyn_name` |

###  <a name="179"></a>Tracking dimension groups (msdyn_producttrackingdimensiongroups)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`SERIALNUMBERCAPTURINGOPERATION` | >< | `msdyn_serialnumbercapturingoperation` |
`GROUPNAME` | = | `msdyn_groupname` |
`GROUPDESCRIPTION` | = | `msdyn_groupdescription` |
`ISSERIALNUMBERENABLEDFORPRODUCTIONCONSUMPTIONPROCESS` | >< | `msdyn_issnenabledforpcprocess` |
`ISSERIALNUMBERCONTROLENABLED` | >< | `msdyn_isserialnumbercontrolenabled` |
`ISSERIALNUMBERENABLEDFORSALESPROCESS` | >< | `msdyn_isserialnumberenabledforsalesprocess` |
`ISSERIALNUMBERACTIVE` | >< | `msdyn_isserialnumberactive` |
`ISSALESPRICEBYSERIALNUMBER` | >< | `msdyn_issalespricebyserialnumber` |
`ISSALESPRICEBYBATCHNUMBER` | >< | `msdyn_issalespricebybatchnumber` |
`ISPURCHASEPRICEBYSERIALNUMBER` | >< | `msdyn_ispurchasepricebyserialnumber` |
`ISPURCHASEPRICEBYBATCHNUMBER` | >< | `msdyn_ispurchasepricebybatchnumber` |
`ISPRIMARYSTOCKINGENABLEDFORSERIALNUMBER` | >< | `msdyn_isprimarystockingenabledforsn` |
`ISPRIMARYSTOCKINGENABLEDFORBATCHNUMBER` | >< | `msdyn_isprimarystockingenabledforbn` |
`ISPHYSICALINVENTORYENABLEDFORSERIALNUMBER` | >< | `msdyn_isphysicalinventoryenabledforsn` |
`ISPHYSICALINVENTORYENABLEDFORBATCHNUMBER` | >< | `msdyn_isphysicalinventoryenabledforbn` |
`ISFINANCIALINVENTORYENABLEDFORSERIALNUMBER` | >< | `msdyn_isfinancialinventoryenabledforsn` |
`ISFINANCIALINVENTORYENABLEDFORBATCHNUMBER` | >< | `msdyn_isfinancialinventoryenabledforbn` |
`ISCOVERAGEPLANENABLEDFORSERIALNUMBER` | >< | `msdyn_iscoverageplanenabledforserialnumber` |
`ISCOVERAGEPLANENABLEDFORBATCHNUMBER` | >< | `msdyn_iscoverageplanenabledforbatchnumber` |
`ISBLANKRECEIPTALLOWEDFORSERIALNUMBER` | >< | `msdyn_isblankreceiptallowedforserialnumber` |
`ISBLANKRECEIPTALLOWEDFORBATCHNUMBER` | >< | `msdyn_isblankreceiptallowedforbatchnumber` |
`ISBLANKISSUEALLOWEDFORSERIALNUMBER` | >< | `msdyn_isblankissueallowedforserialnumber` |
`ISBLANKISSUEALLOWEDFORBATCHNUMBER` | >< | `msdyn_isblankissueallowedforbatchnumber` |
`ISBATCHNUMBERACTIVE` | >< | `msdyn_isbatchnumberactive` |
`ISINVENTORYOWNERACTIVE` | >< | `msdyn_isinventoryowneractive` |

###  <a name="199"></a>Unit conversions (msdyn_unitofmeasureconversions)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DENOMINATOR` | = | `msdyn_denominator` |
`NUMERATOR` | = | `msdyn_numerator` |
`FACTOR` | = | `msdyn_factor` |
`INNEROFFSET` | = | `msdyn_inneroffset` |
`OUTEROFFSET` | = | `msdyn_outeroffset` |
`ROUNDING` | >< | `msdyn_rounding` |
`TOUNITSYMBOL` | = | `msdyn_tounit.msdyn_symbol` |
`FROMUNITSYMBOL` | = | `msdyn_fromunit.msdyn_symbol` |

###  <a name="219"></a>Units (uoms)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`UNITSYMBOL` | > | `msdyn_symbol` |
`UNITCLASS` | > | `msdyn_externalunitclassname` |
`DECIMALPRECISION` | > | `msdyn_decimalprecision` |
`ISBASEUNIT` | >> | `msdyn_isbaseunit` |
`ISSYSTEMUNIT` | >> | `msdyn_issystemunit` |
`SYSTEMOFUNITS` | >> | `msdyn_systemofunits` |
`UNITSYMBOL` | > | `name` |
`UNITDESCRIPTION` | > | `msdyn_description` |

###  <a name="231"></a>Vendor document attachments (annotations)

This template synchronizes data between Finance and Operations apps and Dataverse.

Source filter: `((DocumentAttachmentTypeCode == "Note") || (DocumentAttachmentTypeCode == "URL"))`

Reversed source filter: `(objecttypecode eq 'msdyn_vendor'  and msdyn_relatedentityid2 ne null) or (objecttypecode eq 'account' and msdyn_relatedentityid2 ne null)  or (objecttypecode eq 'contact' and msdyn_relatedentityid2 ne null)`

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DOCUMENTID` | = | `msdyn_notesid` |
`NOTES` | = | `notetext` |
`ATTACHMENTDESCRIPTION` | = | `subject` |
`VENDORACCOUNTNUMBER` | = | `msdyn_relatedentityid2` |
`DOCUMENTATTACHMENTTYPECODE` | << | `none` | Note
`none` | >> | `objecttypecode` | msdyn_vendor
`ACCESSRESTRICTION` | >< | `msdyn_restriction` |

###  <a name="200"></a>Vendor groups (msdyn_vendorgroups)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DEFAULTPAYMENTTERMNAME` | = | `msdyn_paymentterms.msdyn_name` |
`DESCRIPTION` | = | `msdyn_description` |
`VENDORGROUPID` | = | `msdyn_vendorgroup` |
`CLEARINGPERIODPAYMENTTERMNAME` | = | `msdyn_clearingperiodpaymentpermname.msdyn_name` |

###  <a name="201"></a>Vendor payment method (msdyn_vendorpaymentmethods)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`NAME` | = | `msdyn_name` |
`DESCRIPTION` | = | `msdyn_description` |
`SUMBYPERIOD` | >< | `msdyn_sumbyperiod` |
`DISCOUNTGRACEPERIODDAYS` | = | `msdyn_discountgraceperioddays` |
`PAYMENTSTATUS` | >< | `msdyn_paymentstatus` |
`ALLOWPAYMENTCOPIES` | >< | `msdyn_allowpaymentcopies` |
`PAYMENTTYPE` | >< | `msdyn_paymenttype` |
`LASTFILENUMBER` | = | `msdyn_lastfilenumber` |
`LASTFILENUMBERTODAY` | = | `msdyn_lastfilenumbertoday` |
`ACCOUNTTYPE` | >< | `msdyn_accounttype` |
`BRIDGINGPOSTINGENABLED` | >< | `msdyn_bridgingposting` |
`ENABLEPOSTDATEDCHECKCLEARINGPOSTING` | >< | `msdyn_postdatedcheckclearingposting` |
`PROMISSORYNOTEDRAFTTYPE` | >< | `msdyn_promissorynotedrafttype` |
`DIRECTDEBIT` | >< | `msdyn_directdebit` |

###  <a name="202"></a>Vendors V2 (msdyn_vendors)

This template synchronizes data between Finance and Operations apps and Dataverse.

Source filter: `((VendorPartyType == "Organization") || (VendorPartyType == "Person"))`

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`VENDORACCOUNTNUMBER` | = | `msdyn_vendoraccountnumber` |
`VENDORGROUPID` | = | `msdyn_vendorgroupid.msdyn_vendorgroup` |
`VENDORPARTYTYPE` | >< | `msdyn_isperson` |
`CREDITLIMIT` | = | `msdyn_vendorcreditlimit` |
`ISFOREIGNENTITY` | >< | `msdyn_isforeignentity` |
`ISONETIMEVENDOR` | >< | `msdyn_isonetimevendor` |
`CREDITRATING` | = | `msdyn_creditrating` |
`DUNSNUMBER` | = | `msdyn_dunsnumber` |
`ETHNICORIGINID` | = | `msdyn_ethnicorigin` |
`OURACCOUNTNUMBER` | = | `msdyn_ourvendoraccountnumber` |
`PAYMENTID` | = | `msdyn_paymentid` |
`PRIMARYURL` | = | `msdyn_primarycontacturl` |
`DEFAULTPAYMENTDAYNAME` | = | `msdyn_defaultpaymentdayname.msdyn_name` |
`DEFAULTPAYMENTSCHEDULENAME` | = | `msdyn_paymentschedule.msdyn_name` |
`DEFAULTPAYMENTTERMSNAME` | = | `msdyn_paymentterms.msdyn_name` |
`HASONLYTAKENBIDS` | >< | `msdyn_hasonlytakenbids` |
`ISMINORITYOWNED` | >< | `msdyn_isminorityowned` |
`ISVENDORLOCALLYOWNED` | >< | `msdyn_isvendorlocallyowned` |
`ISSERVICEVETERANOWNED` | >< | `msdyn_isserviceveteranowned` |
`ISOWNERDISABLED` | >< | `msdyn_ownerisdisabled` |
`ISWOMANOWNER` | >< | `msdyn_womanowner` |
`ORGANIZATIONEMPLOYEEAMOUNT` | = | `msdyn_numberofemployees` |
`VENDORHOLDRELEASEDATE` | = | `msdyn_vendoronholdreleasedate` |
`VENDORPARTYNUMBER` | = | `msdyn_partyid.msdyn_partynumber` |
`ONHOLDSTATUS` | >< | `msdyn_onholdstatus` |
`CURRENCYCODE` | = | `msdyn_currencycode.isocurrencycode` |
`ISVENDORLOCATEDINHUBZONE` | >< | `msdyn_isvendorlocatedinhubzone` |
`DEFAULTVENDORPAYMENTMETHODNAME` | = | `msdyn_vendorpaymentmethod.msdyn_name` |
`INVOICEVENDORACCOUNTNUMBER` | = | `msdyn_invoicevendoraccountnumber.msdyn_vendoraccountnumber` |
`AREPRICESINCLUDINGSALESTAX` | >< | `msdyn_priceincludessalestax` |
`SALESTAXGROUPCODE` | = | `msdyn_taxgroup.msdyn_name` |
`PRIMARYCONTACTPERSONID` | = | `msdyn_primarycontact.msdyn_contactforpartynumber` |

###  <a name="112"></a>Veteran status (cdm_veteranstatuses)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`VETERANSTATUSID` | = | `cdm_name` |
`DESCRIPTION` | = | `cdm_description` |
`ISPROTECTEDVETERAN` | >< | `cdm_isprotectedveteran` |

###  <a name="144"></a>Warehouse locations (msdyn_inventorylocations)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`BINID` | = | `msdyn_binid` |
`CHECKDIGITS` | = | `msdyn_checkdigits` |
`GENERATECHECKDIGITS` | >< | `msdyn_generatecheckdigits` |
`ISSORTORDERCODEMANUAL` | >< | `msdyn_issortordercodemanual` |
`ISWAREHOUSELOCATIONIDMANUAL` | >< | `msdyn_iswarehouselocationidmanual` |
`LASTCOUNTEDUTCDATETIME` | = | `msdyn_lastcountedutcdatetime` |
`PHYSICALDEPTH` | = | `msdyn_physicaldepth` |
`PHYSICALHEIGHT` | = | `msdyn_physicalheight` |
`PHYSICALHEIGHTABOVEGROUND` | = | `msdyn_physicalheightaboveground` |
`PHYSICALMAXIMUMSTORAGEVOLUME` | = | `msdyn_physicalmaximumstoragevolume` |
`PHYSICALMAXIMUMSTORAGEWEIGHT` | = | `msdyn_physicalmaximumstorageweight` |
`PHYSICALWIDTH` | = | `msdyn_physicalwidth` |
`RACKID` | = | `msdyn_rackid` |
`SHELFID` | = | `msdyn_shelfid` |
`WAREHOUSEID` | = | `msdyn_warehouse.msdyn_warehouseidentifier` |
`WAREHOUSELOCATIONID` | = | `msdyn_warehouselocationid` |
`WAREHOUSELOCATIONPROFILEID` | = | `msdyn_warehouselocationprofileid` |
`WAREHOUSELOCATIONTYPE` | >< | `msdyn_warehouselocationtype` |
`INPUTWAREHOUSELOCATIONBLOCKINGCAUSEID` | = | `msdyn_inputwarehouselocationblockingcauseid` |
`OUTPUTWAREHOUSELOCATIONBLOCKINGCAUSEID` | = | `msdyn_outputwarehouselocationblockingcauseid` |
`ISDEFAULTCREDITONLYRETURNWAREHOUSELOCATION` | >< | `msdyn_isdefaultcreditonlyreturnwarehouseloc` |
`ISDEFAULTISSUEWAREHOUSELOCATION` | >< | `msdyn_isdefaultissuewarehouselocation` |
`ISDEFAULTKANBANFINISHEDGOODSWAREHOUSELOCATION` | >< | `msdyn_isdefaultkanbanfinishedgoodswarehouseloc` |
`ISDEFAULTPRODUCTIONFINISHEDGOODSWAREHOUSELOCATION` | >< | `msdyn_isdefaultproductionfinishedgoodswhsloc` |
`ISDEFAULTPRODUCTIONINPUTWAREHOUSELOCATION` | >< | `msdyn_isdefaultproductioninputwarehouseloc` |
`ISDEFAULTRECEIPTWAREHOUSELOCATION` | >< | `msdyn_isdefaultreceiptwarehouselocation` |
`ISDEFAULTRETAILSTORERETURNWAREHOUSELOCATION` | >< | `msdyn_isdefaultretailstorereturnwarehouseloc` |
`ISDEFAULTRETAILSTOREWAREHOUSELOCATION` | >< | `msdyn_isdefaultretailstorewarehouselocation` |
`ISDEFAULTSHIPMENTMAINTENANCEWAREHOUSELOCATION` | >< | `msdyn_isdefaultshipmentmaintenancewarehouseloc` |
`AGINGDATE` | > | `msdyn_agingdate` |
`LASTACTIVITYDATETIME` | > | `msdyn_lastactivitydatetime` |
`LOCATIONSTATUS` | >> | `msdyn_locationstatus` |
`ISITEMINLOCATIONMAINTAINED` | >< | `msdyn_isiteminlocationmaintained` |
`ISLOCATIONACTIVITYDATETIMEMAINTAINED` | >< | `msdyn_islocationactivitydatetimemaintained` |
`ISLOCATIONSTATUSMAINTAINED` | >< | `msdyn_islocationstatusmaintained` |
`ISDEFAULTQUALITYMAINTENANCEWAREHOUSELOCATION` | >< | `msdyn_isdefaultqualitymaintenancewarehouseloc` |
`WAREHOUSEAISLEID` | = | `msdyn_warehouseaisle.msdyn_aisleid` |
`WAREHOUSEID` | > | `msdyn_warehouseaisle.msdyn_warehouse.msdyn_warehouseidentifier` |
`WAREHOUSEZONEID` | = | `msdyn_warehousezone.msdyn_zoneid` |
`FIRSTADDITIONALWAREHOUSEZONEID` | = | `msdyn_firstadditionalwarehousezone.msdyn_zoneid` |
`SECONDADDITIONALWAREHOUSEZONEID` | = | `msdyn_secondadditionalwarehousezone.msdyn_zoneid` |
`THIRDADDITIONALWAREHOUSEZONEID` | = | `msdyn_thirdadditionalwarehousezone.msdyn_zoneid` |
`ITEMNUMBERINLOCATION` | = | `msdyn_itemnumberinlocation.msdyn_itemnumber` |

###  <a name="205"></a>Warehouse work headers (msdyn_warehouseworkheaders)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`ACTUALPROCESSINGTIMESECONDS` | > | `msdyn_actualprocessingtimeseconds` |
`ESTIMATEDPROCESSINGTIMESECONDS` | > | `msdyn_estimatedprocessingtimeseconds` |
`ISWAREHOUSEWORKBLOCKED` | >> | `msdyn_iswarehouseworkblocked` |
`WAREHOUSEID` | > | `msdyn_warehouse.msdyn_warehouseidentifier` |
`INVENTORYSITEID` | > | `msdyn_inventorysite.msdyn_siteid` |
`ISWAREHOUSEWORKERMANUALLYASSIGNED` | >> | `msdyn_iswarehouseworkermanuallyassigned` |
`WAREHOUSEWORKCANCELLEDDATETIME` | > | `msdyn_warehouseworkcancelleddatetime` |
`WAREHOUSEWORKCLOSEDDATETIME` | > | `msdyn_warehouseworkcloseddatetime` |
`WAREHOUSEWORKID` | > | `msdyn_warehouseworkid` |
`WAREHOUSEWORKPROCESSINGSTARTDATETIME` | > | `msdyn_warehouseworkprocessingstartdatetime` |
`WAREHOUSEWORKPRIORITY` | > | `msdyn_warehouseworkpriority` |
`WAREHOUSEWORKSTATUS` | >> | `msdyn_warehouseworkstatus` |
`WAREHOUSEWORKORDERTYPE` | >> | `msdyn_warehouseworkordertype` |
`CONTAINERID` | > | `msdyn_containerid` |
`WAREHOUSEWORKLOCKINGWAREHOUSEMOBILEDEVICEUSERID` | > | `msdyn_warehouseworklockingmobiledeviceuserid` |
`TARGETLICENSEPLATENUMBER` | > | `msdyn_targetlicenseplatenumber` |
`WAVEID` | > | `msdyn_waveid` |
`WAREHOUSEWORKCANCELLINGUSERID` | > | `msdyn_warehouseworkcancellinguserid` |
`WAREHOUSEWORKMANUALLYCOMPLETINGUSERID` | > | `msdyn_warehouseworkmanuallycompletinguserid` |
`WAREHOUSEWORKPOOLID` | > | `msdyn_warehouseworkpoolid` |

###  <a name="206"></a>Warehouse work lines (msdyn_warehouseworklines)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`ACTUALPROCESSINGTIMESECONDS` | > | `msdyn_actualprocessingtimeseconds` |
`ESTIMATEDPROCESSINGTIMESECONDS` | > | `msdyn_estimatedprocessingtimeseconds` |
`FEFOITEMBATCHNUMBER` | > | `msdyn_fefoitembatchnumber` |
`REMAININGHANDLINGQUANTITY` | > | `msdyn_remaininghandlingquantity` |
`HANDLINGQUANTITY` | > | `msdyn_handlingquantity` |
`WORKLINENUMBER` | > | `msdyn_worklinenumber` |
`ISWORKLINEMANDATORY` | >> | `msdyn_isworklinemandatory` |
`REMAININGWORKQUANTITY` | > | `msdyn_remainingworkquantity` |
`WORKQUANTITY` | > | `msdyn_workquantity` |
`ISREPLENISHMENTNEEDED` | >> | `msdyn_isreplenishmentneeded` |
`SORTORDERCODE` | > | `msdyn_sortordercode` |
`WORKQUANTITYUNITSYMBOL` | > | `msdyn_workquantityunit.msdyn_symbol` |
`WAREHOUSEWORKCLOSEDDATETIME` | > | `msdyn_warehouseworkcloseddatetime` |
`WAREHOUSEWORKID` | > | `msdyn_warehousework.msdyn_warehouseworkid` |
`WAREHOUSEWORKPROCESSINGSTARTDATETIME` | > | `msdyn_warehouseworkprocessingstartdatetime` |
`WAREHOUSEWORKSTATUS` | >> | `msdyn_warehouseworkstatus` |
`ISWORKEXECUTIONSTOPPED` | >> | `msdyn_isworkexecutionstopped` |
`WAREHOUSEWORKTYPE` | >> | `msdyn_warehouseworktype` |
`EXTRAHANDLINGQUANTITY` | > | `msdyn_extrahandlingquantity` |
`CAPTUREDWEIGHT` | > | `msdyn_capturedweight` |
`WAREHOUSEID` | > | `msdyn_warehouse.msdyn_warehouseidentifier` |
`INVENTORYSITEID` | > | `msdyn_inventorysite.msdyn_siteid` |
`CONTAINERID` | > | `msdyn_containerid` |
`PROCESSINGWAREHOUSEMOBILEDEVICEUSERID` | > | `msdyn_processingwarehousemobiledeviceuserid` |
`ITEMBATCHNUMBER` | > | `msdyn_itembatchnumber` |
`INVENTORYOWNERID` | > | `msdyn_inventoryownerid` |
`ITEMSERIALNUMBER` | > | `msdyn_itemserialnumber` |
`INVENTORYSTATUSID` | > | `msdyn_inventorystatusid` |
`LICENSEPLATENUMBER` | > | `msdyn_licenseplatenumber` |
`ITEMNUMBER` | > | `msdyn_item.msdyn_itemnumber` |
`WAREHOUSEZONEID` | > | `msdyn_warehousezone.msdyn_zoneid` |
`WAREHOUSELOCATIONID` | > | `msdyn_warehouselocation.msdyn_warehouselocationid` |
`WAREHOUSEID` | > | `msdyn_warehouselocation.msdyn_warehouse.msdyn_warehouseidentifier` |
`PRODUCTCONFIGURATIONID` | > | `msdyn_productconfiguration.msdyn_productconfiguration` |
`PRODUCTCOLORID` | > | `msdyn_productcolor.msdyn_productcolorname` |
`PRODUCTSIZEID` | > | `msdyn_productsize.msdyn_productsize` |
`PRODUCTSTYLEID` | > | `msdyn_productstyle.msdyn_productstyle` |

###  <a name="207"></a>Warehouse zone groups (msdyn_warehousezonegroups)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`GROUPID` | = | `msdyn_groupid` |
`GROUPNAME` | = | `msdyn_groupname` |

###  <a name="208"></a>Warehouse zones (msdyn_warehousezones)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`WAREHOUSEZONEGROUPID` | = | `msdyn_warehousezonegroup.msdyn_groupid` |
`ZONEID` | = | `msdyn_zoneid` |
`ZONENAME` | = | `msdyn_zonename` |

###  <a name="204"></a>Warehouses (msdyn_warehouses)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`DEFAULTCONTAINERTYPEID` | = | `msdyn_defaultcontainertypeid` |
`AREITEMSCOVERAGEPLANNEDMANUALLY` | >< | `msdyn_areitemscoverageplannedmanually` |
`ARELABORSTANDARDSALLOWED` | >< | `msdyn_arelaborstandardsallowed` |
`PRIMARYADDRESSBUILDINGCOMPLIMENT` | = | `msdyn_primaryaddressbuildingcompliment` |
`PRIMARYADDRESSPOSTBOX` | = | `msdyn_primaryaddresspostbox` |
`PRIMARYADDRESSSTREETNUMBER` | = | `msdyn_primaryaddressstreetnumber` |
`AREWAREHOUSELOCATIONCHECKDIGITSUNIQUE` | >< | `msdyn_arewarehouselocationcheckdigitsunique` |
`INVENTORYCOUNTINGREASONCODEPOLICYNAME` | = | `msdyn_inventorycountingreasoncodepolicyname` |
`AUTOUPDATESHIPMENTRULE` | >< | `msdyn_autoupdateshipmentrule` |
`WAREHOUSERELEASERESERVATIONREQUIREMENTRULE` | >< | `msdyn_warehousereleasereservationrequirement` |
`EXTERNALLYLOCATEDWAREHOUSEVENDORACCOUNTNUMBER` | = | `msdyn_externallylocatedwarehousevendoraccountnu` |
`INVENTORYSTATUSCHANGERESERVATIONREMOVALLEVEL` | >< | `msdyn_inventorystatuschangereservationremoval` |
`WAREHOUSEWORKPROCESSINGPOLICYNAME` | = | `msdyn_warehouseworkprocessingpolicyname` |
`ISFALLBACKWAREHOUSE` | >< | `msdyn_isfallbackwarehouse` |
`ISFINANCIALNEGATIVERETAILSTOREINVENTORYALLOWED` | >< | `msdyn_financialnegativestoreinventoryallowed` |
`ISPALLETMOVEMENTDURINGCYCLECOUNTINGALLOWED` | >< | `msdyn_palletmovementduringcyclecountingallowed` |
`ISPHYSICALNEGATIVERETAILSTOREINVENTORYALLOWED` | >< | `msdyn_physicalnegativestoreinventoryallowed` |
`ISREFILLEDFROMMAINWAREHOUSE` | >< | `msdyn_isrefilledfrommainwarehouse` |
`ISRETAILSTOREWAREHOUSE` | >< | `msdyn_isretailstorewarehouse` |
`MAINREFILLINGWAREHOUSEID` | = | `msdyn_mainrefillingwarehouse.msdyn_warehouseidentifier` |
`MASTERPLANNINGWORKCALENDARDID` | = | `msdyn_masterplanningworkcalendarid` |
`MAXIMUMBATCHPICKINGLISTQUANTITY` | = | `msdyn_maximumbatchpickinglistquantity` |
`MAXIMUMPICKINGLISTLINEQUANTITY` | = | `msdyn_maximumpickinglistlinequantity` |
`OPERATIONALSITEID` | = | `msdyn_operationalsite.msdyn_siteid` |
`QUARANTINEWAREHOUSEID` | = | `msdyn_quarantinewarehouse.msdyn_warehouseidentifier` |
`RETAILSTOREQUANTITYALLOCATIONREPLENISMENTRULEWEIGHT` | = | `msdyn_storeqtyallocationreplenishmentweight` |
`SHOULDWAREHOUSELOCATIONIDINCLUDEAISLEID` | >< | `msdyn_shouldwarehouselocationincludeaisleid` |
`TRANSITWAREHOUSEID` | = | `msdyn_transitwarehouse.msdyn_warehouseidentifier` |
`WAREHOUSEID` | = | `msdyn_warehouseidentifier` |
`WAREHOUSEID` | > | `msdyn_name` |
`WAREHOUSELOCATIONIDBINIDFORMAT` | = | `msdyn_warehouselocationidbinidformat` |
`WAREHOUSELOCATIONIDRACKIDFORMAT` | = | `msdyn_warehouselocationidrackidformat` |
`WAREHOUSELOCATIONIDSHELFIDFORMAT` | = | `msdyn_warehouselocationidshelfidformat` |
`WAREHOUSENAME` | = | `msdyn_description` |
`WAREHOUSESPECIFICDEFAULTINVENTORYSTATUSID` | = | `msdyn_warehousespecificdefaultinventorystatusid` |
`WAREHOUSETYPE` | >< | `msdyn_warehousetype` |
`ISPRIMARYADDRESSASSIGNED` | >< | `msdyn_isprimaryaddressassigned` |
`PRIMARYADDRESSCITY` | = | `msdyn_primaryaddresscity` |
`PRIMARYADDRESSCOUNTRYREGIONID` | = | `msdyn_primaryaddresscountryregionid` |
`PRIMARYADDRESSCOUNTYID` | = | `msdyn_primaryaddresscountyid` |
`PRIMARYADDRESSDISTRICTNAME` | = | `msdyn_primaryaddressdistrictname` |
`PRIMARYADDRESSLATITUDE` | = | `msdyn_primaryaddresslatitude` |
`PRIMARYADDRESSLONGITUDE` | = | `msdyn_primaryaddresslongitude` |
`PRIMARYADDRESSLOCATIONROLES` | = | `msdyn_primaryaddresslocationroles` |
`PRIMARYADDRESSLOCATIONSALESTAXGROUPCODE` | = | `msdyn_primaryaddresslocationsalestaxgroupcode` |
`PRIMARYADDRESSSTATEID` | = | `msdyn_primaryaddressstateid` |
`PRIMARYADDRESSSTREET` | = | `msdyn_primaryaddressstreet` |
`PRIMARYADDRESSZIPCODE` | = | `msdyn_primaryaddresszipcode` |
`EXTERNALLYLOCATEDWAREHOUSECUSTOMERACCOUNTNUMBER` | = | `msdyn_externallylocatedwarehousecustomeraccount` |
`PRIMARYADDRESSCITYINKANA` | = | `msdyn_primaryaddresscityinkana` |
`PRIMARYADDRESSSTREETINKANA` | = | `msdyn_primaryaddressstreetinkana` |
`PRIMARYADDRESSDESCRIPTION` | = | `msdyn_primaryaddressdescription` |
`AREADVANCEDWAREHOUSEMANAGEMENTPROCESSESENABLED` | >< | `msdyn_useadvancedwarehousemanagementprocesses` |
`AREPICKINGLISTSDELIVERYMODESPECIFIC` | >< | `msdyn_arepickinglistsdeliverymodespecific` |
`AREPICKINGLISTSSHIPMENTSPECIFICONLY` | >< | `msdyn_arepickinglistshipmentspecificonly` |
`FORMATTEDPRIMARYADDRESS` | = | `msdyn_formattedprimaryaddress` |
`ISBILLOFLADINGPRINTINGBEFORESHIPMENTCONFIRMATIONENABLED` | >< | `msdyn_printbillofladingbeforeshipconfirmation` |
`RAWMATERIALPICKINGINVENTORYISSUESTATUS` | >< | `msdyn_rawmaterialpickinginventoryissuestatus` |
`WILLAUTOMATICLOADRELEASERESERVEINVENTORY` | >< | `msdyn_willautomaticloadreleaseinventory` |
`WILLINVENTORYSTATUSCHANGEREMOVEBLOCKING` | >< | `msdyn_willinventorystatuschangeremoveblocking` |
`WILLMANUALLOADRELEASERESERVEINVENTORY` | >< | `msdyn_willmanualloadreleasereserveinventory` |
`WILLORDERRELEASINGCONSOLIDATESHIPMENTS` | >< | `msdyn_willorderreleasingconsolidateshipments` |
`WILLPRODUCTIONBOMSRESERVEWAREHOUSELEVELONLY` | >< | `msdyn_productionbomsreservewarehouselevel` |
`WILLSHIPPINGCANCELLATIONDECREMENTLOADQUANITY` | >< | `msdyn_shippingcanceldecrementloadquantity` |
`WILLWAREHOUSELOCATIONIDINCLUDEBINIDBYDEFAULT` | >< | `msdyn_warehouselocationidincludeblindid` |
`WILLWAREHOUSELOCATIONIDINCLUDERACKIDBYDEFAULT` | >< | `msdyn_warehouselocationincluderackidbydefault` |
`WILLWAREHOUSELOCATIONIDINCLUDESHELFIDBYDEFAULT` | >< | `msdyn_warehouselocationidincludeshelfid` |

###  <a name="210"></a>Withholding tax codes (msdyn_withholdingtaxcodes)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`WITHHOLDINGCODE` | = | `msdyn_name` |
`WITHHOLDINGTAXNAME` | = | `msdyn_description` |
`WITHHOLDINGTAXROUNDOFF` | = | `msdyn_roundoff` |
`WITHHOLDINGTAXROUNDOFFTYPE` | >< | `msdyn_roundofftype` |
`CURRENCYCODEID` | = | `msdyn_currency.isocurrencycode` |
`WITHHOLDINGTAXBASE` | >< | `msdyn_taxableamountorigin` |

###  <a name="211"></a>Withholding tax groups (msdyn_withholdingtaxgroups)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`WITHHOLDINGTAXGROUPCODE` | = | `msdyn_name` |
`DESCRIPTION` | = | `msdyn_description` |

###  <a name="113"></a>Worker (cdm_workers)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement column | Default value
---|---|---|---
`PERSONNELNUMBER` | = | `cdm_workernumber` |
`FIRSTNAME` | = | `cdm_firstname` |
`MIDDLENAME` | = | `cdm_middlename` |
`LASTNAME` | = | `cdm_lastname` |
`WORKERTYPE` | >> | `cdm_type` |
`WORKERSTATUS` | >> | `cdm_status` |
`PRIMARYCONTACTEMAIL` | = | `cdm_primaryemailaddress` |
`PRIMARYCONTACTPHONE` | = | `cdm_primarytelephone` |
`PRIMARYCONTACTFACEBOOK` | = | `cdm_facebookidentity` |
`PRIMARYCONTACTTWITTER` | = | `cdm_twitteridentity` |
`PRIMARYCONTACTLINKEDIN` | = | `cdm_linkedinidentity` |
`PRIMARYCONTACTURL` | = | `cdm_websiteurl` |
`GENDER` | >< | `cdm_gender` |
`BIRTHDATE` | = | `cdm_birthdate` |
`NAME` | > | `cdm_fullname` |

