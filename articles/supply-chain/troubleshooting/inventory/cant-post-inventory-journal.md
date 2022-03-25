---
title: Inventory journal workflow never completes and the journal can't be processed
description: After you submit a journal approval workflow, workflow processing stops responding, and you can't edit or process your journals.
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


# Inventory journal workflow never completes and the journal can't be processed

## Symptoms

After you submit a journal approval workflow, workflow processing stops responding, and you can't edit or process your journals.

## Resolution

There are several reasons why workflow processing might not be completed. Check for the following issues:

- Go to **Inventory management &gt; Setup &gt; Inventory management workflows**, and review the configuration of the affected workflow. For more information, see [Inventory journal approval workflows](../../inventory/inventory-journal-workflow.md).
- The workflow might be encountering an exception or error. Review the work item history of the affected workflow to see whether it includes an application error that terminates the workflow.
- The inventory journal can be updated or edited only if it's approved. If recall is active, you can try to recall the journal. Execution of the workflow batch job might be suspended for multiple reasons. Some of these reasons might be caused by the workflow framework issue.
