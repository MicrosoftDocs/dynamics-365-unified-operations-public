---
title: Unexpected difference between request and session data in warehouse app task validation results
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

# Unexpected difference between request and session data in warehouse app task validation results

Error code: WarehouseMobileDeviceRequestInputValidationError

## Symptoms

Test run fails and the system shows the following error message:
> Unexpected difference between request and session data. Warehouse Mobile Devices XML protocol violated.REQUEST_XML_TAMPERING

## Cause

Request xml for the warehouse app task validation test step does not match an existing work user session.

The output of the last successful step executed in the test run does not match the recorded input of the next step. Task validator is using recorded xml as input to each step instead of the output of a previous step.
In most cases this error happens on a rerun of a task.

Warehouse app task validation test run is not an idempotent operation. It is modifying the underlying data. Before rerunning a task resetting relevant data may be needed.
 
## Resolution

Investigate output xml of the last test step that succeeded.

Restoring relevant sales orders/transfer order/work/etc. or create a new setup and modify test to use a new sales order.



