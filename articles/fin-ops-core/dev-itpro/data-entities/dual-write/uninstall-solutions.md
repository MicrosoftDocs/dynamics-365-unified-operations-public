---
title: Uninstall dual-write application orchestration solutions
description: This topic describes how to uninstall dual-write application orchestration solutions.
author: RamaKrishnamoorthy
ms.date: 03/16/2022
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2022-01-21
---

# Uninstall dual-write application orchestration solutions

[!include [banner](../../includes/banner.md)]

This topic describes how to uninstall dual-write application orchestration solutions.

Some customers unintentionally install the dual-write application orchestration package that installs multiple solutions in their Microsoft Dataverse environment. Installation of the extraneous solutions in the package can cause unexpected and undesirable issues.

To fix issues that are related to installation of the dual-write application orchestration package, uninstall the unwanted dual-write solutions in the following order:

1. Dynamics365FinanceAndOperationsAnchor_managed
1. msdyn_OneFSSCM_managed (if present)
1. Dynamics365FinanceAndOperationsDualWriteEntityMaps_managed
1. Dynamics365Notes_managed (To uninstall this solution, you must open a support ticket with Microsoft.)
1. DualWriteCore_managed
1. Dynamics365AssetManagementApp_managed
1. Dynamics365AssetManagement_managed
1. Dynamics365SupplyChainExtended_managed
1. Dynamics365FinanceExtended_managed
1. HCMCommon_managed
1. Dynamics365FinanceAndOperationsCommon_managed
1. Dynamics365Company_managed
1. CurrencyExchangeRates_managed
1. msdyn_AssetCommon_managed
1. FieldServiceCommon_managed

If party and global address book solutions were installed, uninstall the solutions in the following order:

1. Dynamics365FinanceAndOperationsAnchor
1. Dynamics365FinanceAndOperationsDualWriteEntityMaps
1. msdyn_DualWriteCore
1. Dynamics365AssetManagementApp
1. Dynamics365AssetManagement
1. Dynamics365SupplyChainExtended
1. Dynamics365FinanceExtended
1. HCMCommon
1. Dynamics365FinanceAndOperationsCommon
1. Party
1. Dynamics365Company_managed
1. CurrencyExchangeRates
1. msdyn_AssetCommon
1. FieldServiceCommon
