---
title: Unexpected difference between request and session data during testing
description: Unexpected difference between request and session data in warehouse app task validation results
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

You are testing the warehouse app with the [task validator enabled](../../warehousing/mobile-device-parameters.md), and the validator returns the following error message:

> Unexpected difference between request and session data. Warehouse Mobile Devices XML protocol violated.REQUEST_XML_TAMPERING

## Cause

This error occurs when the output of the last successful step executed in the test run doesn't match the recorded input of the next step. This is possible because the task validator uses recorded XML as input for each step instead of the output of a previous step.

In most cases this error happens when you are rerunning a task, but the test requires some documents that were modified or removed by a previous run of the same task.

## Resolution

The warehouse app task validation test run is not an idempotent operation&mdash;it modifies the underlying data. So before rerunning a task, you may need to reset the relevant data. 

1. Investigate output XML of the last test step that succeeded to find out where your test run left off.
1. Inspect your test and make sure all the required sales orders, transfer orders, work headers, and other documents are still present and in the expected state.
1. Recreate or edit and missing or modified documents, or create a new test setup and modify the test to use valid existing documents.
