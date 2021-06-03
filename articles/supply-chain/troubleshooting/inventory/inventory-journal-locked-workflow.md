---
title: Your inventory journal is locked and the workflow batch job doesn't work
description: One of your inventory journals is locked by some operation and isn't being released
author: sherry-zheng
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: chuzheng
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.16
---

# Your inventory journal is locked and the workflow batch job doesn't work

## Symptoms

One of your inventory journals is locked by some operation and isn't being released. For example, if an unknown error occurs during posting (which is a system lock operation), the journal might remain in system-locked status. In this case, the workflow work item handler will throw an error while it does lock validation.

## Resolution

Sign in to the SQL Server instance for Supply Chain Management, and check whether **InventJournalTable.SystemBlocked** is set to *1*. If it is, make sure that the journal should not be in locked status, and then reset **InventJournalTable.SystemBlocked** to *0*.
