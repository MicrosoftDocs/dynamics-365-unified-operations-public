---
# required metadata

title: Entity dependency chain (synchronization order)
description: This topic specifies the order of synchronization that you must follow to create the initial data.
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 07/25/2019
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
ms.search.validFrom: 2019-07-15

---

# Entity dependency chain (synchronization order)

[!include [banner](../../includes/banner.md)]

[!include [preview-banner](../../includes/preview-banner.md)]

The entities are listed in the order in which they should be enabled. When you enable a map for initial synchronization, dual-write automatically detects other maps that need to be enabled. You can use the **Dual-write** page in the Finance and Operations apps to select or de-select entities during the initial synchronization.

In the latest version of dual-write, you can simply enable some entities, and the dependencies are handled for you.

## Dynamics 365 Supply Chain Management entities

The following entities for Supply Chain Management are listed in the order you should enable them.

| Mapping name on Dual-write page | Supply Chain Management<br>Entity metadata name  | Common Data Service<br>Entity metadata name   | Notes |
|---|---|---|---|
| Units ... uoms                                                                      | UnitOfMeasureEntity                        | uom                                            |  |
| Unit conversions ... msdyn_unitofmeasureconversions                                 | UnitOfMeasureConversionEntity              | msdyn_unitofmeasureconversion                  |  |
| All products ... msdyn_globalproducts                                               | EcoResEveryProductEntity                   | msdyn_globalproduct                            |  |
| Product dimension groups ... msdyn_productdimensiongroups                           | EcoResProductDimensionGroupEntity          | msdyn_productdimensiongroup                    |  |
| Storage dimension groups ... msdyn_productstoragedimensiongroups                    | EcoResStorageDimensionGroupEntity          | msdyn_productstoragedimensiongroup             |  |
| Tracking dimension groups ... msdyn_producttrackingdimensiongroups                  | EcoResTrackingDimensionGroupEntity         | msdyn_producttrackingdimensiongroup            |  |
| Colors ... msdyn_productcolors                                                      | EcoResProductColorEntity                   | msdyn_productcolor                             |  |
| Sizes ... msdyn_productsizes                                                        | EcoResProductSizeEntity                    | msdyn_productsize                             |  |
| Styles ... msdyn_productstyles                                                      | EcoResProductStyleEntity                   | msdyn_productstyle                            |  |
| Configurations ... msdyn_productconfigurations                                      | EcoResProductConfigurationEntity           | msdyn_productconfiguration                    |  |
| Released products V2 ... msdyn_sharedproductdetails                                 | EcoResReleasedProductV2Entity              | msdyn_sharedproductdetail                     |  |
| Common Data Service released distinct products ... products                         | EcoResReleasedDistinctProductCommon Data ServiceEntity     | product                       |  |
| Product Number Identified Barcode ... msdyn_productbarcodes                         | EcoResProductNumberIdentifiedBarcodeEntity | msdyn_productbarcode                          |  |
| Default order settings ... msdyn_productdefaultordersettings                        | InventProductDefaultOrderSettingsEntity    | msdyn_productdefaultordersetting              |  |
| Product default order settings V2 ... msdyn_productspecificdefaultordersettings     | InventProductSpecificOrderSettingsV2Entity | msdyn_productspecificdefaultordersetting      |  |
| Product specific unit conversions ... msdyn_productspecificunitofmeasureconversions | EcoResProductSpecificUnitConversionEntity  | msdyn_productspecificunitofmeasureconversion  |  |
| Sites ... msdyn_operationalsites                                                    | InventOperationalSiteEntity                | msdyn_operationalsite                |  |
| Warehouses ... msdyn_warehouses                                                     | InventWarehouseEntity                      | msdyn_warehouse                      | See note. |
| Product master colors ... msdyn_sharedproductcolors                                 | EcoResProductMasterColorEntity             | msdyn_sharedproductcolor             |  |
| Product master sizes ... msdyn_sharedproductsizes                                   | EcoResProductMasterSizeEntity              | msdyn_sharedproductsize              |  |
| Product master styles ... msdyn_sharedproductstyles                                 | EcoResProductMasterStyleEntity             | msdyn_sharedproductstyle             |  |
| Product master configurations ... msdyn_sharedproductconfigurations                 | EcoResProductMasterConfigurationEntity     | msdyn_sharedproductconfiguration     |  |
| Product categories ... msdyn_productcategories                                      | EcoResProductCategoryEntity                | msdyn_productcategory                | See note. |
| Product category assignments ... msdyn_productcategoryassignments                   | EcoResProductCategoryAssignmentEntity      | msdyn_productcategoryassignment      |  |
| Product category hierarchies ... msdyn_productcategoryhierarchies                   | EcoResProductCategoryHierarchyEntity       | msdyn_productcategoryhierarchy       |  |
| Product category hierarchy roles ... msdyn_productcategoryhierarchyroles            | EcoResProductCategoryHierarchyRoleEntity   | msdyn_productcategoryhierarchyrole   |  |
| Inventory aisle ... msdyn_warehouseaisles                                           | WMSWarehouseAisleEntity                    | msdyn_warehouseaisle            |  |
| Warehouse zones ... msdyn_warehousezones                                            | WHSWarehouseZoneEntity                     | msdyn_warehousezone             |  |
| Warehouse zone groups ... msdyn_warehousezonegroups                                 | WHSWarehouseZoneGroupEntity                | msdyn_warehousezonegroup        |  |
| Warehouse locations ... msdyn_inventorylocations                                    | WMSWarehouseLocationEntity                 | msdyn_inventorylocation         | See note. |
| Warehouse work headers ... msdyn_warehouseworkheaders                               | WHSWarehouseWorkHeaderEntity               | msdyn_warehouseworkheader       |  |
| Warehouse work lines... msdyn_warehouseworklines                                    | WHSWarehouseWorkLineEntity                 | msdyn_warehouseworklines        | See note. |
| Modes of delivery ... msdyn_shipvias                                                | DlvDeliveryModeEntity                      | msdyn_shipvias                  |  |
| Terms of delivery ... msdyn_termsofdeliveries                                       | DeliveryTermsEntity                        | msdyn_termsofdelivery           |  |
| Sales order origin codes ... msdyn_salesorderorigins                                | SalesOrderOriginEntity                     | msdyn_salesorderorigin          |  |
| Common Data Service sales order headers ... salesorders                             | SalesOrderHeaderCommon Data ServiceEntity       | salesorder                      |  |
| Common Data Service sales order lines ... salesorderdetails                         | SalesOrderLineCommon Data ServiceEntity         | salesorderdetails               |  |
| Common Data Service sales quotation header ... quotes                               | SalesQuotationHeaderCommon Data ServiceEntity   | quote                           |  |
| Common Data Service sales quotation lines ... quotedetails                          | SalesQuotationLineCommon Data ServiceEntity     | QuoteDetails                    |  |
| Sales invoice headers V2 ... invoices                                               | SalesInvoiceHeaderV2Entity                 | invoice                         |  |
| Sales invoice lines V2 ... invoicedetails                                           | SalesInvoiceLineV2Entity                   | invoicedetail                   |  |

