---
title: Business process modeler (BPM) in Lifecycle Services (LCS)
description: This topic provides information about the Business process modeler tool in Lifecycle Services (LCS).
author: AngelMarshall 
manager: AnnBe
ms.date: 06/15/2020
ms.topic: article
ms.prod: 
ms.service:  dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: AX 2012, Operations
# ms.tgt_pltfrm: 
ms.custom: 13301
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tsmarsha
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Business process modeler (BPM) in Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

Business process modeler (BPM) in Microsoft Dynamics Lifecycle Services (LCS) is a tool that you can use to create, view, and modify repeatable implementations that are based on business process libraries. BPM helps you align your business processes with industry-standard processes that are described by the [American Productivity &amp; Quality Center (APQC)](https://www.apqc.org/). You can perform fit-gap analysis between your business requirements and the default processes in Finance and Operations apps. Additionally, you can add new business processes that aren't already defined.

BPM is compatible with the following products:

- **Microsoft Word** – You can generate documentation for business processes.
- **Microsoft Visio** – You can export business process maps to Visio files.

> [!NOTE]
> The information in this topic is specific only to Finance and Operations apps. For information about Business process modeler and Microsoft Dynamics AX 2012, see [Business process modeler (BPM) in Lifecycle Services (LCS)](ax-2012/business-process-modeler-lcs.md). 

## Prerequisites

To effectively use BPM, you must have Microsoft Office 2010 and a Microsoft Azure DevOps project.

## Getting started

Follow these steps to access BPM.

1. Go to [LCS](https://lcs.dynamics.com/).
2. Sign in, open a project, and then select the **Business process modeler** from the drop-down menu. The **Business process libraries** page has three sections:

    - **Project libraries** – This section contains business processes that a user has created or added.
    - **Corporate libraries** – This section contains custom business processes that someone in your organization has published.
    - **Global libraries** – This section contains cross-industry standard business processes, typically published by Microsoft.

3. To copy a standard business process library from the **Global libraries** section to the **Project libraries** section, select the upper-right corner of the tile in the **Global libraries** section, and then select **Copy**.
4. After the business process library has been added to the **Project libraries** section, select the tile to view the business process library.

## Additional resources

- [Create, edit, and browse Business process modeler (BPM) libraries](creating-editing-browsing.md)
- [Synchronize BPM libraries with Azure DevOps](synchronize-bpm-vsts.md)
- [Complete tasks in Business process modeler (BPM)](complete-tasks-bpm.md)
- [Work with activity diagrams in Business process modeler libraries](using-activity-diagrams.md)
- [Business process libraries in Business process modeler (BPM)](business-process-libraries-business-process-modeler.md)
- [Flowcharts in Business process modeler (BPM)](flowcharts-business-process-modeler.md)


