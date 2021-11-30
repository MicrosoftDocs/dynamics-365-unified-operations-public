---
title: Separated Dual-write Application Orchestration Package
description: Dual-write application orchestration package is no more a single monolithic package. 
author: RamaKrishnamoorthy
ms.date: 11/29/2021
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: tfehr
ms.custom: "separate-solution"
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2021-11-29
---

# Separated Dual-write Application Orchestration Package

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

So far, dual-write application orchestration package has been a single monolithic package comprising of the following solutions and created an “all” or “nothing” situation for customers.

-   CurrencyExchangeRates

-   Dynamics365Company

-   Dynamics365FinanceAndOperationsCommon

-   Dynamics365FinanceExtended

-   Dynamics365SupplyChainExtended

-   Dynamics365AssetManagement

-   Dynamics365AssetManagementApp

-   Dynamics365Notes

-   Dynamics365FinanceAndOperationsDualWriteMaps

-   Dynamics365FinanceAndOperationsAnchor

Now we have split this package into smaller packages which allows to pick and choose the solutions as necessary. Say for example, you may be a supply chain customer and doesn’t need human resources, notes and asset integrations. In such case, you can exclude those solutions from installing. Since the underlying solution names, publisher and map versions remain the same, this is a non-breaking change. Existing installations are upgradable as well.

![separated-package](media/separated-package-1.png)

This page explains the solutions and maps covered in each package and its dependency on the other packages.



## Dual-write Application Core

Dual-write Application Core package allows users to install and configure dual-write without any Customer Engagement app. It contains 5 solutions namely:

| Unique Name                           | Display Name                                              |
|---------------------------------------|-----------------------------------------------------------|
| Dynamics365Company                    | Dynamics 365 Company                                      |
| Dynamics365FinanceAndOperationsCommon | Dynamics 365 Finance and Operations Common                |
| CurrencyExchangeRates                 | Currency Exchange Rates                                   |
| msdyn_DualWriteAppCoreMaps            | Dynamics 365 Dual Write Applications Core Entity Maps     |
| msdyn_DualWriteAppCoreAnchor          | Dynamics 365 Dual Write Applications Core Anchor solution |

Following are the maps available on this package:

| Finance and Operations          | Customer Engagement                         |
|---------------------------------|---------------------------------------------|
| Operating unit                  | msdyn_internalorganizations                 |
| Organization hierarchy          | msdyn_internalorganizationhierarchies       |
| Legal entities                  | msdyn_internalorganizations                 |
| Legal entities                  | cdm_companies                               |
| Organization hierarchy purposes | msdyn_internalorganizationhierarchypurposes |
| Exchange rate currency pair     | msdyn_currencyexchangeratepairs             |
| Name affixes                    | msdyn_nameaffixes                           |
| Exchange rate type              | msdyn_exchangeratetypes                     |
| CDS Exchange Rates              | msdyn_currencyexchangerates                 |
| Organization hierarchy type     | msdyn_internalorganizationhierarchytypes    |
| Currencies                      | transactioncurrencies                       |
| Mixed reality guides entity     | msmrw_guides                                |

**Dependency Information:** None



## Dual-write Human Resources


Dual-write Human Resources package contains solutions and maps necessary to sync Dynamics 365 Human Resources data. It contains 3 solutions namely:

| Unique Name                | Display Name                                                      |
|----------------------------|-------------------------------------------------------------------|
| HCMCommon                  | HCM Common                                                        |
| msdyn_Dynamics365HCMMaps   | Dynamics 365 Dual Write Applications HCM Entity Maps              |
| msdyn_Dynamics365HCMAnchor | Dynamics 365 Dual Write Applications Asset Management Entity Maps |

Following are the maps available on this package:

| Finance and Operations      | Customer Engagement              |
|-----------------------------|----------------------------------|
| Ethnic origins              | cdm_ethnicorigins                |
| Compensation job function   | cdm_jobfunctions                 |
| Positions V2                | cdm_jobpositions                 |
| Jobs                        | cdm_jobs                         |
| Compensation job type       | cdm_jobtypes                     |
| Language codes              | cdm_languages                    |
| Position type               | cdm_positiontypes                |
| Position worker assignments | cdm_positionworkerassignmentmaps |
| Veteran status              | cdm_veteranstatuses              |
| Worker                      | cdm_workers                      |
| Employment per company      | cdm_employments                  |

**Dependency information:** Dual-write Application Core package



## Dual-write Supply Chain

Dual-write Supply Chain package contains solutions and maps necessary to sync Dynamics 365 Supply Chain data. It contains 3 solutions namely:


| Unique Name                                | Display Name                                                               |
|--------------------------------------------|----------------------------------------------------------------------------|
| Dynamics365SupplyChainExtended             | Dynamics 365 Supply Chain Extended                                         |
| msdyn_Dynamics365SupplyChainExtendedMaps   | Dynamics 365 Dual Write Applications Supply Chain Extended Entity Maps     |
| msdyn_Dynamics365SupplyChainExtendedAnchor | Dynamics 365 Dual Write Applications Supply Chain Extended Anchor solution |

Following are the maps available on this package:

| Finance and Operations                      | Customer Engagement                           |
|---------------------------------------------|-----------------------------------------------|
| Units                                       | uoms                                          |
| CDS sales order headers                     | salesorders                                   |
| CDS sales order lines                       | salesorderdetails                             |
| CDS sales quotation header                  | quotes                                        |
| CDS sales quotation lines                   | quotedetails                                  |
| CDS released distinct products              | products                                      |
| Warehouse zones                             | msdyn_warehousezones                          |
| Warehouse zone groups                       | msdyn_warehousezonegroups                     |
| Warehouse work lines                        | msdyn_warehouseworklines                      |
| Warehouse work headers                      | msdyn_warehouseworkheaders                    |
| Warehouses                                  | msdyn_warehouses                              |
| Inventory aisle                             | msdyn_warehouseaisles                         |
| Unit conversions                            | msdyn_unitofmeasureconversions                |
| Terms of delivery                           | msdyn_termsofdeliveries                       |
| Modes of delivery                           | msdyn_shipvias                                |
| Product master styles                       | msdyn_sharedproductstyles                     |
| Sales invoice lines V2                      | invoicedetails                                |
| Sales invoice headers V2                    | invoices                                      |
| Product master sizes                        | msdyn_sharedproductsizes                      |
| Released products V2                        | msdyn_sharedproductdetails                    |
| Product master configurations               | msdyn_sharedproductconfigurations             |
| Product master colors                       | msdyn_sharedproductcolors                     |
| Sales order origin codes                    | msdyn_salesorderorigins                       |
| Product receipt header                      | msdyn_purchaseorderreceipts                   |
| Product receipt line                        | msdyn_purchaseorderreceiptproducts            |
| Purchase order headers V2                   | msdyn_purchaseorders                          |
| CDS purchase order line soft deleted entity | msdyn_purchaseorderproducts                   |
| CDS purchase order line entity              | msdyn_purchaseorderproducts                   |
| Tracking dimension groups                   | msdyn_producttrackingdimensiongroups          |
| Styles                                      | msdyn_productstyles                           |
| Storage dimension groups                    | msdyn_productstoragedimensiongroups           |
| Product specific unit conversions           | msdyn_productspecificunitofmeasureconversions |
| Product default order settings V2           | msdyn_productspecificdefaultordersettings     |
| Sizes                                       | msdyn_productsizes                            |
| Product dimension groups                    | msdyn_productdimensiongroups                  |
| Default order settings                      | msdyn_productdefaultordersettings             |
| Configurations                              | msdyn_productconfigurations                   |
| All products                                | msdyn_globalproducts                          |
| Colors                                      | msdyn_productcolors                           |
| Product category hierarchy roles            | msdyn_productcategoryhierarchyroles           |
| Product category hierarchies                | msdyn_productcategoryhierarchies              |
| Product category assignments                | msdyn_productcategoryassignments              |
| Product categories                          | msdyn_productcategories                       |
| Warehouse locations                         | msdyn_inventorylocations                      |
| CDS inventory on                            | msdyn_inventoryonhandentries                  |
| Product categories                          | msdyn_productcategories                       |
| CDS inventory on                            | msdyn_inventoryonhandrequests                 |
| Product Number Identified Barcode           | msdyn_productbarcodes                         |
| Loyalty card                                | msdyn_loyaltycards                            |
| Loyalty reward points                       | msdyn_loyaltyrewardpoints                     |
| Price customer groups                       | msdyn_pricecustomergroups                     |
| Sites                                       | msdyn_operationalsites                        |
| CDS sales quotation lines                   | quotedetails                                  |
| CDS sales order lines                       | salesorderdetails                             |

**Dependency information:**

-   Dual-write Application Core package

-   Dual-write Finance and Extended package

-   Dual-write HCM package



## Dual-write Finance

Dual-write Finance package contains solutions and maps necessary to sync Dynamics 365 Finance data. It contains 3 solutions namely:

| Unique Name                            | Display Name                                                           |
|----------------------------------------|------------------------------------------------------------------------|
| Dynamics365FinanceExtended             | Dynamics 365 Finance Extended                                          |
| msdyn_Dynamics365FinanceExtendedMaps   | Dynamics 365 Dual Write Applications Finance Extended Entity Maps      |
| msdyn_Dynamics365FinanceExtendedAnchor | Dynamics 365 Dual Write  Applications Finance Extended Anchor solution |

Following are the maps available on this package:

| Finance and Operations                  | Customer Engagement             |
|-----------------------------------------|---------------------------------|
| Withholding tax groups                  | msdyn_withholdingtaxgroups      |
| CDS Contacts V2 (Customer)              | contacts                        |
| CDS Contacts V2 (Vendor)                | contacts                        |
| Customers V3                            | contacts                        |
| Withholding tax codes                   | msdyn_withholdingtaxcodes       |
| Vendors V2                              | msdyn_vendors                   |
| Vendor payment method                   | msdyn_vendorpaymentmethods      |
| Vendor groups                           | msdyn_vendorgroups              |
| Chart of accounts                       | msdyn_chartofaccountses         |
| Sales tax ledger posting groups V2      | msdyn_taxpostinggroups          |
| Item sales tax group                    | msdyn_taxitemgroups             |
| Sales tax groups                        | msdyn_taxgroups                 |
| Sales tax exempt code entity CDS        | msdyn_taxexemptcodes            |
| Customer groups                         | msdyn_customergroups            |
| Customer payment method                 | msdyn_customerpaymentmethods    |
| Financial dimensions                    | msdyn_dimensionattributes       |
| Sales tax authorities                   | msdyn_taxauthorities            |
| Financial dimension format              | msdyn_financialdimensionformats |
| Fiscal calendar period                  | msdyn_fiscalcalendarperiods     |
| Fiscal calendar integration entity      | msdyn_fiscalcalendars           |
| Fiscal calendar year integration entity | msdyn_fiscalcalendaryears       |
| Terms of payment                        | msdyn_paymentterms              |
| Payment schedule                        | msdyn_paymentschedules          |
| Payment schedule lines                  | msdyn_paymentschedulelines      |
| Payment days CDS                        | msdyn_paymentdays               |
| Payment day lines CDS V2                | msdyn_paymentdaylines           |
| Main account                            | msdyn_mainaccounts              |
| Main account categories                 | msdyn_mainaccountcategories     |
| Ledger                                  | msdyn_ledgers                   |
| Customers V3                            | accounts                        |

**Dependency information:** Dual-write Application Core package



## Dual-write Notes

Dual-write Notes package contains solutions and maps necessary to sync notes or annotations data. It contains 4 solutions namely:

| Unique Name                  | Display Name                                               |
|------------------------------|------------------------------------------------------------|
| Dynamics365Notes             | Dynamics 365 Notes                                         |
| Dynamics365NotesExtended     | Dynamics 365 Notes Extended                                |
| msdyn_Dynamics365NotesMaps   | Dynamics 365 Dual Write Applications Notes Entity Maps     |
| msdyn_Dynamics365NotesAnchor | Dynamics 365 Dual Write Applications Notes Anchor solution |

Following are the maps available on this package:

| Finance and Operations                     | Customer Engagement |
|--------------------------------------------|---------------------|
| Sales order header document attachments    | annotations         |
| Customer Attachments                       | annotations         |
| Vendor document attachments                | annotations         |
| Purchase order header document attachments | annotations         |

**Dependency information:**

-   Dual-write Application Core package

-   Dual-write Finance and Extended package



## Dual-write Asset Management

Dual-write Asset Management package contains solutions and maps necessary to sync assets data from Dynamics 365 Supply Chain data or Dynamics 365 Field Service data. It contains 4 solutions namely:

| Unique Name                          | Display Name                                                          |
|--------------------------------------|-----------------------------------------------------------------------|
| Dynamics365AssetManagement           | Dynamics 365 Asset Management                                         |
| Dynamics365AssetManagementApp        | Dynamics365 Asset Management App                                      |
| msdyn_DualWriteAssetManagementMaps   | Dual Write Applications Asset Management Entity Maps                  |
| msdyn_DualWriteAssetManagementAnchor | Dynamics 365 Dual Write Applications Asset Management solution Anchor |

Following are the maps available on this package:

| Finance and Operations                                | Customer Engagement                     |
|-------------------------------------------------------|-----------------------------------------|
| Asset management warranty                             | msdyn_warranties                        |
| Asset management models                               | msdyn_models                            |
| Asset management manufacturers                        | msdyn_manufacturers                     |
| Asset management functional location types            | msdyn_functionallocationtypes           |
| Asset management functional locations                 | msdyn_functionallocations               |
| Asset management functional location lifecycle states | msdyn_functionallocationlifecyclestates |
| Asset management functional location lifecycle models | msdyn_functionallocationlifecyclemodels |
| Asset management assets                               | msdyn_customerassets                    |
| Asset management asset types                          | msdyn_customerassetcategories           |
| Asset management asset lifecycle states               | msdyn_assetlifecyclestates              |
| Asset management asset lifecycle models               | msdyn_assetlifecyclemodels              |

**Dependency information:** Dual-write Application Core package