### Mapping-specific notes
+ **Warehouses ... msdyn_warehouses**: Because of self-dependency, you may need to run the initial sync twice.
+ **Product categories ... msdyn_productcategories**: Initial sync is turned off by default because of parent-child relationship ("smart" ordering not handled by platform). So the existing product categories needs to be manually synced (for example by updating the description of the category) in the right order (root category first, then children, then children of children) Path: Product information management \> Setup \> Categories and attributes \> Category hierarchies form, from which you can select each hierarchy and see the product categories in it.
+ **Warehouse locations ... msdyn_inventorylocations**: Mapping of empty lookup fields ItemNumberInLocation and first/second/third addition warehouse zone will cause initial sync failed. So these mappings are removed for now.
+ **Warehouse work lines... msdyn_warehouseworklines**: Mapping of empty field CaptureWeight will cause initial sync failed. It is removed for now.

### Setup-related information

+ The records in the **Products** entity of model-driven apps in Dynamics 365 are created in **Draft** state. To change the state to **Active**, in the model-driven app, navigate to **Settings \> Administration \> System Settings \> Sales**, and set **Create products in active state** to **Yes**.
+ The records in the **Products** entity that you create in model-driven apps in Dynamics 365 or in Common Data Service before you enable dual-write will not be updated unless the entire key, incuding **Company** matches data in the Finance and Operations app.
+ The **Products** entity sync is unidirectional, from Finance and Operations apps to Common Data Service (Finance and Operations to Common Data Service). Any update to a mapped field on in the **Products** entity in model-driven app is overwritten during the next sync from the Finance and Operations app.

