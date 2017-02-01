---
# required metadata

title: System diagnostics (AX 2012) | Microsoft Docs
description: 
author: kfend
manager: AnnBe
ms.date: 2015-12-05 23:28:02
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.suite: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 19061
ms.assetid: ac41930e-8e85-46ba-823e-603501e2b065
ms.region: Global
# ms.industry: 
ms.author: murtazac

---

# System diagnostics (AX 2012)



In Microsoft Dynamics Lifecycle Services, the System diagnostics helps administrators monitor and understand the health of one or more Microsoft Dynamics AX environments. It is a cloud-based tool that has a locally-installed component that can be configured to perform the following tasks:
-   Discover on-premises Microsoft Dynamics AX environments (database instances and Microsoft Dynamics AX Application Object Server (AOS) instances).
-   Collect data from the environments that were discovered.
-   Run rules on the collected data.
-   Report rule violations on a dashboard.
-   Provide reports.

Data is collected by using jobs that run on predefined schedules. The following diagram describes how System diagnostics and the locally-installed components interact.
System diagnostic service

![System diagnostic service (Lifecycle Services)](./media/systemdiagnosticservicelifecycleservices.png) System diagnostics supports the following versions of Microsoft Dynamics AX:
-   Microsoft Dynamics AX 2012 R2
-   Microsoft Dynamics AX 2012 Feature Pack
-   Microsoft Dynamics AX 2012
-   Microsoft Dynamics AX 2012 R3

## Prerequisites
Before you can use the System diagnostics, you must complete the following tasks:
-   Download and run the installer for the Diagnostic service.
-   Run the Discovery wizard.
-   Schedule or run data collection.

## Getting started
The following topics explain how to install and use System diagnostics.
-   [Install and run System diagnostics (Lifecycle Services)](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/lifecycle-services/ax-2012/install-and-run-system-diagnostics-lifecycle-services)
-   [Use System diagnostics (Lifecycle Services)](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/lifecycle-services/ax-2012/use-system-diagnostics-lifecycle-services)



