---
title: What's new or changed in dual-write
description: Access links to the release plans, major announcements, and documentation for dual-write, including a table that provides descriptions and number for various bug types.
author: jaredha
ms.author: jaredha
ms.topic: whats-new
ms.date: 10/04/2024
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: 10.0.8
---

# What's new or changed in dual-write

[!include [banner](../../includes/banner.md)]

Dual-write is an out-of-box infrastructure that provides near-real-time interaction between customer engagement apps in Microsoft Dynamics 365 and finance and operations apps. To get started with dual-write, see the [Dual-write home page](dual-write-home-page.md).

## September 2024

### Security update 

| Feature | Description | Status |
|---|---|---|
|Security update |Security enhancements affecting service bus, table storage and blobs impacting the Dynamics 365 finance and operations and Dual-write core solutions.<br>The security fixes are mandatory. By November 30, 2024, all customers using Dual-write are required to upgrade. <ul><li>PU63 Minimum platform version 7.0.7198.188 or PU64 Minimum platform version 7.0.7279.121.</li><li>Dual-write core solution version in Dataverse - 1.0.24073.3.</li></ul><br>If the upgrade isn't enabled by the November 30 2024, the Dual-write pause and resume and auto-alerts features won't function. These features haven't changed in functionality but are more secure.|General availability|


## June 2024

### Global address book

The June regular release of Dual-write GAB solution 3.5.2.131 contains the following bug fixes.

| Feature | Description | Status |
|---|---|---|
|Bug fix |Fix for creating contacts with last name greater than 25 characters, CE isn't able to create a party record due to disparity between the allowed max field length between contact and party entity.	|General availability|
|Bug fix|	Removed **Add existing postal address** from **Postal address** tab, sharing postal addresses between parties isn't supported. In some specific cases, like contact for party creation.|	General availability|

#### GAB solution details

| Solution name | Has new changes? | Previous version | New version |
|---|---|---|---|
| Party | Yes | 3.5.2.52 | 3.5.2.89 |
| Dynamics365GABExtended | Yes | 3.5.2.52| 3.5.2.89 |
| Dynamics365GABDualWriteEntityMaps | Yes | 3.5.2.52| 3.5.2.89 |
| Dynamics365GABPartyAnchor |Yes | 3.5.2.52| 3.5.2.89|
| Dynamics365GABPartyCommon | Yes | 3.5.2.52 | 3.5.2.89 |


## March 2024
Release notes for March 2024 releases of [Dual-write core solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).<br>

### Version 1.0.24031.1

| Type | Number | Description | Status | 
| --- | --- | --- | --- |
| Bug | 3833504 | Critical bug fix for asynchronous processing with Dual-write. | General availability |
| Bug | 3801381 | Bug fixes and code enhancements for the data synchronization pipeline between finance and operations apps and Dataverse. | General availability | 
| Bug | 25500975 | <ul><li>Optimizing fetch for non-relational database tables to improve data sync performance between finance and operations apps and Dataverse.</li><li> Correcting column values for msdyn_datasyncexecutionsummary_elastic, sourceType, update count, and error count.</li></ul>  | General availability |

### Global address book

The March regular release of Dual-write GAB solution 3.5.2.52 contains the following bug fixes.

| Feature | Description | Status |
|---|---|---|
| Sales order page enhancements | Restrict the creation of ship-to and bill-to addresses by locking the address fields on the sales order page. Customers are expected to select these addresses from the existing postal address entity by using the **Choose ship/bill to address** lookup fields that are attached to the **Order** page. A new shipping/billing address can be created by using the quick create new postal address page option in the same lookup field. | General availability |
| **Postal address** tab on accounts and contacts pages | Add the postal address component as a new tab on the **Account and contact** page. The **Customer address** tab is kept as is. The postal address entity that's introduced in Dual-write GAB solutions has no customization restrictions. Customers can create lookups to custom entities. They can also create country/region, county, and state/province entities, implement lookup filtering, and easily validate addresses in Dataverse. Customers who want to continue to use the customer address for address input can hide the existing **Address** tab or the new **Postal address** tab. | General availability |
| Xmultiple for performance | Optimize the existing logic in Dataverse that creates customer addresses during the initial/live synchronization of customer records from postal addresses. This optimization increases the synchronization record capacity and prevents plugin time-outs, especially when a large number of addresses are associated with customers. | General availability |
| Bug fix | Enable postal address records to be created from the **Postal address** main page. Previously, postal addresses could be created only by using the postal address quick create page or the quick view page that's attached to the **Postal address** tab on the party page. | General availability |
| Enhancement | Restrict customization of Microsoft global address book (GAB) business rules to help prevent data corruption. | General availability |
| Bug fix | Fix an issue with the creation of a contact via the marketing app page. Because of a depth limitation, only the party was created. The plugin couldn't create the corresponding contact entity record. | General availability |
| Bug fix | Fix the update of postal addresses when the corresponding customer address is updated and the name is longer than 60 characters. The **Postal address name** field has a limit of 60 characters. This limit is now validated and truncated via GAB plugins. | General availability |

#### GAB solution details

| Solution name | Has new changes? | Previous version | New version |
|---|---|---|---|
| Party | Yes | 3.5.2.35 | 3.5.2.52 |
| Dynamics365GABExtended | Yes | 3.5.2.35 | 3.5.2.52 |
| Dynamics365GABDualWriteEntityMaps | Yes | 3.5.2.35| 3.5.2.52 |
| Dynamics365GABPartyAnchor |Yes | 3.5.2.35 | 3.5.2.52 |
| Dynamics365GABPartyCommon | Yes | 3.5.2.35 | 3.5.2.52 |

### Global address book
The March release of Dual-write GAB solution 3.5.2.35 contains the following bug fixes.

| Feature | Description | Status |
| ---|---|---|
|Bug fix |Dataverse solutions must be CAB based by August 21st.|	General availability|
|Bug fix |Dual-write Global address book plugin county isn't propagated properly in CE|	General availability|

#### GAB solution details

| Solution name | Has new changes? | Previous version | New version |
|---|---|---|---|
| Party | Yes | 3.5.2.2 | 3.5.2.35 |
| Dynamics365GABExtended | Yes | 3.5.2.2 | 3.5.2.35 |
| Dynamics365GABDualWriteEntityMaps | Yes | 3.5.2.2| 3.5.2.35 |
| Dynamics365GABPartyAnchor |Yes | 3.5.2.2 | 3.5.2.35 |
| Dynamics365GABPartyCommon | Yes | 3.5.2.2 | 3.5.2.35 |

