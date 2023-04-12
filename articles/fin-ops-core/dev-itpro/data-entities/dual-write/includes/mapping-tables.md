###  <a name="138"></a>All products (msdyn_globalproducts)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PRODUCTNAME | > | msdyn_productname |
PRODUCTNUMBER | > | msdyn_productnumber |

###  <a name="119"></a>Asset management asset lifecycle models (msdyn_assetlifecyclemodels)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
ACTIVELIFECYCLESTATEID | = | msdyn_activelifecyclestate.msdyn_assetlifecyclestate_id |
INBOUNDLIFECYCLESTATEID | = | msdyn_inboundlifecyclestate.msdyn_assetlifecyclestate_id |
INSTORAGELIFECYCLESTATEID | = | msdyn_instoragelifecyclestate.msdyn_assetlifecyclestate_id |
LIFECYCLEMODELID | = | msdyn_assetlifecyclemodel_id |
NAME | = | msdyn_name |
ONLOANLIFECYCLESTATEID | = | msdyn_onloanlifecyclestate.msdyn_assetlifecyclestate_id |
OUTBOUNDLIFECYCLESTATEID | = | msdyn_outboundlifecyclestate.msdyn_assetlifecyclestate_id |
RECEIVEDLIFECYCLESTATEID | = | msdyn_receivedlifecyclestate.msdyn_assetlifecyclestate_id |

###  <a name="120"></a>Asset management asset lifecycle states (msdyn_assetlifecyclestates)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DELETEOPENCALENDARLINES | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_deleteopencalendarlines |
LIFECYCLESTATEID | = | msdyn_assetlifecyclestate_id |
LINE | = | msdyn_line |
MAINTENANCEASSETACTIVE | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_maintenanceassetactive |
NAME | = | msdyn_name |

###  <a name="124"></a>Asset management asset types (msdyn_customerassetcategories)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
LIFECYCLEMODELID | = | msdyn_lifecyclemodel.msdyn_assetlifecyclemodel_id |
MAINTENANCEASSETTYPEID | = | msdyn_maintenanceassettypeid |
NAME | = | msdyn_name |
CALCULATEKPITOTAL | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_calculatekpitotal |

###  <a name="125"></a>Asset management assets (msdyn_customerassets)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
ACQUISITIONCOST | = | msdyn_acquisitioncost |
ACQUISITIONDATE | = | msdyn_acquisitiondate |
ACTIVEFROM | = | msdyn_activefrom |
ACTIVETO | = | msdyn_activeto |
FUNCTIONALLOCATIONID | = | msdyn_functionallocation.msdyn_functionallocation_id |
MAINTENANCEASSETLIFECYCLESTATEID | = | msdyn_assetlifecyclestate.msdyn_assetlifecyclestate_id |
MODELID | = | msdyn_model.msdyn_model_id |
MODELPRODUCTID | = | msdyn_model.msdyn_manufacturer.msdyn_manufacturer_id |
MODELYEAR | = | msdyn_modelyear |
NAME | = | msdyn_name |
NOTES | = | msdyn_notes |
PURCHASEORDERID | = | msdyn_purchaseorderid |
REPLACEMENTDATE | ><<br>`1/1/1900` : blank | msdyn_replacementdate |
REPLACEMENTVALUE | = | msdyn_replacementvalue |
SERIALID | = | msdyn_serialid |
VENDACCOUNT | = | msdyn_vendaccount |
WARRANTYDATEFROMVEND | = | msdyn_warrantydatefromvend |
WARRANTYID | = | msdyn_warranty.msdyn_warranty_id |
WRKCTRID | = | msdyn_wrkctrid |
FIXEDASSETID | = | msdyn_fixedassetid |
MAINTENANCEASSETID | = | msdyn_maintenanceassetid |
PARENTMAINTENANCEASSETID | = | msdyn_parentasset.msdyn_maintenanceassetid |
MAINTENANCEASSETTYPEID | = | msdyn_customerassetcategory.msdyn_maintenanceassettypeid |
PRODUCTID | = | msdyn_manufacturer.msdyn_manufacturer_id |

###  <a name="134"></a>Asset management functional location lifecycle models (msdyn_functionallocationlifecyclemodels)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
LIFECYCLEMODELID | = | msdyn_functionallocationlifecyclemodel_id |
NAME | = | msdyn_name |

###  <a name="135"></a>Asset management functional location lifecycle states (msdyn_functionallocationlifecyclestates)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
ALLOWDELETELOCATION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_allowdeletelocation |
ALLOWNEWSUBLOCATIONS | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_allownewsublocations |
ALLOWRENAMELOCATION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_allowrenamelocation |
FUNCTIONALLOCATIONACTIVE | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_functionallocationactive |
LIFECYCLESTATEID | = | msdyn_functionallocationlifecyclestate_id |
NAME | = | msdyn_name |
ALLOWINSTALLMAINTENANCEASSETS | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_allowinstallmaintenanceassets |
CREATELOCATIONMAINTENANCEASSET | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_createlocationmaintenanceasset |
MAINTENANCEASSETLIFECYCLESTATEID | = | msdyn_assetlifecyclestate.msdyn_assetlifecyclestate_id |

###  <a name="137"></a>Asset management functional location types (msdyn_functionallocationtypes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
ALLOWMULTIPLEINSTALLEDASSETS | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_allowmultipleinstalledassets |
FUNCTIONALLOCATIONTYPEID | = | msdyn_functionallocationtype_id |
NAME | = | msdyn_name |
UPDATEASSETDIMENSION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_updateassetdimension |
LIFECYCLEMODELID | = | msdyn_lifecyclemodelid.msdyn_functionallocationlifecyclemodel_id |
MAINTENANCEASSETTYPEID | = | msdyn_maintenanceassettype.msdyn_maintenanceassettypeid |

###  <a name="136"></a>Asset management functional locations (msdyn_functionallocations)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
FUNCTIONALLOCATIONID | = | msdyn_functionallocation_id |
INVENTORYLOCATIONID | = | msdyn_inventorylocationid |
INVENTORYSITEID | = | msdyn_inventorysiteid |
NAME | = | msdyn_name |
NOTES | = | msdyn_notes |
PARENTFUNCTIONALLOCATIONID | = | msdyn_parentfunctionallocation.msdyn_functionallocation_id |
FUNCTIONALLOCATIONLIFECYCLESTATEID | = | msdyn_functionallocationlifecyclestate.msdyn_functionallocationlifecyclestate_id |
FUNCTIONALLOCATIONTYPEID | = | msdyn_functionallocationtype.msdyn_functionallocationtype_id |

###  <a name="153"></a>Asset management manufacturers (msdyn_manufacturers)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DESCRIPTION | = | msdyn_description |
PRODUCTID | = | msdyn_manufacturer_id |

###  <a name="154"></a>Asset management models (msdyn_models)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DESCRIPTION | = | msdyn_description |
MODELID | = | msdyn_model_id |
PRODUCTID | = | msdyn_manufacturer.msdyn_manufacturer_id |
MAINTENANCEASSETTYPEID | = | msdyn_maintenanceassettype.msdyn_maintenanceassettypeid |

###  <a name="209"></a>Asset management warranty (msdyn_warranties)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
NAME | = | msdyn_name |
WARRANTYID | = | msdyn_warranty_id |

###  <a name="115"></a>CDS Contacts V2 (contacts)

This template synchronizes data between finance and operations apps and Dataverse.

Source filter: (AssociatedContactType = 1)

Reversed source filter: msdyn_contactforvendor eq true and msdyn_sellable eq false and msdyn_contactpersonid ne null

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CONTACTPERSONPARTYNUMBER | = | msdyn_partyid.msdyn_partynumber |
ASSOCIATEDCONTACTTYPE | << | none | Vendor
ASSOCIATEDCONTACTNUMBER | = | msdyn_vendorcontactid.msdyn_vendoraccountnumber |
EMPLOYMENTDEPARTMENT | = | department |
NOTES | = | description |
GOVERNMENTIDENTIFICATIONNUMBER | = | governmentid |
ISRECEIVINGDIRECTMAIL | ><<br>`no` : `False`<br>`yes` : `True` | donotemail |
SPOUSENAME | = | spousesname |
none | >> | msdyn_contactforvendor | True
CONTACTPERSONID | = | msdyn_contactpersonid |

###  <a name="123"></a>CDS Exchange Rates (msdyn_currencyexchangerates)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
EXCHANGERATETYPENAME | > | msdyn_currencyexchangeratepair.msdyn_currencyexchangeratetypeid.msdyn_name |
FROMCURRENCYCODE | > | msdyn_currencyexchangeratepair.msdyn_fromtransactioncurrencyid.isocurrencycode |
TOCURRENCYCODE | > | msdyn_currencyexchangeratepair.msdyn_totransactioncurrencyid.isocurrencycode |
RATE | > | msdyn_exchangerate |
VALIDFROM | > | msdyn_validfrom |
VALIDTO | > | msdyn_validto |

###  <a name="220"></a>CDS Parties (msdyn_parties)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PARTYNUMBER | = | msdyn_partynumber |
PARTYTYPE | ><<br>`person` : `192350001`<br>`organization` : `192350002`<br>`legalEntity` : `192350003`<br>`team` : `192350004`<br>`operatingUnit` : `192350005`<br>`none` : `192350000` | msdyn_partytype |
NAMEALIAS | = | msdyn_namealias |
KNOWNAS | = | msdyn_nickname |
LANGUAGEID | ><<br>`ar` : `192350000`<br>`ar-ae` : `192350001`<br>`en-us` : `192350015`<br>`en-gb` : `192350009`<br>`cs` : `192350002`<br>`da` : `192350003`<br>`de` : `192350004`<br>`de-at` : `192350005`<br>`de-ch` : `192350006`<br>`en-au` : `192350007`<br>`en-ca` : `192350008`<br>`en-ie` : `192350010`<br>`en-in` : `192350011`<br>`en-my` : `192350012`<br>`en-nz` : `192350013`<br>`en-sg` : `192350014`<br>`en-za` : `192350016`<br>`es` : `192350017`<br>`es-mx` : `192350018`<br>`et` : `192350019`<br>`fi` : `192350020`<br>`fr` : `192350021`<br>`fr-be` : `192350022`<br>`fr-ca` : `192350023`<br>`fr-ch` : `192350024`<br>`hu` : `192350025`<br>`is` : `192350026`<br>`it` : `192350027`<br>`it-ch` : `192350028`<br>`ja` : `192350029`<br>`lt` : `192350030`<br>`lv` : `192350031`<br>`nb-no` : `192350032`<br>`nl` : `192350033`<br>`nl-be` : `192350034`<br>`pl` : `192350035`<br>`pt-br` : `192350036`<br>`ru` : `192350037`<br>`sv` : `192350038`<br>`th` : `192350039`<br>`tr` : `192350040`<br>`zh-hans` : `192350041` | msdyn_language |
ORGANIZATIONNAME | = | msdyn_organizationname |
ORGANIZATIONABCCODE | ><<br>`a` : `192350000`<br>`b` : `192350001`<br>`c` : `192350002`<br>`none` : `192350003` | msdyn_organizationabccode |
ORGANIZATIONNUMOFEMPLOYEES | = | msdyn_numberofemployees |
ORGANIZATIONNUMBER | = | msdyn_organizationnumber |
ORGANIZATIONPHONETICNAME | = | msdyn_organizationphoneticname |
PERSONFIRSTNAME | = | msdyn_firstname |
PERSONMIDDLENAME | = | msdyn_middlename |
PERSONLASTNAME | = | msdyn_lastname |
PERSONLASTNAMEPREFIX | = | msdyn_lastnameprefix |
PERSONINITIALS | = | msdyn_initials |
PERSONPROFESSIONALTITLE | = | msdyn_professionaltitle |
PERSONPROFESSIONALSUFFIX | = | msdyn_professionalsuffix |
PERSONPHONETICFIRSTNAME | = | msdyn_phoneticfirstname |
PERSONPHONETICLASTNAME | = | msdyn_phoneticlastname |
PERSONPHONETICMIDDLENAME | = | msdyn_phoneticmiddlename |
PERSONGENDER | ><<br>`male` : `1`<br>`female` : `2`<br>`non-Specific` : `192350000`<br>`unknown` : `192350001` | msdyn_gender |
PERSONMARITALSTATUS | ><<br>`single` : `1`<br>`married` : `2`<br>`divorced` : `3`<br>`widowhood` : `4`<br>`none` : `192350000` | msdyn_maritalstatus |
PERSONHOBBIES | = | msdyn_hobbies |
PERSONCHILDRENNAMES | = | msdyn_childrennames |
PERSONANNIVERSARYDAY | = | msdyn_anniversaryday |
PERSONANNIVERSARYYEAR | = | msdyn_anniversaryyear |
PERSONBIRTHDAY | = | msdyn_birthday |
PERSONBIRTHYEAR | = | msdyn_birthyear |
PERSONANNIVERSARYMONTH | ><<br>`january` : `1`<br>`february` : `2`<br>`march` : `3`<br>`none` : `0`<br>`april` : `4`<br>`may` : `5`<br>`june` : `6`<br>`july` : `7`<br>`august` : `8`<br>`september` : `9`<br>`october` : `10`<br>`november` : `11`<br>`december` : `12` | msdyn_anniversarymonth |
PERSONBIRTHMONTH | ><<br>`none` : `0`<br>`january` : `1`<br>`february` : `2`<br>`march` : `3`<br>`april` : `4`<br>`may` : `5`<br>`june` : `6`<br>`july` : `7`<br>`august` : `8`<br>`september` : `9`<br>`october` : `10`<br>`november` : `11`<br>`december` : `12` | msdyn_birthmonth |

###  <a name="233"></a>CDS Party postal address locations (msdyn_partypostaladdresses)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
ISPRIMARY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isprimary |
LOCATIONID | = | msdyn_postaladdresscollectionid.msdyn_location |
PARTYNUMBER | = | msdyn_partyid.msdyn_partynumber |
PURPOSE | = | msdyn_postaladdresspurposenames |
ISLOCATIONOWNER | >><br>`no` : `False`<br>`yes` : `True` | msdyn_islocationowner |

###  <a name="145"></a>CDS inventory on-hand entries (msdyn_inventoryonhandentries)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
REQUESTID | = | msdyn_request.msdyn_requestid |
INVENTORYSITEID | = | msdyn_inventorysite.msdyn_siteid |
INVENTORYWAREHOUSEID | = | msdyn_inventorywarehouse.msdyn_warehouseidentifier |
AVAILABLEONHANDQUANTITY | > | msdyn_availableonhandquantity |
AVAILABLEORDEREDQUANTITY | > | msdyn_availableorderedquantity |
ONHANDQUANTITY | > | msdyn_onhandquantity |
ONORDERQUANTITY | > | msdyn_onorderquantity |
ORDEREDQUANTITY | > | msdyn_orderedquantity |
RESERVEDONHANDQUANTITY | > | msdyn_reservedonhandquantity |
RESERVEDORDEREDQUANTITY | > | msdyn_reservedorderedquantity |
TOTALAVAILABLEQUANTITY | > | msdyn_totalavailablequantity |
ATPDATE | = | msdyn_atpdate |
ATPQUANTITY | > | msdyn_atpquantity |
PROJECTEDISSUEQUANTITY | > | msdyn_projectedissuequantity |
PROJECTEDONHANDQUANTITY | > | msdyn_projectedonhandquantity |
PROJECTEDRECEIPTQUANTITY | > | msdyn_projectedreceiptquantity |
ORDERQUANTITY | > | msdyn_orderquantity |
UNAVAILABLEONHANDQUANTITY | > | msdyn_unavailableonhandquantity |

###  <a name="147"></a>CDS inventory on-hand requests (msdyn_inventoryonhandrequests)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
REQUESTID | = | msdyn_requestid |
PRODUCTNUMBER | < | msdyn_product.msdyn_productnumber |
ISATPCALCULATION | <<<br>`no` : `False`<br>`yes` : `True` | msdyn_isatpcalculation |
ORDERQUANTITY | < | msdyn_orderquantity |
INVENTORYSITEID | < | msdyn_inventorysite.msdyn_siteid |
INVENTORYWAREHOUSEID | < | msdyn_inventorywarehouse.msdyn_warehouseidentifier |
REFERENCENUMBER | < | msdyn_referencenumber |
LINECREATIONSEQUENCENUMBER | < | msdyn_linecreationsequencenumber |

###  <a name="235"></a>CDS postal address history V2 (msdyn_postaladdresses)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
LOCATIONID | = | msdyn_postaladdresscollectionid.msdyn_location |
VALIDFROM | = | msdyn_validfrom |
VALIDTO | = | msdyn_validto |
DESCRIPTION | = | msdyn_name |
STREET | = | msdyn_street |
STREETNUMBER | = | msdyn_streetnumber |
CITY | = | msdyn_city |
STATE | = | msdyn_state |
COUNTRYREGIONID | = | msdyn_countryregionid |
ZIPCODE | = | msdyn_zipcode |
COUNTY | = | msdyn_county |
DISTRICTNAME | = | msdyn_district |
BUILDINGCOMPLIMENT | = | msdyn_buildingcompliment |
POSTBOX | = | msdyn_postbox |

###  <a name="234"></a>CDS postal address locations (msdyn_postaladdresscollections)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DESCRIPTION | = | msdyn_description |
LOCATIONID | = | msdyn_location |

###  <a name="181"></a>CDS purchase order line entity (msdyn_purchaseorderproducts)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
REQUESTEDDELIVERYDATE | = | msdyn_dateexpected |
LINEDESCRIPTION | = | msdyn_description |
LINENUMBER | = | msdyn_lineorder |
PRODUCTNUMBER | = | msdyn_product.msdyn_productnumber |
PURCHASEORDERNUMBER | = | msdyn_purchaseorder.msdyn_name |
ORDEREDPURCHASEQUANTITY | = | msdyn_quantity |
LINEAMOUNT | > | msdyn_lineamount |
PURCHASEPRICE | > | msdyn_unitcost |
BARCODE | = | msdyn_barcode |
CATCHWEIGHTUNITSYMBOL | = | msdyn_catchweightunitsymbol.msdyn_symbol |
CONFIRMEDSHIPPINGDATE | = | msdyn_confirmedshippingdate |
CUSTOMERREFERENCE | = | msdyn_customerreference |
CUSTOMERREQUISITIONNUMBER | = | msdyn_customerrequisitionnumber |
EXTERNALITEMNUMBER | = | msdyn_externalitemnumber |
ISPARTIALDELIVERYPREVENTED | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_ispartialdeliveryprevented |
LINEDISCOUNTAMOUNT | > | msdyn_linediscountamount |
LINEDISCOUNTPERCENTAGE | > | msdyn_linediscountpercentage |
ORDEREDCATCHWEIGHTQUANTITY | = | msdyn_orderedcatchweightquantity |
PURCHASEORDERLINESTATUS | >><br>`none` : `192350000`<br>`backorder` : `192350001`<br>`received` : `192350002`<br>`invoiced` : `192350003`<br>`canceled` : `192350004` | msdyn_purchaseorderlinestatus |
PURCHASEPRICEQUANTITY | = | msdyn_purchasepricequantity |
RECEIVINGSITEID | = | msdyn_receivingsiteid.msdyn_siteid |
REQUESTEDSHIPPINGDATE | = | msdyn_requestedshippingdate |
REQUESTERPERSONNELNUMBER | = | msdyn_requesterpersonnelnumber.cdm_workernumber |
PROCUREMENTPRODUCTCATEGORYNAME | > | msdyn_procurementproductcategory.msdyn_name |
PROCUREMENTPRODUCTCATEGORYHIERACHYNAME | > | msdyn_procurementproductcategory.msdyn_hierarchy.msdyn_name |
CURRENCYCODE | > | transactioncurrencyid.isocurrencycode |
CONFIRMEDDELIVERYDATE | = | msdyn_confirmeddeliverydate |
DELIVERYADDRESSCITY | > | msdyn_deliveryaddresscity |
DELIVERYADDRESSCOUNTRYREGIONID | > | msdyn_deliveryaddresscountryregionid |
DELIVERYADDRESSSTATEID | > | msdyn_deliveryaddressstate |
DELIVERYADDRESSSTREET | > | msdyn_deliveryaddressstreet |
DELIVERYADDRESSSTREETNUMBER | > | msdyn_deliveryaddressstreetnumber |
DELIVERYADDRESSZIPCODE | > | msdyn_deliveryaddresszipcode |
FORMATTEDDELVERYADDRESS | > | msdyn_formatteddeliveryaddress |
PURCHASEUNITSYMBOL | = | msdyn_unit.msdyn_symbol |
RECEIVINGWAREHOUSEID | = | msdyn_associatetowarehouse.msdyn_warehouseidentifier |
DELIVERYADDRESSDESCRIPTION | > | msdyn_deliveryaddressdescription |
DELIVERYADDRESSNAME | > | msdyn_deliveryaddressname |

###  <a name="182"></a>CDS purchase order line soft deleted entity (msdyn_purchaseorderproducts)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
LINENUMBER | > | msdyn_lineorder |
PURCHASEORDERNUMBER | > | msdyn_purchaseorder.msdyn_name |
ISDELETED | >><br>`yes` : `true`<br>`no` : `false` | msdyn_issoftdeletedinscm |

###  <a name="213"></a>CDS released distinct products (products)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PRODUCTNUMBER | > | msdyn_productnumber |
PRODUCTNAME | > | name |
PRODUCTDESCRIPTION | > | description |
ITEMNUMBER | > | msdyn_itemnumber |
CURRENCYCODE | > | transactioncurrencyid.isocurrencycode |
SALESUNITSYMBOL | > | defaultuomid.msdyn_symbol |
SALESPRICE | > | price |
UNITCOST | > | currentcost |
PRODUCTTYPE | >><br>`item` : `1`<br>`service` : `3` | producttypecode |
SALESUNITDECIMALPRECISION | >> | quantitydecimal | 0
ISCATCHWEIGHTPRODUCT | >><br>`no` : `false`<br>`yes` : `true` | msdyn_iscatchweight |
ISSTOCKEDPRODUCT | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isstockedproduct |
PRODUCTCOLORID | > | msdyn_productcolor.msdyn_productcolorname |
PRODUCTCONFIGURATIONID | > | msdyn_productconfiguration.msdyn_productconfiguration |
PRODUCTSIZEID | > | msdyn_productsize.msdyn_productsize |
PRODUCTSTYLEID | > | msdyn_productstyle.msdyn_productstyle |
FIELDSERVICEPRODUCTTYPE | >><br>`Inventory` : `690970000`<br>`NonInventory` : `690970001`<br>`Service` : `690970002` | msdyn_fieldserviceproducttype |

###  <a name="217"></a>CDS sales order headers (salesorders)

This template synchronizes data between finance and operations apps and Dataverse.