### Known issues

There is an error when deleting a **Unit** in Finance and Operations. When syncing **Unit of measures** from Finance and Operations to Common Data Service, the first unit of a specific class will be created as the **Primary Unit** and prevent deletion.

    Mitigation: Delete the unit in Common Data Service first, then it can be deleted in Finance and Operations.

There is an error when deleting an **Operational Site** in Common Data Service. The error message is *Infolog: Warning: Primary address cannot be deleted.; Warning: The entity record could not be deleted because validation failed for the following data source: InventSiteLogisticsLocation (InventSiteLogisticsLocation).* This is due to a bug in the Finance and Operations data entity.

    Mitigation: You can delete the site in the Finance and Operations app. The site will then be deleted in Common Data Service, if the corresponding dual-write map is running.

## Dynamics 365 Finance entities

The following entities for Dynamics 365 Finance are listed in the order you should enable them.

| Mapping name on Dual-write page | Supply Chain Management<br>Entity metadata name  | Common Data Service<br>Entity metadata name   | Notes |
|---|---|---|---|
| Currencies ... transactioncurrencies                                            | CurrencyEntity                         | Currency                                   |  |
| Exchange rate type ... msdyn_exchangeratetypes                                  | ExchangeRateTypeEntity                 | msdyn_exchangeratetype                     |  |
| Exchange rate currency pair ... msdyn_currencyexchangeratepairs                 | ExchangeRateCurrencyPairEntity         | msdyn_currencyexchangeratepair             |  |
| Common Data Service Exchange rates ... msdyn_currencyexchangerates              | ExchangeRateCommon Data ServiceEntity  | msdyn_currencyexchangerate                 | See note. |
| Fiscal calendar integration entity ... msdyn_fiscalcalendars                    | FiscalCalendarEntity                   | msdyn_fiscalcalendar                       |  |
| Fiscal calendar year integration entity ... msdyn_fiscalcalendaryears           | FiscalCalendarYearEntity               | msdyn_fiscalcalendaryear                   |  |
| Fiscal calendar period ... msdyn_fiscalcalendarperiods                          | FiscalPeriodEntity                     | msdyn_fiscalcalendarperiod                 |  |
| Organization hierarchy type ... msdyn_internalorganizationhierarchytypes        | OMOrganizationHierarchyTypeEntity      | msdyn_internalorganizationhierarchytype    | See note. |
| Organization hierarchy purposes ... msdyn_internalorganizationhierarchypurposes | OMOrganizationHierarchyPurposeEntity   | msdyn_internalorganizationhierarchypurpose | See note. |
| Legal entities ... msdyn_internalorganizations                                  | OMLegalEntity                          | msdyn_internalorganization                 | See note. |
| Legal entities ... cdm_companies                                                | OMLegalEntity                          | cdm_company                                |  |
| Operating Unit ... msdyn_internalorganizations                                  | OMOperatingUnitEntity                  | msdyn_internalorganization                 | See note. |
| Organization hierarchy - published ... msdyn_internalorganizationhierarchies    | OMOrganizationHierarchyPublishedEntity | msdyn_internalorganizationhierarchy        | See note. |
| Name affixes ... msdyn_nameaffixes                                              | DirNameAffixEntity                     | msdyn_nameaffix                            |  |
| Payment days Common Data Service ... msdyn_paymentdays                          | PaymentDayCommon Data ServiceEntity       | msdyn_paymentday                        |  |
| Payment day lines Common Data Service V2 ... msdyn_paymentdaylines              | PaymentDayLineCommon Data ServiceV2Entity | msdyn_paymentdayline                    |  |
| Payment schedule ... msdyn_paymentschedules                                     | PaymentScheduleEntity                  | msdyn_paymentschedule                      |  |
| Payment schedule lines ... msdyn_paymentschedulelines                           | PaymentScheduleLineEntity              | msdyn_paymentscheduleline                  |  |
| Terms of payment ... msdyn_paymentterms                                         | PaymentTermEntity                      | msdyn_paymentterm                          |  |
| Customer payment method ... msdyn_customerpaymentmethods                        | CustomerPaymentMethodEntity            | msdyn_customerpaymentmethod                |  |
| Vendor payment method ... msdyn_vendorpaymentmethods                            | VendorPaymentMethodEntity              | msdyn_vendorpaymentmethod                  |  |
| Customer groups ... msdyn_customergroups                                        | CustCustomerGroupEntity                | msdyn_customergroup                        |  |
| Vendor groups ... msdyn_vendorgroups                                            | VendVendorGroupEntity                  | msdyn_vendorgroup                          |  |
| Sales tax groups ... msdyn_taxgroups                                            | TaxGroupEntity                         | msdyn_taxgroup                             |  |
| Item sales tax groups ... msdyn_taxitemgroups                                   | TaxItemGroupEntity                     | msdyn_taxitemgroup                         |  |
| Sales tax ledger posting groups V2 ... msdyn_taxpostinggroups                   | TaxPostingGroupEntityV2                | msdyn_taxpostinggroup                      |  |
| Sales tax exempt code entity Common Data Service ... msdyn_taxexemptcodes       | TaxExemptCodeCommon Data ServiceEntity    | msdyn_taxexemptcode                     |  |
| Sales tax authorities ... msdyn_taxauthorities                                  | TaxAuthorityEntity                     | msdyn_taxauthority                         |  |
| Sales tax code ... msdyn_taxcodes                                               | TaxCodeEntity                          | msdyn_taxcode                              | See note. |
| Financial dimension format ... msdyn_financialdimensionformats                  | DimensionIntegrationFormatEntity       | msdyn_financialdimensionformat             |  |
| Financial dimensions ... msdyn_dimensionattributes                              | DimensionAttributeEntity               | msdyn_dimensionattribute                   |  |
| Withholding tax groups ... msdyn_withholdingtaxgroups                           | TaxWithholdingGroupEntity              | msdyn_withholdingtaxgroup                  |  |
| Withholding tax codes ... msdyn_withholdingtaxcodes                             | TaxWithholdingTaxCodes                 | msdyn_withholdingtaxcode                   |  |
| Chart of accounts ... msdyn_chartofaccountses                                   | LedgerChartOfAccountsEntity            | msdyn_chartofaccounts                      |  |
| Ledger ... msdyn_ledgers                                                        | LedgerEntity                           | msdyn_ledger                               | See note. |
| Main account categories ... msdyn_mainaccountcategories                         | MainAccountCategoryEntity              | msdyn_mainaccountcategory                  |  |
| Main account ... msdyn_mainaccounts                                             | MainAccountEntity                      | msdyn_mainaccount                          |  |
| Customers V3 ... accounts                                                       | CustCustomerV3Entity                   | account                                    | See note. |
| Customers V3 ... contacts                                                       | CustCustomerV3Entity                   | contact                                    | See note. |
| Vendors V2 ... msdyn_vendors                                                    | VendVendorV2Entity                     | msdyn_vendor                               | See note. |
| Common Data Service Contacts V2 ... contacts                                    | smmContactPersonCommon Data ServiceV2Entity       | contact                         | See note. |
| Common Data Service Contacts V2 ... contacts                                    | smmContactPersonCommon Data ServiceV2Entity       | contact                         | See note. |

