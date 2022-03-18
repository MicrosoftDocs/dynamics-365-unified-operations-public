--- 
title: Same trade agreement selected when creating sales order lines 
description: If there is more than one trade agreement defined for a given date, the one with the lowest price is always selected when creating sales order lines. 
author: SmithaNataraj
ms.date: 06/24/2021 
ms.topic: troubleshooting 
ms.search.form: SalesTable, SalesTableListPage, SalesTableListPage_SalesCancelOrder
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
---

# If two trade agreements exist for overlapping dates, the same one is always selected

## Symptoms

If two trade agreements are defined for the same period or overlapping periods, the same trade agreement seems to be selected every time when creating sales order lines that contain those items.

## Resolution

If there is more than one trade agreement for a given date, the trade agreement that has the lowest price is always selected. For more information, download the following white paper: [Trade agreements in Microsoft Dynamics AX 2012](https://www.axug.com/HigherLogic/System/DownloadDocumentFile.ashx?DocumentFileKey=3396a3a8-1f48-4d85-8cd6-5fa982f62e90).
