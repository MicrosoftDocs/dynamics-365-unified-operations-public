---
# required metadata

title: Power BI integration
description: This article explains how you can use the features and services that are included in Microsoft Power BI to access, explore, and gain insight from your data. 
author: MilindaV2
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: PowerBIConfiguration
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 31001
ms.assetid: bf6eff60-4a30-4338-a55f-1f2a97d3debe
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Power BI integration

[!include[banner](../includes/banner.md)]

Power BI is a suite of business analytics tools to analyze data and share insights. Using Power BI tools, you can explore data and quickly create rich reports and dashboards. You and your colleagues can then use these reports on many devices interactively. Dynamics 365 for Finance and Operations, Enterprise edition uses Power BI for data exploration. 

## Data exploration with Power BI 
There are different types of reporting in Dynamics 365 for Finance and Operations, Enterprise edition:

Chart controls are used for building embedded experiences that require visuals. 

SSRS is an engine designed for pixel-perfect, formatted reports that often require printing. We leverage SSRS for document style reports such as invoices and purchase orders. Our investments on SSRS integration focus on document generation and printing scenarios. 

For all non-document reports or reports that don’t need to be printed, we want to embrace Power BI.
 
We have used the word “self-service reports” or “ad-hoc reports” in the past when referring to Power BI. We will use the word “data exploration” in the future.  There’s a subtle shift in paradigms hidden behind this change of name. Self-service reports were reports that the users themselves created (or a power-user created it and shared with others, who continued to tweak it to their needs). Often, users need to change the shape of a chart, add a new column, change the grouping or simply create a new view of data. While we could think of it as a report, as a user you are trying to understand the data, exploring it, pivoting it around columns, changing the shape of charts. Technologies of the past didn’t allow exploring large volumes of data interactively. So users had to resort to creating “reports” – many views of the same data.

With Power BI (and many thanks to in-memory database technologies in SQL Server), a report is a just the starting point for interactive data exploration. Charts in a Power BI report beg to be clicked, visuals change shape interactively and data can be filtered with ease. Users can tweak existing reports with ease and create their own views of the data. The reports can be shared and teams can collaborate over data.

So while you may use the term “report” when referring to Power BI artifacts, you should think about the larger scenario at play. Your users are exploring data! Power BI is the tool of choice when you are addressing data exploration and visualization needs.
See [Information access and reporting](information-access-reporting.md) for a detailed discussion on reporting concepts in Dynamics 365 for Finance and Operations, Enterprise edition.

## Ready-made Power BI content
You can use ready-made Power BI reports right away. There are 2 flavors of Power BI content available:

- Power BI content available in Lifecycle Service (LCS) 
- Power BI content packs distributed in PowerBI.com marketplace 

Depending on your version, either one of both of these type of content can be used.

### Power BI content available in Lifecycle Service (LCS)
Lifecycle services (LCS) is a service operated by Microsoft. LCS is a service that can manage your Dynamics 365 for Finance and Operations, Enterprise edition environments. Power BI reports, developed using Entity store, are distributed in LCS as implementation assets. You will find content developed by Microsoft as well as ISVs and partners in LCS.

We will continue to release Power BI content based on the Entity store in the future. Please see the [Roadmap](https://roadmap.dynamics.com). 

### Power BI content packs distributed in PowerBI.com marketplace 
There are several Power BI content packs in PowerBI.com marketplace. While these content packs will continue to be supported until further notice, our future investments into content packs will be based on Entity store and released via Lifecycle Services.
For more information about the content, see [Power BI content recently released](power-bi-content-released.md).

## Extend, author, and distribute Power BI reports
You should use the ready-made Power BI content as a first step. You have the ability to modify ready-made reports or extend them using capabilities built into PowerBI.com. In addition to modifying ready-made reports, you can also extend them using Power BI authoring tools such as PowerBI desktop. You can also create new reports. There are several approaches to authoring new PowerBI reports.

### High volume, near-real time “operational Power BI reports” authored using Entity store 
Entity store is an operational data store purpose built for Power BI integration. A business analyst or a developer can create high volume, near-real time Power BI reports using Entity store using PowerBI desktop, the authoring tool for PowerBI reports. These reports must be distributed to your users (similar to other developer created artifacts) via LCS.

Reports authored using Entity store leverage DirectQuery technology which enables creation of reports over large volumes of data. Reports authored using DirectQuery technology does not cache data in PowerBI.com service; data is always stored with Dynamics 365 for Finance and Operations, Enterprise edition.

For an overview of Power BI integration with Entity store, see [Overview of Power BI integration with Entity store](power-bi-integration-entity-store.md). For more information on authoring reports with Entity store, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md). 

