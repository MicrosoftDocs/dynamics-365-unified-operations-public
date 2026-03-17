---
title: Configure the Workflow Message Processing batch job as critical
description: Learn about how to configure the workflow Message Processing batch job as critical, including a step-by-step process.
author: ChrisGarty
ms.author: cgarty
ms.topic: how-to
ms.date: 02/24/2026
ms.custom: 
ms.reviewer: twheeloc
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-05-19
ms.search.form:  BatchJob
ms.dyn365.ops.version: Platform update 6
ms.assetid: 9dc45189-6e7e-4207-ad78-dbbb644dd1ce
---

# Configure the Workflow message processing batch job as critical

[!INCLUDE [banner](../../../finance/includes/banner.md)]


The workflow system uses various batch jobs. **Workflow message processing** is an important batch job that processes workflow messages. If workflow is a key component of your organization, consider configuring the **Workflow message processing** batch job as critical.

When you configure the **Workflow message processing** batch job as critical, the system actively tracks its status. When a critical batch job fails, the support team can better monitor failures and take action to resolve any problems that caused the failure.

Follow these steps to configure the **Workflow message processing** batch job as critical:

1. Navigate to the **Batch jobs** page.
1. Search for **Workflow message processing** using the quick filter.
1. Select the **Workflow message processing** batch job.
1. Select **Edit** in the action pane.
1. Select the **Critical Job** check box.
1. Select **Save** in the action pane.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
