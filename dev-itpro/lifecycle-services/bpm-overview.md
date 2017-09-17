---

title: Business process modeler
description:
author: kfend
manager: AnnBe
ms.date: 09/17/2017
ms.topic: article
ms.prod: 
ms.service:  dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 2012, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 13301
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ntecklu
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Business process modeler

[!include[banner](../includes/banner.md)]

The Business Process Modeler (BPM) for Microsoft Dynamics is a tool you can use to create, view, and modify repeatable implementations based on business-process libraries and flowcharts. BPM helps you align your Dynamics 365 processes with industry-standard processes as described by the [American Productivity &amp; Quality Center (APQC)](http://www.apqc.org/). You can perform fit-gap analysis between your business needs and the default processes in Dynamics 365. Additionally, you may add new business processes and create flowcharts for processes that are not already defined in Microsoft Dynamics 365. BPM is compatible with the following applications:

- Microsoft Visual Studio Team Foundation Server (TFS) – You can generate a consolidated list of gaps and import them manually into TFS as work items that include a reference to the process flow.
- Microsoft Word – You can generate documentation for business processes.
- Microsoft Visio – You can export business process maps to Visio files.

## Prerequisites

To effectively use the Business process modeler, Microsoft Office 2010 and a Visual Studio Team Services project is required.

## Getting started

Follow these steps to access the Business Process Modeler:

1. [Go to Lifecycle Services](https://lcs.dynamics.com/).
2. Sign in, open a project, and then click the **Business process modeler** tile. The **Business process libraries** displays three sections:

  - **My libraries** contains business processes that the user has created or added.
  - **Corporate libraries** contains custom-created business processes that have been uploaded by someone in your organization.
  - **Global libraries** contains cross-industry standard business processes.

3. To copy a standard business process library from the **Global libraries** section to the **My libraries** section, click the top right corner of the tile in the **Global libraries** section, and select **Copy**.
4. After the business process library has been added to the **My libraries** section, click the tile to view the business process library.

## Work in BPM libraries
The following topics provide more information about working with BPM libraries:
- [Create, edit, or browse a BPM library](creating-editing-browsing.md)
- [Synchronize a BPM library with Visual Studio Team Services (VSTS)](implementation.md)
- [Complete tasks in BPM](complete-tasks-bpm.md)
- [Use activity diagrams](using-activity-diagrams.md)

## See also

[Business process libraries in Business process modeler](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/lifecycle-services/business-process-libraries-business-process-modeler)

[Upload custom business processes to BPM](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/lifecycle-services/upload-business-processes-bpm-task-recorder)
