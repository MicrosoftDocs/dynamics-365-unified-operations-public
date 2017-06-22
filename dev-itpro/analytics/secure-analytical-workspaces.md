---
# required metadata

title: 
description: 
author: robinarh
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 21551
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tjvass
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: AX 7.0.0

---

# Secure analytical workspaces and reports using Power BI Embedded

[!include[banner](../includes/banner.md)]


> [!NOTE]
> This feature is supported in release Dynamics 365 (v7.2) and after.


# Introduction
This article offers a walk-thru for Application Developers seeking to secure Analytical Workspaces & Reports delivered using Power BI Embedded.  We’ll discuss the recommended strategies for securing both access to the reports as well as the data set based on viewer access rights.  Using the techniques described below, reports can be hidden from users and filtered to show the data set appropriate for the user based on the active company context.

# Prerequisites
+ Access to a developer environment running on Platform Update 8 or later.
+ Analytical report (PBIX file) authored using Power BI Desktop with a data model sourced from the Dynamics Entity Store Database.

# Overview
Whether you are extending an existing application workspace or introducing one of your own, embedded analytical views can be used to deliver insightful and interactive views of your business data.  Before introducing new analytical workspaces and reports, it’s important that you first establish a strategy for securing the content.  There are several considerations to be aware of when developing Analytical solutions using Power BI Embedded.

Analytical reports can be secured using menu items.  Once the user has access, the underlying data models defined within the report is accessible by all viewers of the report.  Although, service options are available to automatically hide the Fields backing a report data set, all viewers of the report have effective access to the fields in the data model.  X++ extensions are available to influence the report presentation in the client.  Both the **Filter** pane and **Report** tabs can be hidden.  However, Power BI filters can be altered using client side script injections.  

## Recommendation
Create scenario-specific PBIX files to deliver analytical views:
+ Area overviews are delivered using workspaces
+ Subject matter specific analytical reports 

> [!NOTE]
> These are often used to deliver reports containing medium and high business impact data.


