---
title: You receive an error when running the built-in master planning engine
description: You receive an error when running the deprecated built-in master planning engine
author: ankubik
ms.date: 06/10/2021
ms.topic: troubleshooting
ms.search.form: Dialog_ReqCalcScheduleItemTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: ankubik
ms.search.validFrom: 2021-06-10
ms.dyn365.ops.version: 10.0.20
---

# You receive an error when running the built-in master planning engine

Error code: ReqCalcScheduleItemTablePlanningOptimizationFitError

## Symptoms

When you run master planning using the deprecated built-in master planning engine, the system shows the following error message:

> You receive this error message because the built-in master planning engine was used for scenarios supported by Planning Optimization. You should migrate to Planning Optimization now, as the current built-in master planning will be deprecated. Note that this master planning run did complete successfully.  In case your migration has strong dependencies on pending features, an exception to continued usage of the built-in master planning engine can be requested.  Please complete the following questionnaire to get started and, if relevant, request an exception from migration to Planning Optimization.  [Planning Optimization migration and exception questionnaire](https://go.microsoft.com/fwlink/?linkid=2144962)

## Cause

If you are running planning and aren't using production control features, you should consider migrating to Planning Optimization. The built-in master planning engine is being deprecated, so to continue to use it without getting the error, you must apply for an exception from Microsoft.

## Resolution

To learn more about migrating to Planning Optimization, and how to apply for an exception to continue using the deprecated built-in planning engine instead, see [Migration to Planning Optimization for master planning](dynamics365/supply-chain/master-planning/new-master-planning-engine).