### Mapping-specific notes
+ Common Data Service Exchange rates ... msdyn_currencyexchangerates: One-way sync from Finance and Operations apps to Common Data Service.
+ Organization hierarchy type ... msdyn_internalorganizationhierarchytypes: One-way sync from Finance and Operations apps to Common Data Service.
+ Organization hierarchy purposes ... msdyn_internalorganizationhierarchypurposes: One-way sync from Finance and Operations apps to Common Data Service.
+ Legal entities ... msdyn_internalorganizations: One-way sync from Finance and Operations apps to Common Data Service.
+ Operating Unit ... msdyn_internalorganizations: One-way sync from Finance and Operations apps to Common Data Service.
+ Organization hierarchy - published ... msdyn_internalorganizationhierarchies: One way sync from Finance and Operations apps to Common Data Service.
+ Sales tax code ... msdyn_taxcodes: One-way sync from Finance and Operations apps to Common Data Service.
+ Ledger ... msdyn_ledgers: One-way sync from Finance and Operations apps to Common Data Service.
+ Customers V3 ... accounts: Because of self-dependency, you might need to run the initial sync more than once. Make sure to select **RelationshipType** as **Customer** when creating an account from Common Data Service by using the **Accounts** form. If you run into issues with the **Primary Contact** field during initial sync, remove the **Primary Contact** field from the mapping and run the initial sync. Once the initial sync is successful, stop the mapping, add the **Primary Contact** field back to the mapping and start the mapping by skipping initial sync. The primary contact field value will not be synced initially and you have to manually migrate the values.
+ Customers V3 ... contacts: Make sure to select **Sellable** as **Yes** in **Contacts** form of Common Data Service when trying to create a customer of type **Person**.
+ Vendors V2 ... msdyn_vendors: Because of self-dependency, you might need to run the initial sync more than once. Make sure to select **RelationshipType** as **Customer** when creating an account from Common Data Service by using the **Accounts** form. If you run into issues with the **Primary Contact** field during initial sync, remove the **Primary Contact** field from the mapping and run the initial sync. Once the initial sync is successful, stop the mapping, add the **Primary Contact** field back to the mapping and start the mapping by skipping initial sync. The primary contact field value will not be synced initially and you have to manually migrate the values.
+ Common Data Service Contacts V2 ... contacts: This mapping contains a filter on both sides to link **Customer contacts**. Navigate to the mapping details. Click on the filter icon next to the **Sales.Contact** entity name and ensure that the file criteria contains **msdyn_contactforvendor eq true and msdyn_sellable eq false**.
+ Common Data Service Contacts V2 ... contacts: This mapping contains a filter on both sides to link **Vendor contacts**. Navigate to the mapping details. Click on the filter icon next to the **Sales.Contact** entity name and ensure that the filter criteria containts **msdyn_contactforvendor eq true and msdyn_sellable eq false**. 

