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

For more information on creating analytical reports, [Getting started with Power BI Desktop](https://powerbi.microsoft.com/en-us/documentation/powerbi-desktop-getting-started/) is a great source for insights on authoring compelling analytical reporting solutions.

# Secure analytical views provided through embedded Power BI reports
Power BI report filters and the filter pane serve as a mechanism to pass session context into the report embedded in **Analytics** tab. Toggling filter pane visibility is not a security feature.  Using Power BI report filters and hiding/showing the filters pane is a user experience decision for the application designer. 
 
Row level security defined in Dynamics 365 for Operations is not inherited by Power BI reports.  Instead, application developers can secure the workspace or secure the report.

## Securing Analytical Workspace on the Analytics tab	
Analytical workspaces are embedded Power BI reports displayed in a within form control.  Without this step, anyone who has access to the workspace would see the **Analytics** tab and have access to PBI report.
 
Steps:
1. Add an menu item for the analytical workspace.
2. Form initialization verifies user has access to menu item using **hasMenuItemAccess** API: 
```
// Note: secure entry point into the Workspace's Analytics report
if (Global::hasMenuItemAccess(menuItemDisplayStr(FMClerkWorkspace), MenuItemType::Display))
{
    FMPBIWorkspaceController controller = new FMPBIWorkspaceController();
    PBIReportHelper::initializeReportControl('FMPBIWorkspaces', powerBIReportGroup);  
}
``` 

This logic will prevent initialization of the Power BI Viewer control resulting in an empty tab section on the form.  By default, empty tabs are automatically hidden by the framework.  As a result, the **Analytics** tab is hidden and inaccessible in cases where the user does not have access to the menu item associated with the analytical workspace.   


## Secure analytical reports 
Embedded Power BI reports in the application are secured using menu items.  Users attempting to directly access a Power BI report using an AX menu item will receive an error.
 
Steps:
1. Add a menu item for the Report or specific tab. By default, the first tab of the report will be displayed if no other tab is selected.
2. Link the menu item to the **PowerBIEmbedded_App** configuration key.
 
The menu item will now be associated with the availability of the Power BI Embedded service.  In cases where the service is unavailable, the links for the menu items will be removed from the application.
 
# Secure analytical workspaces and reports by company
Power BI workspaces and reports can be secured by Company (e.g. **DataAreaID**).  The following steps must be applied by application solutions for company-level security in analytical workspaces and reports.  
 
In this scenario, the sales manager from Contoso USA is presented with analytical workspaces and reports limited to data related to Contoso USA. The report viewer must not have access data associated to any other company without switching company context.

Steps:
1. Open the analytical report in Power BI Desktop by double-clicking the resource in a Visual Studio project.
1. On the **Modeling** tab, click **Manage Roles**. 
1. Create a new role called **CompanyFilter** against a column in the data model containing the **Company** field. A **COMPANY** field must be present in the data model to restrict access by company.
1. In the **Table** filter DAX expression enter the following: **[COMPANY] = USERNAME()**.
1. To make sure the rules are working, on the **Modeling** tab, click **View as Roles**, and then enter the following:

The reports will now show data as if you were running the USMF company. For more information, see the article on [Row level security with Power BI Embedded](https://docs.microsoft.com/en-us/azure/power-bi-embedded/power-bi-embedded-rls).


