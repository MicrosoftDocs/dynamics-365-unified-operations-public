---
title: Unexpected difference between request and session data during testing
description: An unexpected difference occurs between request and session data in warehouse app task validation results.
author: mamuszal
ms.date: 03/11/2022
ms.topic: troubleshooting
ms.search.form: WHSValidatorRunInstance_executeRun
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mamuszal
ms.search.validFrom: 2022-03-11
ms.dyn365.ops.version: 10.0.18
---

# Unexpected difference between request and session data during testing

Error code: WarehouseMobileDeviceRequestInputValidationError

## Symptoms

When you're using the [warehouse app task validation framework](/dynamics365-release-plan/2019wave2/dynamics365-supply-chain-management/warehouse-app-task-validation-rsat), the validator returns the following error message:

> Unexpected difference between request and session data. Warehouse Mobile Devices XML protocol violated.REQUEST_XML_TAMPERING

## Cause

The error occurs when the output of the last step that was successfully run in the test run doesn't match the recorded input for the next step. This situation can arise because the task validator doesn't use the output of a previous step as input for a successive step. Instead, it uses recorded XML as input for each step.

In most cases, the error occurs when you rerun a task, but the test requires some records that were modified or removed by a previous run of the same task.

## Resolution

The warehouse app task validation test run isn't an idempotent operation but modifies the underlying data. Therefore, before you rerun a task, you might have to reset the relevant data.

1. Review the output XML of the last successful test step to determine where your test run left off.
1. Inspect your test, and make sure that all the required sales orders, transfer orders, work headers, and other records are still present and in the expected state.
1. Re-create or edit the missing or modified records. Alternatively, create a new test setup, and design the test to use valid existing records.