## Dynamics 365 Human Resources entities

The following entities for Dynamics 365 Human Resources are listed in the order you should enable them.

| Mapping name on Dual-write page | Supply Chain Management<br>Entity metadata name  | Common Data Service<br>Entity metadata name   | Notes |
|---|---|---|---|
| cdm_jobfunction - Job Function                                |                                   | cdm_jobfunction                  |                                             |
| cdm_jobtypes - Job Types                                      |                                   | cdm_jobtypes                     |                                             |
| cdm_jobs - Jobs                                               |                                   | cdm_jobs                         |                                             |
| cdm_jobs - Job Details                                        |                                   | cdm_jobs                         |                                             |
| cdm_positiontype - PositionType                               | HcmPositionTypeEntity             | cdm_positiontype                 |                                             |
| cdm_jobpositions - Base position                              | HcmPositionBaseEntity             | cdm_jobposition                  | See note. |
| cdm_jobposition - Position Details                            | HcmPositionDetailEntity           | cdm_jobposition                  | See note. |
| cdm_jobposition - Position Duration                           | HcmPositionDurationEntity         | cdm_jobposition                  | See note. |
| cdm_jobposition - Position Hierarchies                        | HcmPositionHierarchyEntity        | cdm_jobposition                  | See note. |
| cdm_veteranstatus - Veteran Status                            |                                   | cdm_veteranstatus                |                                             |
| cdm_ethnicorigin - Ethnic Origin                              |                                   | cdm_ethnicorigin                 |                                             |
| cdm_languagecode - Language Code                              |                                   | cdm_languagecode                 |                                             |
| cdm_worker - Worker                                           | HcmWorkerEntity                   | cdm_worker                       |                                             |
| cdm_employments - Employments                                 |                                   | cdm_employments                  |                                             |
| cdm_employments - Employment Detail                           |                                   | cdm_employments                  |                                             |
| cdm_positionworkerassignmentmaps - Position Worker Assignment | HcmPositionWorkerAssignmentEntity | cdm_positionworkerassignmentmaps | Contains a self reference                   |
|                                                               |                                   |                                  |                                             |

