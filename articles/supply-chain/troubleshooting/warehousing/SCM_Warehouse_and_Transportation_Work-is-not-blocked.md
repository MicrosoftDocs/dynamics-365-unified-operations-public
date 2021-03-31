---
title: Work is not blocked
description: Work is not blocked
author: SmithaNataraj
manager: tfehr
ms.date: 3/24/2021
ms.topic: troubleshooting
ms.search.form: WHSWorkTable_WHSWorkUnblocking
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-03-24
ms.dyn365.ops.version: 10.0.18
---

# Work is not blocked

Error code: WHSUnblockNotBlockedWorkErrorMessage

The system displays the following error message:

> Work with Id %1 is not blocked.

## Issue description

The **Blocked wave** setting on the wave is set to *No*.

## Resolution

The work cannot be unblocked because it currently not blocked. Only work with the **Blocked wave** set to *Yes* can be unblocked.