Reversed source filter: msdyn_ordertype eq 192350000

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
SALESORDERNUMBER | = | msdyn_salesordernumber |
ORDERINGCUSTOMERACCOUNTNUMBER | = | customerid.Account(accountnumber).Contact(msdyn_contactpersonid) |
CURRENCYCODE | = | transactioncurrencyid.isocurrencycode |
DELIVERYADDRESSCITY | = | shipto_city |
DELIVERYADDRESSCOUNTRYREGIONISOCODE | ><<br>`us` : `united states`<br>`de` : `germany`<br>`fr` : `france`<br>`gb` : `united kingdom`<br>`jp` : `japan`<br>`in` : `india`<br>`es` : `spain`<br>`nz` : `new zealand`<br>`au` : `australia`<br>`co` : `columbia`<br>`za` : `south africa`<br>`be` : `belgium`<br>`ca` : `canada`<br>`at` : `austria`<br>`tr` : `türkiye`<br>`cn` : `china`<br>`dk` : `denmark`<br>`se` : `sweden`<br>`no` : `norway`<br>`fi` : `finland`<br>`eg` : `egypt` | shipto_country |
DELIVERYADDRESSSTREETNUMBER | = | shipto_line2 |
DELIVERYADDRESSZIPCODE | = | shipto_postalcode |
DELIVERYADDRESSSTREET | = | shipto_line1 |
DELIVERYADDRESSSTATEID | = | shipto_stateorprovince |
SALESORDERNAME | > | name |
INVOICEADDRESSCITY | > | billto_city |
INVOICEADDRESSSTREET | > | billto_line1 |
INVOICEADDRESSSTREETNUMBER | > | billto_line2 |
INVOICEADDRESSCOUNTRYREGIONISOCODE | > | billto_country |
INVOICEADDRESSSTATEID | > | billto_stateorprovince |
INVOICEADDRESSZIPCODE | > | billto_postalcode |
ORDERTOTALAMOUNT | > | totalamount |
TOTALDISCOUNTAMOUNT | > | discountamount |
ORDERTOTALTAXAMOUNT | > | totaltax |
ORDERTOTALCHARGESAMOUNT | > | freightamount |
AREPRICESINCLUDINGSALESTAX | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_arepricesincludingsalestax |
CONFIRMEDRECEIPTDATE | = | msdyn_confirmedreceiptdate |
CONFIRMEDSHIPPINGDATE | = | msdyn_confirmedshippingdate |
CONTACTPERSONID | = | msdyn_associatedcontact.msdyn_contactforpartynumber |
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
FORMATTEDDELVERYADDRESS | > | msdyn_formatteddeliveryaddress |
EMAIL | = | emailaddress |
FORMATTEDINVOICEADDRESS | > | msdyn_formattedinvoiceaddress |
INVOICEADDRESSCOUNTYID | > | msdyn_invoiceaddresscountyid |
INVOICEADDRESSDISTRICTNAME | > | msdyn_invoiceaddressdistrictname |
INVOICEADDRESSLATITUDE | > | msdyn_invoiceaddresslatitude |
INVOICEADDRESSLONGITUDE | > | msdyn_invoiceaddresslongitude |
INVOICEADDRESSPOSTBOX | > | msdyn_invoiceaddresspostbox |
INVOICEBUILDINGCOMPLIMENT | > | msdyn_invoicebuildingcompliment |
INVOICECUSTOMERACCOUNTNUMBER | = | msdyn_invoicecustomerid.Account(accountnumber).Contact(msdyn_contactpersonid) |
ISDELIVERYADDRESSORDERSPECIFIC | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressorderspecific |
ISDELIVERYADDRESSPRIVATE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressprivate |
ISINVOICEADDRESSPRIVATE | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isinvoiceaddressprivate |
ISONETIMECUSTOMER | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isonetimecustomer |
ISSALESPROCESSINGSTOPPED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_issalesprocessingstopped |
PAYMENTTERMSBASEDATE | = | msdyn_paymenttermsbasedate |
PAYMENTTERMSNAME | = | msdyn_paymentterms.msdyn_name |
PRICECUSTOMERGROUPCODE | = | msdyn_pricecustomergroup.msdyn_groupcode |
QUOTATIONNUMBER | = | msdyn_quotationnumber |
REQUESTEDRECEIPTDATE | = | msdyn_requestedreceiptdate |
REQUESTEDSHIPPINGDATE | = | requestdeliveryby |
SALESORDERPROMISINGMETHOD | ><<br>`none` : `192350000`<br>`salesLeadTime` : `192350001`<br>`atp` : `192350002`<br>`atpPlusIssueMargin` : `192350003`<br>`ctp` : `192350004` | msdyn_salesorderpromisingmethod |
URL | = | msdyn_url |
SALESORDERPROCESSINGSTATUS | ><<br>`active` : `192350000`<br>`confirmed` : `192350001`<br>`picked` : `192350002`<br>`partiallyDelivered` : `192350003`<br>`delivered` : `192350004`<br>`invoiced` : `192350005`<br>`partiallyInvoiced` : `192350006`<br>`canceled` : `192350007` | msdyn_processingstatus |
LANGUAGEID | ><<br>`ar` : `192350000`<br>`ar-ae` : `192350001`<br>`cs` : `192350002`<br>`da` : `192350003`<br>`de` : `192350004`<br>`de-at` : `192350005`<br>`de-ch` : `192350006`<br>`en-au` : `192350007`<br>`en-gb` : `192350009`<br>`en-ie` : `192350010`<br>`en-in` : `192350011`<br>`en-ca` : `192350008`<br>`en-my` : `192350012`<br>`en-nz` : `192350013`<br>`en-sg` : `192350014`<br>`en-us` : `192350015`<br>`en-za` : `192350016`<br>`es` : `192350017`<br>`es-mx` : `192350018`<br>`et` : `192350019`<br>`fi` : `192350020`<br>`fr` : `192350021`<br>`fr-be` : `192350022`<br>`fr-ca` : `192350023`<br>`fr-ch` : `192350024`<br>`hu` : `192350025`<br>`is` : `192350026`<br>`it` : `192350027`<br>`it-ch` : `192350028`<br>`ja` : `192350029`<br>`lt` : `192350030`<br>`lv` : `192350031`<br>`nb-no` : `192350032`<br>`nl` : `192350033`<br>`nl-be` : `192350034`<br>`pl` : `192350035`<br>`pt-br` : `192350036`<br>`ru` : `192350037`<br>`sv` : `192350038`<br>`th` : `192350039`<br>`tr` : `192350040`<br>`zh-hans` : `192350041` | msdyn_language |
CUSTOMERSORDERREFERENCE | = | msdyn_customersorderreference |
DELIVERYMODECODE | = | msdyn_deliverymode.msdyn_name |
DELIVERYTERMSCODE | = | msdyn_deliveryterms.msdyn_termscode |
SALESORDERORIGINCODE | = | msdyn_salesorderorigin.msdyn_origincode |
none | >> | msdyn_ordertype | 192350000
CURRENCYCODE | > | msdyn_isocurrencycode |

###  <a name="216"></a>CDS sales order lines (salesorderdetails)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CURRENCYCODE | > | transactioncurrencyid.isocurrencycode |
DELIVERYADDRESSCITY | = | shipto_city |
DELIVERYADDRESSCOUNTRYREGIONISOCODE | ><<br>`us` : `united states`<br>`de` : `germany`<br>`fr` : `france`<br>`gb` : `united kingdom`<br>`jp` : `japan`<br>`in` : `india`<br>`es` : `spain`<br>`nz` : `new zealand`<br>`au` : `australia`<br>`co` : `columbia`<br>`za` : `south africa`<br>`be` : `belgium`<br>`ca` : `canada`<br>`at` : `austria`<br>`tr` : `türkiye`<br>`cn` : `china`<br>`dk` : `denmark`<br>`se` : `sweden`<br>`no` : `norway`<br>`fi` : `finland`<br>`eg` : `egypt` | shipto_country |
DELIVERYADDRESSZIPCODE | = | shipto_postalcode |
DELIVERYADDRESSSTATEID | = | shipto_stateorprovince |
DELIVERYADDRESSSTREET | = | shipto_line1 |
DELIVERYADDRESSSTREETNUMBER | = | shipto_line2 |
LINEAMOUNT | > | extendedamount |
LINECREATIONSEQUENCENUMBER | = | sequencenumber |
ORDEREDSALESQUANTITY | = | quantity |
PRODUCTNAME | = | description |
PRODUCTNUMBER | = | productid.msdyn_productnumber |
SALESORDERNUMBER | = | salesorderid.msdyn_salesordernumber |
SALESUNITSYMBOL | = | uomid.msdyn_symbol |
TOTALDISCOUNTAMOUNT | = | manualdiscountamount |
TOTALTAXAMOUNT | > | tax |
SALESPRICE | = | priceperunit |
LINEAMOUNT | > | baseamount |
SALESPRODUCTCATEGORYNAME | = | msdyn_salesproductcategory.msdyn_name |
SALESPRODUCTCATEGORYHIERARCHYNAME | > | msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name |
ISDELIVERYADDRESSORDERSPECIFIC | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressspecific |
ISDELIVERYADDRESSPRIVATE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressprivate |
ISLINESTOPPED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_islinestopped |
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
LINEDISCOUNTAMOUNT | = | msdyn_linediscountamount |
LINEDISCOUNTPERCENTAGE | = | msdyn_linediscountpercentage |
MULTILINEDISCOUNTAMOUNT | = | msdyn_multilinediscountamount |
MULTILINEDISCOUNTPERCENTAGE | = | msdyn_multilinediscountpercentage |
REQUESTEDRECEIPTDATE | = | msdyn_requestedreceiptdate |
REQUESTEDSHIPPINGDATE | = | requestdeliveryby |
SALESORDERLINESTATUS | >><br>`none` : `192350000`<br>`backorder` : `192350001`<br>`delivered` : `192350002`<br>`invoiced` : `192350003`<br>`canceled` : `192350004` | msdyn_linestatus |
SALESORDERPROMISINGMETHOD | ><<br>`none` : `192350000`<br>`salesLeadTime` : `192350001`<br>`atp` : `192350002`<br>`atpPlusIssueMargin` : `192350003`<br>`ctp` : `192350004` | msdyn_salesorderpromisingmethod |
SALESPRICEQUANTITY | = | msdyn_salespricequantity |
SHIPPINGSITEID | = | msdyn_shippingsite.msdyn_siteid |
SHIPPINGWAREHOUSEID | = | msdyn_shippingwarehouse.msdyn_warehouseidentifier |
none | >> | ispriceoverridden | true
TOTALCHARGESAMOUNT | > | msdyn_totalchargesamount |
DELIVERYMODECODE | = | msdyn_deliverymode.msdyn_name |
DELIVERYTERMSID | = | msdyn_deliveryterms.msdyn_termscode |

###  <a name="215"></a>CDS sales quotation header (quotes)

This template synchronizes data between finance and operations apps and Dataverse.

Reversed source filter: msdyn_ordertype eq 192350000 and statecode eq 0

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
SALESQUOTATIONNUMBER | = | msdyn_quotenumber |
REQUESTINGCUSTOMERACCOUNTNUMBER | = | customerid.Account(accountnumber).Contact(msdyn_contactpersonid) |
CURRENCYCODE | = | transactioncurrencyid.isocurrencycode |
CUSTOMERSREFERENCE | = | msdyn_customersreference |
DELIVERYADDRESSCITY | = | shipto_city |
DELIVERYADDRESSCOUNTRYREGIONISOCODE | ><<br>`us` : `united states`<br>`de` : `germany`<br>`fr` : `france`<br>`gb` : `united kingdom`<br>`jp` : `japan`<br>`in` : `india`<br>`es` : `spain`<br>`nz` : `new zealand`<br>`au` : `australia`<br>`co` : `columbia`<br>`za` : `south africa`<br>`be` : `belgium`<br>`ca` : `canada`<br>`at` : `austria`<br>`tr` : `türkiye`<br>`cn` : `china`<br>`dk` : `denmark`<br>`se` : `sweden`<br>`no` : `norway`<br>`fi` : `finland`<br>`eg` : `egypt` | shipto_country |
DELIVERYADDRESSSTREETNUMBER | = | shipto_line2 |
DELIVERYADDRESSZIPCODE | = | shipto_postalcode |
DELIVERYADDRESSSTREET | = | shipto_line1 |
DELIVERYADDRESSSTATEID | = | shipto_stateorprovince |
SALESQUOTATIONNAME | = | name |
INVOICEADDRESSCITY | > | billto_city |
INVOICEADDRESSSTREET | > | billto_line1 |
INVOICEADDRESSSTREETNUMBER | > | billto_line2 |
INVOICEADDRESSCOUNTRYREGIONISOCODE | > | billto_country |
INVOICEADDRESSSTATEID | > | billto_stateorprovince |
INVOICEADDRESSZIPCODE | > | billto_postalcode |
QUOTATIONTOTALAMOUNT | > | totalamount |
TOTALDISCOUNTAMOUNT | > | discountamount |
QUOTATIONTOTALTAXAMOUNT | > | totaltax |
QUOTATIONTOTALCHARGESAMOUNT | > | freightamount |
AREPRICESINCLUDINGSALESTAX | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_arepricesincludingsalestax |
CONTACTPERSONID | = | msdyn_associatedcontact.msdyn_contactforpartynumber |
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
FORMATTEDDELIVERYADDRESS | > | msdyn_formatteddeliveryaddress |
FORMATTEDINVOICEADDRESS | > | msdyn_formattedinvoiceaddress |
GENERATEDSALESORDERNUMBER | = | msdyn_generatedsalesordernumber.msdyn_salesordernumber |
INVOICEADDRESSCOUNTRYREGIONID | > | msdyn_invoiceaddresscountryregionid |
INVOICEADDRESSCOUNTYID | > | msdyn_invoiceaddresscountyid |
INVOICEADDRESSDISTRICTNAME | > | msdyn_invoiceaddressdistrictname |
INVOICEADDRESSLATITUDE | > | msdyn_invoiceaddresslatitude |
INVOICEADDRESSLONGITUDE | > | msdyn_invoiceaddresslongitude |
INVOICEADDRESSPOSTBOX | > | msdyn_invoiceaddresspostbox |
INVOICEBUILDINGCOMPLIMENT | > | msdyn_invoicebuildingcompliment |
INVOICECUSTOMERACCOUNTNUMBER | = | msdyn_invoicecustomerid.Account(accountnumber).Contact(msdyn_contactpersonid) |
ISDELIVERYADDRESSORDERSPECIFIC | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressorderspecific |
ISDELIVERYADDRESSPRIVATE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressprivate |
ISINVOICEADDRESSPRIVATE | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isinvoiceaddressprivate |
LANGUAGEID | ><<br>`ar` : `192350000`<br>`ar-ae` : `192350001`<br>`cs` : `192350002`<br>`da` : `192350003`<br>`de` : `192350004`<br>`de-at` : `192350005`<br>`de-ch` : `192350006`<br>`en-au` : `192350007`<br>`en-gb` : `192350009`<br>`en-ie` : `192350010`<br>`en-in` : `192350011`<br>`en-ca` : `192350008`<br>`en-my` : `192350012`<br>`en-nz` : `192350013`<br>`en-sg` : `192350014`<br>`en-us` : `192350015`<br>`en-za` : `192350016`<br>`es` : `192350017`<br>`es-mx` : `192350018`<br>`et` : `192350019`<br>`fi` : `192350020`<br>`fr` : `192350021`<br>`fr-be` : `192350022`<br>`fr-ca` : `192350023`<br>`fr-ch` : `192350024`<br>`hu` : `192350025`<br>`is` : `192350026`<br>`it` : `192350027`<br>`it-ch` : `192350028`<br>`ja` : `192350029`<br>`lt` : `192350030`<br>`lv` : `192350031`<br>`nb-no` : `192350032`<br>`nl` : `192350033`<br>`nl-be` : `192350034`<br>`pl` : `192350035`<br>`pt-br` : `192350036`<br>`ru` : `192350037`<br>`sv` : `192350038`<br>`th` : `192350039`<br>`tr` : `192350040`<br>`zh-hans` : `192350041` | msdyn_language |
PAYMENTTERMSNAME | = | msdyn_paymentterms.msdyn_name |
PRICECUSTOMERGROUPCODE | = | msdyn_pricecustomergroup.msdyn_groupcode |
RECEIPTDATEREQUESTED | = | msdyn_requestedreceiptdate |
REQUESTEDSHIPPINGDATE | = | requestdeliveryby |
SALESORDERPROMISINGMETHOD | ><<br>`none` : `192350000`<br>`salesLeadTime` : `192350001`<br>`atp` : `192350002`<br>`atpPlusIssueMargin` : `192350003`<br>`ctp` : `192350004` | msdyn_salesorderpromisingmethod |
SALESQUOTATIONCONFIRMATIONDATE | = | msdyn_salesquotationconfirmationdate |
SALESQUOTATIONEXPIRYDATE | = | msdyn_salesquotationexpirydate |
SALESQUOTATIONFOLLOWUPDATE | = | msdyn_salesquotationfollowupdate |
SALESQUOTATIONSTATUS | ><<br>`created` : `192350000`<br>`sent` : `192350001`<br>`confirmed` : `192350002`<br>`lost` : `192350003`<br>`cancelled` : `192350004`<br>`reset` : `192350005`<br>`modified` : `192350006`<br>`submitted` : `192350007`<br>`approved` : `192350008`<br>`revised` : `192350009` | msdyn_salesquotationstatus |
TOTALDISCOUNTPERCENTAGE | = | msdyn_totaldiscountpercentage |
URL | = | msdyn_url |
EMAIL | = | emailaddress |
none | >> | msdyn_ordertype | 192350000
CURRENCYCODE | > | msdyn_isocurrencycode |
OPERATINGUNITPARTYNUMBER | = | msdyn_operatingunit.msdyn_partynumber |

###  <a name="214"></a>CDS sales quotation lines (quotedetails)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
ALLOWEDOVERDELIVERYPERCENTAGE | = | msdyn_allowedoverdeliverypercentage |
ALLOWEDUNDERDELIVERYPERCENTAGE | = | msdyn_allowedunderdeliverypercentage |
SALESQUOTATIONNUMBER | = | quoteid.msdyn_quotenumber |
LINECREATIONSEQUENCENUMBER | = | sequencenumber |
CURRENCYCODE | > | transactioncurrencyid.isocurrencycode |
DELIVERYADDRESSCITY | = | shipto_city |
DELIVERYADDRESSCOUNTRYREGIONISOCODE | ><<br>`us` : `united states`<br>`de` : `germany`<br>`fr` : `france`<br>`gb` : `united kingdom`<br>`jp` : `japan`<br>`in` : `india`<br>`es` : `spain`<br>`nz` : `new zealand`<br>`au` : `australia`<br>`co` : `columbia`<br>`za` : `south africa`<br>`be` : `belgium`<br>`ca` : `canada`<br>`at` : `austria`<br>`tr` : `türkiye`<br>`cn` : `china`<br>`dk` : `denmark`<br>`se` : `sweden`<br>`no` : `norway`<br>`fi` : `finland`<br>`eg` : `egypt` | shipto_country |
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
ISDELIVERYADDRESSPRIVATE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressprivate |
ISDELIVERYADDRESSORDERSPECIFIC | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressspecific |
LINEAMOUNT | > | baseamount |
LINEAMOUNT | > | extendedamount |
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
SALESQUOTATIONPROMISINGMETHOD | ><<br>`none` : `192350000`<br>`salesLeadTime` : `192350001`<br>`atp` : `192350002`<br>`atpPlusIssueMargin` : `192350003`<br>`ctp` : `192350004` | msdyn_salesquotationpromisingmethod |
SALESQUOTATIONSTATUS | ><<br>`created` : `192350000`<br>`sent` : `192350001`<br>`confirmed` : `192350002`<br>`lost` : `192350003`<br>`cancelled` : `192350004`<br>`reset` : `192350005`<br>`modified` : `192350006`<br>`submitted` : `192350007`<br>`approved` : `192350008`<br>`revised` : `192350009` | msdyn_salesquotationstatus |
SALESUNITSYMBOL | = | uomid.msdyn_symbol |
SHIPPINGSITEID | = | msdyn_shippingsite.msdyn_siteid |
SHIPPINGWAREHOUSEID | = | msdyn_shippingwarehouse.msdyn_warehouseidentifier |
TOTALCHARGESAMOUNT | > | msdyn_totalchargesamount |
TOTALDISCOUNTAMOUNT | = | manualdiscountamount |
TOTALTAXAMOUNT | > | tax |
SALESPRODUCTCATEGORYHIERARCHYNAME | > | msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name |
SALESPRODUCTCATEGORYNAME | = | msdyn_salesproductcategory.msdyn_name |
none | >> | ispriceoverridden | true

###  <a name="121"></a>Chart of accounts (msdyn_chartofaccountses)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DESCRIPTION | = | msdyn_description |
MAINACCOUNTMASK | = | msdyn_mainaccountmask |
CHARTOFACCOUNTS | = | msdyn_name |

###  <a name="170"></a>Colors (msdyn_productcolors)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
COLORID | > | msdyn_productcolorname |

###  <a name="105"></a>Compensation job function (cdm_jobfunctions)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
JOBFUNCTIONID | = | cdm_name |
DESCRIPTION | = | cdm_description |

###  <a name="108"></a>Compensation job type (cdm_jobtypes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
JOBTYPEID | = | cdm_name |
DESCRIPTION | = | cdm_description |
EXEMPTSTATUS | ><<br>`exempt` : `754400000`<br>`nonexempt` : `754400001`<br>`doesnotapply` : `754400002` | cdm_exemptstatus |

###  <a name="222"></a>Complimentary closings (msdyn_complimentaryclosings)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CLOSINGPHRASE | = | msdyn_closingphrase |

###  <a name="171"></a>Configurations (msdyn_productconfigurations)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CONFIGURATIONID | > | msdyn_productconfiguration |

###  <a name="223"></a>Contact person titles (msdyn_salescontactpersontitles)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
JOBTITLE | = | msdyn_jobtitle |
JOBTITLEALIAS | = | msdyn_jobtitlealias |

###  <a name="221"></a>Contacts V2 (msdyn_contactforparties)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CONTACTPERSONID | = | msdyn_contactforpartynumber |
CONTACTPERSONPARTYNUMBER | = | msdyn_contactpartyid.msdyn_partynumber |
ASSOCIATEDPARTYNUMBER | = | msdyn_associatedpartyid.msdyn_partynumber |
EMPLOYMENTPROFESSION | = | msdyn_employmentprofession |
EMPLOYMENTDEPARTMENT | = | msdyn_employmentdepartment |
PRIMARYSALUTATIONPHRASE | = | msdyn_primarysalutationphrase.msdyn_salutationphrase |
ASSISTANTNAME | = | msdyn_assistantname |
ASSISTANTPHONENUMBER | = | msdyn_assistantphonenumber |
AVAILABLEFROMTIME | = | msdyn_availablefromtime |
AVAILABLETOTIME | = | msdyn_availabletotime |
CONTACTACTIVITYSENSITIVITYLEVEL | ><<br>`normal` : `192350000`<br>`personal` : `192350001`<br>`private` : `192350002`<br>`confidential` : `192350003` | msdyn_contactactivitysensitivitylevel |
CONTACTPERSONRESPONSIBLEPERSONNELNUMBER | = | msdyn_employeeresponsible.cdm_workernumber |
DECISIONMAKINGROLECODE | = | msdyn_decisionmakingrole.msdyn_rolename |
EMPLOYMENTCOMPUTERNETWORKNAME | = | msdyn_employmentcomputernetworkname |
EMPLOYMENTJOBFUNCTIONNAME | = | msdyn_employmentjobfunctionname |
EMPLOYMENTJOBTITLE | = | msdyn_jobtitle.msdyn_jobtitlealias |
EMPLOYMENTOFFICELOCATION | = | msdyn_employmentofficelocation |
GOVERNMENTIDENTIFICATIONNUMBER | = | msdyn_governmentidentificationnumber |
HASREQUESTEDINTERNETACCESS | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_hasrequestedinternetaccess |
IDENTITYCARDNUMBER | = | msdyn_identitycardnumber |
ISRECEIVINGDIRECTMAIL | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isreceivingdirectmail |
ISVIP | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isvip |
LOYALTYLEVELPHRASE | = | msdyn_loyaltylevelphrase.msdyn_levelphrase |
MANAGERCONTACTPERSONID | = | msdyn_parentcontactforpartyid.msdyn_contactforpartynumber |
MICROSOFTOUTLOOKCATEGORIES | = | msdyn_microsoftoutlookcategories |
MILEAGEDISTANCE | = | msdyn_mileagedistance |
NOTES | = | msdyn_notes |
ORGANIZATIONIDENTIFICATIONNUMBER | = | msdyn_organizationidentificationnumber |
PERSONALCHARACTERTYPECODE | = | msdyn_personalcharactertypecode.msdyn_typename |
PRIMARYCOMPLIMENTARYCLOSINGPHRASE | = | msdyn_primarycomplimentaryclosingphrase.msdyn_closingphrase |
CONTACTINFORMATIONLANGUAGEID | ><<br>`ar` : `192350000`<br>`ar-ae` : `192350001`<br>`cs` : `192350002`<br>`da` : `192350003`<br>`de` : `192350004`<br>`de-at` : `192350005`<br>`de-ch` : `192350006`<br>`en-au` : `192350007`<br>`en-gb` : `192350009`<br>`en-ie` : `192350010`<br>`en-in` : `192350011`<br>`en-ca` : `192350008`<br>`en-my` : `192350012`<br>`en-nz` : `192350013`<br>`en-sg` : `192350014`<br>`en-us` : `192350015`<br>`en-za` : `192350016`<br>`es` : `192350017`<br>`es-mx` : `192350018`<br>`et` : `192350019`<br>`fi` : `192350020`<br>`fr` : `192350021`<br>`fr-be` : `192350022`<br>`fr-ca` : `192350023`<br>`fr-ch` : `192350024`<br>`hu` : `192350025`<br>`is` : `192350026`<br>`it` : `192350027`<br>`it-ch` : `192350028`<br>`ja` : `192350029`<br>`lt` : `192350030`<br>`lv` : `192350031`<br>`nb-no` : `192350032`<br>`nl` : `192350033`<br>`nl-be` : `192350034`<br>`pl` : `192350035`<br>`pt-br` : `192350036`<br>`ru` : `192350037`<br>`sv` : `192350038`<br>`th` : `192350039`<br>`tr` : `192350040`<br>`zh-hans` : `192350041` | msdyn_nativelanguage |
SPOUSENAME | = | msdyn_spousename |

###  <a name="218"></a>Currencies (transactioncurrencies)

This template synchronizes data between finance and operations apps and Dataverse.

Source filter: ((CURRENCYCODE != "999"))

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CURRENCYCODE | = | isocurrencycode |
NAME | = | currencyname |
SYMBOL | = | currencysymbol |
none | >> | exchangerate | 1.0000000000

###  <a name="230"></a>Customer Attachments (annotations)

This template synchronizes data between finance and operations apps and Dataverse.

Source filter: ((TypeId == "Note") || (TypeId == "URL"))

Reversed source filter: (objecttypecode eq 'account' or objecttypecode eq 'contact') and msdyn_relatedentityid ne null

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DOCUMENTID | = | msdyn_notesid |
NAME | = | subject |
none | >> | objecttypecode | account
CUSTOMERACCOUNTNUMBER | = | msdyn_relatedentityid |
TYPEID | << | none | Note
NOTES | = | notetext |
RESTRICTION | ><<br>`internal` : `0`<br>`external` : `1` | msdyn_restriction |

###  <a name="126"></a>Customer groups (msdyn_customergroups)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CUSTOMERGROUPID | = | msdyn_groupid |
DESCRIPTION | = | msdyn_description |
ISSALESTAXINCLUDEDINPRICE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_issalestaxincludedinprice |
PAYMENTTERMID | = | msdyn_paymenttermid.msdyn_name |
CLEARINGPERIODPAYMENTTERMNAME | = | msdyn_clearingperiodpaymenttermname.msdyn_name |

###  <a name="146"></a>Customer hierarchies (msdyn_customerhierarchies)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CUSTOMERHIERARCHYID | = | msdyn_customerhierarchynumber |
NAME | = | msdyn_name |
ORGANIZATIONPARTYNUMBER | = | msdyn_organizationpartynumber.msdyn_partynumber |
PURPOSE | ><<br>`B2BOrganization` : `192350000` | msdyn_purpose |

###  <a name="163"></a>Customer hierarchy nodes (msdyn_customerhierarchynodes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CUSTOMERHIERARCHYID | = | msdyn_customerhierarchynumber.msdyn_customerhierarchynumber |
NODEPARTYNUMBER | = | msdyn_nodepartynumber.msdyn_partynumber |
NODETYPE | ><<br>`Customer` : `192350000` | msdyn_nodetype |
ROLE | ><<br>`Admin` : `192350000`<br>`User` : `192350001` | msdyn_role |