### Mapping-specific notes

+ cdm_jobpositions - Base position: One Common Data Service entity is mapped to several Finance and Operations entities.
+ cdm_jobposition - Position Details: One Common Data Service entity is mapped to several Finance and Operations entityies.
+ cdm_jobposition - Position Duration: One Common Data Service entity is mapped to several Finance and Operations entities.
+ cdm_jobposition - Position Hierarchies: One Common Data Service entity is mapped to several Finance and Operations entities.
+ cdm_positionworkerassignmentmaps: Contains a self reference.

## Asset Management entities

The following entities for Asset Management are listed in the order you should enable them.

| Mapping name on Dual-write page | Supply Chain Management<br>Entity metadata name  | Common Data Service<br>Entity metadata name   | Notes |
|---|---|---|---|
| FO.AssetManagementAssetLifecycleStates--Common Data Service.msdyn_assetlifecyclestates                           | Asset management asset lifecycle states               | msdyn_assetlifecyclestates               | |
| FO.AssetManagementAssetLifecycleModels--Common Data Service.msdyn_assetlifecyclemodels                           | Asset management asset lifecycle models               | msdyn_assetlifecyclemodels               | |
| FO.AssetManagementFunctionalLocationLifecycleModels--Common Data Service.msdyn_functionallocationlifecyclemodels | Asset management functional location lifecycle models | msdyn_functionallocationlifecyclemodels  | |
| FO.AssetManagementFunctionalLocationLifecycleStates--Common Data Service.msdyn_functionallocationlifecyclestates | Asset management functional location lifecycle states | msdyn_functionallocationlifecyclestates  | |
| FO.AssetManagementAssetTypes--Common Data Service.msdyn_customerassetcategories                                  | Asset management asset types                          | msdyn_customerassetcategories            | |
| FO.AssetManagementFunctionalLocationTypes--Common Data Service.msdyn_functionallocationtypes                     | Asset management functional location types            | msdyn_functionallocationtypes            | |
| FO.AssetManagementFunctionalLocations--Common Data Service.msdyn_functionallocations                             | Asset management functional locations                 | msdyn_functionallocations                | See note. |
| FO.AssetManagementAssets--Common Data Service.msdyn_customerassets                                               | Asset management assets                               | msdyn_customerassets                     | See note. |
| FO.AssetManagementManufacturers--Common Data Service.msdyn_manufacturers                                         | Asset management manufacturers                        | msdyn_manufacturers                      | |
| FO.AssetManagementModels--Common Data Service.msdyn_models                                                       | Asset management models                               | msdyn_models                             | |
| FO.AssetManagementWarranty--Common Data Service.msdyn_warranties                                                 | Asset management warranty                             | msdyn_warranties                         | |

### Mapping-specific notes

+ FO.AssetManagementFunctionalLocations--Common Data Service.msdyn_functionallocations: Because of self-dependency, you may need to run the initial sync more than once. |
+ FO.AssetManagementAssets--Common Data Service.msdyn_customerassets: Because of self-dependency, you may need to run the initial sync more than once. |