## January 2024
Release notes for January 2024 releases of [Dual-write core solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).<br>

### Version 1.0.24014.1

| Type | Number | Description | Status | 
| --- | --- | --- | --- |
| Feature | 3786097 | Provide more actionable error messages to users in Dataverse in cases of system errors from finance and operations apps during live sync. | General availability |
| Bug | 3782920 | Optimize asynchronous integration job operations for performance improvements | General availability |
| Bug | 3771402 | Optimize asynchronous integration job operations for performance improvements | General availability |

**Release timeline for version 1.0.24014.1**

| Geography | Package publish date | Publisher-driven update|
| --- | --- | --- |
| First Release | January 29, 2024 | February 5, 2024 | 
| Brazil, Canada, India, France, Africa, Germany, Switzerland, Norway, Korea, Singapore | February 5, 2024 | February 12, 2024 |
| UAE, Japan, Asia, Australia, UK | February 12, 2024 | February 19, 2024 | 
| Europe | February 19, 2024 | February 26, 2024 | 
| North America | February 26, 2024 | March 4, 2024 | 
| GCC | March 4, 2024 | March 11, 2024 | 

### Version: 1.0.24011.1

| Type | Number | Description | Status | 
| --- | --- | --- | --- |
| Bug | 1045001 | Allow customized views of `Dual Write Async Execution Summary` and `Dual Write Async Execution Error` tables. | General availability |
| Bug | 25981168 | Update the SourceKey in `Dual Write Async Execution Error` table with the Dataverse RowVersion for sync from Dataverse to finance and operations apps. | General availability |
| Bug | 3679902 | Update `Dual Write Async Execution Summary` table with Enqueue Count | General availability |
| Bug | 3761962 | Fix for issue with queued records for asynchronous integration jobs not displaying correctly in the dual-write configuration interface. | General availability |

## December 2023

### Dual-write core
Release notes for the December 2023 release of [Dual-write core solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).<br>
**Version:** 1.0.23114.1

| Type | Number | Description | Status | 
| --- | --- | --- | --- |
| Feature | 3620696 | Performance improvement in dual-write plugins by reducing the number of calls to the linked finance and operations apps environment. | General availability |
| Bug fix | 3603874 | Fix for custom date field transformation from Dataverse to finance and operations apps environment during live sync. The GetTransformedValue method in the dual-write plugin returns a null value for unrecognized transform types instead of the passed in values. | General availability |
| Optimization | N/A | Minor security improvements and updates | General availability | 

**Version:** 1.0.23121.1

Other December updates in version 1.0.23121.1 of the Dual-write core solution include minor fixes for asynchronous integration jobs for dual-write.

| Type | Number | Description | Status | 
| --- | --- | --- | --- |
| Update | 3730825 | Remove tables used for tracking reconciliation status and optimize the related API. | General availability |

### Global address book
The December release of Dual-write GAB solution 3.5.2.2 contains the following bug fixes.

| Feature | Description | Status |
| ---|---|---|
|Bug fix |	Dual-write initial sync creates multiple active postal addresses on the same location ID.|	General availability|

#### GAB solution details

| Solution name | Has new changes? | Previous version | New version |
|---|---|---|---|
| Party | Yes | 3.5.1.135 | 3.5.2.2 |
| Dynamics365GABExtended | Yes | 3.5.1.135 | 3.5.2.2 |
| Dynamics365GABDualWriteEntityMaps | Yes | 3.5.1.135 | 3.5.2.2 |
| Dynamics365GABPartyAnchor |Yes | 3.5.1.135 | 3.5.2.2 |
| Dynamics365GABPartyCommon | Yes | 3.5.1.135 | 3.5.2.2 |


## November 2023 
The November release of Dual-write Supply Chain solution 2.3.4.265 contains the following bug fixes.

| Feature | Description | Status |
| ---|---|---|
|Bug fix | ATP Information is returning incorrect site/warehouse results in CE.	|General availability |
|Bug fix | When you create a sales order in CE, an inactive price list is selected. |General availability |
|Bug fix | The warning message **Feature management states map not running** shouldn't be displayed if no quotation map is running. |General availability |
|Bug fix | Ensure dual write supply chain solution is compatible with an important Dual-write platform fix. |General availability |

### Solution details

| Solution name | Has new changes? | Previous version | New version |
|---|---|---|---|
| Dynamics365SupplyChainExtended | Yes | 2.3.4.203 | 2.3.4.265 |
| msdyn_Dynamics365SupplyChainExtendedMaps | Yes | 2.3.4.203 | 2.3.4.265 |
| msdyn_Dynamics365SupplyChainExtendedAnchor | Yes | 2.3.4.203 | 2.3.4.265 |

The November release of Dual-write Asset Management solution 2.2.2.101 contains the following bug fixes.

| Feature | Description | Status |
| ---|---|---|
|Bug fix | Ensure dual write asset management solution is compatible with an important Dual-write platform fix. |General availability |

### Solution details

| Solution name | Has new changes? | Previous version | New version |
|---|---|---|---|
| Dynamics365AssetManagement | Yes | 2.2.2.52 | 2.2.2.101 |
| Dynamics365AssetManagementApp | Yes | 2.2.2.52 | 2.2.2.101 |
| msdyn_DualWriteAssetManagementMaps | Yes | 2.2.2.52 | 2.2.2.101 |
| msdyn_DualWriteAssetManagementAnchor | Yes | 2.2.2.52 | 2.2.2.101 |

## October 2023 
The October release of Dual-write GAB solution 3.5.1.135 contains the following bug fixes.

| Feature | Description | Status |
| ---|---|---|
|Bug fix | Address primary flag removed in Customer experience when adding contacts.	|General availability |

### Solution details

| Solution name | Has new changes? | Previous version | New version |
|---|---|---|---|
| Party | Yes | 3.5.1.102 | 3.5.1.135 |
| Dynamics365GABExtended | Yes | 3.5.1.102 | 3.5.1.135 |
| Dynamics365GABDualWriteEntityMaps | Yes | 3.5.1.102 | 3.5.1.135 |
| Dynamics365GABPartyAnchor |Yes | 3.5.1.102 | 3.5.1.135 |
| Dynamics365GABPartyCommon | Yes | 3.5.1.102 | 3.5.1.135 |


## September 2023
Release notes for the September 2023 release of [Dual-write core solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).<br>
**Version:** 1.0.23084.2

