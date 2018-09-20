---
# required metadata

title: Data management error descriptions
description: This topic describes the error messages that you might encounter in data management.
author: Sunil-Garg
manager: AnnBe
ms.date: 09/20/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 25341
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2018-09-15
ms.dyn365.ops.version: Platform update 20

---

# Data management error descriptions

[!include [banner](../includes/banner.md)]

## Import to target failed due to an update conflict as more than one process is trying to update the same record at the same time
When you use recurring imports (enqueue API), if the files are sent to the end point at high frequency and the sequential processing of messages isn't enabled, data management will try to process the files in parallel. 
When files are processed in parallel, and multiple files have the same record, multiple threads will try to update the same record at the same time. 
If this is a data issue, you must update the data so that the same records don’t repeat across files. 
If this is not a data issue and the entity is expected to handle such cases, you can chose to sequentially process the files or reduce the frequency of which the files are sent to the end point. However, if you reduce the frequency, you might still run in to this error depending on the timing.