###  <a name="127"></a>Customer payment method (msdyn_customerpaymentmethods)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
NAME | = | msdyn_name |
ACCOUNTTYPE | ><<br>`ledger` : `806380000`<br>`cust` : `806380001`<br>`vend` : `806380002`<br>`project` : `806380003`<br>`fixedassets` : `806380004`<br>`bank` : `806380005` | msdyn_accounttype |
DISCOUNTGRACEPERIODDAYS | = | msdyn_discountgraceperioddays |
BRIDGINGPOSTINGENABLED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_bridgingpostingenabled |
ISSEPA | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_issepa |
LASTFILENUMBER | = | msdyn_lastfilenumber |
LASTFILENUMBERTODAY | = | msdyn_lastfilenumbertoday |
DESCRIPTION | = | msdyn_description |
PAYMENTTYPE | ><<br>`other` : `806380000`<br>`electronicPayment` : `806380001`<br>`check` : `806380002`<br>`billOfExchange` : `806380003`<br>`creditCard` : `806380004` | msdyn_paymenttype |
CREATEANDDRAWBILLOFEXCHANGEDURINGINVOICEPOSTING | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_invoiceupdate |
PAYMENTSTATUS | ><<br>`none` : `806380000`<br>`sent` : `806380001`<br>`recieved` : `806380002`<br>`confirmed` : `806380003`<br>`rejected` : `806380004` | msdyn_paymentstatus |
SUMBYPERIOD | ><<br>`invoice` : `806380000`<br>`week` : `806380002`<br>`total` : `806380003`<br>`transDate` : `806380001` | msdyn_sumbyperiod |
ENABLEPOSTDATEDCHECKCLEARINGPOSTING | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_enablepostdatescheckclearingposting |
BILLOFEXCHANGEDRAFTTYPE | ><<br>`acceptance` : `806380002`<br>`promissory` : `806380003`<br>`bankAcceptance` : `806380004`<br>`nodraft` : `806380000`<br>`noacceptance` : `806380001` | msdyn_billofexchangedrafttype |
DIRECTDEBIT | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_directdebit |

###  <a name="101"></a>Customers V3 (accounts)

This template synchronizes data between finance and operations apps and Dataverse.

Source filter: ((PartyType == "Organization"))

Reversed source filter: customertypecode eq 3

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CUSTOMERACCOUNT | = | accountnumber |
CREDITLIMIT | = | creditlimit |
SALESCURRENCYCODE | = | transactioncurrencyid.isocurrencycode |
SALESMEMO | = | description |
CREDITLIMITISMANDATORY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_creditlimitismandatory |
CREDITRATING | = | msdyn_creditrating |
CUSTOMERGROUPID | = | msdyn_customergroupid.msdyn_groupid |
IDENTIFICATIONNUMBER | = | msdyn_identificationnumber |
INVOICEACCOUNT | = | msdyn_billingaccount.accountnumber |
ISONETIMECUSTOMER | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_onetimecustomer |
ONHOLDSTATUS | ><<br>`no` : `806380000`<br>`invoice` : `806380001`<br>`all` : `806380002`<br>`payment` : `806380003`<br>`requisition` : `806380004`<br>`never` : `806380005` | msdyn_onholdstatus |
PARTYCOUNTRY | = | msdyn_partycountry |
PARTYSTATE | = | msdyn_partystateprovince |
PAYMENTDAY | = | msdyn_paymentday.msdyn_name |
PAYMENTMETHOD | = | msdyn_customerpaymentmethod.msdyn_name |
PAYMENTSCHEDULE | = | msdyn_paymentschedule.msdyn_name |
PAYMENTTERMS | = | msdyn_paymentterm.msdyn_name |
PAYMENTTERMSBASEDAYS | = | msdyn_paymenttermsbasedays |
TAXEXEMPTNUMBER | = | msdyn_taxexemptnumber |
VENDORACCOUNT | = | msdyn_vendor.msdyn_vendoraccountnumber |
none | >> | customertypecode | 3
PARTYTYPE | << | none | Organization
PARTYNUMBER | = | msdyn_partyid.msdyn_partynumber |
CONTACTPERSONID | = | msdyn_primarycontact.msdyn_contactforpartynumber |
SALESTAXGROUP | = | msdyn_salestaxgroup.msdyn_name |

###  <a name="116"></a>Customers V3 (contacts)

This template synchronizes data between finance and operations apps and Dataverse.

Source filter: ((PartyType == "Person"))

Reversed source filter: msdyn_sellable eq true  and msdyn_contactpersonid ne null

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
none | >> | msdyn_sellable | True
PARTYTYPE | << | none | Person
PARTYNUMBER | = | msdyn_partyid.msdyn_partynumber |
CUSTOMERACCOUNT | = | msdyn_contactpersonid |
CUSTOMERGROUPID | = | msdyn_customergroupid.msdyn_groupid |
IDENTIFICATIONNUMBER | = | msdyn_identificationnumber |
PARTYCOUNTRY | = | msdyn_partycountry |
PARTYSTATE | = | msdyn_partystateprovince |
SALESCURRENCYCODE | = | transactioncurrencyid.isocurrencycode |
SALESMEMO | = | description |
PAYMENTDAY | = | msdyn_paymentday.msdyn_name |
PAYMENTSCHEDULE | = | msdyn_paymentschedule.msdyn_name |
PAYMENTMETHOD | = | msdyn_customerpaymentmethod.msdyn_name |
SALESTAXGROUP | = | msdyn_salestaxgroup.msdyn_name |
PAYMENTTERMS | = | msdyn_paymentterms.msdyn_name |
CONTACTPERSONID | = | msdyn_primarycontact.msdyn_contactforpartynumber |

###  <a name="224"></a>Decision making roles (msdyn_decisionmakingroles)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
ROLEDESCRIPTION | = | msdyn_roledescription |
ROLENAME | = | msdyn_rolename |

###  <a name="172"></a>Default order settings (msdyn_productdefaultordersettings)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
INVENTWAREHOUSEID | = | msdyn_inventorywarehouse.msdyn_warehouseidentifier |
INVENTORYSITEID | = | msdyn_inventorysite.msdyn_siteid |
INVENTORYATPDELAYEDDEMANDOFFSETDAYS | = | msdyn_inventoryatpdelayeddemandoffsetdays |
INVENTORYATPDELAYEDSUPPLYOFFSETDAYS | = | msdyn_inventoryatpdelayedsupplyoffsetdays |
ITEMNUMBER | = | msdyn_itemnumber.msdyn_itemnumber |
INVENTORYATPBACKWARDDEMANDTIMEFENCEDAYS | = | msdyn_inventoryatpbackwarddemandtimefencedays |
INVENTORYATPBACKWARDSUPPLYTIMEFENCEDAYS | = | msdyn_inventoryatpbackwardsupplytimefencedays |
INVENTORYATPTIMEFENCEDAYS | = | msdyn_inventoryatptimefencedays |
MAXIMUMINVENTORYORDERQUANTITY | = | msdyn_maximuminventoryorderquantity |
MAXIMUMPROCUREMENTORDERQUANTITY | = | msdyn_maximumprocurementorderquantity |
MAXIMUMSALESORDERQUANTITY | = | msdyn_maximumsalesorderquantity |
MINIMUMINVENTORYORDERQUANTITY | = | msdyn_minimuminventoryorderquantity |
MINIMUMPROCUREMENTORDERQUANTITY | = | msdyn_minimumprocurementorderquantity |
MINIMUMSALESORDERQUANTITY | = | msdyn_minimumsalesorderquantity |
STANDARDINVENTORYORDERQUANTITY | = | msdyn_standardinventoryorderquantity |
STANDARDPROCUREMENTORDERQUANTITY | = | msdyn_standardprocurementorderquantity |
STANDARDSALESORDERQUANTITY | = | msdyn_standardsalesorderquantity |
INVENTORYLEADTIMEDAYS | = | msdyn_inventoryleadtimedays |
INVENTORYQUANTITYMULTIPLES | = | msdyn_inventoryquantitymultiples |
PROCUREMENTQUANTITYMULTIPLES | = | msdyn_procurementquantitymultiples |
SALESQUANTITYMULTIPLES | = | msdyn_salesquantitymultiples |
PROCUREMENTSITEID | = | msdyn_procurementsite.msdyn_siteid |
PROCUREMENTLEADTIMEDAYS | = | msdyn_procurementleadtimedays |
SALESSITEID | = | msdyn_salessite.msdyn_siteid |
SALESATPDELAYEDDEMANDOFFSETDAYS | = | msdyn_salesatpdelayeddemandoffsetdays |
SALESATPDELAYEDSUPPLYOFFSETDAYS | = | msdyn_salesatpdelayedsupplyoffsetdays |
SALESATPBACKWARDDEMANDTIMEFENCEDAYS | = | msdyn_salesatpbackwarddemandtimefencedays |
SALESATPBACKWARDSUPPLYTIMEFENCEDAYS | = | msdyn_salesatpbackwardsupplytimefencedays |
SALESATPTIMEFENCEDAYS | = | msdyn_salesatptimefencedays |
SALESLEADTIMEDAYS | = | msdyn_salesleadtimedays |
PROCUREMENTWAREHOUSEID | = | msdyn_procurementwarehouse.msdyn_warehouseidentifier |
SALESWAREHOUSEID | = | msdyn_saleswarehouse.msdyn_warehouseidentifier |
AREINVENTORYORDERPROMISINGDEFAULTSOVERRIDDEN | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_areinventoryorderdefaultsoverridden |
INVENTORYORDERPROMISINGMETHOD | ><<br>`none` : `192350000`<br>`salesLeadTime` : `192350001`<br>`atp` : `192350002`<br>`atpPlusIssueMargin` : `192350003`<br>`ctp` : `192350004` | msdyn_inventoryorderpromisingmethod |
ISINVENTORYATPINCLUDINGPLANNEDORDERS | ><<br>`false` : `False`<br>`true` : `True` | msdyn_isinventoryatpincludingplannedorders |
ISINVENTORYUSINGWORKINGDAYS | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isinventoryusingworkingdays |
ISINVENTORYSITEMANDATORY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isinventorysitemandatory |
ISINVENTORYPROCESSINGSTOPPED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isinventoryprocessingstopped |
ISPROCUREMENTUSINGWORKINGDAYS | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isprocurementusingworkingdays |
ISPROCUREMENTSITEMANDATORY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isprocurementsitemandatory |
ISPROCUREMENTPROCESSINGSTOPPED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isprocurementprocessingstopped |
ARESALESORDERPROMISINGDEFAULTSOVERRIDDEN | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_aresalesorderdefaultsoverridden |
SALESORDERPROMISINGMETHOD | ><<br>`none` : `192350000`<br>`salesLeadTime` : `192350001`<br>`atp` : `192350002`<br>`atpPlusIssueMargin` : `192350003`<br>`ctp` : `192350004` | msdyn_salesorderpromisingmethod |
ISSALESATPINCLUDINGPLANNEDORDERS | ><<br>`false` : `False`<br>`true` : `True` | msdyn_issalesatpincludingplannedorders |
ISSALESSITEMANDATORY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_issalessitemandatory |
ISSALESLEADTIMEOVERRIDDEN | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_issalesleadtimeoverridden |
ISSALESPROCESSINGSTOPPED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_issalesprocessingstopped |
ISINVENTORYWAREHOUSEMANDATORY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isinventorywarehousemandatory |
ISPROCUREMENTWAREHOUSEMANDATORY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isprocurementwarehousemandatory |
ISSALESWAREHOUSEMANDATORY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_issaleswarehousemandatory |

###  <a name="237"></a>Dynamics 365 Sales feature management states (msdyn_supplychainfeaturestates)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
NAME | = | msdyn_name |
ISENABLED | ><<br>`no` : `1`<br>`yes` : `0` | statecode |

###  <a name="238"></a>Dynamics 365 Sales order headers (salesorders)

This template synchronizes data between finance and operations apps and Dataverse.

Reversed source filter: msdyn_ordertype eq 192350000 and msdyn_isreadytosync eq true

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
SALESORDERNUMBER | = | msdyn_salesordernumber |
ORDERINGCUSTOMERACCOUNTNUMBER | = | customerid.Account(accountnumber).Contact(msdyn_contactpersonid) |
CURRENCYCODE | = | transactioncurrencyid.isocurrencycode |
DELIVERYADDRESSCITY | = | shipto_city |
DELIVERYADDRESSCOUNTRYREGIONISOCODE | ><<br>`us` : `united states`<br>`de` : `germany`<br>`fr` : `france`<br>`gb` : `united kingdom`<br>`jp` : `japan`<br>`in` : `india`<br>`es` : `spain`<br>`nz` : `new zealand`<br>`au` : `australia`<br>`co` : `columbia`<br>`za` : `south africa`<br>`be` : `belgium`<br>`ca` : `canada`<br>`at` : `austria`<br>`tr` : `turkey`<br>`cn` : `china`<br>`dk` : `denmark`<br>`se` : `sweden`<br>`no` : `norway`<br>`fi` : `finland`<br>`eg` : `egypt` | shipto_country |
DELIVERYADDRESSSTREETNUMBER | = | shipto_line2 |
DELIVERYADDRESSZIPCODE | = | shipto_postalcode |
DELIVERYADDRESSSTREET | = | shipto_line1 |
DELIVERYADDRESSSTATEID | = | shipto_stateorprovince |
SALESORDERNAME | > | name |
INVOICEADDRESSCITY | > | billto_city |
INVOICEADDRESSSTREET | > | billto_line1 |
INVOICEADDRESSSTREETNUMBER | > | billto_line2 |
INVOICEADDRESSCOUNTRYREGIONISOCODE | > | billto_country |
INVOICEADDRESSSTATEID | > | billto_stateorprovince |
INVOICEADDRESSZIPCODE | > | billto_postalcode |
ORDERTOTALAMOUNT | > | totalamount |
TOTALDISCOUNTAMOUNT | > | discountamount |
ORDERTOTALTAXAMOUNT | > | totaltax |
ORDERTOTALCHARGESAMOUNT | > | freightamount |
AREPRICESINCLUDINGSALESTAX | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_arepricesincludingsalestax |
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
FORMATTEDDELVERYADDRESS | > | msdyn_formatteddeliveryaddress |
EMAIL | = | emailaddress |
FORMATTEDINVOICEADDRESS | > | msdyn_formattedinvoiceaddress |
INVOICEADDRESSCOUNTYID | > | msdyn_invoiceaddresscountyid |
INVOICEADDRESSDISTRICTNAME | > | msdyn_invoiceaddressdistrictname |
INVOICEADDRESSLATITUDE | > | msdyn_invoiceaddresslatitude |
INVOICEADDRESSLONGITUDE | > | msdyn_invoiceaddresslongitude |
INVOICEADDRESSPOSTBOX | > | msdyn_invoiceaddresspostbox |
INVOICEBUILDINGCOMPLIMENT | > | msdyn_invoicebuildingcompliment |
INVOICECUSTOMERACCOUNTNUMBER | = | msdyn_invoicecustomerid.Account(accountnumber).Contact(msdyn_contactpersonid) |
ISDELIVERYADDRESSORDERSPECIFIC | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressorderspecific |
ISDELIVERYADDRESSPRIVATE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressprivate |
ISINVOICEADDRESSPRIVATE | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isinvoiceaddressprivate |
ISONETIMECUSTOMER | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isonetimecustomer |
ISSALESPROCESSINGSTOPPED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_issalesprocessingstopped |
PAYMENTTERMSBASEDATE | = | msdyn_paymenttermsbasedate |
PAYMENTTERMSNAME | = | msdyn_paymentterms.msdyn_name |
PRICECUSTOMERGROUPCODE | = | msdyn_pricecustomergroup.msdyn_groupcode |
QUOTATIONNUMBER | = | msdyn_quotationnumber |
REQUESTEDRECEIPTDATE | = | msdyn_requestedreceiptdate |
REQUESTEDSHIPPINGDATE | = | requestdeliveryby |
SALESORDERPROMISINGMETHOD | ><<br>`none` : `192350000`<br>`salesLeadTime` : `192350001`<br>`atp` : `192350002`<br>`atpPlusIssueMargin` : `192350003`<br>`ctp` : `192350004` | msdyn_salesorderpromisingmethod |
URL | = | msdyn_url |
SALESORDERPROCESSINGSTATUS | ><<br>`active` : `192350000`<br>`confirmed` : `192350001`<br>`picked` : `192350002`<br>`partiallyDelivered` : `192350003`<br>`delivered` : `192350004`<br>`invoiced` : `192350005`<br>`partiallyInvoiced` : `192350006`<br>`canceled` : `192350007`<br>`deliveredPartiallyInvoiced` : `192350008` | msdyn_processingstatus |
LANGUAGEID | ><<br>`ar` : `192350000`<br>`ar-ae` : `192350001`<br>`cs` : `192350002`<br>`da` : `192350003`<br>`de` : `192350004`<br>`de-at` : `192350005`<br>`de-ch` : `192350006`<br>`en-au` : `192350007`<br>`en-gb` : `192350009`<br>`en-ie` : `192350010`<br>`en-in` : `192350011`<br>`en-ca` : `192350008`<br>`en-my` : `192350012`<br>`en-nz` : `192350013`<br>`en-sg` : `192350014`<br>`en-us` : `192350015`<br>`en-za` : `192350016`<br>`es` : `192350017`<br>`es-mx` : `192350018`<br>`et` : `192350019`<br>`fi` : `192350020`<br>`fr` : `192350021`<br>`fr-be` : `192350022`<br>`fr-ca` : `192350023`<br>`fr-ch` : `192350024`<br>`hu` : `192350025`<br>`is` : `192350026`<br>`it` : `192350027`<br>`it-ch` : `192350028`<br>`ja` : `192350029`<br>`lt` : `192350030`<br>`lv` : `192350031`<br>`nb-no` : `192350032`<br>`nl` : `192350033`<br>`nl-be` : `192350034`<br>`pl` : `192350035`<br>`pt-br` : `192350036`<br>`ru` : `192350037`<br>`sv` : `192350038`<br>`th` : `192350039`<br>`tr` : `192350040`<br>`zh-hans` : `192350041` | msdyn_language |
CUSTOMERSORDERREFERENCE | = | msdyn_customersorderreference |
DELIVERYMODECODE | = | msdyn_deliverymode.msdyn_name |
DELIVERYTERMSCODE | = | msdyn_deliveryterms.msdyn_termscode |
SALESORDERORIGINCODE | = | msdyn_salesorderorigin.msdyn_origincode |
none | >> | msdyn_ordertype | 192350000
CURRENCYCODE | > | msdyn_isocurrencycode |

###  <a name="239"></a>Dynamics 365 Sales order lines (salesorderdetails)

This template synchronizes data between finance and operations apps and Dataverse.

Reversed source filter:
- Version 1.x.x.x: msdyn_isreadytosync eq true <br>(to be used in the context of Supply Chain solution without Project Operations or Field Services solution installed.)
- Version 2.x.x.x: (msdyn_linetype ne 690970000 or msdyn_linetype eq null) and msdyn_isreadytosync eq true <br>(to be used in the context of Supply Chain solution and Project Operations or Field Services solution installed.)

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CURRENCYCODE | > | transactioncurrencyid.isocurrencycode |
DELIVERYADDRESSCITY | = | shipto_city |
DELIVERYADDRESSCOUNTRYREGIONISOCODE | ><<br>`us` : `united states`<br>`de` : `germany`<br>`fr` : `france`<br>`gb` : `united kingdom`<br>`jp` : `japan`<br>`in` : `india`<br>`es` : `spain`<br>`nz` : `new zealand`<br>`au` : `australia`<br>`co` : `columbia`<br>`za` : `south africa`<br>`be` : `belgium`<br>`ca` : `canada`<br>`at` : `austria`<br>`tr` : `turkey`<br>`cn` : `china`<br>`dk` : `denmark`<br>`se` : `sweden`<br>`no` : `norway`<br>`fi` : `finland`<br>`eg` : `egypt` | shipto_country |
DELIVERYADDRESSZIPCODE | = | shipto_postalcode |
DELIVERYADDRESSSTATEID | = | shipto_stateorprovince |
DELIVERYADDRESSSTREET | = | shipto_line1 |
DELIVERYADDRESSSTREETNUMBER | = | shipto_line2 |
LINEAMOUNT | > | extendedamount |
LINECREATIONSEQUENCENUMBER | = | sequencenumber |
ORDEREDSALESQUANTITY | = | quantity |
PRODUCTNAME | = | description |
PRODUCTNUMBER | = | productid.msdyn_productnumber |
SALESORDERNUMBER | = | salesorderid.msdyn_salesordernumber |
SALESUNITSYMBOL | = | uomid.msdyn_symbol |
TOTALDISCOUNTAMOUNT | = | manualdiscountamount |
TOTALTAXAMOUNT | > | tax |
SALESPRICE | = | priceperunit |
LINEAMOUNT | > | baseamount |
SALESPRODUCTCATEGORYNAME | = | msdyn_salesproductcategory.msdyn_name |
SALESPRODUCTCATEGORYHIERARCHYNAME | > | msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name |
ISDELIVERYADDRESSORDERSPECIFIC | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressspecific |
ISDELIVERYADDRESSPRIVATE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressprivate |
ISLINESTOPPED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_islinestopped |
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
LINEDISCOUNTAMOUNT | = | msdyn_linediscountamount |
LINEDISCOUNTPERCENTAGE | = | msdyn_linediscountpercentage |
MULTILINEDISCOUNTAMOUNT | = | msdyn_multilinediscountamount |
MULTILINEDISCOUNTPERCENTAGE | = | msdyn_multilinediscountpercentage |
REQUESTEDRECEIPTDATE | = | msdyn_requestedreceiptdate |
REQUESTEDSHIPPINGDATE | = | requestdeliveryby |
SALESORDERLINESTATUS | >><br>`none` : `192350000`<br>`backorder` : `192350001`<br>`delivered` : `192350002`<br>`invoiced` : `192350003`<br>`canceled` : `192350004` | msdyn_linestatus |
SALESORDERPROMISINGMETHOD | ><<br>`none` : `192350000`<br>`salesLeadTime` : `192350001`<br>`atp` : `192350002`<br>`atpPlusIssueMargin` : `192350003`<br>`ctp` : `192350004` | msdyn_salesorderpromisingmethod |
SALESPRICEQUANTITY | = | msdyn_salespricequantity |
SHIPPINGSITEID | = | msdyn_shippingsite.msdyn_siteid |
SHIPPINGWAREHOUSEID | = | msdyn_shippingwarehouse.msdyn_warehouseidentifier |
none | >> | ispriceoverridden | true
TOTALCHARGESAMOUNT | > | msdyn_totalchargesamount |
DELIVERYMODECODE | = | msdyn_deliverymode.msdyn_name |
DELIVERYTERMSID | = | msdyn_deliveryterms.msdyn_termscode |
SALESDELIVERNOW | = | quantityshipped |
INVENTORYSERVICERESERVATIONID | = | msdyn_reservationid |

###  <a name="240"></a>Dynamics 365 Sales quotation header (quotes)

This template synchronizes data between finance and operations apps and Dataverse.

