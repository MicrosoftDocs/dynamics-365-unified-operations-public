---
title: Work isn't blocked
description: Work isn't blocked
author: perlynne
ms.date: 04/15/2021
ms.topic: troubleshooting
ms.search.form: WHSWorkTable_WHSWorkUnblocking
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-05-15
ms.dyn365.ops.version: 10.0.18
---

# Work isn't blocked

Error code: WHSUnblockNotBlockedWorkErrorMessage

## Symptoms

The system shows the following error message:

> Work with Id %1 is not blocked.

## Cause

The **Blocked wave** option on the wave is set to *No*. The work can't be unblocked because it isn't currently blocked.

## Resolution

 Only work where the **Blocked wave** option is set to *Yes* can be unblocked.
