---
# required metadata

title: Add analytics to workspaces using Power BI Embedded
description: This topic demonstrates how you embed a Power BI report in the Analytics tab of a workspace. 
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
audience: Application user, IT Pro
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: tjvass
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.intro: Platform update 8
ms.dyn365.ops.version: July 2017 update 
---




# Add analytics to workspaces using Power BI Embedded

[!include[banner](../includes/banner.md)]


> [!NOTE]
> This feature is supported in release Dynamics 365 (v7.2) and after.

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

> [!NOTE]
> For more information on creating analytical reports, the [Getting started with Power BI Desktop](https://powerbi.microsoft.com/documentation/powerbi-desktop-getting-started/) article is a great source for insights on authoring compelling analytical reporting solutions.

# Add a PBIX file as a Dynamics 365 Resource
To begin, you'll need to author or obtain the Power BI Report to embed in the workspace.  For more information on creating analytical reports, see [Getting started with Power BI Desktop](https://powerbi.microsoft.com/documentation/powerbi-desktop-getting-started/).
 
To add a PBIX file as an Operations Resource artifact:
1.	Create a new project in the appropriate model
2.	Select the project in the Solution Explorer, then right-click and select **Add** > **New Item** 
3.	In the **Add New Item** form, select the **Resource** template under **Operations Artifacts**
4.	Provide a name to use when referencing the report in X++ metadata then click **Add**
    ![Add new item dialog](media/analytical-workspace-add.png)
5.	Locate the PBIX file containing the analytical report definition and then click **Open**
    ![Select a resource dialog](media/analytical-workspace-select-resource.png)
  
Now that you've added the PBIX file as an Dynamics 365 Resource, you'll be able to embed the reports in workspaces and add direct links using menu items.

# Add a tab control to an application workspace
For this walk-thru, we'll extend the Reservation Management Workspace in the Fleet Management model by adding the **Analytics** tab to the form definition **FMClerkWorkspace**.
 
Here’s how the **FMClerkWorkspace** form appears in the Visual Studio designer:

![FMClerkWorkspace before changes](media/analytical-workspace-definition-before.png)


To extend the form definition for the **Reservation Management** workspace:
1.	Open the form designer to extend the design definition.
2.	Select the top element in the design definition labeled **Design | Pattern: Workspace Operational**.
3.	Right-click then select **New** > **Tab** to add a new control named **FormTabControl1**.
4.	Select **FormTabControl1** in the form designer.
5.	Right-click then select **New Tab Page** to add a new tab page.
6.	Rename the tab page to something meaningful like **Workspace**.
7.	Select **FormTabControl1** in the form designer.
8.	Right-click then select **New Tab Page**.
9.	Rename the tab page to something meaningful like **Analytics**.
10.	Select **Analytics (Tab Page)** in the form designer.
11.	Set the **Caption** property to **Analytics**.
12.	Right-click on the control then select **New** > **Group** to add a new form group control.
13.	Rename the form group to something meaningful like **powerBIReportGroup**.
14.	Select **PanoramaBody (Tab)** in the designer, then drag and drop the control into the **Workspace** tab. 
15.	Select the top element in the design definition labeled **Design | Pattern: Workspace Operational**.
16.	Right-click then select **Remove pattern**.
17.	Right-click again then select **Add pattern** > **Workspace Tabbed**.
18.	Perform a build to verify your changes.
 
Here’s what the design will look like after applying these changes:

![FMClerkWorkspace after changes](media/analytical-workspace-definition-after.png)

Now that you have added the form controls that will be used to embed the workspace report, you will need to define the size of the parent control to accommodate the layout.  By default, the report will be displayed with both the **Filters Pane** and the **Tab** pages in the report visible.  However, you can toggle the visibility of these controls as appropriate for the target consumer of the report.  
 
> [!NOTE]
> For embedded workspaces, we recommend using extensions to hide both the **Filters Pane** and **Tab** pages for consistency.
 
You have completed the task of Extending the application Form definition.  For more information on customizations using extensions, see  [Customization: Overlayering and extensions](../extensibility/customization-overlayering-extensions.md).

# Add X++ business logic to embed a viewer control
To add business logic to initialize the report viewer control embedded in the Reservation Management Workspace:
1.	Open the **FMClerkWorkspace** form designer to extend the design definition.
2.	Press **F7** to access the code behind the code definition.
3.	Add the following X++ code:
```
[Form] 
public class FMClerkWorkspace extends FormRun
{
    private boolean initReportControl = true;
 
    protected void initAnalyticalReport()
    {
        if (!initReportControl)
        {
            return;
        }
 
        // Note: secure entry point into the Workspace's Analytics report
        if (Global::hasMenuItemAccess(menuItemDisplayStr(FMClerkWorkspace), MenuItemType::Display))
        {
            FMPBIWorkspaceController controller = new FMPBIWorkspaceController();
            PBIReportHelper::initializeReportControl('FMPBIWorkspaces', powerBIReportGroup);
        }
 
        initReportControl = false;
    }
 
    /// <summary>
    /// Initializes the form.
    /// </summary>
    public void init()
    {
        super();
        this.initAnalyticalReport();
    }
 
}
```

4. Perform a build to verify your changes.

You have completed the task of Adding business logic to initialize the embedded report viewer control. Here’s what the workspace will look like after applying these changes:

![Report embedded in workspace](media/analytical-workspace-final.png)

> [!NOTE]
> The existing operational view is accessible via the **Workspace Tabs** displayed below the page title.

# Reference

## PBIReportHelper.initializeReportControl Method [AX7.2]
Helper class used to embed a Power BI report (PBIX resource) in a form group control

### Syntax
```
public static void initializeReportControl(
     str                 _resourceName,
     FormGroupControl    _formGroupControl,
     str                 _defaultPageName = '',
     boolean             _showFilterPane = false,
     boolean             _showNavPane = false,
     List                _defaultFilters = new List(Types::Class))
```

### Parameters

| Name | Description |
|---|---|---|
|resourceName|The pbix resource name|
|formGroupControl|The form group control to apply power bi report control.|
|defaultPageName|The default page name.|
|showFilterPane|True show filter pane. Otherwise, false.|
|showNavPane|True show navigation pane. Otherwise, false.|
|defaultFilters|The default power bi report filters|