Reversed source filter: msdyn_ordertype eq 192350000

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
SALESQUOTATIONNUMBER | = | msdyn_quotenumber |
REQUESTINGCUSTOMERACCOUNTNUMBER | = | customerid.Account(accountnumber).Contact(msdyn_contactpersonid) |
CURRENCYCODE | = | transactioncurrencyid.isocurrencycode |
CUSTOMERSREFERENCE | = | msdyn_customersreference |
DELIVERYADDRESSCITY | = | shipto_city |
DELIVERYADDRESSCOUNTRYREGIONISOCODE | ><<br>`us` : `united states`<br>`de` : `germany`<br>`fr` : `france`<br>`gb` : `united kingdom`<br>`jp` : `japan`<br>`in` : `india`<br>`es` : `spain`<br>`nz` : `new zealand`<br>`au` : `australia`<br>`co` : `columbia`<br>`za` : `south africa`<br>`be` : `belgium`<br>`ca` : `canada`<br>`at` : `austria`<br>`tr` : `turkey`<br>`cn` : `china`<br>`dk` : `denmark`<br>`se` : `sweden`<br>`no` : `norway`<br>`fi` : `finland`<br>`eg` : `egypt` | shipto_country |
DELIVERYADDRESSSTREETNUMBER | = | shipto_line2 |
DELIVERYADDRESSZIPCODE | = | shipto_postalcode |
DELIVERYADDRESSSTREET | = | shipto_line1 |
DELIVERYADDRESSSTATEID | = | shipto_stateorprovince |
SALESQUOTATIONNAME | = | name |
INVOICEADDRESSCITY | > | billto_city |
INVOICEADDRESSSTREET | > | billto_line1 |
INVOICEADDRESSSTREETNUMBER | > | billto_line2 |
INVOICEADDRESSCOUNTRYREGIONISOCODE | > | billto_country |
INVOICEADDRESSSTATEID | > | billto_stateorprovince |
INVOICEADDRESSZIPCODE | > | billto_postalcode |
QUOTATIONTOTALAMOUNT | > | totalamount |
TOTALDISCOUNTAMOUNT | > | discountamount |
QUOTATIONTOTALTAXAMOUNT | > | totaltax |
QUOTATIONTOTALCHARGESAMOUNT | > | freightamount |
AREPRICESINCLUDINGSALESTAX | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_arepricesincludingsalestax |
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
FORMATTEDDELIVERYADDRESS | > | msdyn_formatteddeliveryaddress |
FORMATTEDINVOICEADDRESS | > | msdyn_formattedinvoiceaddress |
GENERATEDSALESORDERNUMBER | = | msdyn_generatedsalesordernumber.msdyn_salesordernumber |
INVOICEADDRESSCOUNTRYREGIONID | > | msdyn_invoiceaddresscountryregionid |
INVOICEADDRESSCOUNTYID | > | msdyn_invoiceaddresscountyid |
INVOICEADDRESSDISTRICTNAME | > | msdyn_invoiceaddressdistrictname |
INVOICEADDRESSLATITUDE | > | msdyn_invoiceaddresslatitude |
INVOICEADDRESSLONGITUDE | > | msdyn_invoiceaddresslongitude |
INVOICEADDRESSPOSTBOX | > | msdyn_invoiceaddresspostbox |
INVOICEBUILDINGCOMPLIMENT | > | msdyn_invoicebuildingcompliment |
INVOICECUSTOMERACCOUNTNUMBER | = | msdyn_invoicecustomerid.Account(accountnumber).Contact(msdyn_contactpersonid) |
ISDELIVERYADDRESSORDERSPECIFIC | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressorderspecific |
ISDELIVERYADDRESSPRIVATE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressprivate |
ISINVOICEADDRESSPRIVATE | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isinvoiceaddressprivate |
LANGUAGEID | ><<br>`ar` : `192350000`<br>`ar-ae` : `192350001`<br>`cs` : `192350002`<br>`da` : `192350003`<br>`de` : `192350004`<br>`de-at` : `192350005`<br>`de-ch` : `192350006`<br>`en-au` : `192350007`<br>`en-gb` : `192350009`<br>`en-ie` : `192350010`<br>`en-in` : `192350011`<br>`en-ca` : `192350008`<br>`en-my` : `192350012`<br>`en-nz` : `192350013`<br>`en-sg` : `192350014`<br>`en-us` : `192350015`<br>`en-za` : `192350016`<br>`es` : `192350017`<br>`es-mx` : `192350018`<br>`et` : `192350019`<br>`fi` : `192350020`<br>`fr` : `192350021`<br>`fr-be` : `192350022`<br>`fr-ca` : `192350023`<br>`fr-ch` : `192350024`<br>`hu` : `192350025`<br>`is` : `192350026`<br>`it` : `192350027`<br>`it-ch` : `192350028`<br>`ja` : `192350029`<br>`lt` : `192350030`<br>`lv` : `192350031`<br>`nb-no` : `192350032`<br>`nl` : `192350033`<br>`nl-be` : `192350034`<br>`pl` : `192350035`<br>`pt-br` : `192350036`<br>`ru` : `192350037`<br>`sv` : `192350038`<br>`th` : `192350039`<br>`tr` : `192350040`<br>`zh-hans` : `192350041` | msdyn_language |
PAYMENTTERMSNAME | = | msdyn_paymentterms.msdyn_name |
PRICECUSTOMERGROUPCODE | = | msdyn_pricecustomergroup.msdyn_groupcode |
RECEIPTDATEREQUESTED | = | msdyn_requestedreceiptdate |
REQUESTEDSHIPPINGDATE | = | requestdeliveryby |
SALESORDERPROMISINGMETHOD | ><<br>`none` : `192350000`<br>`salesLeadTime` : `192350001`<br>`atp` : `192350002`<br>`atpPlusIssueMargin` : `192350003`<br>`ctp` : `192350004` | msdyn_salesorderpromisingmethod |
SALESQUOTATIONCONFIRMATIONDATE | = | msdyn_salesquotationconfirmationdate |
SALESQUOTATIONEXPIRYDATE | = | msdyn_salesquotationexpirydate |
SALESQUOTATIONFOLLOWUPDATE | = | msdyn_salesquotationfollowupdate |
SALESQUOTATIONSTATUS | ><<br>`created` : `192350000`<br>`sent` : `192350001`<br>`confirmed` : `192350002`<br>`lost` : `192350003`<br>`cancelled` : `192350004`<br>`reset` : `192350005`<br>`modified` : `192350006`<br>`submitted` : `192350007`<br>`approved` : `192350008`<br>`revised` : `192350009` | msdyn_salesquotationstatus |
TOTALDISCOUNTPERCENTAGE | = | msdyn_totaldiscountpercentage |
URL | = | msdyn_url |
EMAIL | = | emailaddress |
none | >> | msdyn_ordertype | 192350000
CURRENCYCODE | > | msdyn_isocurrencycode |
OPERATINGUNITPARTYNUMBER | = | msdyn_operatingunit.msdyn_partynumber |
SALESQUOTATIONHEADERCREATIONMETHOD | >><br>`SCM` : `776160000`<br>`Dynamics365Sales` : `776160001` | msdyn_quotationcreationmethod |
SALESQUOTATIONOWNERSHIP | >><br>`BasedOnOrigin` : `776160000`<br>`SCM` : `776160001`<br>`Dynamics365Sales` : `776160002` | msdyn_quotationownership |

###  <a name="241"></a>Dynamics 365 Sales quotation lines (quotedetails)

This template synchronizes data between finance and operations apps and Dataverse.

Reversed source filter:
- Version 1.x.x.x: None <br>(to be used in the context of Supply Chain solution without Project Operations or Field Services solution installed.)
- Version 2.x.x.x: msdyn_linetype ne 690970000 or msdyn_linetype eq null <br>(to be used in the context of Supply Chain solution and Project Operations or Field Services solution installed.)

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
ALLOWEDOVERDELIVERYPERCENTAGE | = | msdyn_allowedoverdeliverypercentage |
ALLOWEDUNDERDELIVERYPERCENTAGE | = | msdyn_allowedunderdeliverypercentage |
SALESQUOTATIONNUMBER | = | quoteid.msdyn_quotenumber |
LINECREATIONSEQUENCENUMBER | = | sequencenumber |
CURRENCYCODE | > | transactioncurrencyid.isocurrencycode |
DELIVERYADDRESSCITY | = | shipto_city |
DELIVERYADDRESSCOUNTRYREGIONISOCODE | ><<br>`us` : `united states`<br>`de` : `germany`<br>`fr` : `france`<br>`gb` : `united kingdom`<br>`jp` : `japan`<br>`in` : `india`<br>`es` : `spain`<br>`nz` : `new zealand`<br>`au` : `australia`<br>`co` : `columbia`<br>`za` : `south africa`<br>`be` : `belgium`<br>`ca` : `canada`<br>`at` : `austria`<br>`tr` : `turkey`<br>`cn` : `china`<br>`dk` : `denmark`<br>`se` : `sweden`<br>`no` : `norway`<br>`fi` : `finland`<br>`eg` : `egypt` | shipto_country |
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
ISDELIVERYADDRESSPRIVATE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressprivate |
ISDELIVERYADDRESSORDERSPECIFIC | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdeliveryaddressspecific |
LINEAMOUNT | > | baseamount |
LINEAMOUNT | > | extendedamount |
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
SALESQUOTATIONPROMISINGMETHOD | ><<br>`none` : `192350000`<br>`salesLeadTime` : `192350001`<br>`atp` : `192350002`<br>`atpPlusIssueMargin` : `192350003`<br>`ctp` : `192350004` | msdyn_salesquotationpromisingmethod |
SALESQUOTATIONSTATUS | ><<br>`created` : `192350000`<br>`sent` : `192350001`<br>`confirmed` : `192350002`<br>`lost` : `192350003`<br>`cancelled` : `192350004`<br>`reset` : `192350005`<br>`modified` : `192350006`<br>`submitted` : `192350007`<br>`approved` : `192350008`<br>`revised` : `192350009` | msdyn_salesquotationstatus |
SALESUNITSYMBOL | = | uomid.msdyn_symbol |
SHIPPINGSITEID | = | msdyn_shippingsite.msdyn_siteid |
SHIPPINGWAREHOUSEID | = | msdyn_shippingwarehouse.msdyn_warehouseidentifier |
TOTALCHARGESAMOUNT | > | msdyn_totalchargesamount |
TOTALDISCOUNTAMOUNT | = | manualdiscountamount |
TOTALTAXAMOUNT | > | tax |
SALESPRODUCTCATEGORYHIERARCHYNAME | > | msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name |
SALESPRODUCTCATEGORYNAME | = | msdyn_salesproductcategory.msdyn_name |
none | >> | ispriceoverridden | true

###  <a name="225"></a>Employment job functions (msdyn_employmentjobfunctions)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
FUNCTIONDESCRIPTION | = | msdyn_functiondescription |
FUNCTIONNAME | = | msdyn_functionname |

###  <a name="104"></a>Employment per company (cdm_employments)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
EMPLOYMENTENDDATE | = | cdm_employmentenddate |
PERSONNELNUMBER | = | cdm_workerid.cdm_workernumber |
EMPLOYMENTSTARTDATE | = | cdm_employmentstartdate |
WORKERTYPE | >><br>`employee` : `754400000`<br>`contractor` : `754400001`<br>`both` : `754400000` | cdm_workertype |

###  <a name="103"></a>Ethnic origins (cdm_ethnicorigins)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
ETHNICORIGINID | = | cdm_name |
DESCRIPTION | = | cdm_description |

###  <a name="122"></a>Exchange rate currency pair (msdyn_currencyexchangeratepairs)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
EXCHANGERATEDISPLAYFACTOR | ><<br>`one` : `192350000`<br>`ten` : `192350001`<br>`hundred` : `192350002`<br>`thousand` : `192350003`<br>`tenThousand` : `192350004` | msdyn_displayfactor |
EXCHANGERATETYPENAME | = | msdyn_currencyexchangeratetypeid.msdyn_name |
FROMCURRENCYCODE | = | msdyn_fromtransactioncurrencyid.isocurrencycode |
TOCURRENCYCODE | = | msdyn_totransactioncurrencyid.isocurrencycode |

###  <a name="129"></a>Exchange rate type (msdyn_exchangeratetypes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
NAME | = | msdyn_name |
DESCRIPTION | = | msdyn_description |

###  <a name="130"></a>Financial dimension format (msdyn_financialdimensionformats)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DIMENSIONFORMATNAME | = | msdyn_dimensionformatname |
DIMENSIONFORMATTYPE | ><<br>`dataEntityDefaultDimensionFormat` : `192350000`<br>`dataEntityLedgerDimensionFormat` : `192350001`<br>`dataEntityBudgetDimensionFormat` : `192350002`<br>`dataEntityBudgetPlanningDimensionFormat` : `192350003` | msdyn_dimensionformattype |
FINANCIALDIMENSIONFORMAT | = | msdyn_financialdimensionformat |
ISACTIVE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isactive |

###  <a name="128"></a>Financial dimensions (msdyn_dimensionattributes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DIMENSIONNAME | = | msdyn_dimensionname |
COPYVALUESONCREATE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_copyvaluesoncreate |
REPORTCOLUMNNAME | = | msdyn_reportcolumnname |
GIVEDERIVEDDIMENSIONSPRECEDENCE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_givederiveddimensionsprecedence |
UseValuesFrom | = | msdyn_usevaluesfrom |
DimensionValueMask | = | msdyn_dimensionvaluemask |

###  <a name="132"></a>Fiscal calendar integration entity (msdyn_fiscalcalendars)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CALENDARID | = | msdyn_calendar |
DESCRIPTION | = | msdyn_description |

###  <a name="131"></a>Fiscal calendar period (msdyn_fiscalcalendarperiods)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
COMMENTS | = | msdyn_comments |
ENDDATE | = | msdyn_enddate |
MONTH | ><<br>`month1` : `192350000`<br>`month2` : `192350001`<br>`month3` : `192350002`<br>`month4` : `192350003`<br>`month5` : `192350004`<br>`month6` : `192350005`<br>`month7` : `192350006`<br>`month8` : `192350007`<br>`month9` : `192350008`<br>`month10` : `192350009`<br>`month11` : `192350010`<br>`month12` : `192350011` | msdyn_month |
CALENDAR | = | msdyn_fiscalcalendar.msdyn_calendar |
QUARTER | ><<br>`q1` : `192350000`<br>`q2` : `192350001`<br>`q3` : `192350002`<br>`q4` : `192350003` | msdyn_quarter |
SHORTNAME | = | msdyn_shortname |
STARTDATE | = | msdyn_startdate |
TYPE | ><<br>`opening` : `192350000`<br>`operating` : `192350001`<br>`closing` : `192350002` | msdyn_fiscalperiodtype |
PERIODNAME | = | msdyn_periodname |
FISCALYEAR | = | msdyn_fiscalcalendaryear.msdyn_name |
CALENDAR | = | msdyn_fiscalcalendaryear.msdyn_fiscalcalendarname |

###  <a name="133"></a>Fiscal calendar year integration entity (msdyn_fiscalcalendaryears)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
FISCALCALENDAR_CALENDARID | = | msdyn_fiscalcalendarname |
NAME | = | msdyn_name |
STARTDATE | = | msdyn_startdate |
ENDDATE | = | msdyn_enddate |
FISCALCALENDAR_CALENDARID | = | msdyn_calendar.msdyn_calendar |

###  <a name="203"></a>Inventory aisle (msdyn_warehouseaisles)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
AISLEID | = | msdyn_aisleid |
AISLENUMBER | = | msdyn_aislenumber |
WAREHOUSEID | = | msdyn_warehouse.msdyn_warehouseidentifier |
AISLENAME | = | msdyn_aislename |
MANUALSTARTINGSORTORDERCODE | = | msdyn_manualstartingsortordercode |
ISSORTORDERCODEASSIGNEDDESCENDING | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_issortordercodeassigneddescending |

###  <a name="196"></a>Item sales tax group (msdyn_taxitemgroups)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
TAXITEMGROUP | = | msdyn_name |
NAME | = | msdyn_description |

###  <a name="107"></a>Jobs (cdm_jobs)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
JOBID | = | cdm_name |
MAXIMUMNUMBEROFPOSITIONS | = | cdm_maximumnumberofpositions |
ALLOWUNLIMITEDPOSITIONS | ><<br>`yes` : `true`<br>`no` : `false` | cdm_allowunlimitedpositions |
DESCRIPTION | = | cdm_description |
JOBDESCRIPTION | = | cdm_jobdescription |
JOBTYPEID | = | cdm_jobtypeid.cdm_name |
FUNCTIONID | = | cdm_jobfunctionid.cdm_name |
EFFECTIVE | = | cdm_validfrom |
EXPIRATION | = | cdm_validto |
FULLTIMEEQUIVALENT | = | cdm_defaultfulltimeequivalent |

###  <a name="109"></a>Language codes (cdm_languages)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
LANGUAGECODEID | = | cdm_name |
DESCRIPTION | = | cdm_description |

###  <a name="148"></a>Ledger (msdyn_ledgers)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
LEGALENTITYID | > | msdyn_company.cdm_companycode |
DESCRIPTION | > | msdyn_description |
ACCOUNTINGCURRENCY | > | msdyn_accountingcurrency.isocurrencycode |
ISBUDGETCONTROLENABLED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isbudgetcontrolenabled |
NAME | > | msdyn_name |
REPORTINGCURRENCY | > | msdyn_reportingcurrency.isocurrencycode |
BUDGETEXCHANGERATETYPE | > | msdyn_budgetexchangeratetype.msdyn_name |
CHARTOFACCOUNTS | > | msdyn_chartofaccounts.msdyn_name |
EXCHANGERATETYPE | > | msdyn_exchangeratetype.msdyn_name |
FISCALCALENDAR | > | msdyn_fiscalcalendar.msdyn_calendar |
REPORTINGCURRENCYEXCHANGERATETYPE | > | msdyn_reportingcurrencyexchangeratetype.msdyn_name |

###  <a name="102"></a>Legal entities (cdm_companies)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
NAME | > | cdm_name |
LEGALENTITYID | > | cdm_companycode |

###  <a name="142"></a>Legal entities (msdyn_internalorganizations)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
NAMEALIAS | > | msdyn_namealias |
LANGUAGEID | > | msdyn_languageid |
NAME | > | msdyn_name |
PARTYNUMBER | > | msdyn_partynumber |
none | >> | msdyn_type | 806380000
LEGALENTITYID | > | msdyn_companycode |

###  <a name="149"></a>Loyalty card (msdyn_loyaltycards)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CARDNUMBER | = | msdyn_cardnumber |
CARDTENDERTYPE | ><<br>`asCardTender` : `806380000`<br>`asContactTender` : `806380001`<br>`noTender` : `806380002`<br>`blocked` : `806380003` | msdyn_cardtendertype |
PARTYNUMBER | = | msdyn_partynumber |
REPLACEMENTCARDNUMBER | > | msdyn_replacementcardnumber |
OMOPERATINGUNITNUMBER | = | msdyn_operatingunitnumber |
LOYALTYENROLLMENTDATE | = | msdyn_enrollmentdate |
LOYALTYENROLLMENTDATELOCAL | = | msdyn_effectivedate |

###  <a name="226"></a>Loyalty levels (msdyn_loyaltylevels)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
LEVELPHRASE | = | msdyn_levelphrase |
LEVELDESCRIPTION | = | msdyn_description |

###  <a name="150"></a>Loyalty reward points (msdyn_loyaltyrewardpoints)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
EXPIRATIONTIMEUNIT | ><<br>`day` : `806380000`<br>`month` : `806380001`<br>`year` : `806380002` | msdyn_expirationtimeunit |
EXPIRATIONTIMEVALUE | = | msdyn_expirationtimevalue |
REDEEMABLE | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_redeemable |
REDEEMRANKING | = | msdyn_redeemranking |
REWARDPOINTCURRENCY | = | msdyn_rewardpointcurrency.isocurrencycode |
REWARDPOINTID | = | msdyn_rewardpointid |
REWARDPOINTTYPE | ><<br>`quantity` : `192350000`<br>`amount` : `192350001` | msdyn_rewardpointtype |
MAXIMUMLOYALTYREWARDPOINTS | = | msdyn_maximumloyaltyrewardpoints |
VESTINGTIMEUNIT | ><<br>`day` : `806380000`<br>`month` : `806380001`<br>`year` : `806380002` | msdyn_vestingtimeunit |
VESTINGTIMEVALUE | = | msdyn_vestingtimevalue |

###  <a name="152"></a>Main account (msdyn_mainaccounts)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
MAINACCOUNTID | = | msdyn_accountnumber |
CHARTOFACCOUNTS | = | msdyn_chartofaccounts.msdyn_name |
NAME | = | msdyn_name |
BALANCECONTROL | ><<br>`none` : `192350000`<br>`debit` : `192350001`<br>`credit` : `192350002` | msdyn_balancecontrol |
EXCHANGEADJUSTMENTRATETYPE | = | msdyn_exchangeadjustmentratetype.msdyn_name |
CLOSING | ><<br>`none` : `192350000`<br>`result` : `192350001`<br>`balanceSheet` : `192350002`<br>`capital` : `192350003` | msdyn_closing |
REPORTINGEXCHANGEADJUSTMENTRATETYPE | = | msdyn_reportingexchangeadjustmentratetype.msdyn_name |
DEBITCREDITREQUIREMENT | ><<br>`none` : `192350000`<br>`debit` : `192350001`<br>`credit` : `192350002` | msdyn_debitcreditrequirement |
FINANCIALREPORTINGEXCHANGERATETYPE | = | msdyn_financialreportingexchangeratetype.msdyn_name |
FOREIGNCURRENCYREVALUATION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_foreigncurrencyrevaluation |
MAINACCOUNTCATEGORY | = | msdyn_mainaccountcategoryname |
MANDATORYPAYMENTREFERENCE | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_mandatorypaymentreference |
MONETARY | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_monetary |
OFFSETACCOUNTDISPLAYVALUE | = | msdyn_offsetaccount |
POSTINGTYPE | ><<br>`none` : `192350000`<br>`exchRateGain` : `192350001`<br>`exchRateLoss` : `192350002`<br>`interCompany` : `192350003`<br>`tax` : `192350004`<br>`vATRoundOff` : `192350005`<br>`allocation` : `192350006`<br>`investmentDuty` : `192350007`<br>`liquidity` : `192350008`<br>`mSTDiffSecond` : `192350009`<br>`errorAccount` : `192350010`<br>`mSTDiff` : `192350011`<br>`yearResult` : `192350012`<br>`closing` : `192350013`<br>`ledgerJournal` : `192350014`<br>`cashDiscount` : `192350015`<br>`consolidateDiffBalance` : `192350016`<br>`taxReport` : `192350017`<br>`transferOpeningClosing` : `192350018`<br>`bank` : `192350019`<br>`conversionProfit` : `192350020`<br>`conversionLoss` : `192350021`<br>`taxwithhold` : `192350022`<br>`consolidateDiffProfitLoss` : `192350023`<br>`indirectEstimatedAbsorptionOffset` : `192350024`<br>`indirectAbsorption` : `192350025`<br>`indirectAbsorptionOffset` : `192350026`<br>`freeTextInvoice` : `192350027`<br>`conversionReportingLoss` : `192350029`<br>`conversionReportingProfit` : `192350030`<br>`custBalance` : `192350031`<br>`custRevenue` : `192350032`<br>`custInterest` : `192350033`<br>`custCashDisc` : `192350034`<br>`custCollectionLetterFee` : `192350035`<br>`custInterestFee` : `192350036`<br>`custInvoiceDisc` : `192350028`<br>`custPayment` : `192350037`<br>`custReimbursement` : `192350038`<br>`custSettlement` : `192350039`<br>`vendBalance` : `192350040`<br>`vendPurchLedger` : `192350041`<br>`vendOffsetAccount` : `192350042`<br>`vendInterest` : `192350043`<br>`vendCashDisc` : `192350044`<br>`vendPayment` : `192350045`<br>`vendInvoiceDisc` : `192350046`<br>`vendSettlement` : `192350047`<br>`crossCompanySettlement` : `192350048`<br>`inventIssueFixedAsset` : `192350049`<br>`salesRevenue` : `192350050`<br>`salesConsump` : `192350051`<br>`salesDisc` : `192350052`<br>`salesCash` : `192350053`<br>`salesFreight` : `192350054`<br>`salesFee` : `192350055`<br>`salesPostage` : `192350056`<br>`salesRoundOff` : `192350057`<br>`salesPackingSlip` : `192350058`<br>`salesOffsetAccountPackingSlip` : `192350059`<br>`salesIssue` : `192350060`<br>`salesCommission` : `192350061`<br>`salesOffsetAccountCommission` : `192350062`<br>`salesPckSlipRevenue` : `192350063`<br>`salesPckSlipRevenueOffsetAccount` : `192350064`<br>`rebate` : `192350065`<br>`pdsCWLoss` : `192350066`<br>`pdsCWProfit` : `192350067`<br>`purchConsump` : `192350068`<br>`purchDisc` : `192350069`<br>`purchCash` : `192350070`<br>`purchFreight` : `192350071`<br>`purchFee` : `192350072`<br>`purchPostage` : `192350073`<br>`purchOffsetAccount` : `192350074`<br>`purchaseInvoiceRoundOff` : `192350075`<br>`purchMarkupFreight` : `192350076`<br>`purchMarkupCustoms` : `192350077`<br>`purchMarkupInsurance` : `192350078`<br>`purchPckSlp` : `192350079`<br>`purchOffsetAccountPckSlp` : `192350080`<br>`purchReceipt` : `192350081`<br>`purchStdProfit` : `192350082`<br>`purchStdLoss` : `192350083`<br>`purchStdOffsetAccount` : `192350084`<br>`inventReceipt` : `192350085`<br>`inventIssue` : `192350086`<br>`inventProfit` : `192350087`<br>`inventLoss` : `192350088`<br>`inventStdProfit` : `192350089`<br>`inventStdLoss` : `192350090`<br>`opening_ES` : `192350091`<br>`purchReq` : `192350092`<br>`aPInvoice` : `192350093`<br>`budget` : `192350094`<br>`purchOrderYearEnd` : `192350095`<br>`inflationAdjustment_MX` : `192350096`<br>`prodReportFinished` : `192350097`<br>`prodReportFinishedOffsetAccount` : `192350098`<br>`prodIssue` : `192350099`<br>`prodIssueOffsetAccount` : `192350100`<br>`prodReceipt` : `192350101`<br>`prodReceiptOffsetAccount` : `192350102`<br>`prodPicklistOffsetAccount` : `192350103`<br>`prodPicklist` : `192350104`<br>`prodWIPValuation` : `192350105`<br>`prodWIPIssue` : `192350106`<br>`prodWrkCtrIssue` : `192350107`<br>`prodScrap` : `192350108`<br>`prodScrapOffsetAccount` : `192350109`<br>`prodLeanWIPServiceReceipt` : `192350110`<br>`prodLeanWIPServiceClearing` : `192350111`<br>`projCost` : `192350112`<br>`projPayrollAllocation` : `192350113`<br>`projWIPCostvalue` : `192350114`<br>`projOffsetAccountItem` : `192350115`<br>`projStatusAccountItem` : `192350116`<br>`projTurnover` : `192350117`<br>`projOnAccount` : `192350118`<br>`projSalesvalue` : `192350119`<br>`projSalesvalueOffset` : `192350120`<br>`projAccruedTurnoverProd` : `192350121`<br>`projWIPProduction` : `192350122`<br>`proJAccruedTurnoverProfit` : `192350123`<br>`projWIPProfit` : `192350125`<br>`projNeverLedger` : `192350126`<br>`projAccruedCost` : `192350127`<br>`projWIPCost` : `192350128`<br>`projAccruedRevenueOnAccount` : `192350129`<br>`projWIPInvoicedOnAccount` : `192350130`<br>`projNoLedger` : `192350131`<br>`payrollDebitAccount` : `192350132`<br>`payrollCreditAccount` : `192350133`<br>`emplPayment_RU` : `192350134`<br>`rTSLTranslationDifference` : `192350135`<br>`rCash` : `192350136`<br>`inventRoundingLoss_RU` : `192350137`<br>`inventRoundingProfit_RU` : `192350138`<br>`advanceAdjustmentGain_RU` : `192350139`<br>`advanceAdjustmentLoss_RU` : `192350140`<br>`fixedAssetsDebit` : `192350141`<br>`fixedAssetsCredit` : `192350142`<br>`cACLedgerJournalNoOff` : `192350143`<br>`amountDiffGain_RU` : `192350144`<br>`amountDiffLoss_RU` : `192350145`<br>`misc_IN` : `192350146`<br>`transferGoodsTransit_IN` : `192350147`<br>`transferScrap_IN` : `192350148`<br>`purchCharge` : `192350149`<br>`purchStockVariation` : `192350150`<br>`purchPckSlpPurchaseOffsetAccount` : `192350151`<br>`purchPckSlpTax` : `192350152`<br>`purchPckSlpPurchase` : `192350153`<br>`salesPackingslipTax` : `192350154`<br>`projAccruedRevenueSubscription` : `192350155`<br>`projWIPSubscription` : `192350156`<br>`taxOffsetWithhold_TH` : `192350157`<br>`inventStdCostChangeVariance` : `192350158`<br>`inventSystemRounding` : `192350159`<br>`purchAdvance` : `192350160`<br>`purchStdCostPurchasePriceVariance` : `192350161`<br>`purchAdvanceApplication` : `192350162`<br>`prodStdCostProductionVariance` : `192350163`<br>`salesGoodsInRoute_RU` : `192350164`<br>`salesGoodsInRouteOffset_RU` : `192350165`<br>`inventInterUnitPayable` : `192350166`<br>`inventInterUnitReceivable` : `192350167`<br>`indirectEstimatedAbsorption` : `192350168`<br>`prodStdCostLotSizeVariance` : `192350169`<br>`prodStdCostQuantityVariance` : `192350170`<br>`prodStdCostSubstitutionVariance` : `192350171`<br>`inventStdCostRoundingVariance` : `192350172`<br>`purchReceiptFixedAsset` : `192350173`<br>`pSATransportation` : `192350174`<br>`pSACompanyCCClearing` : `192350175`<br>`pSAEmployeeClearing` : `192350176`<br>`pSAEmployeeAdvance` : `192350177`<br>`pSAWriteOffCap` : `192350178`<br>`pSAProjRetain` : `192350179`<br>`pSAProjPurchRetain` : `192350180`<br>`inventStdCostRevaluation` : `192350181`<br>`purchExpense` : `192350182`<br>`vAT_IN` : `192350183`<br>`inventMovingAveragePriceDifference` : `192350184`<br>`salesTax_IN` : `192350185`<br>`inventMovingAverageCostRevaluation` : `192350186`<br>`excise_IN` : `192350187`<br>`intercompanyCost` : `192350188`<br>`serviceTax_IN` : `192350189`<br>`intercompanyRevenue` : `192350190`<br>`customs_IN` : `192350191`<br>`tDS_IN` : `192350192`<br>`tCS_IN` : `192350193`<br>`transferIssue_IN` : `192350194`<br>`transferReceipt_IN` : `192350195`<br>`transferProfit_IN` : `192350196`<br>`transferLoss_IN` : `192350197`<br>`taxAdjustmentSettlement_IN` : `192350198`<br>`taxExpense_BR` : `192350199`<br>`bankStatement` : `192350200`<br>`emplBalance_RU` : `192350201`<br>`debitNote_BR` : `192350202`<br>`custFine_BR` : `192350203`<br>`vendFine_BR` : `192350204`<br>`payroll` : `192350205`<br>`interunitDebit` : `192350206`<br>`interunitCredit` : `192350207`<br>`fixedAssetsDebit_RU` : `192350208`<br>`fixedAssetsCredit_RU` : `192350209`<br>`transferInterim_In` : `192350210`<br>`deferralsDebit_RU` : `192350211`<br>`deferralsCredit_RU` : `192350212`<br>`mCRReturns` : `192350213`<br>`mCRReturnsConsump` : `192350214`<br>`mCRUnderpayWriteOff` : `192350215`<br>`mCRBrokerFee` : `192350216`<br>`rPayTaxRefundOffset` : `192350217`<br>`budgetReservation_PSN` : `192350218`<br>`budgetReservationYearEnd_PSN` : `192350219`<br>`billSchUnbilledAccountsReceivable` : `192350220`<br>`billSchAccruedRevenue` : `192350221`<br>`gST_IN` : `192350222`<br>`reportingCurrencyAdjustment` : `192350223`<br>`revRecDeferredRevenue` : `192350224`<br>`revRecDeferredCostOfGoodsSold` : `192350225`<br>`revRecPartialRevenue` : `192350226`<br>`revRecDeferredCost` : `192350227` | msdyn_postingtype |
SRUCODE | = | msdyn_srucode |
VALIDATECURRENCY | ><<br>`optional` : `192350000`<br>`fillIn` : `192350001`<br>`table` : `192350002`<br>`list` : `192350003` | msdyn_validatecurrencycode |
VALIDATEUSER | ><<br>`optional` : `192350000`<br>`fillIn` : `192350001`<br>`table` : `192350002`<br>`list` : `192350003` | msdyn_validateuser |
DEBITCREDITDEFAULT | ><<br>`none` : `192350000`<br>`debit` : `192350001`<br>`credit` : `192350002` | msdyn_debitcreditdefault |
DEFAULTCURRENCY | = | msdyn_defaultcurrency.isocurrencycode |
MAINACCOUNTTYPE | ><<br>`blank` : `192350000`<br>`profitAndLoss` : `192350001`<br>`revenue` : `192350002`<br>`expense` : `192350003`<br>`balanceSheet` : `192350004`<br>`asset` : `192350005`<br>`liability` : `192350006`<br>`equity` : `192350007`<br>`total` : `192350008`<br>`reporting` : `192350009`<br>`common_CN` : `192350010` | msdyn_mainaccounttype |
FINANCIALREPORTINGCURRENCYTRANSLATIONTYPE | ><<br>`weightedAverage` : `192350000`<br>`standardAverage` : `192350001`<br>`current` : `192350002`<br>`transactionDate` : `192350003` | msdyn_financialreportingcurrencytrantype |
USER | = | msdyn_user |
VALIDATEPOSTINGTYPE | ><<br>`optional` : `192350000`<br>`fillIn` : `192350001`<br>`table` : `192350002`<br>`list` : `192350003` | msdyn_validateposting |

