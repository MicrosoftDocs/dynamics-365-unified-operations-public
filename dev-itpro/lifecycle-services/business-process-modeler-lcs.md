---
# required metadata

title: Business process modeler
description: This article provides information about Business process modeler in Microsoft Dynamics Lifecycle Services (LCS). You can use this tool to create, view, and modify business process libraries and flowcharts for Microsoft Dynamics AX. The article also lists the prerequisites and explains how to start using Business process modeler.
author: RobinARH
manager: AnnBe
ms.date: 2015-12-03 18 - 57 - 30
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 15031
ms.assetid: 01c38560-f588-4558-a7ec-3af1bb518069
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Business process modeler

This article provides information about Business process modeler in Microsoft Dynamics Lifecycle Services (LCS). You can use this tool to create, view, and modify business process libraries and flowcharts for Microsoft Dynamics AX. The article also lists the prerequisites and explains how to start using Business process modeler.

In Microsoft Dynamics Lifecycle Services, you can use Business process modeler to create, view, and modify business-process libraries and flowcharts for Microsoft Dynamics AX. Business process modeler helps you align your Microsoft Dynamics AX processes with industry-standard processes as described by [American Productivity & Quality Center (APQC)](http://www.apqc.org/). You can perform fit-gap analysis between the business needs and the default processes in Microsoft Dynamics AX. You can also add new business processes and create flowcharts for processes that are not already defined in Microsoft Dynamics AX 2012. You can use Business process modeler artifacts with the following applications:

-   Microsoft Visual Studio Team Foundation Server (TFS) – You can generate a consolidated list of gaps and import them manually into TFS as work items that include a reference to the process flow.
-   Microsoft Word – You can generate documentation for business processes.
-   Microsoft Visio – You can export business process maps to Visio files.

## Prerequisites
To use the Business process modeler, the following products are required:

-   The Task recorder that is included in AX 2012 R3 and cumulative update 7 for Microsoft Dynamics AX 2012 R2 supports generating custom processes in Business process modeler.For earlier releases, an updated Task recorder is available as a hotfix. The hotfix includes a client update and a model file. You must install the client update on all Microsoft Dynamics AX 2012 clients. There are two hotfixes available:
    -   Microsoft Dynamics AX 2012 R2 – Knowledgebase article [2863182](http://go.microsoft.com/fwlink/?LinkId=309911)
    -   Microsoft Dynamics AX 2012 and Microsoft Dynamics AX 2012 Feature Pack – Knowledgebase article [2863182](http://go.microsoft.com/fwlink/?LinkId=309910)
-   Microsoft Office 2010 or later versions supports generating documents.
-   Windows Media Player supports playing business process videos.

## Getting started
To access Business process modeler, follow these steps:

1.  [Go to Lifecycle Services](https://lcs.dynamics.com).
2.  Sign in, open a project, and then click the **Business process modeler** tile. The **Business process libraries** displays three sections:
    -   **My libraries** contains business processes that the user has created or added.
    -   **Corporate libraries** contains custom-created business processes that have been uploaded by someone in your organization.
    -   **Global libraries** contains cross-industry standard business processes.

3.  To copy a standard business process library from the **Global libraries** section to the **My libraries** section, right-click the tile in the **Global libraries** section, and then on the app bar, click **Copy**.
4.  After the business process library has been added to the **My libraries** section, click the tile to view the business process library.


See also
--------

[Business process libraries in Business process modeler](business-process-libraries-business-process-modeler.md)

[Flowcharts in Business process modeler](flowcharts-business-process-modeler.md)

