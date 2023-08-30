---
# required metadata

title: Configure the Workflow Message Processing batch job as critical
description: Configure the workflow Message Processing batch job as critical
author: ChrisGarty
ms.date: 05/11/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  BatchJob
audience: IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 9dc45189-6e7e-4207-ad78-dbbb644dd1ce
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2017-05-19
ms.dyn365.ops.version: Platform update 6
---

# Configure the Workflow message processing batch job as critical

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

The workflow system uses various batch jobs. **Workflow message processing** is an important batch job used to process workflow messages. If workflow is a key component of your organization, you should consider configuring the **Workflow message processing** batch job as critical.

Configuring the **Workflow message processing** batch job as critical ensures that the system actively tracks its status. When a critical batch job fails, the support team can better monitor failures and take action to resolve any issues that may have caused the failure.

Follow these steps to configure the **Workflow message processing** batch job as critical.

1. Navigate to the **Batch jobs** page.
2. Search for **Workflow message processing** using the quick filter.
3. Select the **Workflow message processing** batch job.
4. Click **Edit** in the action pane.
5. Select the **Critical Job** check box.
6. Click **Save** in the action pane.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