###  <a name="151"></a>Main account categories (msdyn_mainaccountcategories)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
MAINACCOUNTCATEGORY | = | msdyn_mainaccountcategory |
REFERENCEID | = | msdyn_referenceid |
DESCRIPTION | = | msdyn_description |
DISPLAYORDER | = | msdyn_displayorder |
CLOSED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_closed |
MAINACCOUNTTYPE | ><<br>`blank` : `192350000`<br>`profitAndLoss` : `192350001`<br>`revenue` : `192350002`<br>`expense` : `192350003`<br>`balanceSheet` : `192350004`<br>`asset` : `192350005`<br>`liability` : `192350006`<br>`equity` : `192350007` | msdyn_mainaccounttypevalue |

###  <a name="212"></a>Mixed reality guides entity (msmrw_guides)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
INTEGRATIONKEY | < | msmrw_integrationkey |
NAME | < | msmrw_name |
SCHEMAVERSION | < | msmrw_schemaversion |
GUIDEID | < | msmrw_guideid |
CREATEDON | < | createdon |
LASTMODIFIEDON | < | modifiedon |

###  <a name="192"></a>Modes of delivery (msdyn_shipvias)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
MODECODE | = | msdyn_name |
MODEDESCRIPTION | = | msdyn_description |

###  <a name="155"></a>Name affixes (msdyn_nameaffixes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
AFFIX | = | msdyn_affix |
TYPE | ><<br>`personalSuffix` : `806380001`<br>`personalPrefix` : `806380000` | msdyn_affixtype |
DESCRIPTION | = | msdyn_description |

###  <a name="143"></a>Operating unit (msdyn_internalorganizations)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
LANGUAGEID | > | msdyn_languageid |
NAMEALIAS | > | msdyn_namealias |
NAME | > | msdyn_name |
PARTYNUMBER | > | msdyn_partynumber |
OPERATINGUNITTYPE | >><br>`omDepartment` : `806380001`<br>`none` : `806380002`<br>`omCostCenter` : `806380003`<br>`omValueStream` : `806380004`<br>`omBusinessUnit` : `806380005`<br>`omAnyOU` : `806380006`<br>`retailChannel` : `192350000` | msdyn_type |

###  <a name="139"></a>Organization hierarchy - published (msdyn_internalorganizationhierarchies)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
VALIDTO | > | msdyn_validto |
VALIDFROM | > | msdyn_validfrom |
HIERARCHYTYPE | > | msdyn_hierarchytypename |
PARENTORGANIZATIONPARTYNUMBER | > | msdyn_parentpartyid |
CHILDORGANIZATIONPARTYNUMBER | > | msdyn_childpartyid |
HIERARCHYTYPE | > | msdyn_hierarchytypeid.msdyn_name |
CHILDORGANIZATIONPARTYNUMBER | > | msdyn_childid.msdyn_partynumber |
PARENTORGANIZATIONPARTYNUMBER | > | msdyn_parentid.msdyn_partynumber |

###  <a name="140"></a>Organization hierarchy purposes (msdyn_internalorganizationhierarchypurposes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
HIERARCHYTYPE | > | msdyn_hierarchypurposetypename |
HIERARCHYTYPE | > | msdyn_hierarchytype.msdyn_name |
HIERARCHYPURPOSE | >><br>`notSet` : `806380000`<br>`purchaseControl` : `806380001`<br>`expenseControl` : `806380002`<br>`organizationChart` : `806380003`<br>`signingLimitControl` : `806380004`<br>`invoiceControl` : `806380005`<br>`auditInternalControl` : `806380006`<br>`centralizedPayments` : `806380007`<br>`security` : `806380008`<br>`retailAssortment` : `806380009`<br>`retailReplenishment` : `806380010`<br>`retailReporting` : `806380011`<br>`benefitEligibilityControl` : `806380012`<br>`budgetPlanning` : `806380013`<br>`retailPOSPosting` : `806380014`<br>`project` : `806380015`<br>`premiumEarningGeneration` : `806380016`<br>`distributedOrderManagement` : `806380017` | msdyn_hierarchypurpose |
IMMUTABLE | >><br>`no` : `False`<br>`yes` : `True` | msdyn_immutable |
SETASDEFAULT | >><br>`no` : `False`<br>`yes` : `True` | msdyn_setasdefault |

###  <a name="141"></a>Organization hierarchy type (msdyn_internalorganizationhierarchytypes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
NAME | > | msdyn_name |

###  <a name="236"></a>Party contacts V3 (msdyn_partyelectronicaddresses)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
COUNTRYREGIONCODE | = | msdyn_internationalcallingcode |
DESCRIPTION | = | msdyn_description |
ELECTRONICADDRESSID | = | msdyn_electronicaddressnumber |
PARTYNUMBER | = | msdyn_partyid.msdyn_partynumber |
LOCATOR | = | msdyn_locator |
LOCATOREXTENSION | = | msdyn_locatorextension |
ISINSTANTMESSAGE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isinstantmessage |
ISMOBILEPHONE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_ismobile |
ISPRIMARY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isprimary |
ISPRIVATE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isprivate |
PURPOSE | = | msdyn_purpose |
TYPE | ><<br>`phone` : `192350001`<br>`email` : `192350002`<br>`url` : `192350003`<br>`telex` : `192350004`<br>`fax` : `192350005`<br>`facebook` : `192350006`<br>`twitter` : `192350007`<br>`linkedin` : `192350008` | msdyn_type |

###  <a name="157"></a>Payment day lines CDS V2 (msdyn_paymentdaylines)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
NAME | = | msdyn_paymentday.msdyn_name |
LINENUMBER | = | msdyn_linenumber |
FREQUENCY | ><<br>`week` : `806380000`<br>`month` : `806380001` | msdyn_frequency |
DAYOFWEEK | ><<br>`none` : `806380000`<br>`monday` : `806380001`<br>`tuesday` : `806380002`<br>`wednesday` : `806380003`<br>`thursday` : `806380004`<br>`friday` : `806380005`<br>`saturday` : `806380006`<br>`sunday` : `806380007` | msdyn_dayofweek |
DAYOFMONTH | = | msdyn_dayofmonth |

###  <a name="158"></a>Payment days CDS (msdyn_paymentdays)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
NAME | = | msdyn_name |
DESCRIPTION | = | msdyn_description |

###  <a name="160"></a>Payment schedule (msdyn_paymentschedules)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
NAME | = | msdyn_name |
DESCRIPTION | = | msdyn_description |
ALLOCATIONMETHOD | ><<br>`total` : `806380000`<br>`amountByPayment` : `806380001`<br>`numOfPayment` : `806380002`<br>`specified` : `806380003` | msdyn_allocationmethod |
PAYMENTFREQUENCYUNITS | ><<br>`day` : `806380000`<br>`month` : `806380001`<br>`year` : `806380002` | msdyn_paymentfrequencyunit |
PAYMENTFREQUENCY | = | msdyn_paymentfrequency |
NUMBEROFPAYMENTS | = | msdyn_numberofpayments |
FIXEDPAYMENTAMOUNT | = | msdyn_fixedpaymentamount |
MINIMUMPAYMENTAMOUNT | = | msdyn_minimumpaymentamount |
SALESTAXALLOCATIONMETHOD | ><<br>`proportional` : `806380000`<br>`firstRate` : `806380001`<br>`lastRate` : `806380002` | msdyn_salestaxallocationmethod |
NOTES | = | msdyn_note |

###  <a name="159"></a>Payment schedule lines (msdyn_paymentschedulelines)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PAYMENTSCHEDULENAME | = | msdyn_paymentschedule.msdyn_name |
LINENUMBER | = | msdyn_linenumber |
PERIODSAFTERDUEDATE | = | msdyn_periodsafterduedate |
PERCENTORAMOUNT | ><<br>`percent` : `806380000`<br>`amount` : `806380001` | msdyn_percentoramount |
PERCENTORAMOUNTVALUE | = | msdyn_percentoramountvalue |

###  <a name="227"></a>Personal character types (msdyn_personalcharactertypes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
TYPEDESCRIPTION | = | msdyn_typedescription |
TYPENAME | = | msdyn_typename |

###  <a name="110"></a>Position type (cdm_positiontypes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
POSITIONTYPEID | = | cdm_name |
DESCRIPTION | = | cdm_description |
CLASSIFICATION | ><<br>`fulltime` : `754400000`<br>`parttime` : `754400001`<br>blank : `754400002` | cdm_classification |

###  <a name="111"></a>Position worker assignments (cdm_positionworkerassignmentmaps)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PERSONNELNUMBER | = | cdm_workerid.cdm_workernumber |
POSITIONID | = | cdm_jobpositionid.cdm_jobpositionnumber |
VALIDFROM | = | cdm_validfrom |
VALIDTO | = | cdm_validto |

###  <a name="106"></a>Positions V2 (cdm_jobpositions)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
POSITIONID | = | cdm_jobpositionnumber |
DESCRIPTION | = | cdm_description |
ACTIVATION | = | cdm_activation |
AVAILABLEFORASSIGNMENT | = | cdm_availableforassignment |
FULLTIMEEQUIVALENT | = | cdm_fulltimeequivalent |
DETAILEFFECTIVE | = | cdm_validfrom |
DETAILEXPIRATION | = | cdm_validto |
RETIREMENT | = | cdm_retirement |
POSITIONTYPEID | = | cdm_positiontypeid.cdm_name |
JOBID | = | cdm_jobid.cdm_name |

###  <a name="162"></a>Price customer groups (msdyn_pricecustomergroups)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
GROUPCODE | = | msdyn_groupcode |
GROUPNAME | = | msdyn_groupname |

###  <a name="164"></a>Product Number Identified Barcode (msdyn_productbarcodes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PRODUCTNUMBER | > | msdyn_productnumberid.msdyn_productnumber |
BARCODE | > | msdyn_name |
BARCODE | > | msdyn_barcode |
PRODUCTQUANTITY | > | msdyn_productquantity |
PRODUCTDESCRIPTION | > | msdyn_productdescription |
BARCODESETUPID | > | msdyn_barcodesetupid |
PRODUCTQUANTITYUNITSYMBOL | > | msdyn_unitofmeasureid.msdyn_symbol |
ISDEFAULTSCANNEDBARCODE | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isdefaultscannedbarcode |
ISDEFAULTPRINTEDBARCODE | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isdefaultprintedbarcode |
ISDEFAULTDISPLAYEDBARCODE | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isdefaultdisplayedbarcode |

###  <a name="166"></a>Product categories (msdyn_productcategories)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PRODUCTCATEGORYHIERARCHYNAME | = | msdyn_hierarchy.msdyn_name |
ISCATEGORYINHERITINGPARENTPRODUCTATTRIBUTES | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isinheritingparentproductattributes |
PROJECTCATEGORYNAME | = | msdyn_projectcategoryname |
ISTANGIBLEPRODUCT | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_istangibleproduct |
ISCATEGORYINHERITINGPARENTCATEGORYATTRIBUTES | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isinheritingparentcategoryattributes |
CATEGORYCODE | = | msdyn_code |
CATEGORYDESCRIPTION | = | msdyn_description |
CATEGORYKEYWORDS | = | msdyn_keywords |
CATEGORYNAME | = | msdyn_name |
FRIENDLYCATEGORYNAME | = | msdyn_friendlycategoryname |
PARENTPRODUCTCATEGORYNAME | = | msdyn_parentproductcategory.msdyn_name |
PARENTPRODUCTCATEGORYHIERARCHYNAME | > | msdyn_parentproductcategory.msdyn_hierarchy.msdyn_name |
CATEGORYRECORDID | > | msdyn_externalproductcategoryid |
EXTERNALID | = | msdyn_integrationid |

###  <a name="167"></a>Product category assignments (msdyn_productcategoryassignments)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PRODUCTNUMBER | = | msdyn_globalproduct.msdyn_productnumber |
PRODUCTCATEGORYNAME | = | msdyn_productcategory.msdyn_name |
PRODUCTCATEGORYHIERARCHYNAME | = | msdyn_productcategory.msdyn_hierarchy.msdyn_name |
PRODUCTNUMBER | > | msdyn_name |

###  <a name="168"></a>Product category hierarchies (msdyn_productcategoryhierarchies)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
HIERARCHYNAME | = | msdyn_name |
HIERARCHYDESCRIPTION | = | msdyn_description |

###  <a name="169"></a>Product category hierarchy roles (msdyn_productcategoryhierarchyroles)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PRODUCTCATEGORYHIERARCHYNAME | = | msdyn_hierarchy.msdyn_name |
HIERARCHYROLE | ><<br>`procurement` : `192350000`<br>`sales` : `192350001`<br>`retail` : `192350002`<br>`commodity` : `192350003`<br>`financials` : `192350004`<br>`retailSpecialGroup` : `192350005`<br>`retailVendorProductHierarchy` : `192350006`<br>`retailChannelNavigation` : `192350007`<br>`packingMaterials_W` : `192350008`<br>`commonDataService` : `192350009`<br>`costManagement` : `192350010`<br>`engineeringProduct` : `192350011` | msdyn_hierarchyrole |

###  <a name="175"></a>Product default order settings V2 (msdyn_productspecificdefaultordersettings)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
INVENTORYWAREHOUSEID | = | msdyn_inventorywarehouse.msdyn_warehouseidentifier |
INVENTORYSITEID | = | msdyn_inventorysite.msdyn_siteid |
INVENTORYATPDELAYEDDEMANDOFFSETDAYS | = | msdyn_inventoryatpdelayeddemandoffsetdays |
INVENTORYATPDELAYEDSUPPLYOFFSETDAYS | = | msdyn_inventoryatpdelayedsupplyoffsetdays |
ITEMNUMBER | = | msdyn_itemnumber.msdyn_itemnumber |
INVENTORYATPBACKWARDDEMANDTIMEFENCEDAYS | = | msdyn_inventoryatpbackwarddemandtimefencedays |
INVENTORYATPBACKWARDSUPPLYTIMEFENCEDAYS | = | msdyn_inventoryatpbackwardsupplytimefencedays |
INVENTORYATPTIMEFENCEDAYS | = | msdyn_inventoryatptimefencedays |
MAXIMUMINVENTORYORDERQUANTITY | = | msdyn_maximuminventoryorderquantity |
MAXIMUMPROCUREMENTORDERQUANTITY | = | msdyn_maximumprocurementorderquantity |
MAXIMUMSALESORDERQUANTITY | = | msdyn_maximumsalesorderquantity |
MINIMUMINVENTORYORDERQUANTITY | = | msdyn_minimuminventoryorderquantity |
MINIMUMPROCUREMENTORDERQUANTITY | = | msdyn_minimumprocurementorderquantity |
MINIMUMSALESORDERQUANTITY | = | msdyn_minimumsalesorderquantity |
STANDARDINVENTORYORDERQUANTITY | = | msdyn_standardinventoryorderquantity |
STANDARDPROCUREMENTORDERQUANTITY | = | msdyn_standardprocurementorderquantity |
STANDARDSALESORDERQUANTITY | = | msdyn_standardsalesorderquantity |
INVENTORYLEADTIMEDAYS | = | msdyn_inventoryleadtimedays |
INVENTORYQUANTITYMULTIPLES | = | msdyn_inventoryquantitymultiples |
PROCUREMENTQUANTITYMULTIPLES | = | msdyn_procurementquantitymultiples |
SALESQUANTITYMULTIPLES | = | msdyn_salesquantitymultiples |
PROCUREMENTSITEID | = | msdyn_procurementsite.msdyn_siteid |
PROCUREMENTLEADTIMEDAYS | = | msdyn_procurementleadtimedays |
SALESSITEID | = | msdyn_salessite.msdyn_siteid |
SALESATPDELAYEDDEMANDOFFSETDAYS | = | msdyn_salesatpdelayeddemandoffsetdays |
SALESATPDELAYEDSUPPLYOFFSETDAYS | = | msdyn_salesatpdelayedsupplyoffsetdays |
SALESATPBACKWARDDEMANDTIMEFENCEDAYS | = | msdyn_salesatpbackwarddemandtimefencedays |
SALESATPBACKWARDSUPPLYTIMEFENCEDAYS | = | msdyn_salesatpbackwardsupplytimefencedays |
SALESATPTIMEFENCEDAYS | = | msdyn_salesatptimefencedays |
SALESLEADTIMEDAYS | = | msdyn_salesleadtimedays |
PROCUREMENTWAREHOUSEID | = | msdyn_procurementwarehouse.msdyn_warehouseidentifier |
SALESWAREHOUSEID | = | msdyn_saleswarehouse.msdyn_warehouseidentifier |
AREINVENTORYDEFAULTORDERSETTINGSOVERRIDDEN | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_areinventoryorderdefaultsoverridden |
INVENTORYORDERPROMISINGMETHOD | ><<br>`none` : `192350000`<br>`salesLeadTime` : `192350001`<br>`atp` : `192350002`<br>`atpPlusIssueMargin` : `192350003`<br>`ctp` : `192350004` | msdyn_inventoryorderpromisingmethod |
ISINVENTORYATPINCLUDINGPLANNEDORDERS | ><<br>`false` : `False`<br>`true` : `True` | msdyn_isinventoryatpincludingplannedorders |
ISINVENTORYUSINGWORKINGDAYS | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isinventoryusingworkingdays |
ISINVENTORYSITEMANDATORY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isinventorysitemandatory |
ISINVENTORYPROCESSINGSTOPPED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isinventoryprocessingstopped |
ISPROCUREMENTUSINGWORKINGDAYS | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isprocurementusingworkingdays |
ISPROCUREMENTSITEMANDATORY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isprocurementsitemandatory |
ISPROCUREMENTPROCESSINGSTOPPED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isprocurementprocessingstopped |
ARESALESDEFAULTORDERSETTINGSOVERRIDDEN | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_aresalesorderdefaultsoverridden |
SALESORDERPROMISINGMETHOD | ><<br>`none` : `192350000`<br>`salesLeadTime` : `192350001`<br>`atp` : `192350002`<br>`atpPlusIssueMargin` : `192350003`<br>`ctp` : `192350004` | msdyn_salesorderpromisingmethod |
ISSALESATPINCLUDINGPLANNEDORDERS | ><<br>`false` : `False`<br>`true` : `True` | msdyn_issalesatpincludingplannedorders |
ISSALESSITEMANDATORY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_issalessitemandatory |
ISSALESLEADTIMEOVERRIDDEN | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_issalesleadtimeoverridden |
ISSALESPROCESSINGSTOPPED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_issalesprocessingstopped |
ISINVENTORYWAREHOUSEMANDATORY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isinventorywarehousemandatory |
ISPROCUREMENTWAREHOUSEMANDATORY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isprocurementwarehousemandatory |
ISSALESWAREHOUSEMANDATORY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_issaleswarehousemandatory |
OPERATIONALSITEID | = | msdyn_operationalsite.msdyn_siteid |
PRODUCTCOLORID | = | msdyn_productcolor.msdyn_productcolorname |
PRODUCTCONFIGURATIONID | = | msdyn_productconfiguration.msdyn_productconfiguration |
PRODUCTSIZEID | = | msdyn_productsize.msdyn_productsize |
PRODUCTSTYLEID | = | msdyn_productstyle.msdyn_productstyle |

###  <a name="173"></a>Product dimension groups (msdyn_productdimensiongroups)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
WILLSALESPRICESEARCHUSEPRODUCTSTYLE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willsalespricesearchuseproductstyle |
WILLPURCHASEPRICESEARCHUSEPRODUCTSIZE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willpurchasepricesearchuseproductsize |
WILLSALESPRICESEARCHUSEPRODUCTCONFIGURATION | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willsalespricesearchuseprodconfig |
WILLSALESPRICESEARCHUSEPRODUCTCOLOR | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willsalespricesearchuseproductcolor |
WILLPURCHASEPRICESEARCHUSEPRODUCTSTYLE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willpurchasepricesearchuseproductstyle |
WILLPURCHASEPRICESEARCHUSEPRODUCTCONFIGURATION | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willpurchpricesearchuseprodconfig |
WILLPURCHASEPRICESEARCHUSEPRODUCTCOLOR | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willpurchpricesearchuseproductcolor |
ISPRODUCTSTYLEACTIVE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isproductstyleactive |
ISPRODUCTSIZEACTIVE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isproductsizeactive |
ISPRODUCTCONFIGURATIONACTIVE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isproductconfigurationactive |
ISPRODUCTCOLORACTIVE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isproductcoloractive |
GROUPNAME | = | msdyn_groupname |
GROUPDESCRIPTION | = | msdyn_groupdescription |
PRODUCTVARIANTNOMENCLATURENAME | = | msdyn_productvariantnomenclaturename |
WILLSALESPRICESEARCHUSEPRODUCTSIZE | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_willsalespricesearchuseproductsize |

###  <a name="187"></a>Product master colors (msdyn_sharedproductcolors)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PRODUCTCOLORID | > | msdyn_productcolor.msdyn_productcolorname |
PRODUCTMASTERNUMBER | > | msdyn_globalproduct.msdyn_productnumber |
REPLENISHMENTWEIGHT | > | msdyn_replenishmentweight |
DISPLAYSEQUENCENUMBER | > | msdyn_displaysequencenumber |

