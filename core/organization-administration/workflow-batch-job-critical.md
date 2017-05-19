---
# required metadata

title: Configure the Workflow Message Processing batch job as critical
description: Configure the workflow Message Processing batch job as critical
author: aneesmsft
manager: AnnBe
ms.date: 05/11/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
# ms.reviewer: sericks
# ms.search.scope: [Which Operations client to show this topic as help for, to be set by content strategist, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 9dc45189-6e7e-4207-ad78-dbbb644dd1ce
ms.search.region: Global
# ms.search.industry: 
ms.author: aneesa
ms.dyn365.intro: 2017-05-19]
ms.dyn365.version: Platform update 6
---

# Configure the **Workflow message processing** batch job as critical

[!include[banner](../includes/banner.md)]

The workflow system uses various batch jobs. **Workflow message processing** is an important batch job used to process workflow messages. If workflow is a key component of your organization, you should consider configuring the **Workflow message processing** batch job as critical.

Configuring the **Workflow message processing** batch job as critical ensures that the system actively tracks its status. When a critical batch job fails, the support team can better monitor failures and take action to resolve any issues that may have caused the failure.

Follow these steps to configure the **Workflow message processing** batch job as critical.

1. Navigate to the **Batch jobs** page.
2. Search for **Workflow message processing** using the quick filter.
3. Select the **Workflow message processing** batch job.
4. Click **Edit** in the action pane.
5. Select the **Critical Job** check box.
6. Click **Save** in the action pane.
