---
# required metadata

title: What's new or changed in the Virtual Entity solution provider?
description: This article describes new features and bug fixes that have been released in the Virtual Entity solution provider for finance and operations apps.
author: RamaKrishnamoorthy
ms.date: 06/22/2023
ms.topic: Virtual Entities
audience: IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2023-06-1
---

# What's new or changed in the Virtual Entity solution provider?

[!include[banner](../includes/banner.md)]

The [Virtual Entity solution provider for finance and operations apps](https://appsource.microsoft.com/product/dynamics-365/mscrm.finance_and_operations_virtual_entity) is a Microsoft AppSource package that provides near-real-time interaction with finance and operations apps data on Microsoft Power Platform.

## June 2023 release

The June release of Finance and Operations Virtual Entity Solution Changes in Release 2.8.7 contains the following changes.

### Virtual entity changes

| Type | Description | Status |
|---|---|---|
| Feature | You can access fields that expose aggregation results. For example, if the on-hand inventory of Surface Pro 128 GB is 10 at the Chicago site and 15 at the Montana site, the results are aggregated and exposed as 25. | General availability |
| Feature | You can call Dataverse tables and APIs from finance and operations apps by using `IOrganizationService`. | General availability |
| Performance improvement | The performance of the virtual entity metadata generation process for finance and operations apps is improved. | General availability |
| Bug fix | An issue is corrected, where the translation of data that's returned from finance and operations apps causes the following error message: "An item with the same key has already been added." | General availability |
| Bug fix | The query expression for joins to `CompanyInfoEntity` is fixed to prevent an SQL error. | General availability |

### Business event changes

| Type | Description | Status |
|---|---|---|
| Bug fix | Filter endpoints that have a missing or bad Azure app ID. | General availability |
| Bug fix | Handle synchronization failures during callback registration deletion, and proceed with the deletion to prevent orphaned records. | General availability |
| Bug fix | Ignore any business event endpoints that are missing required fields. | General availability |
| Bug fix | Capture the original serialized event contract in the finance and operations apps exception log. | General availability |

### Data archival changes

| Type | Description | Status |
|---|---|---|
| Bug fix | Improvements have been added to the authorization experience during development. | General availability |
| Bug fix | The retention flow has been disabled. | General availability |
| Bug fix | A null-reference exception occurs during virtual entity metadata creation. | General availability |