###  <a name="188"></a>Product master configurations (msdyn_sharedproductconfigurations)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CONTAINERUNITSYMBOL | > | msdyn_containerunit.msdyn_symbol |
PRODUCTCONFIGURATIONID | > | msdyn_productconfiguration.msdyn_productconfiguration |
PRODUCTMASTERNUMBER | > | msdyn_globalproduct.msdyn_productnumber |
REPLENISHMENTWEIGHT | > | msdyn_replenishmentweight |
DISPLAYSEQUENCENUMBER | > | msdyn_displaysequencenumber |

###  <a name="190"></a>Product master sizes (msdyn_sharedproductsizes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PRODUCTMASTERNUMBER | > | msdyn_globalproduct.msdyn_productnumber |
PRODUCTSIZEID | > | msdyn_productsize.msdyn_productsize |
REPLENISHMENTWEIGHT | > | msdyn_replenishmentweight |
DISPLAYSEQUENCENUMBER | > | msdyn_displaysequencenumber |

###  <a name="191"></a>Product master styles (msdyn_sharedproductstyles)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PRODUCTMASTERNUMBER | > | msdyn_globalproduct.msdyn_productnumber |
PRODUCTSTYLEID | > | msdyn_productstyle.msdyn_productstyle |
REPLENISHMENTWEIGHT | > | msdyn_replenishmentweight |
DISPLAYSEQUENCENUMBER | > | msdyn_displaysequencenumber |

###  <a name="185"></a>Product receipt header (msdyn_purchaseorderreceipts)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
RECORDID | > | msdyn_recordid |
PRODUCTRECEIPTDATE | > | msdyn_datereceived |
DELIVERYADDRESSLATITUDE | > | msdyn_deliveryaddresslatitude |
DELIVERYADDRESSLONGITUDE | > | msdyn_deliveryaddresslongitude |
PURCHASEORDERNUMBER | > | msdyn_purchaseorder.msdyn_name |
DELIVERYMODEID | > | msdyn_shipvia.msdyn_name |
DELIVERYTERMSID | > | msdyn_deliveryterm.msdyn_termscode |
ORDERVENDORACCOUNTNUMBER | > | msdyn_ordervendor.msdyn_vendoraccountnumber |
REQUESTERPERSONNELNUMBER | > | msdyn_requesterpersonnel.cdm_workernumber |
ISDELIVERYADDRESSPRIVATE | >><br>`Yes` : `true`<br>`No` : `false` | msdyn_isdeliveryaddressprivate |
DELIVERYADDRESSCOUNTRYREGIONID | > | msdyn_deliveryaddresscountryregionid |
DELIVERYADDRESSCOUNTYID | > | msdyn_deliveryaddresscountyid |
DELIVERYADDRESSSTATEID | > | msdyn_deliveryaddressstateid |
DELIVERYADDRESSZIPCODE | > | msdyn_deliveryaddresszipcode |
DELIVERYADDRESSNAME | > | msdyn_deliveryaddressname |
DELIVERYADDRESSTIMEZONE | > | msdyn_deliveryaddresstimezone |
DELIVERYADDRESSPOSTBOX | > | msdyn_deliveryaddresspostbox |
DELIVERYADDRESSSTREETNUMBER | > | msdyn_deliveryaddressstreetnumber |
DELIVERYADDRESSSTREET | > | msdyn_deliveryaddressstreet |
PRODUCTRECEIPTNUMBER | > | msdyn_name |
ATTENTIONINFORMATION | > | msdyn_note |
DELIVERYCITYINKANA | > | msdyn_deliverycityinkana |
DELIVERYSTREETINKANA | > | msdyn_deliverystreetinkana |
FORMATTEDDELIVERYADDRESS | > | msdyn_formatteddeliveryaddress |
DELIVERYADDRESSLOCATIONID | > | msdyn_deliveryaddresslocationid |
DELIVERYADDRESSCITY | > | msdyn_deliveryaddresscity |
DELIVERYADDRESSDESCRIPTION | > | msdyn_deliveryaddressdescription |
DELIVERYADDRESSDISTRICTNAME | > | msdyn_deliveryaddressdistrictname |
DELIVERYBUILDINGCOMPLIMENT | > | msdyn_deliverybuildingcompliment |
DELIVERYADDRESSDUNSNUMBER | > | msdyn_deliveryaddressdunsnumber |

###  <a name="184"></a>Product receipt line (msdyn_purchaseorderreceiptproducts)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
RECORDID | > | msdyn_recordid |
DELIVERYADDRESSCOUNTRYREGIONID | > | msdyn_deliveryaddresscountryregionid |
DELIVERYADDRESSCOUNTYID | > | msdyn_deliveryaddresscountyid |
DELIVERYADDRESSSTATEID | > | msdyn_deliveryaddressstateid |
EXPECTEDDELIVERYDATE | > | msdyn_expecteddeliverydate |
EXTERNALITEMNUMBER | > | msdyn_externalitemnumber |
ITEMBATCHNUMBER | > | msdyn_itembatchnumber |
ITEMSERIALNUMBER | > | msdyn_itemserialnumber |
LINEDESCRIPTION | > | msdyn_linedescription |
ORDEREDPURCHASEQUANTITY | > | msdyn_orderedpurchasequantity |
PROCUREMENTPRODUCTCATEGORYNAME | > | msdyn_procurementproductcategory.msdyn_name |
PROCUREMENTPRODUCTCATEGORYHIERARCHYNAME | > | msdyn_procurementproductcategory.msdyn_hierarchy.msdyn_name |
PRODUCTRECEIPTDATE | > | msdyn_productreceiptdate |
PRODUCTRECEIPTHEADERRECORDID | > | msdyn_purchaseorderreceipt.msdyn_recordid |
PRODUCTRECEIPTNUMBER | > | msdyn_productreceiptnumber |
PURCHASEORDERLINENUMBER | > | msdyn_purchaseorderproduct.msdyn_lineorder |
PURCHASEORDERNUMBER | > | msdyn_purchaseorderproduct.msdyn_purchaseorder.msdyn_name |
PURCHASEORDERNUMBER | > | msdyn_purchaseorder.msdyn_name |
PURCHASEUNITSYMBOL | > | msdyn_purchaseunitsymbol.msdyn_symbol |
RECEIVEDINVENTORYQUANTITY | > | msdyn_receivedinventoryquantity |
RECEIVEDINVENTORYSTATUSID | > | msdyn_receivedinventorystatusid |
RECEIVEDPURCHASEQUANTITY | > | msdyn_quantity |
RECEIVINGSITEID | > | msdyn_receivingsiteid.msdyn_siteid |
RECEIVINGWAREHOUSEID | > | msdyn_associatetowarehouse.msdyn_warehouseidentifier |
RECEIVINGWAREHOUSELOCATIONID | > | msdyn_receivingwarehouselocation.msdyn_warehouselocationid |
RECEIVINGWAREHOUSEID | > | msdyn_receivingwarehouselocation.msdyn_warehouse.msdyn_warehouseidentifier |
REMAININGINVENTORYQUANTITY | > | msdyn_remaininginventoryquantity |
REMAININGPURCHASEQUANTITY | > | msdyn_remainingpurchasequantity |
PRODUCTNUMBER | > | msdyn_product.msdyn_productnumber |

###  <a name="176"></a>Product specific unit conversions (msdyn_productspecificunitofmeasureconversions)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DENOMINATOR | = | msdyn_denominator |
NUMERATOR | = | msdyn_numerator |
FACTOR | = | msdyn_factor |
FROMUNITSYMBOL | = | msdyn_fromunit.msdyn_symbol |
TOUNITSYMBOL | = | msdyn_tounit.msdyn_symbol |
PRODUCTNUMBER | = | msdyn_globalproduct.msdyn_productnumber |
INNEROFFSET | = | msdyn_inneroffset |
OUTEROFFSET | = | msdyn_outeroffset |
ROUNDING | ><<br>`nearest` : `192350000`<br>`up` : `192350001`<br>`down` : `192350002` | msdyn_rounding |

###  <a name="180"></a>Prospects (leads)

This template synchronizes data between finance and operations apps and Dataverse.

Source filter: (IsB2BProspect == 1)

Reversed source filter: (msdyn_b2bcommerceprospect eq true)

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PROSPECTNAME | = | fullname |
PROSPECTPARTYNUMBER | = | msdyn_partyid.msdyn_partynumber |
PROSPECTID | = | msdyn_prospectid |
PRIMARYPHONENUMBER | = | telephone1 |
PRIMARYPHONENUMBEREXTENSION | = | msdyn_telephone1extension |
PRIMARYPHONENUMBERDESCRIPTION | = | description |
PRIMARYEMAILADDRESS | = | emailaddress1 |
PRIMARYEMAILADDRESSDESCRIPTION | = | msdyn_emailaddress1description |
PRIMARYURL | = | websiteurl |
PRIMARYURLDESCRIPTION | = | msdyn_websiteurldescription |
ADDRESSCITY | = | address1_city |
ADDRESSCOUNTRYREGIONISOCODE | = | address1_country |
ADDRESSCOUNTYID | = | address1_county |
ADDRESSSTATEID | = | address1_stateorprovince |
ADDRESSSTREET | = | address1_line1 |
ADDRESSZIPCODE | = | address1_postalcode |
ADDRESSPOSTBOX | = | address1_postofficebox |
ADDRESSLOCATIONROLES | << | none | Business
none | >> | address1_addresstypecode | 1
COMPANYNAME | = | companyname |
COMPANYSIZE | = | numberofemployees |
ADDRESSLATITUDE | = | address1_latitude |
ADDRESSLONGITUDE | = | address1_longitude |
CURRENCYCODE | = | transactioncurrencyid.isocurrencycode |
CUSTOMERGROUPID | = | msdyn_customergroupid.msdyn_groupid |
SALESTAXGROUPCODE | = | msdyn_salestaxgroup.msdyn_name |
PRIMARYFAXNUMBER | = | fax |
PRIMARYFAXNUMBERDESCRIPTION | = | msdyn_faxdescription |
PRIMARYFAXNUMBEREXTENSION | = | msdyn_faxextension |
RETAILCHANNELOPERATINGUNITPARTYNUMBER | = | msdyn_retailchannel.msdyn_partynumber |
ISB2BPROSPECT | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_b2bcommerceprospect |
B2BPROSPECTSTATUS | ><<br>`Pending` : `192350000`<br>`Approved` : `192350001`<br>`Rejected` : `192350002` | msdyn_b2bprospectstatus |

###  <a name="232"></a>Purchase order header document attachments (annotations)

This template synchronizes data between finance and operations apps and Dataverse.

Source filter: ((DocumentAttachmentTypeCode == "Note") || (DocumentAttachmentTypeCode == "URL"))

Reversed source filter: objecttypecode eq 'msdyn_purchaseorder'

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DOCUMENTID | = | msdyn_notesid |
NOTES | = | notetext |
ATTACHMENTDESCRIPTION | = | subject |
PURCHASEORDERNUMBER | = | msdyn_relatedentityid |
DOCUMENTATTACHMENTTYPECODE | << | none | Note
none | >> | objecttypecode | msdyn_purchaseorder
ACCESSRESTRICTION | ><<br>`internal` : `0`<br>`external` : `1` | msdyn_restriction |

###  <a name="183"></a>Purchase order headers V2 (msdyn_purchaseorders)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DELIVERYADDRESSNAME | > | msdyn_addressname |
REQUESTEDDELIVERYDATE | = | msdyn_dateexpected |
PURCHASEORDERNUMBER | = | msdyn_name |
PAYMENTTERMSNAME | = | msdyn_paymentterm.msdyn_name |
DEFAULTRECEIVINGWAREHOUSEID | = | msdyn_receivetowarehouse.msdyn_warehouseidentifier |
ACCOUNTINGDATE | = | msdyn_accountingdate |
AREPRICESINCLUDINGSALESTAX | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_arepriceincludingsalestax |
ATTENTIONINFORMATION | > | msdyn_attentioninformation |
CASHDISCOUNTCODE | = | msdyn_cashdiscountcode |
CASHDISCOUNTPERCENTAGE | = | msdyn_cashdiscountpercentage |
CONTACTPERSONID | = | msdyn_contactpersonid.msdyn_contactpersonid |
CURRENCYCODE | = | transactioncurrencyid.isocurrencycode |
DEFAULTRECEIVINGSITEID | = | msdyn_defaultreceivingsiteid.msdyn_siteid |
DELIVERYTERMSID | = | msdyn_deliveryterm.msdyn_termscode |
EMAIL | = | msdyn_email |
ISCHANGEMANAGEMENTACTIVE | >><br>`yes` : `True`<br>`no` : `False` | msdyn_ischangemanagementactive |
ISDELIVEREDDIRECTLY | >><br>`yes` : `True`<br>`no` : `False` | msdyn_isdeliverydirectly |
LANGUAGEID | ><<br>`ar` : `192350000`<br>`ar-ae` : `192350001`<br>`cs` : `192350002`<br>`da` : `192350003`<br>`de` : `192350004`<br>`de-at` : `192350005`<br>`de-ch` : `192350006`<br>`en-au` : `192350007`<br>`en-gb` : `192350009`<br>`en-ie` : `192350010`<br>`en-in` : `192350011`<br>`en-ca` : `192350008`<br>`en-my` : `192350012`<br>`en-nz` : `192350013`<br>`en-sg` : `192350014`<br>`en-us` : `192350015`<br>`en-za` : `192350016`<br>`es` : `192350017`<br>`es-mx` : `192350018`<br>`et` : `192350019`<br>`fi` : `192350020`<br>`fr` : `192350021`<br>`fr-be` : `192350022`<br>`fr-ca` : `192350023`<br>`fr-ch` : `192350024`<br>`hu` : `192350025`<br>`is` : `192350026`<br>`it` : `192350027`<br>`it-ch` : `192350028`<br>`ja` : `192350029`<br>`lt` : `192350030`<br>`lv` : `192350031`<br>`nb-no` : `192350032`<br>`nl` : `192350033`<br>`nl-be` : `192350034`<br>`pl` : `192350035`<br>`pt-br` : `192350036`<br>`ru` : `192350037`<br>`sv` : `192350038`<br>`th` : `192350039`<br>`tr` : `192350040`<br>`zh-hans` : `192350041` | msdyn_language |
ORDERERPERSONNELNUMBER | = | msdyn_ordererpersonnelnumber.cdm_workernumber |
REASONCODE | = | msdyn_reasoncode |
REASONCOMMENT | = | msdyn_reasoncomment |
TOTALDISCOUNTPERCENTAGE | = | msdyn_totaldiscountpercentage |
URL | = | msdyn_url |
VENDORORDERREFERENCE | = | msdyn_vendororderreference |
VENDORPAYMENTMETHODNAME | = | msdyn_vendorpaymentmethod.msdyn_name |
VENDORPAYMENTMETHODSPECIFICATIONNAME | > | msdyn_vendorpaymentmethodspecificationname |
ORDERVENDORACCOUNTNUMBER | = | msdyn_vendor.accountnumber |
DELIVERYMODEID | = | msdyn_shipvia.msdyn_name |
INVOICEVENDORACCOUNTNUMBER | = | msdyn_invoicevendoraccount.accountnumber |
DOCUMENTAPPROVALSTATUS | >><br>`draft` : `192350000`<br>`inReview` : `192350001`<br>`rejected` : `192350002`<br>`approved` : `192350003`<br>`inExternalReview` : `192350004`<br>`finalized` : `192350005`<br>`confirmed` : `192350006` | msdyn_documentapprovalstatus |
PURCHASEORDERSTATUS | >><br>`none` : `192350000`<br>`backorder` : `192350001`<br>`received` : `192350002`<br>`invoiced` : `192350003`<br>`canceled` : `192350004` | msdyn_purchaseorderstatus |
DELIVERYADDRESSCITY | > | msdyn_city |
DELIVERYADDRESSCOUNTRYREGIONISOCODE | > | msdyn_country |
DELIVERYADDRESSSTATEID | > | msdyn_stateorprovince |
DELIVERYADDRESSZIPCODE | > | msdyn_postalcode |
DELIVERYADDRESSSTREET | > | msdyn_address1 |
INVOICEADDRESSSTREETNUMBER | > | msdyn_invoiceaddressstreetnumber |
CONFIRMEDDELIVERYDATE | = | msdyn_confirmeddeliverydate |
DELIVERYADDRESSLONGITUDE | > | msdyn_longitude |
DELIVERYADDRESSLATITUDE | > | msdyn_latitude |
DELIVERYADDRESSCOUNTRYREGIONID | > | msdyn_deliveryaddresscountryregionid |
DELIVERYADDRESSCOUNTYID | > | msdyn_deliveryaddresscountyid |
DELIVERYADDRESSDESCRIPTION | > | msdyn_deliveryaddressdescription |
DELIVERYADDRESSDISTRICTNAME | > | msdyn_deliveryaddressdistrictname |
DELIVERYADDRESSDUNSNUMBER | > | msdyn_deliveryaddressdunsnumber |
DELIVERYADDRESSLOCATIONID | > | msdyn_deliveryaddresslocationid |
DELIVERYADDRESSPOSTBOX | > | msdyn_deliveryaddresspostbox |
DELIVERYADDRESSTIMEZONE | > | msdyn_deliveryaddresstimezone |
DELIVERYBUILDINGCOMPLIMENT | > | msdyn_deliverybuildingcompliment |
FORMATTEDDELIVERYADDRESS | > | msdyn_formatteddeliveryaddress |
FORMATTEDINVOICEADDRESS | > | msdyn_formattedinvoiceaddress |
INVOICEADDRESSCITY | > | msdyn_invoiceaddresscity |
INVOICEADDRESSCOUNTRYREGIONID | > | msdyn_invoiceaddresscountryregionid |
INVOICEADDRESSCOUNTY | > | msdyn_invoiceaddresscounty |
INVOICEADDRESSSTATE | > | msdyn_invoiceaddressstate |
INVOICEADDRESSSTREET | > | msdyn_invoiceaddressstreet |
DELIVERYADDRESSSTREETNUMBER | > | msdyn_address2 |
INVOICEADDRESSZIPCODE | > | msdyn_invoiceaddresszipcode |

###  <a name="189"></a>Released products V2 (msdyn_sharedproductdetails)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PRODUCTNUMBER | > | msdyn_globalproduct.msdyn_productnumber |
INTRASTATCHARGEPERCENTAGE | > | msdyn_intrastatchargepercentage |
ITEMNUMBER | > | msdyn_itemnumber |
APPROXIMATESALESTAXPERCENTAGE | > | msdyn_approximatesalestaxpercentage |
BESTBEFOREPERIODDAYS | > | msdyn_bestbeforeperioddays |
CARRYINGCOSTABCCODE | >><br>`none` : `806380000`<br>`a` : `806380001`<br>`b` : `806380002`<br>`c` : `806380003` | msdyn_carryingcostabccode |
CONSTANTSCRAPQUANTITY | > | msdyn_constantscrapquantity |
COSTCHARGESQUANTITY | > | msdyn_costchargesquantity |
DEFAULTRECEIVINGQUANTITY | > | msdyn_defaultreceivingquantity |
FIXEDPURCHASEPRICECHARGES | > | msdyn_fixedpurchasepricecharges |
FIXEDSALESPRICECHARGES | > | msdyn_fixedsalespricecharges |
GROSSDEPTH | > | msdyn_grossdepth |
GROSSPRODUCTHEIGHT | > | msdyn_grossproductheight |
GROSSPRODUCTWIDTH | > | msdyn_grossproductwidth |
INVENTORYUNITSYMBOL | > | msdyn_inventoryunitsymbol.msdyn_symbol |
ISDISCOUNTPOSREGISTRATIONPROHIBITED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isdiscountposregistrationprohibited |
ISEXEMPTFROMAUTOMATICNOTIFICATIONANDCANCELLATION | >><br>`no` : `False`<br>`yes` : `True` | msdyn_exemptautomaticnotificationcancel |
ISINSTALLMENTELIGIBLE | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isinstallmenteligible |
ISINTERCOMPANYPURCHASEUSAGEBLOCKED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isintercompanypurchaseusageblocked |
ISINTERCOMPANYSALESUSAGEBLOCKED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isintercompanysalesusageblocked |
ISMANUALDISCOUNTPOSREGISTRATIONPROHIBITED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_ismanualdiscposregistrationprohibited |
ISPHANTOM | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isphantom |
ISPOSREGISTRATIONBLOCKED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isposregistrationblocked |
ISPOSREGISTRATIONQUANTITYNEGATIVE | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isposregistrationquantitynegative |
ISPURCHASEPRICEAUTOMATICALLYUPDATED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_ispurchasepriceautomaticallyupdated |
ISPURCHASEPRICEINCLUDINGCHARGES | >><br>`no` : `False`<br>`yes` : `True` | msdyn_ispurchasepriceincludingcharges |
ISSALESWITHHOLDINGTAXCALCULATED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_issaleswithholdingtaxcalculated |
ISRESTRICTEDFORCOUPONS | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isrestrictedforcoupons |
ISSALESPRICEADJUSTMENTALLOWED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_issalespriceadjustmentallowed |
ISSALESPRICEINCLUDINGCHARGES | >><br>`no` : `False`<br>`yes` : `True` | msdyn_issalespriceincludingcharges |
ISSCALEPRODUCT | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isscaleproduct |
ISSHIPALONEENABLED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isshipaloneenabled |
ISUNITCOSTPRODUCTVARIANTSPECIFIC | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isunitcostproductvariantspecific |
ISVARIANTSHELFLABELSPRINTINGENABLED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isvariantshelflabelsprintingenabled |
ISZEROPRICEPOSREGISTRATIONALLOWED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_iszeropriceposregistrationallowed |
KEYINPRICEREQUIREMENTSATPOSREGISTER | >><br>`notMandatory` : `806380000`<br>`newPrice` : `806380001`<br>`higherEqual` : `806380002`<br>`lowerEqual` : `806380003`<br>`noPrice` : `806380004` | msdyn_keyinpricerequirementsatposregister |
KEYINQUANTITYREQUIREMENTSATPOSREGISTER | >><br>`notMandatory` : `806380000`<br>`keyIn` : `806380001`<br>`notKeyIn` : `806380002` | msdyn_keyinquantityrequirementsatposregister |
MARGINABCCODE | >><br>`none` : `806380000`<br>`a` : `806380001`<br>`b` : `806380002`<br>`c` : `806380003` | msdyn_marginabccode |
MAXIMUMPICKQUANTITY | > | msdyn_maximumpickquantity |
MUSTKEYINCOMMENTATPOSREGISTER | >><br>`no` : `False`<br>`yes` : `True` | msdyn_mustkeyincommentatposregister |
NECESSARYPRODUCTIONWORKINGTIMESCHEDULINGPROPERTYID | > | msdyn_necessaryproductionworkingtimeschedulingp |
NETPRODUCTWEIGHT | > | msdyn_netproductweight |
PACKINGDUTYQUANTITY | > | msdyn_packingdutyquantity |
POSREGISTRATIONACTIVATIONDATE | > | msdyn_posregistrationactivationdate |
POSREGISTRATIONBLOCKEDDATE | > | msdyn_posregistrationblockeddate |
POSREGISTRATIONPLANNEDBLOCKEDDATE | > | msdyn_posregistrationplannedblockeddate |
POTENCYBASEATTIBUTETARGETVALUE | > | msdyn_potencybaseattibutetargetvalue |
POTENCYBASEATTRIBUTEVALUEENTRYEVENT | >><br>`purchProdReceipt` : `806380000`<br>`quality` : `806380001` | msdyn_potencybaseattributevalueentryevent |
PRODUCTTYPE | >><br>`item` : `806380001`<br>`service` : `806380002` | msdyn_producttype |
PRODUCTIONCONSUMPTIONDENSITYCONVERSIONFACTOR | > | msdyn_productionconsumptiondensityconversion |
PRODUCTIONCONSUMPTIONDEPTHCONVERSIONFACTOR | > | msdyn_productionconsumptiondepthconversion |
PRODUCTIONCONSUMPTIONHEIGHTCONVERSIONFACTOR | > | msdyn_productionconsumptionheightconversion |
PRODUCTIONCONSUMPTIONWIDTHCONVERSIONFACTOR | > | msdyn_productionconsumptionwidthconversion |
PRODUCTVOLUME | > | msdyn_productvolume |
PURCHASECHARGESQUANTITY | > | msdyn_purchasechargesquantity |
PURCHASEOVERDELIVERYPERCENTAGE | > | msdyn_purchaseoverdeliverypercentage |
PURCHASEPRICE | > | msdyn_purchaseprice |
PURCHASEPRICEDATE | > | msdyn_purchasepricedate |
PURCHASEPRICINGPRECISION | > | msdyn_purchasepricingprecision |
PURCHASEUNDERDELIVERYPERCENTAGE | > | msdyn_purchaseunderdeliverypercentage |
RAWMATERIALPICKINGPRINCIPLE | >><br>`staging` : `806380000`<br>`orderPicking` : `806380001` | msdyn_rawmaterialpickingprinciple |
SALESCHARGESQUANTITY | > | msdyn_saleschargesquantity |
SALESOVERDELIVERYPERCENTAGE | > | msdyn_salesoverdeliverypercentage |
SALESPRICE | > | msdyn_salesprice |
SALESPRICECALCULATIONCHARGESPERCENTAGE | > | msdyn_salespricecalculationchargespercentage |
SALESPRICECALCULATIONCONTRIBUTIONRATIO | > | msdyn_salespricecalculationcontributionratio |
SALESPRICECALCULATIONMODEL | >><br>`none` : `806380000`<br>`contributionratio` : `806380001`<br>`percentMarkup` : `806380002` | msdyn_salespricecalculationmodel |
SALESPRICEDATE | > | msdyn_salespricedate |
SALESPRICINGPRECISION | > | msdyn_salespricingprecision |
SALESUNDERDELIVERYPERCENTAGE | > | msdyn_salesunderdeliverypercentage |
SALESUNITSYMBOL | > | msdyn_salesunitsymbol.msdyn_symbol |
SCALEINDICATOR | >><br>`relevant` : `806380000`<br>`notRelevant` : `806380001` | msdyn_scaleindicator |
SELLSTARTDATE | > | msdyn_sellstartdate |
SHELFADVICEPERIODDAYS | > | msdyn_shelfadviceperioddays |
SHELFLIFEPERIODDAYS | > | msdyn_shelflifeperioddays |
SHIPSTARTDATE | > | msdyn_shipstartdate |
TAREPRODUCTWEIGHT | > | msdyn_tareproductweight |
TRANSFERORDEROVERDELIVERYPERCENTAGE | > | msdyn_transferorderoverdeliverypercentage |
TRANSFERORDERUNDERDELIVERYPERCENTAGE | > | msdyn_transferorderunderdeliverypercentage |
UNITCOST | > | msdyn_unitcost |
UNITCOSTDATE | > | msdyn_unitcostdate |
UNITCOSTQUANTITY | > | msdyn_unitcostquantity |
VARIABLESCRAPPERCENTAGE | > | msdyn_variablescrappercentage |
WAREHOUSEMOBILEDEVICEDESCRIPTIONLINE1 | > | msdyn_warehousemobiledevicedescriptionline1 |
WAREHOUSEMOBILEDEVICEDESCRIPTIONLINE2 | > | msdyn_warehousemobiledevicedescriptionline2 |
WILLINVENTORYISSUEAUTOMATICALLYREPORTASFINISHED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_willinventoryissueautoreportasfinished |
WILLINVENTORYRECEIPTIGNOREFLUSHINGPRINCIPLE | >><br>`no` : `False`<br>`yes` : `True` | msdyn_willinventoryreceiptignoreflushing |
WILLPICKINGWORKBENCHAPPLYBOXINGLOGIC | >><br>`no` : `False`<br>`yes` : `True` | msdyn_willpickingworkbenchapplyboxinglogic |
WILLTOTALPURCHASEDISCOUNTCALCULATIONINCLUDEPRODUCT | >><br>`no` : `False`<br>`yes` : `True` | msdyn_willtotalpurchdiscountcalcincludeproduct |
WILLTOTALSALESDISCOUNTCALCULATIONINCLUDEPRODUCT | >><br>`no` : `False`<br>`yes` : `True` | msdyn_willtotalsalesdiscountcalcincludeproduct |
WILLWORKCENTERPICKINGALLOWNEGATIVEINVENTORY | >><br>`no` : `False`<br>`yes` : `True` | msdyn_willworkcenterpickingallownegativeinvent |
YIELDPERCENTAGE | > | msdyn_yieldpercentage |
ISUNITCOSTAUTOMATICALLYUPDATED | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isunitcostautomaticallyupdated |
PURCHASEUNITSYMBOL | > | msdyn_purchaseunitsymbol.msdyn_symbol |
PURCHASEPRICEQUANTITY | > | msdyn_purchasepricequantity |
ISUNITCOSTINCLUDINGCHARGES | >><br>`no` : `False`<br>`yes` : `True` | msdyn_isunitcostincludingcharges |
FIXEDCOSTCHARGES | > | msdyn_fixedcostcharges |
MINIMUMCATCHWEIGHTQUANTITY | > | msdyn_minimumcatchweightquantity |
MAXIMUMCATCHWEIGHTQUANTITY | > | msdyn_maximumcatchweightquantity |
ALTERNATIVEITEMNUMBER | > | msdyn_alternativeitemnumber.msdyn_itemnumber |
BOMUNITSYMBOL | > | msdyn_bomunitsymbol.msdyn_symbol |
CATCHWEIGHTUNITSYMBOL | > | msdyn_catchweightunitsymbol.msdyn_symbol |
COMPARISONPRICEBASEUNITSYMBOL | > | msdyn_comparisonpricebaseunitsymbol.msdyn_symbol |
PRIMARYVENDORACCOUNTNUMBER | > | msdyn_vendorid.msdyn_vendoraccountnumber |
ISCATCHWEIGHTPRODUCT | >><br>`no` : `False`<br>`yes` : `True` | msdyn_iscatchweight |
PRODUCTDIMENSIONGROUPNAME | > | msdyn_productdimensiongroupid.msdyn_groupname |
STORAGEDIMENSIONGROUPNAME | > | msdyn_storagedimensiongroup.msdyn_groupname |
TRACKINGDIMENSIONGROUPNAME | > | msdyn_trackingdimensiongroup.msdyn_groupname |

