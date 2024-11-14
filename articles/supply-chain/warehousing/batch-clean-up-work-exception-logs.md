---
title: Batch clean-up job of work exception logs
description: Learn how to clean up work exception logs.
author: sservulo
ms.author: samuoliveira
ms.topic: article
ms.date: 11/06/20424
ms.reviewer: --
ms.search.form: WHSWorkExceptionLogCleanUp
---

# Batch clean-up of Work Exception Logs

[!include [banner](../includes/banner.md)]

The functionality for batch clean-up job of work exception logs lets
you remove these logs by using a batch job.

## Where it applies

For this functionality,  a
batch job given a specific criteria removes work exception logs. This functionality is useful when you want to remove old work exception logs that might be affecting the performance of your system, for example, searching for locations with open work exceptions.

## How to set up

### Specify cleanup criteria for work exception logs

To access the cleanup dialog, navigate to **Warehouse management \> Periodic Tasks \> Clean up \> Clean up work exception logs**).

Select which exception logs should be removed, **Open**, or **Closed** (default: Closed), how many days older than today should be kept (default: 30). A maximum number of records to be removed can be specified as well (default: 100000). This parameter can improve system performance by preventing removal of a large number of records in a single operation.

Other configurations such as recurrence, alerts, and batch group can be configured as well.

Once the job finishes execution, a notification with how many records were removed is displayed.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
