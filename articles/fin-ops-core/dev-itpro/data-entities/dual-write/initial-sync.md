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

In the following tables, the entities are listed in the order in which you should enable them. When you enable a map for initial synchronization, dual-write automatically detects other maps that must be enabled. You can use the **Dual-write** page in Finance and Operations apps to select or cancel the selection of entities during the initial synchronization.

In the latest version of dual-write, you can enable just some entities, and the dependencies are handled for you.

## Dynamics 365 Supply Chain Management entities

The following entities for Supply Chain Management are listed in the order in which you should enable them.

| Mapping name on the Dual-write page | Entity metadata name in Supply Chain Management | Entity metadata name in Common Data Service | Notes |
|---|---|---|---|
| Units ... uoms                                                                      | UnitOfMeasureEntity                                    | uom                                          | |
| Unit conversions ... msdyn_unitofmeasureconversions                                 | UnitOfMeasureConversionEntity                          | msdyn_unitofmeasureconversion                | |
| All products ... msdyn_globalproducts                                               | EcoResEveryProductEntity                               | msdyn_globalproduct                          | |
| Product dimension groups ... msdyn_productdimensiongroups                           | EcoResProductDimensionGroupEntity                      | msdyn_productdimensiongroup                  | |
| Storage dimension groups ... msdyn_productstoragedimensiongroups                    | EcoResStorageDimensionGroupEntity                      | msdyn_productstoragedimensiongroup           | |
| Tracking dimension groups ... msdyn_producttrackingdimensiongroups                  | EcoResTrackingDimensionGroupEntity                     | msdyn_producttrackingdimensiongroup          | |
| Colors ... msdyn_productcolors                                                      | EcoResProductColorEntity                               | msdyn_productcolor                           | |
| Sizes ... msdyn_productsizes                                                        | EcoResProductSizeEntity                                | msdyn_productsize                            | |
| Styles ... msdyn_productstyles                                                      | EcoResProductStyleEntity                               | msdyn_productstyle                           | |
| Configurations ... msdyn_productconfigurations                                      | EcoResProductConfigurationEntity                       | msdyn_productconfiguration                   | |
| Released products V2 ... msdyn_sharedproductdetails                                 | EcoResReleasedProductV2Entity                          | msdyn_sharedproductdetail                    | |
| Common Data Service released distinct products ... products                         | EcoResReleasedDistinctProductCommon Data ServiceEntity | product                                      | |
| Product Number Identified Barcode ... msdyn_productbarcodes                         | EcoResProductNumberIdentifiedBarcodeEntity             | msdyn_productbarcode                         | |
| Default order settings ... msdyn_productdefaultordersettings                        | InventProductDefaultOrderSettingsEntity                | msdyn_productdefaultordersetting             | |
| Product default order settings V2 ... msdyn_productspecificdefaultordersettings     | InventProductSpecificOrderSettingsV2Entity             | msdyn_productspecificdefaultordersetting     | |
| Product specific unit conversions ... msdyn_productspecificunitofmeasureconversions | EcoResProductSpecificUnitConversionEntity              | msdyn_productspecificunitofmeasureconversion | |
| Sites ... msdyn_operationalsites                                                    | InventOperationalSiteEntity                            | msdyn_operationalsite                        | |
| Warehouses ... msdyn_warehouses                                                     | InventWarehouseEntity                                  | msdyn_warehouse                              | See [note 1](#scm-notes). |
| Product master colors ... msdyn_sharedproductcolors                                 | EcoResProductMasterColorEntity                         | msdyn_sharedproductcolor                     | |
| Product master sizes ... msdyn_sharedproductsizes                                   | EcoResProductMasterSizeEntity                          | msdyn_sharedproductsize                      | |
| Product master styles ... msdyn_sharedproductstyles                                 | EcoResProductMasterStyleEntity                         | msdyn_sharedproductstyle                     | |
| Product master configurations ... msdyn_sharedproductconfigurations                 | EcoResProductMasterConfigurationEntity                 | msdyn_sharedproductconfiguration             | |
| Product categories ... msdyn_productcategories                                      | EcoResProductCategoryEntity                            | msdyn_productcategory                        | See [note 2](#scm-notes). |
| Product category assignments ... msdyn_productcategoryassignments                   | EcoResProductCategoryAssignmentEntity                  | msdyn_productcategoryassignment              | |
| Product category hierarchies ... msdyn_productcategoryhierarchies                   | EcoResProductCategoryHierarchyEntity                   | msdyn_productcategoryhierarchy               | |
| Product category hierarchy roles ... msdyn_productcategoryhierarchyroles            | EcoResProductCategoryHierarchyRoleEntity               | msdyn_productcategoryhierarchyrole           | |
| Inventory aisle ... msdyn_warehouseaisles                                           | WMSWarehouseAisleEntity                                | msdyn_warehouseaisle                         | |
| Warehouse zones ... msdyn_warehousezones                                            | WHSWarehouseZoneEntity                                 | msdyn_warehousezone                          | |
| Warehouse zone groups ... msdyn_warehousezonegroups                                 | WHSWarehouseZoneGroupEntity                            | msdyn_warehousezonegroup                     | |
| Warehouse locations ... msdyn_inventorylocations                                    | WMSWarehouseLocationEntity                             | msdyn_inventorylocation                      | See [note 3](#scm-notes). |
| Warehouse work headers ... msdyn_warehouseworkheaders                               | WHSWarehouseWorkHeaderEntity                           | msdyn_warehouseworkheader                    | |
| Warehouse work lines... msdyn_warehouseworklines                                    | WHSWarehouseWorkLineEntity                             | msdyn_warehouseworklines                     | See [note 4](#scm-notes). |
| Modes of delivery ... msdyn_shipvias                                                | DlvDeliveryModeEntity                                  | msdyn_shipvias                               | |
| Terms of delivery ... msdyn_termsofdeliveries                                       | DeliveryTermsEntity                                    | msdyn_termsofdelivery                        | |
| Sales order origin codes ... msdyn_salesorderorigins                                | SalesOrderOriginEntity                                 | msdyn_salesorderorigin                       | |
| Common Data Service sales order headers ... salesorders                             | SalesOrderHeaderCommon Data ServiceEntity              | salesorder                                   | |
| Common Data Service sales order lines ... salesorderdetails                         | SalesOrderLineCommon Data ServiceEntity                | salesorderdetails                            | |
| Common Data Service sales quotation header ... quotes                               | SalesQuotationHeaderCommon Data ServiceEntity          | quote                                        | |
| Common Data Service sales quotation lines ... quotedetails                          | SalesQuotationLineCommon Data ServiceEntity            | QuoteDetails                                 | |
| Sales invoice headers V2 ... invoices                                               | SalesInvoiceHeaderV2Entity                             | invoice                                      | |
| Sales invoice lines V2 ... invoicedetails                                           | SalesInvoiceLineV2Entity                               | invoicedetail                                | |

### <a id='scm-notes'></a>Mapping-specific notes

1. Because of self-dependency, you might have to run the initial synchronization two times.
2. By default, initial synchronization is turned off because of the parent-child relationship ("smart" ordering isn't handled by the platform). Therefore, the existing product categories must be manually synced (for example, by updating the description of the category) in the correct order (root category first, then children, and then children of children). Go to **Product information management \> Setup \> Categories and attributes \> Category hierarchies**. On the **Category hierarchies** page, you can select each hierarchy and see the product categories in it.
3. The mapping of empty **ItemNumberInLocation** lookup fields and the first, second, and third additional warehouse zones will cause initial synchronization to fail. Therefore, these mappings are removed for now.
4. The mapping of the empty **CaptureWeight** field will cause initial synchronization to fail. Therefore, this mapping is removed for now.

### Setup-related information

+ When records are first created in the **Products** entity in model-driven apps in Dynamics 365, they have a status of **Draft**. To change the status to **Active**, go to **Settings \> Administration \> System Settings \> Sales** in the model-driven app, and set the **Create products in active state** option to **Yes**.
+ If you create records in the **Products** entity in model-driven apps in Dynamics 365 or in Common Data Service before you enable dual-write, those records will be updated only if the whole key, including **Company**, matches data in the Finance and Operations app.
+ Synchronization of the **Products** entity is unidirectional, from Finance and Operations apps to Common Data Service. If a mapped field in the **Products** entity in model-driven apps in Dynamics 365 is updated, the update will be overwritten during the next synchronization from the Finance and Operations app.

### Known issues

- An error occurs when a unit is deleted in a Finance and Operations app. When units of measure are synced from the Finance and Operations app to Common Data Service, the first unit of a specific class will be created as the primary unit and will prevent deletion.

    **Mitigation:** First delete the unit in Common Data Service. It can then be deleted in the Finance and Operations app.

- An error occurs when an operational site is deleted in Common Data Service. The error message states, "Infolog: Warning: Primary address cannot be deleted.; Warning: The entity record could not be deleted because validation failed for the following data source: InventSiteLogisticsLocation (InventSiteLogisticsLocation)." This error is caused by an issue in the data entity in the Finance and Operations app.

    **Mitigation:** You can delete the site in the Finance and Operations app. The site will then be deleted in Common Data Service if the corresponding dual-write map is running.

## Dynamics 365 Finance entities

The following entities for Dynamics 365 Finance are listed in the order in which you should enable them.

| Mapping name on the Dual-write page | Entity metadata name in Finance | Entity metadata name in Common Data Service | Notes |
|---|---|---|---|
| Currencies ... transactioncurrencies                                            | CurrencyEntity                              | Currency                                   | |
| Exchange rate type ... msdyn_exchangeratetypes                                  | ExchangeRateTypeEntity                      | msdyn_exchangeratetype                     | |
| Exchange rate currency pair ... msdyn_currencyexchangeratepairs                 | ExchangeRateCurrencyPairEntity              | msdyn_currencyexchangeratepair             | |
| Common Data Service Exchange rates ... msdyn_currencyexchangerates              | ExchangeRateCommon Data ServiceEntity       | msdyn_currencyexchangerate                 | See [note 1](#fin-notes). |
| Fiscal calendar integration entity ... msdyn_fiscalcalendars                    | FiscalCalendarEntity                        | msdyn_fiscalcalendar                       | |
| Fiscal calendar year integration entity ... msdyn_fiscalcalendaryears           | FiscalCalendarYearEntity                    | msdyn_fiscalcalendaryear                   | |
| Fiscal calendar period ... msdyn_fiscalcalendarperiods                          | FiscalPeriodEntity                          | msdyn_fiscalcalendarperiod                 | |
| Organization hierarchy type ... msdyn_internalorganizationhierarchytypes        | OMOrganizationHierarchyTypeEntity           | msdyn_internalorganizationhierarchytype    | See [note 1](#fin-notes). |
| Organization hierarchy purposes ... msdyn_internalorganizationhierarchypurposes | OMOrganizationHierarchyPurposeEntity        | msdyn_internalorganizationhierarchypurpose | See [note 1](#fin-notes). |
| Legal entities ... msdyn_internalorganizations                                  | OMLegalEntity                               | msdyn_internalorganization                 | See [note 1](#fin-notes). |
| Legal entities ... cdm_companies                                                | OMLegalEntity                               | cdm_company                                | |
| Operating Unit ... msdyn_internalorganizations                                  | OMOperatingUnitEntity                       | msdyn_internalorganization                 | See [note 1](#fin-notes). |
| Organization hierarchy - published ... msdyn_internalorganizationhierarchies    | OMOrganizationHierarchyPublishedEntity      | msdyn_internalorganizationhierarchy        | See [note 1](#fin-notes). |
| Name affixes ... msdyn_nameaffixes                                              | DirNameAffixEntity                          | msdyn_nameaffix                            | |
| Payment days Common Data Service ... msdyn_paymentdays                          | PaymentDayCommon Data ServiceEntity         | msdyn_paymentday                           | |
| Payment day lines Common Data Service V2 ... msdyn_paymentdaylines              | PaymentDayLineCommon Data ServiceV2Entity   | msdyn_paymentdayline                       | |
| Payment schedule ... msdyn_paymentschedules                                     | PaymentScheduleEntity                       | msdyn_paymentschedule                      | |
| Payment schedule lines ... msdyn_paymentschedulelines                           | PaymentScheduleLineEntity                   | msdyn_paymentscheduleline                  | |
| Terms of payment ... msdyn_paymentterms                                         | PaymentTermEntity                           | msdyn_paymentterm                          | |
| Customer payment method ... msdyn_customerpaymentmethods                        | CustomerPaymentMethodEntity                 | msdyn_customerpaymentmethod                | |
| Vendor payment method ... msdyn_vendorpaymentmethods                            | VendorPaymentMethodEntity                   | msdyn_vendorpaymentmethod                  | |
| Customer groups ... msdyn_customergroups                                        | CustCustomerGroupEntity                     | msdyn_customergroup                        | |
| Vendor groups ... msdyn_vendorgroups                                            | VendVendorGroupEntity                       | msdyn_vendorgroup                          | |
| Sales tax groups ... msdyn_taxgroups                                            | TaxGroupEntity                              | msdyn_taxgroup                             | |
| Item sales tax groups ... msdyn_taxitemgroups                                   | TaxItemGroupEntity                          | msdyn_taxitemgroup                         | |
| Sales tax ledger posting groups V2 ... msdyn_taxpostinggroups                   | TaxPostingGroupEntityV2                     | msdyn_taxpostinggroup                      | |
| Sales tax exempt code entity Common Data Service ... msdyn_taxexemptcodes       | TaxExemptCodeCommon Data ServiceEntity      | msdyn_taxexemptcode                        | |
| Sales tax authorities ... msdyn_taxauthorities                                  | TaxAuthorityEntity                          | msdyn_taxauthority                         | |
| Sales tax code ... msdyn_taxcodes                                               | TaxCodeEntity                               | msdyn_taxcode                              | See [note 1](#fin-notes). |
| Financial dimension format ... msdyn_financialdimensionformats                  | DimensionIntegrationFormatEntity            | msdyn_financialdimensionformat             | |
| Financial dimensions ... msdyn_dimensionattributes                              | DimensionAttributeEntity                    | msdyn_dimensionattribute                   | |
| Withholding tax groups ... msdyn_withholdingtaxgroups                           | TaxWithholdingGroupEntity                   | msdyn_withholdingtaxgroup                  | |
| Withholding tax codes ... msdyn_withholdingtaxcodes                             | TaxWithholdingTaxCodes                      | msdyn_withholdingtaxcode                   | |
| Chart of accounts ... msdyn_chartofaccountses                                   | LedgerChartOfAccountsEntity                 | msdyn_chartofaccounts                      | |
| Ledger ... msdyn_ledgers                                                        | LedgerEntity                                | msdyn_ledger                               | See [note 1](#fin-notes). |
| Main account categories ... msdyn_mainaccountcategories                         | MainAccountCategoryEntity                   | msdyn_mainaccountcategory                  | |
| Main account ... msdyn_mainaccounts                                             | MainAccountEntity                           | msdyn_mainaccount                          | |
| Customers V3 ... accounts                                                       | CustCustomerV3Entity                        | account                                    | See [note 2](#fin-notes). |
| Customers V3 ... contacts                                                       | CustCustomerV3Entity                        | contact                                    | See [note 3](#fin-notes). |
| Vendors V2 ... msdyn_vendors                                                    | VendVendorV2Entity                          | msdyn_vendor                               | See [note 2](#fin-notes). |
| Common Data Service Contacts V2 ... contacts                                    | smmContactPersonCommon Data ServiceV2Entity | contact                                    | See [note 4](#fin-notes). |
| Common Data Service Contacts V2 ... contacts                                    | smmContactPersonCommon Data ServiceV2Entity | contact                                    | See [note 5](#fin-notes). |

### <a id='fin-notes'></a>Mapping-specific notes

1. One-way synchronization occurs from Finance and Operations apps to Common Data Service.
2. Because of self-dependency, you might have to run the initial synchronization more than one time. Be sure to select **Customer** as the relation type when you create an account by using the **Accounts** page in Common Data Service. If you encounter issues with the **Primary Contact** field during initial synchronization, remove that field from the mapping, and then run the initial synchronization again. After the initial synchronization is successfully completed, stop the mapping, and add the **Primary Contact** field to it again. Then start the mapping, but skip initial synchronization. The value of the **Primary Contact** field won't be included in the initial synchronization, and you must manually migrate the values.
3. Be sure to set the **Sellable** option to **Yes** on the **Contacts** page in Common Data Service when you try to create a customer of the **Person** type.
4. This mapping has a filter on both sides to link customer contacts. Open the mapping details, select the filter button (funnel symbol) next to the **Sales.Contact** entity name, and make sure that the file criteria contain **msdyn_contactforvendor eq true and msdyn_sellable eq false**.
5. This mapping has a filter on both sides to link vendor contacts. Open the mapping details, select the filter button (funnel symbol) next to the **Sales.Contact** entity name, and make sure that the filter criteria contain **msdyn_contactforvendor eq true and msdyn_sellable eq false**. 

## Dynamics 365 Human Resources entities

The following entities for Dynamics 365 Human Resources are listed in the order in which you should enable them.

| Mapping name on the Dual-write page | Entity metadata name in Human Resources | Entity metadata name in Common Data Service | Notes |
|---|---|---|---|
| cdm_jobfunction - Job Function                                |                                   | cdm_jobfunction                  | |
| cdm_jobtypes - Job Types                                      |                                   | cdm_jobtypes                     | |
| cdm_jobs - Jobs                                               |                                   | cdm_jobs                         | |
| cdm_jobs - Job Details                                        |                                   | cdm_jobs                         | |
| cdm_positiontype - PositionType                               | HcmPositionTypeEntity             | cdm_positiontype                 | |
| cdm_jobpositions - Base position                              | HcmPositionBaseEntity             | cdm_jobposition                  | See [note 1](#hr-notes). |
| cdm_jobposition - Position Details                            | HcmPositionDetailEntity           | cdm_jobposition                  | See [note 1](#hr-notes). |
| cdm_jobposition - Position Duration                           | HcmPositionDurationEntity         | cdm_jobposition                  | See [note 1](#hr-notes). |
| cdm_jobposition - Position Hierarchies                        | HcmPositionHierarchyEntity        | cdm_jobposition                  | See [note 1](#hr-notes). |
| cdm_veteranstatus - Veteran Status                            |                                   | cdm_veteranstatus                | |
| cdm_ethnicorigin - Ethnic Origin                              |                                   | cdm_ethnicorigin                 | |
| cdm_languagecode - Language Code                              |                                   | cdm_languagecode                 | |
| cdm_worker - Worker                                           | HcmWorkerEntity                   | cdm_worker                       | |
| cdm_employments - Employments                                 |                                   | cdm_employments                  | |
| cdm_employments - Employment Detail                           |                                   | cdm_employments                  | |
| cdm_positionworkerassignmentmaps - Position Worker Assignment | HcmPositionWorkerAssignmentEntity | cdm_positionworkerassignmentmaps | See [note 2](#hr-notes).|

### <a id='hr-notes'></a>Mapping-specific notes

1. One Common Data Service entity is mapped to several Finance and Operations app entities.
2. This mapping has a self-reference.

## Asset Management entities

The following entities for Asset Management for Dynamics 365 Supply Chain Management are listed in the order in which you should enable them.

| Mapping name on the Dual-write page | Entity metadata name in Asset Management | Entity metadata name in Common Data Service | Notes |
|---|---|---|---|
| FO.AssetManagementAssetLifecycleStates--Common Data Service.msdyn_assetlifecyclestates                           | Asset management asset lifecycle states               | msdyn_assetlifecyclestates               | |
| FO.AssetManagementAssetLifecycleModels--Common Data Service.msdyn_assetlifecyclemodels                           | Asset management asset lifecycle models               | msdyn_assetlifecyclemodels               | |
| FO.AssetManagementFunctionalLocationLifecycleModels--Common Data Service.msdyn_functionallocationlifecyclemodels | Asset management functional location lifecycle models | msdyn_functionallocationlifecyclemodels  | |
| FO.AssetManagementFunctionalLocationLifecycleStates--Common Data Service.msdyn_functionallocationlifecyclestates | Asset management functional location lifecycle states | msdyn_functionallocationlifecyclestates  | |
| FO.AssetManagementAssetTypes--Common Data Service.msdyn_customerassetcategories                                  | Asset management asset types                          | msdyn_customerassetcategories            | |
| FO.AssetManagementFunctionalLocationTypes--Common Data Service.msdyn_functionallocationtypes                     | Asset management functional location types            | msdyn_functionallocationtypes            | |
| FO.AssetManagementFunctionalLocations--Common Data Service.msdyn_functionallocations                             | Asset management functional locations                 | msdyn_functionallocations                | See [the note](#am-notes). |
| FO.AssetManagementAssets--Common Data Service.msdyn_customerassets                                               | Asset management assets                               | msdyn_customerassets                     | See [the note](#am-notes). |
| FO.AssetManagementManufacturers--Common Data Service.msdyn_manufacturers                                         | Asset management manufacturers                        | msdyn_manufacturers                      | |
| FO.AssetManagementModels--Common Data Service.msdyn_models                                                       | Asset management models                               | msdyn_models                             | |
| FO.AssetManagementWarranty--Common Data Service.msdyn_warranties                                                 | Asset management warranty                             | msdyn_warranties                         | |

### <a id='am-notes'></a>Mapping-specific notes

- Because of self-dependency, you might have to run the initial synchronization more than one time.