###  <a name="118"></a>Sales invoice headers V2 (invoices)

This template synchronizes data between finance and operations apps and Dataverse.

Source filter: (SalesOrderNumber != "")

Reversed source filter: msdyn_ordertype eq 192350000

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
none | >> | ispricelocked | False
none | >> | statuscode | 4
CONTACTPERSONID | > | msdyn_associatedcontact.msdyn_contactforpartynumber |
CURRENCYCODE | > | transactioncurrencyid.isocurrencycode |
CUSTOMERSORDERREFERENCE | > | description |
INVOICEADDRESSCITY | > | billto_city |
INVOICEADDRESSCOUNTRYREGIONISOCODE | > | billto_country |
INVOICEADDRESSSTATE | > | billto_stateorprovince |
INVOICEADDRESSSTREET | > | billto_line1 |
INVOICEADDRESSSTREETNUMBER | > | billto_line2 |
INVOICEADDRESSZIPCODE | > | billto_postalcode |
INVOICECUSTOMERACCOUNTNUMBER | > | customerid.Account(accountnumber).Contact(msdyn_contactpersonid) |
INVOICEDATE | > | msdyn_invoicedate |
INVOICENUMBER | > | msdyn_invoicenumber |
LEDGERVOUCHER | > | msdyn_ledgervoucher |
PAYMENTTERMSNAME | > | msdyn_paymentterms.msdyn_name |
SALESORDERNUMBER | > | salesorderid.msdyn_salesordernumber |
TOTALCHARGEAMOUNT | > | freightamount |
TOTALDISCOUNTAMOUNT | > | msdyn_totaldiscountamount |
TOTALDISCOUNTCUSTOMERGROUPCODE | > | discountamount |
TOTALINVOICEAMOUNT | > | msdyn_totalamount |
TOTALTAXAMOUNT | > | msdyn_totaltax |
none | >> | msdyn_ordertype | 192350000

###  <a name="117"></a>Sales invoice lines V2 (invoicedetails)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
CONFIRMEDSHIPPINGDATE | > | msdyn_confirmedshippingdate |
CURRENCYCODE | > | transactioncurrencyid.isocurrencycode |
INVENTORYSITEID | > | msdyn_inventorysite.msdyn_siteid |
INVENTORYWAREHOUSEID | > | msdyn_inventorywarehouse.msdyn_warehouseidentifier |
INVOICEDATE | > | invoiceid.msdyn_invoicedate |
INVOICEDQUANTITY | > | quantity |
INVOICENUMBER | > | invoiceid.msdyn_invoicenumber |
LEDGERVOUCHER | > | invoiceid.msdyn_ledgervoucher |
LINEAMOUNT | > | extendedamount |
LINECREATIONSEQUENCENUMBER | > | sequencenumber |
LINETOTALCHARGEAMOUNT | > | msdyn_totalchargeamount |
LINETOTALDISCOUNTAMOUNT | > | manualdiscountamount |
LINETOTALTAXAMOUNT | > | tax |
PRODUCTNAME | > | description |
PRODUCTNUMBER | > | productid.msdyn_productnumber |
SALESPRICE | > | priceperunit |
SALESPRODUCTCATEGORYHIERARCHYNAME | > | msdyn_salesproductcategory.msdyn_hierarchy.msdyn_name |
SALESPRODUCTCATEGORYNAME | > | msdyn_salesproductcategory.msdyn_name |
SALESUNITSYMBOL | > | uomid.msdyn_symbol |
none | >> | producttypecode | 1
none | >> | propertyconfigurationstatus | 2
none | >> | ispriceoverridden | True

###  <a name="229"></a>Sales order header document attachments (annotations)

This template synchronizes data between finance and operations apps and Dataverse.

Source filter: ((DocumentAttachmentTypeCode == "Note") || (DocumentAttachmentTypeCode == "URL"))

Reversed source filter: objecttypecode eq 'salesorder'

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DOCUMENTID | = | msdyn_notesid |
NOTES | = | notetext |
ATTACHMENTDESCRIPTION | = | subject |
SALESORDERNUMBER | = | msdyn_relatedentityid |
DOCUMENTATTACHMENTTYPECODE | << | none | Note
none | >> | objecttypecode | salesorder
ACCESSRESTRICTION | ><<br>`internal` : `0`<br>`external` : `1` | msdyn_restriction |

###  <a name="186"></a>Sales order origin codes (msdyn_salesorderorigins)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
ORIGINCODE | = | msdyn_origincode |
ORIGINDESCRIPTION | = | msdyn_origindescription |

###  <a name="193"></a>Sales tax authorities (msdyn_taxauthorities)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
TAXAUTHORITYCODE | = | msdyn_taxauthoritycode |
TAXAUTHORITYIDENTIFICATION | = | msdyn_taxauthorityidentificator |
DESCRIPTION | = | msdyn_description |
REPORTLAYOUT | ><<br>`default` : `192350000`<br>`norway` : `192350001`<br>`unitedKingdom` : `192350002`<br>`sweden` : `192350003`<br>`germany` : `192350004`<br>`austria` : `192350005`<br>`netherlands` : `192350006`<br>`usa` : `192350007`<br>`italy` : `192350008`<br>`belgium` : `192350009`<br>`singapore` : `192350010`<br>`japan` : `192350011`<br>`finland` : `192350012`<br>`estonia` : `192350013`<br>`uae` : `192350014` | msdyn_taxreportlayout |
ROUNDOFFTYPE | ><<br>`ordinary` : `192350000`<br>`roundDown` : `192350001`<br>`roundUp` : `192350002`<br>`advantage` : `192350003` | msdyn_roundofftype |
ROUNDOFF | = | msdyn_roundoff |
EMAIL | = | msdyn_email |
PHONE | = | msdyn_phone |
URL | = | msdyn_url |

###  <a name="194"></a>Sales tax exempt code entity CDS (msdyn_taxexemptcodes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
NAME | = | msdyn_name |
DESCRIPTION | = | msdyn_description |

###  <a name="195"></a>Sales tax groups (msdyn_taxgroups)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
TAXGROUPCODE | = | msdyn_name |
DESCRIPTION | = | msdyn_description |

###  <a name="197"></a>Sales tax ledger posting groups V2 (msdyn_taxpostinggroups)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
TAXPOSTINGGROUPCODE | = | msdyn_name |
DESCRIPTION | = | msdyn_description |

###  <a name="228"></a>Salutations (msdyn_salutations)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
SALUTATIONPHRASE | = | msdyn_salutationphrase |

###  <a name="156"></a>Sites (msdyn_operationalsites)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DEFAULTFINANCIALDIMENSIONVALUE | = | msdyn_defaultfinancialdimensionvalue |
DEFAULTINVENTORYSTATUSID | = | msdyn_defaultinventorystatusid |
ISRECEIVINGWAREHOUSEOVERRIDEALLOWED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isreceivingwarehouseoverrideallowed |
SITEID | = | msdyn_siteid |
SITENAME | = | msdyn_sitename |
TAXBRANCHCODE | = | msdyn_taxbranchcode |
FISCALESTABLISHMENTID | = | msdyn_fiscalestablishmentid |
ISPRIMARYADDRESSASSIGNED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isprimaryaddressassigned |
PRIMARYADDRESSCITY | = | msdyn_primaryaddresscity |
PRIMARYADDRESSCOUNTRYREGIONID | = | msdyn_primaryaddresscountryregionid |
PRIMARYADDRESSCOUNTYID | = | msdyn_primaryaddresscountyid |
PRIMARYADDRESSDISTRICTNAME | = | msdyn_primaryaddressdistrictname |
PRIMARYADDRESSLATITUDE | = | msdyn_primaryaddresslatitude |
PRIMARYADDRESSLOCATIONROLES | = | msdyn_primaryaddresslocationrole |
PRIMARYADDRESSLOCATIONSALESTAXGROUPCODE | = | msdyn_primaryaddresslocationsalestaxgroupcode |
PRIMARYADDRESSLONGITUDE | = | msdyn_primaryaddresslongitude |
PRIMARYADDRESSSTATEID | = | msdyn_primaryaddressstateid |
PRIMARYADDRESSSTREET | = | msdyn_primaryaddressstreet |
PRIMARYADDRESSZIPCODE | = | msdyn_primaryaddresszipcode |
PRIMARYADDRESSBUILDINGCOMPLIMENT | = | msdyn_primaryaddressbuildingcompliment |
PRIMARYADDRESSCITYINKANA | = | msdyn_primaryaddresscityinkana |
PRIMARYADDRESSSTREETINKANA | = | msdyn_primaryaddressstreetinkana |
PRIMARYADDRESSDESCRIPTION | = | msdyn_primaryaddressdescription |
FORMATTEDPRIMARYADDRESS | = | msdyn_formattedprimaryaddress |
WILLMASTERPLANNEDINTRASITEMOVEMENTSUSETRANSFERJOURNALS | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_masterplannedusestransferjournal |
PRIMARYADDRESSPOSTBOX | = | msdyn_primaryaddresspostbox |
PRIMARYADDRESSSTREETNUMBER | = | msdyn_primaryaddressstreetnumber |

###  <a name="174"></a>Sizes (msdyn_productsizes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
SIZEID | > | msdyn_productsize |

###  <a name="177"></a>Storage dimension groups (msdyn_productstoragedimensiongroups)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
WILLSALESPRICESEARCHUSEWAREHOUSE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willsalespricesearchusewarehouse |
WILLSALESPRICESEARCHUSESITE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willsalespricesearchusesite |
WILLSALESPRICESEARCHUSEINVENTORYSTATUS | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willsalespricesearchuseinventorystatus |
WILLPURCHASEPRICESEARCHUSEWAREHOUSE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willpurchasepricesearchusewarehouse |
WILLPURCHASEPRICESEARCHUSESITE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willpurchasepricesearchusesite |
WILLPURCHASEPRICESEARCHUSEINVENTORYSTATUS | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willpurchpricesearchuseinventstatus |
WILLCOVERAGEPLANNINGUSEWAREHOUSE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willcoverageplanusewarehouse |
WILLCOVERAGEPLANNINGUSELOCATION | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_iscoverageplanenabledforlocation |
WILLCOVERAGEPLANNINGUSEINVENTORYSTATUS | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_willcoverageplanuseinventorystatus |
AREADVANCEDWAREHOUSEMANAGEMENTPROCESSESENABLED | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_areadvancedwmprocessesenabled |
ISWAREHOUSEPRIMARYSTORAGEDIMENSION | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_iswarehouseprimarystoragedimension |
ISWAREHOUSEMANDATORY | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_iswarehousemandatory |
ISPHYSICALINVENTORYENABLEDFORWAREHOUSE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isphysicalinventoryenabledforwarehouse |
ISPHYSICALINVENTORYENABLEDFORLOCATION | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isphysicalinventoryenabledforlocation |
ISLOCATIONACTIVE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_islocationactive |
ISFINANCIALINVENTORYENABLEDFORWAREHOUSE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isfinancialinventoryenabledforwarehouse |
GROUPNAME | = | msdyn_groupname |
GROUPDESCRIPTION | = | msdyn_groupdescription |
ISBLANKRECEIPTALLOWEDFORLOCATION | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isblankreceiptallowedforlocation |
ISBLANKISSUEALLOWEDFORLOCATION | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isblankissueallowedforlocation |

###  <a name="178"></a>Styles (msdyn_productstyles)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
STYLEID | > | msdyn_productstyle |

###  <a name="198"></a>Terms of delivery (msdyn_termsofdeliveries)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
TERMSCODE | = | msdyn_termscode |
INTRASTATCODE | = | msdyn_intrastatcode |
SALESTAXLOCATIONROLE | ><<br>`none` : `192350000`<br>`invoice` : `192350001`<br>`delivery` : `192350002`<br>`swift` : `192350003`<br>`payment` : `192350004`<br>`service` : `192350005`<br>`home` : `192350006`<br>`other` : `192350007`<br>`business` : `192350008`<br>`remitTo` : `192350009`<br>`statement` : `192350010`<br>`fixedAsset` : `192350011`<br>`oneTime` : `192350012`<br>`recruit` : `192350013`<br>`sms` : `192350014`<br>`lading_W` : `192350015`<br>`unlading_W` : `192350016`<br>`headCompany_IT` : `192350017`<br>`stableOrganization_IT` : `192350018` | msdyn_salestaxlocationrole |
TERMSDESCRIPTION | = | msdyn_termsdescription |
FREIGHTCHARGETERMS | ><<br>`prepaid` : `192350000`<br>`collect` : `192350001`<br>`thirdParty` : `192350002`<br>`nofreight` : `192350003` | msdyn_freightchargeterms |
DORETAILSALESORDERSGETTRANSPORTATIONCHARGESADDED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_doretailsogettransportationchargesadded |
ISCASHONDELIVERY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_iscashondelivery |
WILLSHIPMENTCONFIRMATIONTRANSFERCHARGES | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_willshipmentconfirmationtransfercharges |

###  <a name="161"></a>Terms of payment (msdyn_paymentterms)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DESCRIPTION | = | msdyn_description |
NAME | = | msdyn_name |
NUMBEROFMONTHS | = | msdyn_numberofmonth |
CUTOFFDAYOFMONTH | = | msdyn_cutoffdayofmonth |
ISCASHPAYMENT | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_iscashpayment |
NUMBEROFDAYS | = | msdyn_days |
ISCERTIFIEDCOMPANYCHECK | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_iscertifiedcompanycheck |
ISDEFAULTPAYMENTTERM | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isdefaultpaymentterm |
CREDITCARDPAYMENTTYPE | ><<br>`na` : `806380998`<br>`creditCard` : `806380999` | msdyn_creditcardpaymenttype |
CREDITCARDCREDITCHECKTYPE | ><<br>`normal` : `806380000`<br>`byPass` : `806380001` | msdyn_creditcardcreditchecktype |
PAYMENTDAYNAME | = | msdyn_paymentdayname.msdyn_name |
PAYMENTMETHODTYPE | ><<br>`net` : `806380991`<br>`currentMth` : `806380992`<br>`currentQuart` : `806380993`<br>`currentYear` : `806380994`<br>`currentWeek` : `806380995`<br>`cod` : `806380996`<br>`cutOffDate` : `806380997` | msdyn_paymentmethodtype |
PAYMENTSCHEDULENAME | = | msdyn_paymentschedulename.msdyn_name |

###  <a name="179"></a>Tracking dimension groups (msdyn_producttrackingdimensiongroups)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
SERIALNUMBERCAPTURINGOPERATION | ><<br>`none` : `806380000`<br>`picking` : `806380001`<br>`packing` : `806380002` | msdyn_serialnumbercapturingoperation |
GROUPNAME | = | msdyn_groupname |
GROUPDESCRIPTION | = | msdyn_groupdescription |
ISSERIALNUMBERENABLEDFORPRODUCTIONCONSUMPTIONPROCESS | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_issnenabledforpcprocess |
ISSERIALNUMBERCONTROLENABLED | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isserialnumbercontrolenabled |
ISSERIALNUMBERENABLEDFORSALESPROCESS | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isserialnumberenabledforsalesprocess |
ISSERIALNUMBERACTIVE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isserialnumberactive |
ISSALESPRICEBYSERIALNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_issalespricebyserialnumber |
ISSALESPRICEBYBATCHNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_issalespricebybatchnumber |
ISPURCHASEPRICEBYSERIALNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_ispurchasepricebyserialnumber |
ISPURCHASEPRICEBYBATCHNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_ispurchasepricebybatchnumber |
ISPRIMARYSTOCKINGENABLEDFORSERIALNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isprimarystockingenabledforsn |
ISPRIMARYSTOCKINGENABLEDFORBATCHNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isprimarystockingenabledforbn |
ISPHYSICALINVENTORYENABLEDFORSERIALNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isphysicalinventoryenabledforsn |
ISPHYSICALINVENTORYENABLEDFORBATCHNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isphysicalinventoryenabledforbn |
ISFINANCIALINVENTORYENABLEDFORSERIALNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isfinancialinventoryenabledforsn |
ISFINANCIALINVENTORYENABLEDFORBATCHNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isfinancialinventoryenabledforbn |
ISCOVERAGEPLANENABLEDFORSERIALNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_iscoverageplanenabledforserialnumber |
ISCOVERAGEPLANENABLEDFORBATCHNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_iscoverageplanenabledforbatchnumber |
ISBLANKRECEIPTALLOWEDFORSERIALNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isblankreceiptallowedforserialnumber |
ISBLANKRECEIPTALLOWEDFORBATCHNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isblankreceiptallowedforbatchnumber |
ISBLANKISSUEALLOWEDFORSERIALNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isblankissueallowedforserialnumber |
ISBLANKISSUEALLOWEDFORBATCHNUMBER | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isblankissueallowedforbatchnumber |
ISBATCHNUMBERACTIVE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isbatchnumberactive |
ISINVENTORYOWNERACTIVE | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_isinventoryowneractive |

###  <a name="199"></a>Unit conversions (msdyn_unitofmeasureconversions)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DENOMINATOR | = | msdyn_denominator |
NUMERATOR | = | msdyn_numerator |
FACTOR | = | msdyn_factor |
INNEROFFSET | = | msdyn_inneroffset |
OUTEROFFSET | = | msdyn_outeroffset |
ROUNDING | ><<br>`nearest` : `192350000`<br>`up` : `192350001`<br>`down` : `192350002` | msdyn_rounding |
TOUNITSYMBOL | = | msdyn_tounit.msdyn_symbol |
FROMUNITSYMBOL | = | msdyn_fromunit.msdyn_symbol |

###  <a name="219"></a>Units (uoms)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
UNITSYMBOL | > | msdyn_symbol |
UNITCLASS | > | msdyn_externalunitclassname |
DECIMALPRECISION | > | msdyn_decimalprecision |
ISBASEUNIT | >><br>`no` : `false`<br>`yes` : `true` | msdyn_isbaseunit |
ISSYSTEMUNIT | >><br>`no` : `false`<br>`yes` : `true` | msdyn_issystemunit |
SYSTEMOFUNITS | >><br>`none` : `192350000`<br>`metric` : `192350001`<br>`us` : `192350002` | msdyn_systemofunits |
UNITSYMBOL | > | name |
UNITDESCRIPTION | > | msdyn_description |

###  <a name="231"></a>Vendor document attachments (annotations)

This template synchronizes data between finance and operations apps and Dataverse.

Source filter: ((DocumentAttachmentTypeCode == "Note") || (DocumentAttachmentTypeCode == "URL"))

Reversed source filter: (objecttypecode eq 'msdyn_vendor'  and msdyn_relatedentityid2 ne null) or (objecttypecode eq 'account' and msdyn_relatedentityid2 ne null)  or (objecttypecode eq 'contact' and msdyn_relatedentityid2 ne null)

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DOCUMENTID | = | msdyn_notesid |
NOTES | = | notetext |
ATTACHMENTDESCRIPTION | = | subject |
VENDORACCOUNTNUMBER | = | msdyn_relatedentityid2 |
DOCUMENTATTACHMENTTYPECODE | << | none | Note
none | >> | objecttypecode | msdyn_vendor
ACCESSRESTRICTION | ><<br>`internal` : `0`<br>`external` : `1` | msdyn_restriction |

###  <a name="200"></a>Vendor groups (msdyn_vendorgroups)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DEFAULTPAYMENTTERMNAME | = | msdyn_paymentterms.msdyn_name |
DESCRIPTION | = | msdyn_description |
VENDORGROUPID | = | msdyn_vendorgroup |
CLEARINGPERIODPAYMENTTERMNAME | = | msdyn_clearingperiodpaymentpermname.msdyn_name |

###  <a name="201"></a>Vendor payment method (msdyn_vendorpaymentmethods)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
NAME | = | msdyn_name |
DESCRIPTION | = | msdyn_description |
SUMBYPERIOD | ><<br>`transDate` : `806380001`<br>`invoice` : `806380000`<br>`week` : `806380002`<br>`total` : `806380003` | msdyn_sumbyperiod |
DISCOUNTGRACEPERIODDAYS | = | msdyn_discountgraceperioddays |
PAYMENTSTATUS | ><<br>`none` : `806380000`<br>`sent` : `806380001`<br>`recieved` : `806380002`<br>`approved` : `806380003`<br>`rejected` : `806380004` | msdyn_paymentstatus |
ALLOWPAYMENTCOPIES | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_allowpaymentcopies |
PAYMENTTYPE | ><<br>`blank` : `806380000`<br>`check` : `806380001`<br>`electronicPayment` : `806380002`<br>`promissoryNote` : `806380003` | msdyn_paymenttype |
LASTFILENUMBER | = | msdyn_lastfilenumber |
LASTFILENUMBERTODAY | = | msdyn_lastfilenumbertoday |
ACCOUNTTYPE | ><<br>`ledger` : `806380000`<br>`bank` : `806380005`<br>`cust` : `806380001`<br>`fixedAssets` : `806380004`<br>`vend` : `806380002`<br>`project` : `806380003` | msdyn_accounttype |
BRIDGINGPOSTINGENABLED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_bridgingposting |
ENABLEPOSTDATEDCHECKCLEARINGPOSTING | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_postdatedcheckclearingposting |
PROMISSORYNOTEDRAFTTYPE | ><<br>`noDraft` : `806380000`<br>`noAcceptance` : `806380001`<br>`acceptance` : `806380002`<br>`promissory` : `806380003`<br>`bankAcceptance` : `806380004` | msdyn_promissorynotedrafttype |
DIRECTDEBIT | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_directdebit |

###  <a name="202"></a>Vendors V2 (msdyn_vendors)

This template synchronizes data between finance and operations apps and Dataverse.

