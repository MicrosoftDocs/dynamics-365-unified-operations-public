---
# required metadata

title: What's new or changed in Virtual Entities?
description: This article provides updates on new features and bug fixes released in virtual entity solution provider for finance and operations apps.
author: RamaKrishnamoorthy
ms.date: 06/22/2023
ms.topic: Virtual Entities
audience: IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2023-06-1
---

# What's new or changed in Virtual Entity solution provider?

[!include[banner](../includes/banner.md)]

[Virtual entity solution provider for finance and operations apps](https://appsource.microsoft.com/en-us/product/dynamics-365/mscrm.finance_and_operations_virtual_entity?tab=Overview) is an Appsource package which provides near-real-time interacion with finance and operations data on Power Platform. 

## June 2023 release
The June release of F&O Virtual Entity Solution Changes in Release 2.8.7 contains the following changes:

### Virtual Entity changes
| Type | Description | Status |
|---|---|---|
| Feature | You can access fields which expose aggregation results. Say for example: The onhand inventory of Surface Pro 128 GB is 10 in Site Chicago and 15 in Site Montana, it can be aggregated and exposed as 25. | General availability |
| Feature | You can call Dataverse tables and APIs from Finance and Operations apps using IOrganizationService. | General availability |
| Performance Improvement	| Improved the performance of virtual entity metadata generation process for finance and operations apps. | General availability |
| Bug Fix | Corrected an issue where the translation of data being returned from finance and operations apps resulted in error "An item with the same key has already been added". | General availability |
| Bug Fix | Fixed query expression for joins to CompanyInfoEntity and avoid SQL error. | General availability |

### Business Events changes
| Type | Description | Status |
|---|---|---|
| Bug Fix | Filter endpoints with missing or bad azure app id. | General availability |
| Bug Fix | Handle sync failures in callbackregistration delete and proceed with delete to prevent orphaned records. | General availability |
| Bug Fix | Ignore Business Events Endpoints which are missing required fields. | General availability |
| Bug Fix | Capture the original serialized event contract under finance and operations Exception Log. | General availability |

### Data Archival changes
| Type | Description | Status |
|---|---|---|
| Bug Fix | Improvements to authoration experience during development. | General availability |
| Bug Fix | Retention flow has been disabled. | General availability |
| Bug Fix | Null-reference exception occurs during virtual entity metadata creation. | General availability |
