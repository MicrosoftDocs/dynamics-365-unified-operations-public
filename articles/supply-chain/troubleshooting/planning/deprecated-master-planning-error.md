---
# required metadata

title: Running deprecated built-in master planning causing error.
description: Running deprecated built-in master planning causing error.
author: ankubik@microsoft.com
manager: tfehr
ms.date: 5/19/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: Dialog_ReqCalcScheduleItemTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: ankubik@microsoft.com
ms.assetid: 
ms.search.region: Global
ms.author: ankubik@microsoft.com

---

# Running deprecated built-in master planning causing error.

Error code: ReqCalcScheduleItemTablePlanningOptimizationFitError

The system displays the followign error message:
	ReqCalcScheduleItemTablePlanningOptimizationFitError



## Symptoms
When running planning the system shows the following error message: > You receive this error message because the built-in master planning engine was used for scenarios supported by Planning Optimization. You should migrate to Planning Optimization now, as the current built-in master planning will be deprecated. Note that this master planning run did complete successfully.  In case your migration has strong dependencies on pending features, an exception to continued usage of the built-in master planning engine can be requested.  Please complete the following questionnaire to get started and, if relevant, request an exception from migration to Planning Optimization.  Planning Optimization migration and exception questionnaire (https://go.microsoft.com/fwlink/?linkid=2144962)

## Cause
If the customer is running planning and doesn't use production feature it is potentially good fit for planning optimization. The built-in master planning engine is being deprecated so to continue to use it without getting error the exception has to be granted.

## Resolution
Read more about migration to Planning Optimization here: https://docs.microsoft.com/en-us/dynamics365/supply-chain/master-planning/new-master-planning-engine



