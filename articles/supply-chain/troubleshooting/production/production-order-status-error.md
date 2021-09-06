---
title: Error when changing status from Reported as finished to End 
description: You may receive an error when changing the status of a production order from Reported as finished to End. This page explains how to mitigate the issue. 
author: SmithaNataraj 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form: 
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# Error when changing status of production order from Reported as finished to End

## Symptoms

When the status of a production order is changed from Reported as finished to End, you receive one of the following error messages:

> Update conflict. The standard cost does not match with the financial inventory value after the update.

> A critical error has occurred in function InventCostMovement.checkVariance.

## Cause

This issue occurs because the underlying data was changed by another process. The process will try to update the data up to five times. If the conflict still exists after five attempts, you'll receive one of the messages listed above.

## Resolution

This behavior is by design. To mitigate the issue, resume the batch job. It should finish running.

If the batch job consistently fails after you resume it, verify that the rounding precision for the ledger's default currency is compliant with the rounding that is applied to values in the InventSum table. If the rounding precision has been changed to a non-compliant value, you must probably change it back to a compliant value. Look for **ModifiedDateTime**. In this case, the value will typically show that the rounding precision was recently changed.
