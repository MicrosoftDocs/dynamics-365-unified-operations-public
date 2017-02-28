---
# required metadata

title: Power BI Embedded integration
description: With Microsoft Dynamics 365 for Operations, Power BI content developed by partners and ISVs can be embedded directly into the application. Read this topic to learn more about some of the amazing things possible using Power BI Embedded.
author: sericks007
manager: AnnBe
ms.date: 2017-02-15 16 - 19 - 38
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 270754
ms.assetid: ca4b2ccf-d68d-4344-833e-1c45d966246c
ms.search.region: Global
# ms.search.industry: 
ms.author: tjvass
ms.dyn365.ops.intro: 01-02-2017
ms.dyn365.ops.version: Platform update 4

---

# Power BI Embedded integration

With Microsoft Dynamics 365 for Operations, Power BI content developed by partners and ISVs can be embedded directly into the application. Read this topic to learn more about some of the amazing things possible using Power BI Embedded.

Overview
--------

Dynamics 365 for Operations integrates with [Microsoft Power BI](http://www.powerbi.com/) to enable data mash-up scenarios that require access to external data sources supported through Power Query. End-users can personalize workspaces by embedding tiles that are hosted on PowerBI.com. Users can also add direct links to access and interact with reports hosted on Power BI.com without leaving the application. Power BI content (PBIX) developed by partners and ISVs can be embedded directly into the application. PBIX files associated with a model file are automatically published in Power BI Embedded as part of the application deployment process. Optionally, you can add X++ extensions for embedded reporting scenarios that require:

-   Drill-down navigation into detailed pages in response to user interactions.
-   Report filters based on user and session context information, such as company or date range.
-   Ability to navigate directly into a specific tab within a Power BI report via menu items.

For more information about customizations using extensions, see [Customization: Overlayering and extensions](customization-overlayering-extensions.md).

## Why would I want to use Microsoft Power BI Embedded?
While both Power BI services are available, it's important to know which is best suited to support target application scenarios. The following illustration offers a feature comparison across services.[![power-bi-embedded-overview](https://msdynamics.blob.core.windows.net/media/2017/02/Power-BI-Embedded-Overview-1024x487.png)](https://msdynamics.blob.core.windows.net/media/2017/02/Power-BI-Embedded-Overview.png) Read the [Power BI Embedded FAQ](https://docs.microsoft.com/en-us/azure/power-bi-embedded/power-bi-embedded-faq) to learn more about the Power BI Embedded Service.

## Advantages of Power BI Embedded
-   **Deliver Power BI workspaces and reports with the application** - If you are a power user or a business analyst, you can tweak ready-made reports or create new ones using Power BI tools. As a developer, you can use the reports developed by your users and create rich navigation experiences within the product as workspaces. If you are in the partner and ISV community, you can build rich workspaces with Power BI experiences and ship as part of your solution.
-   **Power BI Embedded Service license bundled with Dynamics 365 for Operations** - If you are an ISV or a systems integrator, you can package Power BI enabled workspaces (including navigational experiences) as part of a Lifecyle Services (LCS) solution. Your customers would get the same experience without requiring a PowerBI.com subscription - it just works with Dynamics 365 for Operations.
-   **Drill-down into detailed pages from Power BI** - The visuals are the starting point for action. Your users can drill down to business processes and pages to act on issues that they uncover right away. The visuals provide the ability to filter data and uncover trends - action forms reflect just the set of data that needs attention.
-   **Secure access to Power BI reports using menu items** - As a developer, you can use familiar programming concepts available in Dynamics 365 for Operations because we have extended the same concepts to Power BI-based workspaces. You can create new workspaces or extend existing workspaces by adding a Power BI-driven overview page. Developers will be able to associate menu items with Power BI reports and include them as links in workspaces. These menu items will be securable using the role and task based security in Dynamics 365 for Operations.
-   **Filter reports based on application context** - You can build navigation experiences by passing one or more filters to Power BI reports. For example, depending on user’s actions or context, you can filter the Power BI report to reflect data from one business unit or a given product - without the user having to filter the data. You can define drill thru links to Dynamics 365 for Operations forms that take users directly into the transactional details forms.

## Service availability
Power BI Embedded is available in most data centers now. You can check the latest availability on [Azure status](https://azure.microsoft.com/status/).

