---
# required metadata

title: Add an Analytics tab to a workspace
description: [Will fill in later].
author: tjvass
manager: AnnBe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: global
# ms.search.industry: 
ms.author: tjvass
ms.dyn365.ops.intro: Platform update 8
ms.search.validFrom: 2016-11-30
---


# Add analytics to workspaces using Power BI Embedded

[!include[banner](../includes/banner.md)]


Note: This feature is supported in release Dynamics 365 (v7.2)

# Introduction
This topic demonstrates how you embed a Power BI report in the **Analytics** tab of a workspace.  For this scenario, we will extend the Reservation Management Workspace in the Fleet Management application to embed an analytical workspace in an **Analytics** tab.

# Prerequisites
+ Access to a developer environment running on Platform Update 8 or later.
+ An analytical report (.PBIX file) authored using Power BI Desktop with a data model sourced from the Dynamics Entity Store Database.

# Overview
Whether you are extending an existing application workspace or introducing one of your own, embedded analytical views can be used to deliver insightful and interactive views of your business data.  The process for adding an analytical workspace tab is broken down into the four distinct steps:

1. Add a PBIX file as a Dynamics 365 Resource
2. Define Analytical Workspace Tab
3. Embed the PBIX Resource in the Workspace tab
4. Optionally - Add extensions to customize the view
 
Note:  For more information on creating analytical reports, the Getting started with Power BI Desktop article is a great source for insights on authoring compelling analytical reporting solutions.




