---
# required metadata

title: Manage Finance and Operations Support experiences
description: This topic provides information about using the Support tool to on Microsoft Dynamics Lifecycle Services (LCS) to manage support incidents. 
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 60373
ms.assetid: 0fa10573-8146-446e-8124-8a7af9546add
ms.search.region: Global
# ms.search.industry: 
ms.author: anupams
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Manage Finance and Operations Support experiences

[!include[banner](../includes/banner.md)]

Remove all mentions of VMs and then send for review

To use the Support tool, you must have previously created a project in Lifecycle Services and installed and ran the System diagnostics in your environment. For more information, see [System diagnostics (Lifecycle Services, LCS)](/ax-2012/system-diagnostics-lcs.md).

## Open a new incident
1.  [Go to Lifecycle Services](https://lcs.dynamics.com).
2.  Open a project, and then click the **Support** tile.
3.  On the **Incidents list** application bar, click **Create**.
4.  Search for an existing solution by keyword or by object path in the Microsoft Dynamics AX Application Object Tree (AOT).
    
    | **Note**                                                  |
    |-----------------------------------------------------------|
    | If you click a solution, **Issue search** opens on a new tab. |

5.  If you don’t find an existing solution, click **Create incident**.
6.  On the **Share diagnostic data** page, select the appropriate environment. If you have not previously run System diagnostics in your environment, you are prompted to install and run it. After you run System diagnostics, you must update the **Share diagnostic data** page.
7.  On the **Describe the issue** pages, enter details about the issue.
    After you click **Submit**, the following steps occur:
    -   An incident is created and added to the **Incidents** list.
    -   You receive an email message from the Microsoft Support Engineer who is working on your case. This message asks you to grant the engineer access to your project in the Project contributor role. If you do not grant access, the engineer can't work on your case. For more information about how to grant access, see [Projects (Lifecycle Services, LCS)](/ax-2012/projects-lcs.md).





