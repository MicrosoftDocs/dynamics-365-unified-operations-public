---
# required metadata

title: Power BI Embedded integration
description: Power BI content developed by partners and ISVs can be embedded directly into the application. Read this topic to learn more about some of the amazing things possible using Power BI Embedded.
author: TJVass
manager: AnnBe
ms.date: 07/26/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Platform, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 270754
ms.assetid: ca4b2ccf-d68d-4344-833e-1c45d966246c
ms.search.region: Global
# ms.search.industry: 
ms.author: tjvass
ms.search.validFrom: 2017-02-28
ms.dyn365.ops.version: Platform update 4

---

# Power BI Embedded integration

[!include[banner](../includes/banner.md)]

Power BI content developed by partners and ISVs can be embedded directly into the application. Read this topic to learn more about some of the amazing things possible using the Power BI Embedded integration.

Overview
--------

Microsoft Dynamics 365 for Finance and Operations, Enterprise edition integrates with [Microsoft Power BI](http://www.powerbi.com/) to enable data mash-up scenarios that require access to external data sources supported through Power Query. End-users can personalize workspaces by embedding tiles that are hosted on PowerBI.com. Users can also add direct links to access and interact with reports hosted on PowerBI.com without leaving the application. Power BI content (PBIX) developed by partners and ISVs can be embedded directly into the application. PBIX files associated with a model file are automatically published in Power BI Embedded as part of the application deployment process. Optionally, you can add X++ extensions for embedded reporting scenarios that require:

-   Drill-down navigation into detailed pages in response to user interactions.
-   Report filters based on user and session context information, such as company or date range.
-   Ability to navigate directly into a specific tab within a Power BI report via menu items.

For more information about customizations using extensions, see [Customization: Overlayering and extensions](..\extensibility\customization-overlayering-extensions.md).

## Why would I want to use Microsoft Power BI Embedded?
While both Power BI services are available, it's important to know which is best suited to support target application scenarios. The following illustration offers a feature comparison across services.

[![power-bi-embedded-overview](https://msdynamics.blob.core.windows.net/media/2017/02/Power-BI-Embedded-Overview-1024x487.png)](https://msdynamics.blob.core.windows.net/media/2017/02/Power-BI-Embedded-Overview.png) 

Read the [Power BI Embedded FAQ](https://powerbi.microsoft.com/en-us/documentation/powerbi-frequently-asked-questions/) to learn more about the Power BI Embedded Service.

## Advantages of Power BI Embedded
-   **Deliver Power BI workspaces and reports with the application** - If you are a power user or a business analyst, you can tweak ready-made reports or create new ones using Power BI tools. As a developer, you can use the reports developed by your users and create rich navigation experiences within the product as workspaces. If you are in the partner and ISV community, you can build rich workspaces with Power BI experiences and ship as part of your solution.
-   **Power BI Embedded Service license bundled with Finance and Operations** - If you are an ISV or a systems integrator, you can package Power BI enabled workspaces (including navigational experiences) as part of a Lifecyle Services (LCS) solution. Your customers would get the same experience without requiring a PowerBI.com subscription - it just works with Finance and Operations.
-   **Drill-down into detailed pages from Power BI** - The visuals are the starting point for action. Your users can drill down to business processes and pages to act on issues that they uncover right away. The visuals provide the ability to filter data and uncover trends - action forms reflect just the set of data that needs attention.
-   **Secure access to Power BI reports using menu items** - As a developer, you can use familiar programming concepts available in Finance and Operations because we have extended the same concepts to Power BI-based workspaces. You can create new workspaces or extend existing workspaces by adding a Power BI-driven overview page. Developers will be able to associate menu items with Power BI reports and include them as links in workspaces. These menu items will be securable using the role and task based security in Finance and Operations.
-   **Filter reports based on application context** - You can build navigation experiences by passing one or more filters to Power BI reports. For example, depending on user’s actions or context, you can filter the Power BI report to reflect data from one business unit or a given product - without the user having to filter the data. You can define drill thru links to Finance and Operations forms that take users directly into the transactional details forms.

## Service availability
**The Power BI Embedded service is automatically deployed and configured for all cloud-hosted, multi-box deployments.**  Because the service relies on Azure services, application analytical workspaces and reports are unavailable in one-box environments.  The Power BI Embedded service is already available in most Azure data centers.  You can always check the latest availability [here](https://azure.microsoft.com/status/).  
 
**Note:** The Dynamics 365 team is pursuing a solution that will enable analytical workspaces in a one-box environment without requiring customers to host their own instance of the Power BI Embedded service.  Keep an eye out for announcements on the [Dynamics 365 Roadmap](http://roadmap.dynamics.com) site.
 
## Frequently Asked Questions (FAQ)

### Can I customize the Power BI embedded reports?
Yes, simply install Power BI Desktop onto a 1Box to get started using steps described [here](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/analytics/author-distribute-power-bi-reports?toc=dynamics365/unified-operations/fin-and-ops/toc.json).
 
-   **Q:    Do customers need to purchase a separate Power BI license to use the new embedded analytics?** -->
**No** – However, a Power BI Pro license is required to connect to Entity Store using Direct Query from PowerBI.com
 
-   **Q:    Can I perform data mashups using external data in the Embedded Reports?** -->
**No**, not at this time.
 
-  **Q:    Can I secure data to only those companies I have access to?** -->
**Yes**, the single company view prevents users from accessing data from companies they don’t have access to.  For more information on securing custom solutions, follow guidance provided [here](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/analytics/secure-analytical-workspaces?toc=dynamics365/unified-operations/fin-and-ops/toc.json).
 
-  **Q:    How is currency displayed across multiple companies?** --> 
As a **system currency**. (System administration > Setup > System parameters)
 
-  **Q:    Can I drill on summary balances back into Dynamics 365?** --> 
**Yes**, you are able to drill into the details within a Power BI report. There is limited support for drill down into Dynamics 365.
 
-  **Q:    What languages are currently supported?** --> 
**English** only however the PBI team has additional planned.
 
-  **Q:    Can I access Analytical Workspaces & Reports in Local Business Data?** -->
**No**, not at this time.  Systems of Intelligence functions rely on Cloud hosted solutions.





