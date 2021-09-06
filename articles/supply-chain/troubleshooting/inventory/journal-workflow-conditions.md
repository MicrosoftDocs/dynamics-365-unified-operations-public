---
title: Inventory journal workflow conditions apply at the journal level, not line level
description: Inventory journal workflow conditions apply only at the journal level, not at the line level.
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

# Inventory journal workflow conditions apply at the journal level, not line level

## Symptoms

You might experience this issue if, for example, you try to set up an inventory journal workflow condition on the cost amount. You set up the condition so that step 1 is run only when the cost amount is less than 100. You then set up another condition so that step 2 is run only when the cost amount is more than or equal to 100. Then, when the workflow is run, the workflow history shows only one line, and the first condition is always evaluated as *true*, regardless of the value that is submitted.

## Workaround

In the current release, inventory workflow conditions apply only at the journal level, not at the line level. This behavior is by design. We recommend that you set your condition criteria only on journal-level attributes.
