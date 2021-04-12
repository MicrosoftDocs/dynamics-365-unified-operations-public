---
title: Sales Order Line entry function, the filter functionality will not save to "contains" and always defaults to "begins with". 
description: Sales Order Line entry function, the filter functionality will not save to "contains" and always defaults to "begins with". 
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: SalesTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: myvakalo
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Sales Order Line entry function, the filter functionality will not save to "contains" and always defaults to "begins with". 

KB Number: 4611879

## Issue description

Sales Order Line entry function, the filter functionality will not save to "contains" and always defaults to "begins with".

## Resolution

This issue is not reproduceable on the latest application version (10.0.19). On a sales order, when a new sales order line is added and the filtering criteria on the item number is changed to 'contains', then for all the other sales lines, the filtering criteria will be set to 'contains'.