| Type | Number | Description | Status | 
| --- | --- | --- | --- |
| Feature | 24811690 | When resuming a paused dual-write map it's possible that processing queued records before resuming live synchronization can take longer than expected. There's now the option to skip directly to live synchronization of new records when resuming the map, and either move the queued records to asynchronous processing in the **Catch-up errors** list, or discard the queued records.<br><p><br>For more information, see [Pause dual-write for maintenance](./pause-for-maintenance.md). | General availability |
| Bug fix | 3548103 | This update fixes an issue in which the dual-write runtime throws the below error message if the description field has data but the length of the data is less than the length in the truncate function.<br><p><br>"Index and length must refer to a location within the string." | General availability |

## August 2023

Release notes for the August 2023 release of [Dual-write core solution 1.0.23084.0](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write). 

> [!NOTE]
> Beginning with this release there's a new naming convention for version numbers of the dual-write core solution. The format of the version number is **1.0.YYMMW.versionNumber**, where "YYMMW" are the calendar year, month, and week in which the version build is created. The "versionNumber" is **0** by default. With this change we also introduce a more consistent cadence in version rollouts for the dual-write core solution.

| Feature | Description | Status |
| ---|---|---|
| Bug fix | Fix for reported bug in Authentication for the dual-write core plugin. | General availability |

In addition to the above fixes, the following new objects are also included in the dual-write core solution in this release. These objects are related to the asynchronous processing for dual-write, which is a feature coming in a future release. The complete feature isn't yet available. These new objects are added to the environment in this release, but are nonfunctional until the full asynchronous processing feature is available.

| Display name | Name | Type |
| --- | --- | --- |
| AsyncDataEnqueueOperation | AsyncDataEnqueueOperation | Custom API |
| DataSyncAction | DataSyncAction | Custom API |
| DataSyncEntityOperation | DataSyncEntityOperation | Custom API |
| DataSyncExecutionRequest | DataSyncExecutionRequest | Custom API Request Parameter |
| DataSyncExecutionResponse | DataSyncExecutionResponse | Custom API Response Property |
| DataSyncPayload | DataSyncPayload | Custom API Request Parameter |
| Dual Write Async Execution Partition Map Status | msdyn_dualwriteasyncexecutionpartitionmapstatus | Table |
| Dual Write Async Processing Range | msdyn_dualwriteasyncprocessingrange | Table |
| msdyn_datasyncexecutionerror | msdyn_datasyncexecutionerror | Table |
| msdyn_datasyncexecutionsummary | msdyn_datasyncexecutionsummary | Table |
| msdyn_datasyncexecutionsummary_elastic | msdyn_datasyncexecutionsummary_elastic | Table |
| TriggerDataSyncAction | TriggerDataSyncAction | Custom API |


## July 2023 release

The July 2023 release of [Dual-write core solution 1.0.42.1](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write) rolls out in mid July with the following bug fixes and optimizations.

| Feature | Description | Status |
| ---|---|---|
| Bug fix | Fix for Dataverse organizations connected to finance and operations cloud hosted development environments (CHE) using Full Trust Plugins with FinOpsConnectors for token generation. | General availability |
| Optimization | Improvements in token generation code for Full Trust Plugins | General availability |
| Exception handling | Added custom exceptions (DualWritePluginException and DualWriteApplicationException) to separate plugin exceptions from application exceptions | General availability |

## June 2023 release

The June release of Dual-write Global Address Book solution 3.5.1.91 contains the following bug fixes.

| Feature | Description | Status |
|---|---|---|
| Bug fix | CRM workflow performance fix to add another check on update calls. | General availability |
| Bug fix | Updates to the account entity during creation by the CreateVendorsinVendorsTable workflow are causing performance issues. | General availability |
|Bug fix	| Postal address records not created in few cases as address composite fields are null while creation of address via accounts/contacts.	| General availability

The June 2023 release of the Dual-write Supply Chain solution contains the following changes.

