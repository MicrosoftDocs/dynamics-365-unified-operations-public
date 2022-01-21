---
title: Uninstall dual-write application orchestration solutions
description: This topic describes the Party and global address book functionality of dual-write.
author: RamaKrishnamoorthy
ms.date: 01/21/2022
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: tfehr
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2022-01-21
---

# Uninstall dual-write application orchestration solutions

Often we are observing some customers are installing DW package without the need and understanding about Dual Write and then ran into issues as expected. For those customers- they should uninstall the solutions and proceed only after evaluation of DW and going through the documentation. Here is sequence of solution uninstallation

+ Dynamics365FinanceAndOperationsAnchor_managed
+ msdyn_OneFSSCM_managed (if present)
+ Dynamics365FinanceAndOperationsDualWriteEntityMaps_managed
+ Dynamics365Notes_managed (run script through Jarvis on the org before-hand: FixRelationshipMetadataToCustom.sql )
+ DualWriteCore_managed
+ Dynamics365AssetManagementApp_managed
+ Dynamics365AssetManagement_managed
+ Dynamics365SupplyChainExtended_managed
+ Dynamics365FinanceExtended_managed
+ HCMCommon_managed
+ Dynamics365FinanceAndOperationsCommon_managed
+ Dynamics365Company_managed
+ CurrencyExchangeRates_managed
+ msdyn_AssetCommon_managed
+ FieldServiceCommon_managed

If Party/GAB solutions were installed, then below is the uninstall order
+ Dynamics365FinanceAndOperationsAnchor
+ Dynamics365FinanceAndOperationsDualWriteEntityMaps
+ msdyn_DualWriteCore
+ Dynamics365AssetManagementApp
+ Dynamics365AssetManagement
+ Dynamics365SupplyChainExtended
+ Dynamics365FinanceExtended
+ HCMCommon
+ Dynamics365FinanceAndOperationsCommon
+ Party
+ Dynamics365Company_managed
+ CurrencyExchangeRates
+ msdyn_AssetCommon
+ FieldServiceCommon
