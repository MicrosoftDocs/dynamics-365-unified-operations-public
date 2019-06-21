---
title: Impact analysis report
description: This topic provides information about the impact analysis report in Lifecycle Services (LCS).
author: dfroslie
manager: AnnBe
ms.date: 10/18/2017
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
ms.search.scope: AX 2012, Operations
# ms.tgt_pltfrm: 
ms.custom: 13301
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ntecklu
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Impact Analysis Report in Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

The Impact Analysis report can help focus testing efforts for a new release by providing insight into what Microsoft code has changed in the release along with usage information for the Production environment(s) associated with the LCS project.  This document provide an overview of the capabilities along with some important considerations.  The report does not provide comprehensive information, so the report information should be used in combination with other tools when planning test activities for a release.

## Code Churn

A key measure in the report is the amount of code change, or churn, that Microsoft made for selected models for recent releases.  Code change is the number of lines of code that were changed, added, or deleted.  The report has a code change measure for each file check-in that contributed to a release.

Code changes can be aggregated to a module level using a standardized naming convention that is part of the Microsoft engineering system.  This enables a user to determine the relative amount of change in different parts of the product for one or more release.

Besides release and module filters, the code changes can be filtered based on the phase of the engineering cycle.  The Engineering branch is where changes are made before the release is made available as a preview.  This branch has the majority of the changes. The Stabilization branch includes changes made between preview and general availability of the release.  Filtering on changes made during Stabilization can be useful for organizations who start their release review and testing with the preview.

## Usage

The second key measure in the report is the form based usage of the product in the Production environments(s) associated with the active LCS project.  This is measured by summing the user interactions for forms.  A user interaction is an event that is logged whenever interaction is triggered between the web client and the service.  The most common user interaction would be mouse or keyboard input by a user, but system generated interactions could also be counted.

Using the same naming convention as code churn, the usage information is summed to a module level.  The Custom module represents forms that were not provided by Microsoft.

The usage information is not tied to the Release filters but is time based with two levels of detail.  When looking at module based visualizations, the data is from the last 95 days of usage in the Production environment(s) associated with the active LCS project.  When looking at form based visualizations, the data is from the last 35 days of usage in the Production environment(s) associated with the active LCS project.  The reason for these time frames is a compromise between volume of data and enough history to ensure coverage of activities that happen only monthly or quarterly.

## Important considerations

There are a few important considerations when using the report:

- The tool uses lines of code changed (added, updated, or deleted) as an approximation of change impact for the release.  While there is reasonable correlation between the number of lines of code changed and impact, be aware that any single line of code change could be impactful.
- Not all Microsoft models are included in the code change analysis.  Platform changes are not considered, nor are other lower level models such as Ledger, CaseManagement, ApplicationCommon, and others.  The models included are identified in the code change detail in the report.
- Use the report along with the release notes to provide a functional view of the changes.
- The report will show all code changes regardless of the state of feature enablement.  If a feature is disabled using feature control capabilities, the code changes should have limited impact.
- The Production usage is based on user interactions with the web client.  Other uses of the system, such as batch processing or integration scenarios, are not included.
- Code changes from ISV solutions or implementation specific extensions are not included.

In summary, the report provides an approximation of code change and usage.  Along with other activities and tools, this can be useful for assessing risk in a release.
