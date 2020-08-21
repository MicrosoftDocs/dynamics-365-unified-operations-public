---
# required metadata

title: Troubleshoot Purchase orders
description: This topic describes how to fix issues that you might encounter while working with Planning Optimization.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.9

---
# Troubleshoot master planning 

This topic describes how to fix common issues that you might encounter while working with Planning Optimization.

## Unable to get the master planning job from cancelling to waiting state

When a master planning job was cancelled and seems to be in the canceling state for some time now and you want to get it back to the waiting status.

**Fix 1: Through the Unfinished planning processes form:**
Navigate to Master planning > Inquiries and reports > Master planning > Unfinished planning processes
Click "Cancel" on all unfinished tasks.
If cancellation through Unfinished planning processes form didn't work:

**Fix 2: Through the Batch Jobs form:**
Navigate to System administration >Inquiries > Batch jobs
Click "Delete" on the batch job related to MRP
If cancellation through Batch Jobs form didn't work:

**Fix 3: Through the Batch Jobs task form:**
Click on the Job ID of the Batch Job related to MRP
Select the batch tasks in Batch tasks:Click "Abort" in the Batch tasks fast

## Planning of batch jobs fails when Planning Optimization is enabled

When you enable Planning Optimization, the built-in master planning engine is automatically disabled. Master planning batch jobs that were created for the built-in Supply Chain Management planning engine will fail if they are triggered while Planning Optimization is enabled. You may receive an error message such as *This operation triggered master planning that isn't supported when Planning Optimization is enabled*.

**Fix**: Cancel all master planning batch jobs that were created for the built-in Supply Chain Management planning engine.

## Planning Optimization results are different from earlier results

Planning Optimization differs from the built-in master planning design in some areas. This can also be caused by pending features.

**Fix**: Run Planning Optimization fit analysis and then analyze the results while referring to the related documentation to understand the impact. For more information, see [Planning Optimization fit analysis](planning-optimization-fit-analysis.md).

## Master planning doesn't respect the coverage time fence

This is caused by a pending feature for Planning Optimization.

**Fix**: Until the pending feature is available, filter or delete planned orders to remove supply suggestions outside of the coverage time fence.

## Can't enable Planning Optimization

The **Connection status** must be **Connected** before you can set **Use Planning Optimization** to **Yes**. For more information, see [Get started with Planning Optimization](get-started.md).

**Fix**: Make sure that the Planning Optimization add-in was installed successfully.

## Error message is shown during CTP

If you try to run capable to promise (CTP) from a sales order when Planning Optimization is enabled, you will receive the following error message: *This operation triggered master planning that isn't supported when the Planning Optimization is enabled*.

This is related to a pending feature that is planned as part of the support for production orders.

**Fix:** Avoid CTP calculations when Planning Optimization is enabled until CTP support is available.

## Additional resources

[Get started with Planning Optimization](get-started.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)