| Feature | Description | Status |
|---|---|---|
| Feature | [Add efficiency in quote-to-cash with Dynamics 365 Sales.](../../../fin-ops/data-entities/add-efficiency-in-quote-to-cash-concept.md) | General availability |
| Feature | [Set the default ownership for all sales quotations.](../../../fin-ops/data-entities/add-efficiency-in-quote-to-cash-use.md#default-ownership) | General availability |
| Feature	| [Change ownership for a sales quotation.](../../../fin-ops/data-entities/add-efficiency-in-quote-to-cash-use.md#change-ownership-for-a-sales-quotation)	| General availability |
| Feature	| [Make Supply Chain Management the price master.](../../../fin-ops/data-entities/add-efficiency-in-quote-to-cash-use.md#scm-price-master)	| General availability |
| Feature	| [Calculate and push prices, discounts, and totals from Supply Chain Management to Sales.](../../../fin-ops/data-entities/add-efficiency-in-quote-to-cash-use.md#push-to-sales)	| General availability |
| Feature	| [Copy Supply Chain Management sales quotation data to sales orders synced from Sales.](../../../fin-ops/data-entities/add-efficiency-in-quote-to-cash-use.md#copy-quotation-data)	| General availability |
| Feature	| [Process events related to Sales integration.](../../../fin-ops/data-entities/add-efficiency-in-quote-to-cash-use.md#process-events)	| General availability |

### Solution details

| Solution name | Has new changes? | Previous version | New version |
|---|---|---|---|
| Party | Yes | 3.5.1.87 | 3.5.1.91 |
| Dynamics365GABExtended | Yes | 3.5.1.87 | 3.5.1.91 |
| Dynamics365GABDualWriteEntityMaps | Yes | 3.5.1.87 | 3.5.1.91 |
| Dynamics365GABPartyAnchor |Yes | 3.5.1.87 | 3.5.1.91 |
| Dynamics365GABPartyCommon | Yes | 3.5.1.87 | 3.5.1.91 |
| Dynamics365SupplyChainExtended | Yes | 2.3.4.99 | 2.3.4.203 |
| msdyn_Dynamics365SupplyChainExtendedMaps | Yes | 2.3.4.99 | 2.3.4.203 |
| msdyn_Dynamics365SupplyChainExtendedAnchor | Yes | 2.3.4.99 | 2.3.4.203 |

## May 2023 release

The May release of the Dual-write Global Address Book solution 3.5.1.87 contains the following bug fixes.

| Feature | Description | Status |
|---|---|---|
| Bug fix | Contact for **Customer**, **Vendor**, and **Associate organizations** tab fix. | General availability |
| Bug fix | "Object reference not set to an instance of an object" error when the party postal address is updated. | General availability |
| Bug fix | **Add existing** button in the subgrid for multiple entities. | General availability |
| Bug fix | **County** field isn't correctly moved to the customer address in customer engagement apps when it's set in finance and operations apps. | General availability |

## March 2023 release 

The March release of [Dual-write core solution 1.0.41.0](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write) contains monthly security updates. It includes the following bug fixes. The rollout is starting mid March.

| Feature | Description | Status |
|---|---|---|
| Bug | Require more exception handling to PostCommit plugin. | General availability |
|Bug fix|	When you update the postal address page, the street field wasn't concatenating correctly when the street 2 field wasn't populated. |General availability|
|Bug fix|	Fixed the GAB plugin for creation of account. The **Search name** field in Dataverse won't be overwritten at CREATE if the search name is different than the name.|	General availability|
|Bug fix	|Prevent the deactivation of primary postal address and customer addresses in Customer engagement to match functionality with finance and operations and avoid data corruption.|	General availability|
|Bug fix|	When you create an account with the same party and filling a different electronic address on the **Details** tab, duplicate electronic addresses were created.|	General availability|

### Solution details

| Solution name | Has new changes? | Previous version | New version |
|---|---|---|---|
|Party|	Yes|	3.5.1.55	|3.5.1.76|
|Dynamics365GABExtended	|Yes|	3.5.1.55	|3.5.1.76|
|Dynamics365GABDualWriteEntityMaps|	Yes|	3.5.1.55|	3.5.1.76|
|Dynamics365GABPartyAnchor	|Yes	|3.5.1.55	|3.5.1.76|
|Dynamics365GABPartyCommon	|Yes|	3.5.1.55	|3.5.1.76|



## February 2023 release 

The February release of [Dual-write core solution 1.0.40.0](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write) contains monthly security updates. It includes the following bug fixes. 

| Feature | Description | Status |
|---|---|---|
| Bug | Handle Azure resource throttling during live-sync. | GA |

## January 2023 release 

The January release of [Dual-write core solution 1.0.39.0](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write) contains monthly security updates. It doesn't include customer facing bug fixes or features. 

## November 2022 release 

The November release of [Dual-write core solution 1.0.38.0](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write) contains monthly security updates. It doesn't include customer facing bug fixes or features. 

## October 2022 release 

The October release of [Dual-write core solution 1.0.37.0](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write) contains the following changes.

| Feature | Description | Status |
|---|---|---|
| Bug | Before this release, dual-write platform core plugins on the Dataverse side are triggered every time a record is updated regardless of the updated field was in dual-write map or not. As a result, it created performance overhead on all database operations of Dataverse. With this release, dual-write plugins on the Dataverse side triggers only when the updated field is in dual-write map. [Learn more](data-sync-for-map-fields.md) | Preview |

The October release of Dual-write Global Address Book solution 3.5.1.55 contains the following bug fixes.

| Feature | Description | Status |
|---|---|---|
| Bug fix | An OnLoad error occurred when the **Contact for Party** page was used to create a new record in **Contact for Customer or Vendor**. | General availability |
| Bug fix | During some lead qualification scenarios, the postal address and electronic address weren't being synced from the contact entity to the party entity. Global address book plug-ins weren't being invoked in these scenarios. | General availability |
| Error handling | Provide an actionable error message if a company ID isn't included on the **Account** page. | General availability |
| Bug fix | The street information on the **Address** page wasn't shown correctly in the **Street** field on the **Postal address** page if **Street 2** information wasn't present. | General availability |
| Bug fix | County information for the customer address wasn't synced between finance and operations apps and customer engagement apps. Global address book plug-ins were corrected to address this issue. | General availability |

## August 2022 release

The August release of Dual-write Global Address Book solution 3.5.1.22 contains the following bug fixes.

| Feature | Description | Status |
|---|---|---|
| Bug fix | Contacts that were created from the marketing portal and during the lead qualification scenario didn't have a valid party ID. | General availability |
| Bug fix | Fixed the following error that occurred when a contact was created from CRM portals: "The 'contact' entity must be in the default (null) or unchanged state." | General availability |

### Solution details

| Solution name | Has new changes? | Previous version | New version |
|---|---|---|---|
| Party | Yes | 3.5.1.22 | 3.5.1.55 |
| Dynamics365GABExtended | Yes | 3.5.1.22 | 3.5.1.55 |
| Dynamics365GABDualWriteEntityMaps | Yes | 3.5.1.22 | 3.5.1.55 |
| Dynamics365GABPartyAnchor | Yes | 3.5.1.22 | 3.5.1.55 |
| Dynamics365GABPartyCommon | Yes | 3.5.1.22 | 3.5.1.55 |

## July 2022 release 

The July release of [Dual-write core solution 1.0.36.0](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write) contains the following changes.

| Feature | Description | Status |
|---|---|---|
| Feature | Enable a five-minute session time-out window for power platform integrated dual-write environments | General availability |

The July release of Dual-write Global Address Book solution 3.5.1.6 contains the following bug fixes.

| Feature | Description | Status |
|---|---|---|
| Bug fix | Update the Postal address table when an address is updated in the Marketing portal. | General availability |
| Bug fix | Fix the time zone conversion for addresses that have an expiration date of **Never** when a date is passed from customer engagement apps to finance and operations apps. | General availability |

### Solution details

| Solution name | Has new changes? | Previous version | New version |
|---|---|---|---|
| Party | Yes | 3.5.0.1 | 3.5.1.6 |
| Dynamics365GABExtended | Yes | 3.5.0.1 | 3.5.1.6 |
| Dynamics365GABDualWriteEntityMaps | Yes | 3.5.0.1 | 3.5.1.6 |
| Dynamics365GABPartyAnchor | Yes | 3.5.0.1 |3.5.1.6 |
| Dynamics365GABPartyCommon | Yes | 3.5.0.1 | 3.5.1.6 |

## June 2022 release

The June release of [Dual-write core solution 1.0.35.0](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write) contains the following features and bug fixes.

| Feature | Description | Status |
|---|---|---|
| Bug fix | Fixes a bug where dual-write fails for incorrectly formatted table look-ups that have a missing look-up attribute value in the transform. | General availability |
| Error handling | Provides an actionable error message for an invalid authentication failure during the setup from Microsoft Dynamics Lifecycle Services (LCS) or Power Platform admin center. | General availability |
| Performance | Manages the dual-write plug-ins volume and removes outdated plug-ins from the environment. | General availability |
| Bug fix | The dual-write plug-in time-out duration is now synchronized with the finance and operations live sync time-out duration. Therefore, the dual-write transaction commit must succeed on both sides within a two-minute window. Otherwise, it fails on both sides. | General availability |
| Compliance | For compliance reasons, when entity maps are paused in dual-write, the data is stored for only 24 hours. Administrators are requested to run the maps within 24 hours. | General availability |

## April 2022 release

The April release of Dual-write Party and Global Address Book Solutions 3.5.0.1 contains the following features and bug fixes.

| Feature | Description | Status |
|---|---|---|
| Address roles dropdown | Addresses can be classified as invoice addresses, business addresses, home addresses, and so on, through address purposes or roles. In this release, we're replacing the address roles text field with a Power Apps Component Framework (PCF) control that is a multi-select option set. This new control lets you select one or more address roles to assign to a given address. The drop-down list is available for both postal addresses and electronic addresses. | General availability |
| Bug fix | Updates to electronic address fields on the Account table (email, phone, fax) should update the primary electronic address in the msdyn_partyelectronicaddress table. | General availability |
| Bug fix | Updates to electronic address fields on the Contact table (email, phone, fax) should update the primary electronic address in the msdyn_partyelectronicaddress table. | General availability |
| Bug fix | Show the primary contact name for the primary contact that is selected on the **Associated contacts** tab on account, contact, and vendor pages. | General availability |
| Bug fix | Initial synchronization of accounts/contacts isn't creating electronic addresses in accounts/contacts tables, even though electronic addresses are created on the **Electronic addresses** tab (msdyn_partyelectronicaddress table). | General availability |
| Bug fix | Addresses of accounts aren't available under **Ship To/Bill To address** on the quote page after the address is updated for the accounts in finance and operations apps. | General availability |
| Bug fix | Fix the duplicate address record error that occurs while new addresses are created in the Customer Address table in Dataverse. | General availability |
| Bug fix | Fix a language transformation issue that occurs on party records when the **en-us** language is selected in Dataverse. | General availability |
| Bug fix | Fixed the error ("The length of the 'msdyn_firstname' attribute of the 'msdyn_vendor' entity exceeded the maximum allowed") that occurred during update of account records if the workflows for data synchronization between the accounts and msdyn_vendor tables are activated. | General availability |
| Bug fix | Fixed the error ("The 'customeraddress' entity must be in the default (null) or unchanged state") that occurred when the address for an account was created from CRM portals. | General availability |

### Solution details

| Solution name | Has new changes? | Previous version | New version |
|---|---|---|---|
| Party | Yes | 3.3.0.5 | 3.5.0.1 |
| Dynamics365GABExtended | Yes | 3.3.0.5 | 3.5.0.1 |
| Dynamics365GABDualWriteEntityMaps | Yes | 3.3.0.5 | 3.5.0.1 |
| Dynamics365GABPartyAnchor | Yes | 3.3.0.5 | 3.5.0.1 |
| Dynamics365GABPartyCommon | Yes | 3.3.0.5 | 3.5.0.1 |

This release includes the following map changes:

+ Apply the latest map version 1.0.0.2 for the CDS Parties - msdyn_parties map.
+ Run the initial synchronization of the CDS Address roles - msdyn_addressroles map so that all the address role information is synced from finance and operations apps to Dataverse. This map is a new dual-write map that was added as part of this release. No subsequent updates/additions are allowed with this map, because the finance and operations entity for address roles is read only.


## March 2022 release

The March 2022 release of the [Dual-write Supply Chain solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwscm) contains the following changes.

| Feature | Description | Status |
|---|---|---|
| Bug fix | In customer engagement apps, sales quotations with write-in product lines can't generate an order because the sales product category isn't mapped. | General availability |
| Bug fix | The ISO currency code for quotes isn't properly set after a revision. | General availability |

### Solution details

|Solution name | Has new changes? | Previous version | New version |
|---|---|---|---|
| CurrencyExchangeRates | No | 2.2.2.5 | 2.2.2.5 |
| Dynamics365Company | No | 2.2.2.5 | 2.2.2.5 |
| Dynamics365FinanceAndOperationsCommon | No | 2.2.2.50 | 2.2.2.50 |
| Dynamics365FinanceExtended | No | 2.3.1.15 | 2.3.1.15 |
| Dynamics365SupplyChainExtended | Yes | 2.3.3.2 | 2.3.4.3 |
| Dynamics365AssetManagement | No | 2.0.777.68 | 2.0.777.68 |
| Dynamics365AssetManagementApp | No | 2.2.1.23 | 2.2.1.23 |
| Dynamics365Notes | No | 2.2.2.23 | 2.2.2.23 |
| Dynamics365FinanceAndOperationsDualWriteMaps | No | 2.3.0.35 | 2.3.0.36 |
| Dynamics365FinanceAndOperationsAnchor | No | 2.3.3.2 | 2.3.4.3 |

## January 2022 release

The January 2022 release of [Dual-write core version 1.1.33](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write) contains the following changes.

| Feature | Description | Status |
|------|---------|-------|
| Performance| Improves performance of Microsoft Dataverse entity retrieval. | General availability |
| Tracing| Limits excess trace logs during entity handling. | General availability |

The January 2022 release of Dual-write application orchestration solution version 2.3.3.2 contains the following bug fixes.

| Feature | Description | Status |
|------|---------|-------|
| Bug fix| In the customer engagement apps, the quote line information form filters warehouses by site, instead of by company. | General availability |
| Bug fix| In finance and operations apps, when a product is released without an item model group set, the operation fails due to a blank value being set for the **FieldServiceProductType** attribute in customer engagement apps. This is fixed by allowing the **FieldServiceProductType** attribute to allow a “NotAvailable” value. | General availability |
| Bug fix| When Dataverse sends an updated sales price of 0.00, it doesn't get updated in finance and operations apps. | General availability |

This release includes one map change named [CDS released distinct products] - [products]. In order to take the map changes, apply "Dynamics365FinanceAndOperationsDualWriteMaps" solution version 2.3.3.2 and update the [CDS released distinct products] - [products] map to version 1.0.0.3.

### Solution details

|Solution name | Has new changes? | Previous version | New version |
|--------------|--------------|--------------|--------------|
|CurrencyExchangeRates|No|2.2.2.5|2.2.2.5|
|Dynamics365Company|No|2.2.2.5|2.2.2.5|
|Dynamics365FinanceAndOperationsCommon|No|2.2.2.50|2.2.2.50|
|Dynamics365FinanceExtended|No|2.3.1.15|2.3.1.15|
|Dynamics365SupplyChainExtended|Yes|2.3.1.15|2.3.3.2|
|Dynamics365AssetManagement|No|2.0.777.68|2.0.777.68|
|Dynamics365AssetManagementApp|No|2.2.1.23|2.2.1.23|
|Dynamics365Notes|No|2.2.2.23|2.2.2.23|
|Dynamics365FinanceAndOperationsDualWriteMaps|Yes|2.3.0.15|2.3.3.2|
|Dynamics365FinanceAndOperationsAnchor|No|2.3.1.15|2.3.3.2|

## November 2021 release of party and global address book

The November 2021 release of Dual-write Party and Global Address Book Solutions 3.3.0.5 contains the following features and bug fixes.

| Feature | Description | Status |
|------|---------|-------|
| [Single view for party](view-party.md)| We're providing a new form to access Party data. The **Party** form provides the capability to view and manage party records along with all the associated customers, contacts, and vendors and their postal addresses and electronic addresses from a single form.| General availability |
| Bug fix| On the **Accounts** form, postal address updates from the **Summary** tab don't synchronize, which causes a data mismatch between Microsoft Dataverse and finance and operations apps. | General availability |
| Bug fix| When an electronic address is changed from nonprimary to primary, the updates to the telephone extension/description fields don't synchronize from msdyn_partyelectronicaddress to **Contact** table.  | General availability |
| Bug fix| Error while updating the **Gender** field on a Contact record to "nonspecific" in finance and operations apps. | General availability |
| Bug fix| In finance and operations apps, during address creation, when a second address is marked as primary and saved, the IsPrimary value change doesn't reflect in Dataverse. | General availability |

## September 2021 release of party and global address book 

The September 2021 hotfix release of [Dual-write Party and Global Address Book Solutions 3.1.0.4](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwgabsln) is based on [Dual-write core solution version 1.0.29](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).

This release contains bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Bug fix| Some client APIs were deprecated and replaced with new APIs. The JavaScript code is upgraded to use the new client APIs.| General availability |
| Bug fix| Portals registration using email address fails when last name isn't supplied. | General availability |
| Bug fix| Unable to create a new postal address for a vendor.| General availability |

### Solution details

|Solution name | Has new changes? | Previous version | New version |
|--------------|--------------|--------------|--------------|
|Party|Yes|3.1.0.2|3.2.0.4|
|Dynamics365GABExtended|Yes|3.1.0.2|3.2.0.4|
|Dynamics365GABDualWriteEntityMaps|Yes|3.1.0.2|3.1.0.2|
|Dynamics365GABPartyAnchor|Yes|3.1.0.2|3.2.0.4|

## August 2021 release

The August 2021 release of Dual-write application orchestration solution version 2.3.0.15 is based on [Dual-write core solution version 1.0.29](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).  

This release contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
|Bug fix | Fixes the case where dual-write alerts fail to send. | 	General availability |
| System tables |	Adds support for enabling dual-write for system tables. |	General availability |
|Bug fix | Some client APIs were deprecated and replaced with new APIs. The JavaScript code in the dual-write orchestration package was upgraded to use the new client APIs.| 	General availability |
|Bug fix | Because dual-write doesn’t support offline mode, the company name doesn't automatically contain a default value. You must select the company manually.| 	General availability |
 |Bug fix | The **Vendor** group field on the **Accounts** form doesn't filter values based on the selected company.| 	General availability |
|Bug fix | Saving a **Vendor** record in a finance and operations app fails with the error message *Can't convert the literal '' to the expected type 'Edm.Int32'*. | 	General availability |
|Bug fix | The transformation on the **Vendor payment method** map required an update. The enumeration on the **PAYMENTSTATUS** field is incorrect resulting in error message *Can't convert the literal 'Confirmed' to expected type 'Edm.Int32'*. | 	General availability |
|Bug fix | **Sales order header** and **Sales order line** maps conflict with **Project contract header** and **Project contract line** maps. You couldn't enable both at once.| 	General availability |
|Bug fix | Create an error message to state that **Ship To Country/Region** is a mandatory field on **Sales order** and **Purchase order**.| 	General availability |
|Bug fix | Whenever a sales order is created in Dynamics 365 Sales, the default value of the **Invoice Customer** is based on **Billing Account** value of the **Potential Customer**.| 	General availability |
|Bug fix | Ability to toggle **Price override** field to true or false. | 	General availability |

This release includes following map changes.

+ [CDS sales quotation lines] - [quotedetails] map version 1.0.0.1
+ [CDS sales order lines] - [salesorderdetails] map version 1.0.0.1
+ [Vendors V2] - [msdyn_vendors] map version 1.0.0.3
+ [Vendor payment method] - [msdyn_vendorpaymentmethods] map version 1.0.0.1

## August 2021 release of party and global address book 

The August 2021 release of [Dual-write Party and Global Address Book Solutions 3.1.0.2](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwgabsln) is based on [Dual-write core solution version 1.0.29](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).  

This release contains features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Bug fix| Improved performance when more than 20 legal entities are enabled for dual-write. | General availability |
| Bug fix| Fixed issue with **Is primary** setting on postal address. | General availability |
| Bug fix| Fill the contact information on **Contact for customer or vendor** upon party association on main form. | General availability |
| Bug fix| Full name of contact with **IsCustomer=Yes** or **IsVendor=Yes** is blank during initial sync and live sync. | General availability |
| Bug fix| Make the country/region field required on both postal address table and customer address table. | General availability |
| Bug fix| Identify a phone number as mobile. | General availability |
| Bug fix| Update the display name from **Parties Electronic Addresses** table to **Party Electronic Addresses** table. | General availability |
| Party Electronic Address | Synchronize primary electronic address data from lead qualification process, account, and contact creation process to Party Electronic Addresses, and vice versa. | General availability |

## July 2021 release

The July 2021 hotfix release of Dual-write application orchestration solution version is based on [Dual-write core solution version 1.0.28](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).  

This release contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Tracing | Logs basic transaction properties to a remote database for use in analytics and error detection. | General availability |

## June 2021 release

The June 2021 hotfix release of Dual-write application orchestration solution version 2.2.2.98 is based on [Dual-write core solution version 1.0.27](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).  

This release contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Bug fix | Implements rollback of transactions that exceed a 2-minute time limit. | General availability |
| Bug fix | Fixes processing of datetime fields during a catch-up sync. | General availability |
| Tracing | Limits nonessential plugin trace logs for medium-size transactions (five or more records). | General availability |
| Bug fix | Added storage and tracking dimension group lookup fields to the **Shared Product Details** table. Added these lookup fields to the **Released products V2" -> msdyn_sharedproductdetails** dual-write map. | General availability |
| Bug fix | In a sales order, when you select an existing product, the **Sales product category** value defaults to a value that comes from the **Product Category Assignments** table. But when the defaulted value isn't part of sales hierarchy, the line-item addition throws an error message. To prevent the error and allow assignment inside finance and operations apps, the **sales product category** field can be left blank.  | General availability |
| Bug fix | In a sales order, when you select an existing product, the **Sales Product Category** is read-only. It's editable when the product is set to write-in. | General availability |
| Bug fix | The **Total Tax** field in a sales quotation and sales order are read-only. When the **Price per unit** field is changed in the sales quotation line or sales order line in finance and operations apps, it must sync back to the respective sales quotation or sales order line in customer engagement apps.  | General availability |
| Bug fix | Updating the **Warehouse name** field in finance and operations apps caused the **Name** field in Dataverse to be blanked out. | General availability |
| Bug fix | Localization fixes for Ukraine. | General availability |

## May 2021 release

The May 2021 hotfix release of Dual-write application orchestration solution version 2.2.2.60 is based on [Dual-write core solution version 1.0.26](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).  

This release contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Government Community Cloud support | Dual-write runtime on the Government Community Cloud region is supported. | General availability |
| User-friendly error messages | Enables user-friendly error messages for some of the live sync failures. | General availability |

## May 2021 release of party and global address book

The May 2021 hotfix release of the [Dual-write Party and Global Address Book Solutions 3.0.0.26](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwgabsln) is based on [Dual-write core solution version 1.0.24](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).  

This release contains the bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Bug fix| In customer engagement apps, when a lead contains postal address and is qualified, the postal address is associated with the account. It doesn't flow to finance and operations apps, however.| General availability |
| Bug fix| In customer engagement apps, when you add an address to an existing account or contact, the address doesn't flow to finance and operations apps.| General availability |
| Bug fix| More address fields are added to the Customer Address table. | General availability |
| Bug fix| In Dataverse, we changed the display name of msdyn_contactforparties table to **Contact for Customer or Vendor** | General availability |
| Bug fix| We fixed a language transformation in the Contacts V2 (msdyn_contactforparties) mapping. | General availability |
| Bug fix| We fixed an issue in initial sync in the CDS Party postal address locations (msdyn_partypostaladdresses) mapping to avoid loss of some records in Customer Address table. | General availability |

### Solution details

|Solution name | Has new changes? | Previous version | New version |
|--------------|--------------|--------------|--------------|
|Party|Yes|3.0.0.1|3.0.0.26|
|Dynamics365GABExtended|Yes|3.0.0.1|3.0.0.26|
|Dynamics365GABDualWriteEntityMaps|Yes|3.0.0.1|3.0.0.26|
|Dynamics365GABPartyAnchor|Yes|3.0.0.1|3.0.0.26|
|Dynamics365GABPartyCommon|Yes|3.0.0.1|3.0.0.26|

### Map instructions

Follow these steps to apply the new maps:

1. Apply the latest map version 1.0.0.2 for CDS Postal address history V2 (msdyn_postaladdresses) mapping.
2. Apply the latest map version for Contacts V2 (msdyn_contactforparties) mapping.
3. Run the initial sync of the CDS Party postal address locations (msdyn_partypostaladdresses) mapping twice to make sure that there isn't loss of address records in Customer Address table due to concurrent address updates.

## April 2021 release

The April 2021 hotfix release of Dual-write application orchestration solution version 2.2.2.60 is based on [Dual-write core solution version 1.0.25](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).  

This release contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Record deletion | Handle record deletion during transactions with multiple entities. | General availability
| Bug fix | Handle conflict resolution during catch-up sync. | General availability
| Bug fix | Issues related to solution import on environments. | General availability
| Bug fix | The **Notes** table now understands the **Null** value. | General availability |
| Bug fix | Dual write orchestration package 2.2.2.50 doesn't replace the existing key (**msdyn_locationid** field) on the **Address** table with the new key, which is a combination of the **msdyn_locationid** and **parentid** fields. Instead it shows both keys. This was fixed with the new version 2.2.2.60. This new version is applicable only when you're using the [party and global address book](party-gab.md) solution.| General availability |

## March 2021 release

The March 2021 release of Dual-write application orchestration solution version  2.2.2.50 is based on [Dual-write core solution version 1.0.24](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).  

This release contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| [Party and Global Address Book](party-gab.md) | Brings schema parity with finance and operations apps, and gives you the ability to solve complex business problems on Dataverse related to customers, vendors, and contact persons. To use this feature, install [Dual-write Party and Global Address Book Solutions](https://aka.ms/dual-write-gab).<br>Supported finance and operations versions are 10.0.605.30025 (platform update 14), 10.0.644.20031 (platform update15), 10.0.689.10027 (platform update 16), and 10.0.761.1 (platform update 17) | General availability |
| Bug fix | **Product category name** is part of the natural/integration key of the **Product Categories** table. Updating the name using a finance and operations app cause an insert in Dataverse instead of an update. Use the new map for `msdyn_productcategories - Product categories` with version 1.0.0.1. The supported finance and operations version is 10.0.778.0 (platform update 42) | General availability |
| Bug fix| Localization bug fixes and updates. | General availability |
| Bug fix| A note without a description throws error. | General availability |
| Bug fix| In finance and operations apps, running the "Calculate Sales Totals" batch job updates all orders modified within last 24 hours and fixes the totals regardless of the status of the order, for example, **canceled** or **fulfilled**. That action triggers a recancellation or refulfillment causing a conflict error. | General availability |

## February 2021 release

The February 2021 release of Dual-write application orchestration solution version  2.2.2.23 is based on [Dual-write core solution version 1.0.24](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write) and version 10.0.16 (10.0.689.10004) or newer of finance and operations apps and version 9.1.0000.11732 or newer of Dataverse.

This release contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| [Commerce price engine for sales quotations](../../../fin-ops/data-entities/commerce-pricing.md) | Get pricing for sales quotations using commerce price engine. | General availability |
| [Notes integration](../../../fin-ops/data-entities/notes-integration.md) | Notes are integrated between customer engagement apps and finance and operations applications for customers, vendors, sales orders, and purchase orders.  | General availability |

> [!IMPORTANT]
> If you don't need notes integration, don't install or upgrade to Dual-write application orchestration solution version 2.2.2.23 or later. If you install the update, you won't be able to uninstall the notes feature. 

## January 2021 release

The January 2021 release of Dual-write application orchestration solution version 2.2.1.30 is based on [Dual-write core solution version 1.0.24](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write) and version 10.0.14 of finance and operations apps.  

This release contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Bug fix | French-localized strings in the user interface exceeded the maximum limit of 100 characters. | General availability |
| Bug fix | Error while starting the Dataverse released distinct products map. | General availability |

The January 2021 release of Dual-write application orchestration solution version 2.2.1.23 is based on [Dual-write core solution version 1.0.24](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write) and version 10.0.14 of finance and operations apps.  

This release contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| [Purchase order integration](../../../fin-ops/data-entities/scm-field-service-procurement.md) | Integrates purchase order functionality between Dynamics 365 Field Service and Dynamics 365 Supply Chain Management. | General availability |
| Bug fix | Localization updates. | General availability |
| Bug fix | In customer engagement apps, on the **Contact** form, after you set **Is Sellable** to **Yes** and save the record, the contact is considered a customer who can transact. Because customers are associated with transactions, **Is Sellable** becomes read-only after saving. You can't change it back to **No**. | General availability |

## December 2020 release

The December 2020 release of the Dual-write core solution (1.0.24) contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Signal repeater service | Enables the dual-write runtime plugin to communicate with the finance and operations signal repeater service with authentication support. | General availability

## November 2020 release

The November 2020 release of the Dual-write core solution (1.0.23) contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Authentication | Support for new authentication certificate to ensure security. | General availability

## October 2020 release

The October 2020 release of the Dual-write application orchestration solution and the Dual-write core solution contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Camel-cased column mappings | Adds support for column mappings with camel-cased navigation properties. | General availability
| Bug fix | Fixes the bug where an unrecognized tag configuration would cause dual-write execution to be skipped | General availability

## September 2020 release

The September 2020 release of Dual-write application orchestration solution version 2.0.777.493 is based on [Dual-write core solution version 1.0.21](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).  

The September 2020 release contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Lead qualification process in Sales is now company striped | Dynamics 365 Sales users can create a lead, qualify the lead to an opportunity, convert an opportunity into a quote, activate a quote, and create an order. This process was broken in dual-write due to lack of company striping on the **Lead** entity. We implemented company striping on the **Lead** entity, which cascades the company to the underlying **Account** and **Opportunity** tables. Thus the application behavior is restored to support the process. During the **Lead** qualification process, the **Contact** entity isn't company striped. This design supports the **Party** entity model that is due in October 2020. To learn about the **Party** and **GlobalAddressBook** model for dual-write, join the [dual-write Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=66052096&view=all). | General availability |
| [Map state transitions from **Order** to **SalesOrder**](sales-status-map.md) | The **Order** form in Dynamics 365 Sales is always set to **Active**. To create state transitions from **Order** in Dynamics 365 Sales to **SalesOrder** in Dynamics 365 Supply Chain Management, we introduced the **ProcessingStatus** column. |   General availability   |  
| [Money to decimal data type conversion](../../../fin-ops/data-entities/currrency-decimal-places.md) |  Dataverse environments are limited to 4 decimal places for currency and 10 decimal places for exchange rates. finance and operations apps support more decimal places than Dataverse. You can now opt in to extend the decimal support in Dataverse to help ensure there's no loss of decimal place data when using dual-write. | General availability |
| Security role for company and currency exchange | Company and currency exchange tables are global in nature and all dual-write users require read access to these two tables. To simplify the experience, we've added a new security role named **dual-write app user**. Each dual-write user must be added to this security role.   | General availability |
| Security role for setup | Adds the **Dual-write Runtime User** security role. This role allows nonadministrator users to create rows that are set up for dual-write. This feature is part of Dual-write core solution 10.0.21. | General availability |
| Tracing | Internal column added for use in tracing. This feature is part of Dual-write core solution 10.0.21. | General availability |
| Bug fix | Fixes issues where dual-write fails because of a mismatch between the plugin and the destination environments. This fix is part of Dual-write core solution 10.0.21. | General availability |
| Bug fix | Support to ensure that unused plugins are deleted. This fix is part of Dual-write core solution 10.0.21. | General availability |

## August 2020 release

The August 2020 release of the dual-write orchestration package contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Manage multiple table maps | As part of day-to-day operations, you might need to bulk handle table maps. For example, you might want to simultaneously enable or pause a set of table maps. Instead of doing this one-by-one, which is cumbersome and time consuming, you can now enable, pause, resume, or stop more than one table map at the same time in the dual-write list page. | General availability |
| Bug fix | Fixes issues where rows would be skipped in certain cases during project execution. This fix is part of Dual-write core solution version 10.0.19.  | General availability |

## June 2020 release

The June 2020 release of the dual-write orchestration package contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Edit legal entity after setup | The company or legal entity list isn't static and is constantly changing. You might need to add new companies, for example, during a phased rollout or acquisition. Previously, you couldn't add a company or legal entity without system downtime. During this downtime, you would have to unlink and relink your environment. Relinking can be expensive, especially if you have pre-existing data. With this feature, you can add a company in a live environment without having to unlink and relink. | General availability |

## May 2020 release

The May 2020 release of the dual-write orchestration package (version 2.0.777.353) contains the features and bug fixes listed in the following table.

| Feature | Description | Status |
|------|---------|-------|
| Look up on-hand inventory | Ability to look up on-hand inventory and available-to-promise dates on forms in customer engagement apps. | General availability |
| Unit conversions | When unit conversions occur in a finance and operations app at the quote line and order line, the customer engagement app honors the unit conversions and reflects the respective changes to unit and price in the customer engagement app quote detail and order detail. | General availability |
| Currency change restriction | When you try to change the currency in a finance and operations app for an existing quote or order, the change fails.   | General availability |
| Parity in **Account** and **Contact** forms | Bring attribute parity in **Account** and **Contact** forms in customer engagement apps for B2B and B2C customers.  | General availability |
| No address duplication | Don’t duplicate an address in a finance and operations app when there's a create or update action on a customer engagement app quote or order.  | General availability |
| **SalesTaxGroup** support | Support for **SalesTaxGroup** in **Account** and **Contact** forms for business-to-business (B2B) and business-to-consumer (B2C) customers. | General availability |
| Create sellable contacts | Allow creation of a sellable contact using the **Quick Create: Contact** form in customer engagement apps. | General availability |
| Quote and order creation | Enable quote and order creation for B2C customers. | General availability |
| Removal of tenant admin-level consent requirement | Until now, before you could enable dual-write, a tenant admin needed to explicitly give consent to the applications. This wasn't always practical and required more approval, which can be time consuming. With this feature, we removed this prerequisite and the need for explicitly giving consent to the applications. | General availability |
| Force unlink dual-write environment | Previously, while testing dual-write, you had to disable all the table maps before unlinking a dual-write environment, which was cumbersome and sometimes not possible if one of the environments wasn't available. This new feature provides a quick way to unlink your test and trial environments. | General availability |

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