Source filter: ((VendorPartyType == "Organization") || (VendorPartyType == "Person"))

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
VENDORACCOUNTNUMBER | = | msdyn_vendoraccountnumber |
VENDORGROUPID | = | msdyn_vendorgroupid.msdyn_vendorgroup |
VENDORPARTYTYPE | ><<br>`person` : `True`<br>`organization` : `False` | msdyn_isperson |
CREDITLIMIT | = | msdyn_vendorcreditlimit |
ISFOREIGNENTITY | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isforeignentity |
ISONETIMEVENDOR | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isonetimevendor |
CREDITRATING | = | msdyn_creditrating |
DUNSNUMBER | = | msdyn_dunsnumber |
ETHNICORIGINID | = | msdyn_ethnicorigin |
OURACCOUNTNUMBER | = | msdyn_ourvendoraccountnumber |
PAYMENTID | = | msdyn_paymentid |
PRIMARYURL | = | msdyn_primarycontacturl |
DEFAULTPAYMENTDAYNAME | = | msdyn_defaultpaymentdayname.msdyn_name |
DEFAULTPAYMENTSCHEDULENAME | = | msdyn_paymentschedule.msdyn_name |
DEFAULTPAYMENTTERMSNAME | = | msdyn_paymentterms.msdyn_name |
HASONLYTAKENBIDS | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_hasonlytakenbids |
ISMINORITYOWNED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isminorityowned |
ISVENDORLOCALLYOWNED | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_isvendorlocallyowned |
ISSERVICEVETERANOWNED | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_isserviceveteranowned |
ISOWNERDISABLED | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_ownerisdisabled |
ISWOMANOWNER | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_womanowner |
ORGANIZATIONEMPLOYEEAMOUNT | = | msdyn_numberofemployees |
VENDORHOLDRELEASEDATE | = | msdyn_vendoronholdreleasedate |
VENDORPARTYNUMBER | = | msdyn_partyid.msdyn_partynumber |
ONHOLDSTATUS | ><<br>`no` : `806380000`<br>`invoice` : `806380001`<br>`all` : `806380002`<br>`payment` : `806380003`<br>`requisition` : `806380004`<br>`never` : `806380005` | msdyn_onholdstatus |
CURRENCYCODE | = | msdyn_currencycode.isocurrencycode |
ISVENDORLOCATEDINHUBZONE | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_isvendorlocatedinhubzone |
DEFAULTVENDORPAYMENTMETHODNAME | = | msdyn_vendorpaymentmethod.msdyn_name |
INVOICEVENDORACCOUNTNUMBER | = | msdyn_invoicevendoraccountnumber.msdyn_vendoraccountnumber |
AREPRICESINCLUDINGSALESTAX | ><<br>`no` : `False`<br>`yes` : `True` | msdyn_priceincludessalestax |
SALESTAXGROUPCODE | = | msdyn_taxgroup.msdyn_name |
PRIMARYCONTACTPERSONID | = | msdyn_primarycontact.msdyn_contactforpartynumber |

###  <a name="112"></a>Veteran status (cdm_veteranstatuses)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
VETERANSTATUSID | = | cdm_name |
DESCRIPTION | = | cdm_description |
ISPROTECTEDVETERAN | ><<br>`no` : `false`<br>`yes` : `true` | cdm_isprotectedveteran |

###  <a name="144"></a>Warehouse locations (msdyn_inventorylocations)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
BINID | = | msdyn_binid |
CHECKDIGITS | = | msdyn_checkdigits |
GENERATECHECKDIGITS | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_generatecheckdigits |
ISSORTORDERCODEMANUAL | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_issortordercodemanual |
ISWAREHOUSELOCATIONIDMANUAL | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_iswarehouselocationidmanual |
LASTCOUNTEDUTCDATETIME | = | msdyn_lastcountedutcdatetime |
PHYSICALDEPTH | = | msdyn_physicaldepth |
PHYSICALHEIGHT | = | msdyn_physicalheight |
PHYSICALHEIGHTABOVEGROUND | = | msdyn_physicalheightaboveground |
PHYSICALMAXIMUMSTORAGEVOLUME | = | msdyn_physicalmaximumstoragevolume |
PHYSICALMAXIMUMSTORAGEWEIGHT | = | msdyn_physicalmaximumstorageweight |
PHYSICALWIDTH | = | msdyn_physicalwidth |
RACKID | = | msdyn_rackid |
SHELFID | = | msdyn_shelfid |
WAREHOUSEID | = | msdyn_warehouse.msdyn_warehouseidentifier |
WAREHOUSELOCATIONID | = | msdyn_warehouselocationid |
WAREHOUSELOCATIONPROFILEID | = | msdyn_warehouselocationprofileid |
WAREHOUSELOCATIONTYPE | ><<br>`buffer` : `192350000`<br>`pick` : `192350001`<br>`inputPort` : `192350002`<br>`outputPort` : `192350003`<br>`inspectionLocation` : `192350004`<br>`kanbanSupermarket` : `192350005` | msdyn_warehouselocationtype |
INPUTWAREHOUSELOCATIONBLOCKINGCAUSEID | = | msdyn_inputwarehouselocationblockingcauseid |
OUTPUTWAREHOUSELOCATIONBLOCKINGCAUSEID | = | msdyn_outputwarehouselocationblockingcauseid |
ISDEFAULTCREDITONLYRETURNWAREHOUSELOCATION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_isdefaultcreditonlyreturnwarehouseloc |
ISDEFAULTISSUEWAREHOUSELOCATION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_isdefaultissuewarehouselocation |
ISDEFAULTKANBANFINISHEDGOODSWAREHOUSELOCATION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_isdefaultkanbanfinishedgoodswarehouseloc |
ISDEFAULTPRODUCTIONFINISHEDGOODSWAREHOUSELOCATION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_isdefaultproductionfinishedgoodswhsloc |
ISDEFAULTPRODUCTIONINPUTWAREHOUSELOCATION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_isdefaultproductioninputwarehouseloc |
ISDEFAULTRECEIPTWAREHOUSELOCATION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_isdefaultreceiptwarehouselocation |
ISDEFAULTRETAILSTORERETURNWAREHOUSELOCATION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_isdefaultretailstorereturnwarehouseloc |
ISDEFAULTRETAILSTOREWAREHOUSELOCATION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_isdefaultretailstorewarehouselocation |
ISDEFAULTSHIPMENTMAINTENANCEWAREHOUSELOCATION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_isdefaultshipmentmaintenancewarehouseloc |
AGINGDATE | > | msdyn_agingdate |
LASTACTIVITYDATETIME | > | msdyn_lastactivitydatetime |
LOCATIONSTATUS | >><br>`undetermined` : `192350000`<br>`empty` : `192350001`<br>`picking` : `192350002`<br>`storage` : `192350003` | msdyn_locationstatus |
ISITEMINLOCATIONMAINTAINED | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_isiteminlocationmaintained |
ISLOCATIONACTIVITYDATETIMEMAINTAINED | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_islocationactivitydatetimemaintained |
ISLOCATIONSTATUSMAINTAINED | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_islocationstatusmaintained |
ISDEFAULTQUALITYMAINTENANCEWAREHOUSELOCATION | ><<br>`yes` : `True`<br>`no` : `False` | msdyn_isdefaultqualitymaintenancewarehouseloc |
WAREHOUSEAISLEID | = | msdyn_warehouseaisle.msdyn_aisleid |
WAREHOUSEID | > | msdyn_warehouseaisle.msdyn_warehouse.msdyn_warehouseidentifier |
WAREHOUSEZONEID | = | msdyn_warehousezone.msdyn_zoneid |
FIRSTADDITIONALWAREHOUSEZONEID | = | msdyn_firstadditionalwarehousezone.msdyn_zoneid |
SECONDADDITIONALWAREHOUSEZONEID | = | msdyn_secondadditionalwarehousezone.msdyn_zoneid |
THIRDADDITIONALWAREHOUSEZONEID | = | msdyn_thirdadditionalwarehousezone.msdyn_zoneid |
ITEMNUMBERINLOCATION | = | msdyn_itemnumberinlocation.msdyn_itemnumber |

###  <a name="205"></a>Warehouse work headers (msdyn_warehouseworkheaders)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
ACTUALPROCESSINGTIMESECONDS | > | msdyn_actualprocessingtimeseconds |
ESTIMATEDPROCESSINGTIMESECONDS | > | msdyn_estimatedprocessingtimeseconds |
ISWAREHOUSEWORKBLOCKED | >><br>`yes` : `True`<br>`no` : `False` | msdyn_iswarehouseworkblocked |
WAREHOUSEID | > | msdyn_warehouse.msdyn_warehouseidentifier |
INVENTORYSITEID | > | msdyn_inventorysite.msdyn_siteid |
ISWAREHOUSEWORKERMANUALLYASSIGNED | >><br>`yes` : `True`<br>`no` : `False` | msdyn_iswarehouseworkermanuallyassigned |
WAREHOUSEWORKCANCELLEDDATETIME | > | msdyn_warehouseworkcancelleddatetime |
WAREHOUSEWORKCLOSEDDATETIME | > | msdyn_warehouseworkcloseddatetime |
WAREHOUSEWORKID | > | msdyn_warehouseworkid |
WAREHOUSEWORKPROCESSINGSTARTDATETIME | > | msdyn_warehouseworkprocessingstartdatetime |
WAREHOUSEWORKPRIORITY | > | msdyn_warehouseworkpriority |
WAREHOUSEWORKSTATUS | >><br>`open` : `192350000`<br>`inprocess` : `192350001`<br>`skipped` : `192350002`<br>`closed` : `192350003`<br>`cancelled` : `192350004`<br>`combined` : `192350005` | msdyn_warehouseworkstatus |
WAREHOUSEWORKORDERTYPE | >><br>`qualityOrder` : `192350021`<br>`none` : `192350000`<br>`purch` : `192350001`<br>`sales` : `192350002`<br>`prodPick` : `192350003`<br>`prodPut` : `192350004`<br>`prodProcessPut` : `192350005`<br>`transferIssue` : `192350006`<br>`transferReceipt` : `192350007`<br>`invent` : `192350008`<br>`workCancel` : `192350009`<br>`cycleCount` : `192350010`<br>`replenishment` : `192350011`<br>`returnOrder` : `192350012`<br>`kanbanPut` : `192350013`<br>`kanbanPick` : `192350014`<br>`cycleCountAccepted` : `192350015`<br>`packedContainerPicking` : `192350016`<br>`sortedInventoryPicking` : `192350017`<br>`crossDocking` : `192350018`<br>`qualityInQualityCheck` : `192350019`<br>`qualityItemSampling` : `192350020` | msdyn_warehouseworkordertype |
CONTAINERID | > | msdyn_containerid |
WAREHOUSEWORKLOCKINGWAREHOUSEMOBILEDEVICEUSERID | > | msdyn_warehouseworklockingmobiledeviceuserid |
TARGETLICENSEPLATENUMBER | > | msdyn_targetlicenseplatenumber |
WAVEID | > | msdyn_waveid |
WAREHOUSEWORKCANCELLINGUSERID | > | msdyn_warehouseworkcancellinguserid |
WAREHOUSEWORKMANUALLYCOMPLETINGUSERID | > | msdyn_warehouseworkmanuallycompletinguserid |
WAREHOUSEWORKPOOLID | > | msdyn_warehouseworkpoolid |

###  <a name="206"></a>Warehouse work lines (msdyn_warehouseworklines)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
ACTUALPROCESSINGTIMESECONDS | > | msdyn_actualprocessingtimeseconds |
ESTIMATEDPROCESSINGTIMESECONDS | > | msdyn_estimatedprocessingtimeseconds |
FEFOITEMBATCHNUMBER | > | msdyn_fefoitembatchnumber |
REMAININGHANDLINGQUANTITY | > | msdyn_remaininghandlingquantity |
HANDLINGQUANTITY | > | msdyn_handlingquantity |
WORKLINENUMBER | > | msdyn_worklinenumber |
ISWORKLINEMANDATORY | >><br>`yes` : `True`<br>`no` : `False` | msdyn_isworklinemandatory |
REMAININGWORKQUANTITY | > | msdyn_remainingworkquantity |
WORKQUANTITY | > | msdyn_workquantity |
ISREPLENISHMENTNEEDED | >><br>`yes` : `True`<br>`no` : `False` | msdyn_isreplenishmentneeded |
SORTORDERCODE | > | msdyn_sortordercode |
WORKQUANTITYUNITSYMBOL | > | msdyn_workquantityunit.msdyn_symbol |
WAREHOUSEWORKCLOSEDDATETIME | > | msdyn_warehouseworkcloseddatetime |
WAREHOUSEWORKID | > | msdyn_warehousework.msdyn_warehouseworkid |
WAREHOUSEWORKPROCESSINGSTARTDATETIME | > | msdyn_warehouseworkprocessingstartdatetime |
WAREHOUSEWORKSTATUS | >><br>`open` : `192350000`<br>`inProcess` : `192350001`<br>`pendingReview` : `192350002`<br>`skipped` : `192350003`<br>`closed` : `192350004`<br>`cancelled` : `192350005`<br>`combined` : `192350006` | msdyn_warehouseworkstatus |
ISWORKEXECUTIONSTOPPED | >><br>`yes` : `True`<br>`no` : `False` | msdyn_isworkexecutionstopped |
WAREHOUSEWORKTYPE | >><br>`none` : `192350000`<br>`pick` : `192350001`<br>`put` : `192350002`<br>`count` : `192350003`<br>`adjustment` : `192350004`<br>`custom` : `192350005`<br>`quarantine` : `192350006`<br>`licensePlateBuild` : `192350007`<br>`print` : `192350008`<br>`statusChange` : `192350009`<br>`packToNestedLicensePlate` : `192350010`<br>`qualityCheck` : `192350011` | msdyn_warehouseworktype |
EXTRAHANDLINGQUANTITY | > | msdyn_extrahandlingquantity |
CAPTUREDWEIGHT | > | msdyn_capturedweight |
WAREHOUSEID | > | msdyn_warehouse.msdyn_warehouseidentifier |
INVENTORYSITEID | > | msdyn_inventorysite.msdyn_siteid |
CONTAINERID | > | msdyn_containerid |
PROCESSINGWAREHOUSEMOBILEDEVICEUSERID | > | msdyn_processingwarehousemobiledeviceuserid |
ITEMBATCHNUMBER | > | msdyn_itembatchnumber |
INVENTORYOWNERID | > | msdyn_inventoryownerid |
ITEMSERIALNUMBER | > | msdyn_itemserialnumber |
INVENTORYSTATUSID | > | msdyn_inventorystatusid |
LICENSEPLATENUMBER | > | msdyn_licenseplatenumber |
ITEMNUMBER | > | msdyn_item.msdyn_itemnumber |
WAREHOUSEZONEID | > | msdyn_warehousezone.msdyn_zoneid |
WAREHOUSELOCATIONID | > | msdyn_warehouselocation.msdyn_warehouselocationid |
WAREHOUSEID | > | msdyn_warehouselocation.msdyn_warehouse.msdyn_warehouseidentifier |
PRODUCTCONFIGURATIONID | > | msdyn_productconfiguration.msdyn_productconfiguration |
PRODUCTCOLORID | > | msdyn_productcolor.msdyn_productcolorname |
PRODUCTSIZEID | > | msdyn_productsize.msdyn_productsize |
PRODUCTSTYLEID | > | msdyn_productstyle.msdyn_productstyle |

###  <a name="207"></a>Warehouse zone groups (msdyn_warehousezonegroups)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
GROUPID | = | msdyn_groupid |
GROUPNAME | = | msdyn_groupname |

###  <a name="208"></a>Warehouse zones (msdyn_warehousezones)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
WAREHOUSEZONEGROUPID | = | msdyn_warehousezonegroup.msdyn_groupid |
ZONEID | = | msdyn_zoneid |
ZONENAME | = | msdyn_zonename |

###  <a name="204"></a>Warehouses (msdyn_warehouses)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
DEFAULTCONTAINERTYPEID | = | msdyn_defaultcontainertypeid |
AREITEMSCOVERAGEPLANNEDMANUALLY | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_areitemscoverageplannedmanually |
ARELABORSTANDARDSALLOWED | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_arelaborstandardsallowed |
PRIMARYADDRESSBUILDINGCOMPLIMENT | = | msdyn_primaryaddressbuildingcompliment |
PRIMARYADDRESSPOSTBOX | = | msdyn_primaryaddresspostbox |
PRIMARYADDRESSSTREETNUMBER | = | msdyn_primaryaddressstreetnumber |
AREWAREHOUSELOCATIONCHECKDIGITSUNIQUE | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_arewarehouselocationcheckdigitsunique |
INVENTORYCOUNTINGREASONCODEPOLICYNAME | = | msdyn_inventorycountingreasoncodepolicyname |
AUTOUPDATESHIPMENTRULE | ><<br>`always` : `false`<br>`onQuantityDecrease` : `true` | msdyn_autoupdateshipmentrule |
WAREHOUSERELEASERESERVATIONREQUIREMENTRULE | ><<br>`notapplicable` : `192350000`<br>`allowpartialreservation` : `192350001`<br>`requirefullreservation` : `192350002` | msdyn_warehousereleasereservationrequirement |
EXTERNALLYLOCATEDWAREHOUSEVENDORACCOUNTNUMBER | = | msdyn_externallylocatedwarehousevendoraccountnu |
INVENTORYSTATUSCHANGERESERVATIONREMOVALLEVEL | ><<br>`none` : `192350000`<br>`reservation` : `192350001`<br>`markingreservation` : `192350002` | msdyn_inventorystatuschangereservationremoval |
WAREHOUSEWORKPROCESSINGPOLICYNAME | = | msdyn_warehouseworkprocessingpolicyname |
ISFALLBACKWAREHOUSE | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_isfallbackwarehouse |
ISFINANCIALNEGATIVERETAILSTOREINVENTORYALLOWED | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_financialnegativestoreinventoryallowed |
ISPALLETMOVEMENTDURINGCYCLECOUNTINGALLOWED | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_palletmovementduringcyclecountingallowed |
ISPHYSICALNEGATIVERETAILSTOREINVENTORYALLOWED | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_physicalnegativestoreinventoryallowed |
ISREFILLEDFROMMAINWAREHOUSE | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_isrefilledfrommainwarehouse |
ISRETAILSTOREWAREHOUSE | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_isretailstorewarehouse |
MAINREFILLINGWAREHOUSEID | = | msdyn_mainrefillingwarehouse.msdyn_warehouseidentifier |
MASTERPLANNINGWORKCALENDARDID | = | msdyn_masterplanningworkcalendarid |
MAXIMUMBATCHPICKINGLISTQUANTITY | = | msdyn_maximumbatchpickinglistquantity |
MAXIMUMPICKINGLISTLINEQUANTITY | = | msdyn_maximumpickinglistlinequantity |
OPERATIONALSITEID | = | msdyn_operationalsite.msdyn_siteid |
QUARANTINEWAREHOUSEID | = | msdyn_quarantinewarehouse.msdyn_warehouseidentifier |
RETAILSTOREQUANTITYALLOCATIONREPLENISMENTRULEWEIGHT | = | msdyn_storeqtyallocationreplenishmentweight |
SHOULDWAREHOUSELOCATIONIDINCLUDEAISLEID | ><<br>`no` : `false`<br>`yes` : `true` | msdyn_shouldwarehouselocationincludeaisleid |
TRANSITWAREHOUSEID | = | msdyn_transitwarehouse.msdyn_warehouseidentifier |
WAREHOUSEID | = | msdyn_warehouseidentifier |
WAREHOUSEID | > | msdyn_name |
WAREHOUSELOCATIONIDBINIDFORMAT | = | msdyn_warehouselocationidbinidformat |
WAREHOUSELOCATIONIDRACKIDFORMAT | = | msdyn_warehouselocationidrackidformat |
WAREHOUSELOCATIONIDSHELFIDFORMAT | = | msdyn_warehouselocationidshelfidformat |
WAREHOUSENAME | = | msdyn_description |
WAREHOUSESPECIFICDEFAULTINVENTORYSTATUSID | = | msdyn_warehousespecificdefaultinventorystatusid |
WAREHOUSETYPE | ><<br>`goodsinroute_ru` : `192350000`<br>`transit` : `192350001`<br>`quarantine` : `192350002`<br>`standard` : `192350003`<br>`itmgit` : `192350004`<br>`itmunder` : `192350005` | msdyn_warehousetype |
ISPRIMARYADDRESSASSIGNED | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_isprimaryaddressassigned |
PRIMARYADDRESSCITY | = | msdyn_primaryaddresscity |
PRIMARYADDRESSCOUNTRYREGIONID | = | msdyn_primaryaddresscountryregionid |
PRIMARYADDRESSCOUNTYID | = | msdyn_primaryaddresscountyid |
PRIMARYADDRESSDISTRICTNAME | = | msdyn_primaryaddressdistrictname |
PRIMARYADDRESSLATITUDE | = | msdyn_primaryaddresslatitude |
PRIMARYADDRESSLONGITUDE | = | msdyn_primaryaddresslongitude |
PRIMARYADDRESSLOCATIONROLES | = | msdyn_primaryaddresslocationroles |
PRIMARYADDRESSLOCATIONSALESTAXGROUPCODE | = | msdyn_primaryaddresslocationsalestaxgroupcode |
PRIMARYADDRESSSTATEID | = | msdyn_primaryaddressstateid |
PRIMARYADDRESSSTREET | = | msdyn_primaryaddressstreet |
PRIMARYADDRESSZIPCODE | = | msdyn_primaryaddresszipcode |
EXTERNALLYLOCATEDWAREHOUSECUSTOMERACCOUNTNUMBER | = | msdyn_externallylocatedwarehousecustomeraccount |
PRIMARYADDRESSCITYINKANA | = | msdyn_primaryaddresscityinkana |
PRIMARYADDRESSSTREETINKANA | = | msdyn_primaryaddressstreetinkana |
PRIMARYADDRESSDESCRIPTION | = | msdyn_primaryaddressdescription |
AREADVANCEDWAREHOUSEMANAGEMENTPROCESSESENABLED | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_useadvancedwarehousemanagementprocesses |
AREPICKINGLISTSDELIVERYMODESPECIFIC | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_arepickinglistsdeliverymodespecific |
AREPICKINGLISTSSHIPMENTSPECIFICONLY | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_arepickinglistshipmentspecificonly |
FORMATTEDPRIMARYADDRESS | = | msdyn_formattedprimaryaddress |
ISBILLOFLADINGPRINTINGBEFORESHIPMENTCONFIRMATIONENABLED | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_printbillofladingbeforeshipconfirmation |
RAWMATERIALPICKINGINVENTORYISSUESTATUS | ><<br>`pick` : `false`<br>`reserve` : `true` | msdyn_rawmaterialpickinginventoryissuestatus |
WILLAUTOMATICLOADRELEASERESERVEINVENTORY | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_willautomaticloadreleaseinventory |
WILLINVENTORYSTATUSCHANGEREMOVEBLOCKING | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_willinventorystatuschangeremoveblocking |
WILLMANUALLOADRELEASERESERVEINVENTORY | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_willmanualloadreleasereserveinventory |
WILLORDERRELEASINGCONSOLIDATESHIPMENTS | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_willorderreleasingconsolidateshipments |
WILLPRODUCTIONBOMSRESERVEWAREHOUSELEVELONLY | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_productionbomsreservewarehouselevel |
WILLSHIPPINGCANCELLATIONDECREMENTLOADQUANITY | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_shippingcanceldecrementloadquantity |
WILLWAREHOUSELOCATIONIDINCLUDEBINIDBYDEFAULT | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_warehouselocationidincludeblindid |
WILLWAREHOUSELOCATIONIDINCLUDERACKIDBYDEFAULT | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_warehouselocationincluderackidbydefault |
WILLWAREHOUSELOCATIONIDINCLUDESHELFIDBYDEFAULT | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_warehouselocationidincludeshelfid |

###  <a name="210"></a>Withholding tax codes (msdyn_withholdingtaxcodes)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
WITHHOLDINGCODE | = | msdyn_name |
WITHHOLDINGTAXNAME | = | msdyn_description |
WITHHOLDINGTAXROUNDOFF | = | msdyn_roundoff |
WITHHOLDINGTAXROUNDOFFTYPE | ><<br>`ordinary` : `192350000`<br>`roundDown` : `192350001`<br>`roundUp` : `192350002` | msdyn_roundofftype |
CURRENCYCODEID | = | msdyn_currency.isocurrencycode |
WITHHOLDINGTAXBASE | ><<br>`pctPerNet` : `192350000`<br>`pctPerGross` : `192350001` | msdyn_taxableamountorigin |

###  <a name="211"></a>Withholding tax groups (msdyn_withholdingtaxgroups)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
WITHHOLDINGTAXGROUPCODE | = | msdyn_name |
DESCRIPTION | = | msdyn_description |

###  <a name="113"></a>Worker (cdm_workers)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
PERSONNELNUMBER | = | cdm_workernumber |
FIRSTNAME | = | cdm_firstname |
MIDDLENAME | = | cdm_middlename |
LASTNAME | = | cdm_lastname |
WORKERTYPE | >><br>`employee` : `754400000`<br>`contractor` : `754400001`<br>`both` : `754400000` | cdm_type |
WORKERSTATUS | >><br>`employed` : `754400000`<br>`pending` : `754400001`<br>`terminated` : `754400001` | cdm_status |
PRIMARYCONTACTEMAIL | = | cdm_primaryemailaddress |
PRIMARYCONTACTPHONE | = | cdm_primarytelephone |
PRIMARYCONTACTFACEBOOK | = | cdm_facebookidentity |
PRIMARYCONTACTTWITTER | = | cdm_twitteridentity |
PRIMARYCONTACTLINKEDIN | = | cdm_linkedinidentity |
PRIMARYCONTACTURL | = | cdm_websiteurl |
GENDER | ><<br>`male` : `754400000`<br>`female` : `754400001`<br>`nonSpecific` : `754400003`<br>`none` : `754400002` | cdm_gender |
BIRTHDATE | = | cdm_birthdate |
NAME | > | cdm_fullname |

###  <a name="301"></a>CDS location roles (msdyn_addressroles)

This template synchronizes data between finance and operations apps and Dataverse.

Finance and operations field | Map type | Customer engagement column | Default value
---|---|---|---
ISCONTACTINFORMATION | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_iselectronicaddressrole |
ISPOSTALADDRESS | ><<br>`yes` : `true`<br>`no` : `false` | msdyn_ispostaladdressrole |
PURPOSE | = | msdyn_name |

