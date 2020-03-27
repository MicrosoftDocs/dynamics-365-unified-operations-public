---
title: Impact analysis report in Lifecycle Services (LCS)
description: This topic provides information about the Impact analysis report in Microsoft Dynamics Lifecycle Services (LCS).
author: dfroslieMSFT 
manager: AnnBe
ms.date: 07/02/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dfroslie
ms.search.validFrom: 2019-05-31 
ms.dyn365.ops.version: 10.0.2 

---

# Impact analysis report in Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]
[!include [private preview banner](../includes/private-preview-banner.md)]

The **Impact analysis** report can help you focus your testing efforts for a new release. It provides insight into the Microsoft code that was changed in the release, together with usage information for the production environments that are associated with the project in Microsoft Dynamics Lifecycle Services (LCS). This content provides an overview of the capabilities and also some important considerations. However, the report doesn't provide comprehensive information. Therefore, you should use it in combination with other tools when you're planning test activities for a release.

## Code churn

One key measure in the report is the amount of code change, or churn, that Microsoft made for selected models in recent releases. Code change measures the number of lines of code that were changed, added, or deleted. The report has a code change measure for each file check-in that contributed to a release.

Code changes can be aggregated to the level of a specific module by using a standardized naming convention that is part of the Microsoft engineering system. In this way, you can determine the relative amount of change in different parts of the product for one or more releases.

In addition to filtering code changes by the release and module, you can filter them by the phase of the engineering cycle. The Engineering branch is where changes are made before the release is made available as a preview. This branch has most of the changes. The Stabilization branch includes changes that are made between the preview and general availability of the release. The ability to filter for changes that were made during stabilization can be useful for organizations that start their release review and testing when the release is made available as a preview.

## Usage

The second key measure in the report is the form-based usage of the product in the production environments that are associated with the active LCS project. This usage is measured by summing the user interactions for forms. A user interaction is an event that is logged whenever interaction is triggered between the web client and the service. The most frequent type of user interaction is mouse or keyboard input by a user. However, system-generated interactions can also be counted.

By using the same naming convention that is used for code churn, you can have the usage information summed to the module level. The **Custom** module represents forms that weren't provided by Microsoft.

The usage information isn't tied to the release filters. Instead, it's time-based and has two levels of detail. For module-based visualizations, the data is from the last 95 days of usage in the production environments that are associated with the active LCS project. For form-based visualizations, the data is from the last 35 days of usage in the production environments that are associated with the active LCS project. These time frames were chosen because they offer a compromise between volume of data and sufficient history to help guarantee coverage of activities that occur only monthly or quarterly.

## Important considerations

There are a few important considerations when you use the report:

- The tool uses the number of lines of code that were changed (added, updated, or deleted) as an approximation of change impact for the release. Although there is reasonable correlation between the number of lines of code that were changed and the impact, be aware that any single line of code change can cause impact.
- Not all Microsoft models are included in the code change analysis. Platform changes aren't considered. Additionally, changes in other lower-level models, such as Ledger, CaseManagement, and ApplicationCommon, aren't considered. The models that are included are identified in the code change details in the report.
- Use the report together with the documentation for the release to gain a functional view of the changes.
- The report shows all code changes, regardless of whether the related features are enabled. If a feature is disabled through feature control capabilities, the code changes should have limited impact.
- The production usage is based on user interactions with the web client. Other uses of the system, such as batch processing or integration scenarios, are excluded.
- Code changes from solutions from independent software vendors (ISVs), and code changes from implementation-specific extensions, are excluded.

In summary, the report provides an approximation of code change and usage. In combination with other activities and tools, it can be useful for assessing risk in a release.