If you are upgrading from AX 2012, you can upgrade cubes to Aggregate measurements that use Entity store. You can then create PowerBI reports using Entity store. For more information, see [Migrate an upgraded Dynamics AX 2012 R3 sales cube to the entity store](migrate-upgraded-cube-entity-store.md)

### Self-service “Data mash-up” reports authored using OData
Data mash-up is a term used to refer to ad-hoc, self service reports that combine data from multiple sources. As a power user (or a business analyst), you can create Power BI reports using OData end-points. 

Dynamics 365 for Finance and Operations, Enterprise edition is a first-class data source for Power BI authoring tools, such as Excel and Power BI Desktop. Data entities are exposed as data feeds by using OData V4. These data entities include both standard data entities and aggregate data entities that can provide summarized and calculated data in the OData feed. Dynamics 365 for Finance and Operations, Enterprise edition data feeds authenticate users and enable access, based on security permissions that are defined. Any client tool that supports the OData protocol can consume the data securely.

You can access OData endpoints via the URL https://<your Dynamics 365 URL>/Data 

OData endpoints are ideal for quick and convenient data mash-ups. However, for authoring reports that extract large volumes of data Entity store approach is recommended. To create a Power BI report and a dashboard using OData endpoints, see [Create a Power BI report and dashboard](create-powerbi-report-dashboard.md) for more information. Note that this article PowerQuery and PowerPivot tools. You could use the Power BI desktop tool to author reports using OData endpoints similarly.

### Authoring Power BI reports with Excel
In addition to using PowerBI desktop authoring tool, you can use “Power tools” incorporated into Excel to create visualizations. You may have a large number of users within your organization that use Excel every day. For a quick “one-off report”, using Excel may be the best option for them.

There are several scenarios where you can use Excel.

-	A user can export data from a page in Dynamics 365 into Excel. Using the Powerview add-in built into Excel, the data can be visualized. This Excel workbook can be used as a standalone visualization. In addition, this report can be imported into PowerBI.com service.
-	Using the PowerQuery, extension in Excel, a user can combine data in another worksheet (or imported from OData endpoints) with external data. Resulting data can be visualized using Powerview.
-	Using PowerPivot extension in Excel, a user can ingest a larger amount of data into Excel.

For more information on PowerBI integration with Excel, see [Create a Power BI report](create-powerbi-report-data.md).

Consider using export to Excel functionality for ad-hoc “one-off” reports. For reports that are shared with a group of users, you should consider authoring them using Entity store.

## Sharing and using reports in PowerBI.com
PowerBI.com, a service offered by Microsoft, enables creation of dashboards, reports as well as collaboration with a group of users. Regardless of how you author reports, your reports can be shared with users by uploading them into PowerBI.com service (also called “publishing”).

Once uploaded, your reports can be viewed, tweaked and explored by your users either on the web (when they are connected to the internet at home or at office) or using apps in any of the devices.

For more information on PowerBI concepts, see the [Power BI documentation](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-how-should-i-share-my-dashboard/).

## Pinning Power BI content into the Dynamics 365 for Finance and Operations, Enterprise edition client
PowerBI.com can be used on its own as a reporting and dashboard solution for your organization or business unit. However, users can also pin tiles and reports from their own PowerBI.com accounts to Dynamics 365 for Finance and Operations, Enterprise edition workspaces. PowerBI content in Dynamics 365 provides contextual insights that are related to business operations.

Dynamics 365 supports pinning two types of objects from PowerBI.com: namely, tiles in PowerBI.com dashboards and reports.

Before you can proceed, you need to configure PowerBI in your Dynamics 365 environment.

### One-time configuration of PowerBI.com integration
An administrator needs to perform this operation in your Dynamics 365 for Finance and Operations, Enterprise edition environment before you can pin tiles or reports. This operation needs to be performed only once per environment. For instructions, see [Configure Power BI integration for workspaces](configure-power-bi-integration.md) 

### Pinning PowerBI.com tiles 
Power BI tiles that are pinned to the Dynamics 365 client provide insightful visuals at a glance. They also let users open PowerBI.com for interactive analysis. For more information see [Connect to Power BI for the first time](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics/configure-power-bi-integration#connect-to-power-bi-from-dynamics-365-for-operations-for-the-first-time).

### Pinning PowerBI.com reports into workspaces
As a power user, a business analyst or ad a developer, you have the ability to create reports with Power BI desktop using Entity store. Not only are these reports rich and interactive, you can empower your users to make changes without relying on another person. 

While reports in PowerBI.com are powerful and interactive on it’s own, these reports can be pinned into workspaces. Your users can pin the reports into workspaces themselves. For more information on pinning reports into workspaces, see [Pin Power BI reports to workspaces](pin-power-bi-reports.md). 



