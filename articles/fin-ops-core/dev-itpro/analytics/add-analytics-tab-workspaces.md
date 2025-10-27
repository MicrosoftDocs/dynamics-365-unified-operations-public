---
title: Add analytics to workspaces by using Power BI Embedded
description: Learn how to embed a Power BI report on the Analytics tab of a workspace, including prerequisites and how to add resources and controls.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 10/22/2025
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update
---

# Add analytics to workspaces by using Microsoft Power BI Embedded

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This feature is supported in finance and operations (version 7.2 and later).

## Introduction

This article shows how to embed a Microsoft Power BI (PBI) report on the **Analytics** tab of a workspace. In this example, you extend the **Reservation management** workspace in the Fleet Management application to embed an analytical workspace on an **Analytics** tab.

## Prerequisites

+ Access to a developer environment that runs Platform update 8 or later.
+ An analytical report (.pbix file) that you created by using Microsoft Power BI Desktop, with a data model sourced from the Entity store database.

## Overview

Whether you extend an existing application workspace or introduce a new workspace, you can use embedded analytical views to deliver insightful and interactive views of your business data. The process for adding an analytical workspace tab has four steps.

1. Add a .pbix file as a Microsoft Dynamics 365 resource.
1. Define an analytical workspace tab.
1. Embed the .pbix resource on the workspace tab.
1. Optional: Add extensions to customize the view.

> [!NOTE]
> For more information about how to create analytical reports, see [Getting started with Power BI Desktop](https://powerbi.microsoft.com/documentation/powerbi-desktop-getting-started/). This page is a great source for insights that can help you create compelling analytical reporting solutions.

## Add a .pbix file as a resource

Before you begin, you must create or obtain the PBI report that you want to embed in the workspace. For more information about how to create analytical reports, see [Getting started with Power BI Desktop](https://powerbi.microsoft.com/documentation/powerbi-desktop-getting-started/).

Follow these steps to add a .pbix file as a Microsoft Visual Studio (VS) project artifact.

1. Create a new project in the appropriate model.
1. In Solution Explorer, select the project, right-click, and then select **Add** \> **New Item**.
1. In the **Add New Item** dialog box, under **Operations Artifacts**, select the **Resource** template.
1. Enter a name that you use to reference the report in X++ metadata, then select **Add**.

    :::image type="content" source="media/analytical-workspace-add.png" alt-text="Screenshot of Add New Item dialog box.":::

1. Find the .pbix file that contains the definition of the analytical report, then select **Open**.

    :::image type="content" source="media/analytical-workspace-select-resource.png" alt-text="Screenshot of Select a Resource file dialog box.":::

After you add the .pbix file as a Microsoft Dynamics 365 resource, you can embed the reports in workspaces and add direct links by using menu items.

## Add a tab control to an application workspace

In this example, you extend the **Reservation management** workspace in the Fleet Management model by adding the **Analytics** tab to the definition of the **FMClerkWorkspace** form.

The following illustration shows what the **FMClerkWorkspace** form looks like in the designer in Microsoft Visual Studio.

:::image type="content" source="media/analytical-workspace-definition-before.png" alt-text="Screenshot of FMClerkWorkspace form before changes.":::

Follow these steps to extend the form definition for the **Reservation management** workspace.

1. Open the form designer to extend the design definition.
1. In the design definition, select the top element that is labeled **Design | Pattern: Workspace Operational**.
1. Right-click, and then select **New** \> **Tab** to add a new control that is named **FormTabControl1**.
1. In the form designer, select **FormTabControl1**.
1. Right-click, and then select **New Tab Page** to add a new tab page.
1. Rename the tab page to something meaningful, such as **Workspace**.
1. In the form designer, select **FormTabControl1**.
1. Right-click, and then select **New Tab Page**.
1. Rename the tab page to something meaningful, such as **Analytics**.
1. In the form designer, select **Analytics (Tab Page)**.
1. Set the **Caption** property to **Analytics**, and set the **Auto Declaration** property to **Yes**.
1. Right-click the control, and then select **New** \> **Group** to add a new form group control.
1. Rename the form group to something meaningful, such as **powerBIReportGroup**.
1. In the form designer, select **PanoramaBody (Tab)**, and then drag the control onto the **Workspace** tab.
1. In the design definition, select the top element that is labeled **Design | Pattern: Workspace Operational**.
1. Right-click, and then select **Remove pattern**.
1. Right-click again, and then select **Add pattern** \> **Workspace Tabbed**.
1. Build the project to verify your changes.

The following illustration shows what the design looks like after these changes are applied.

:::image type="content" source="media/analytical-workspace-definition-after.png" alt-text="Screenshot of FMClerkWorkspace after changes.":::

Now that you've added the form controls that are used to embed the workspace report, you must define the size of the parent control so that it accommodates the layout. By default, both the **Filters Pane** page and the **Tab** page are visible on the report. However, you can change the visibility of these controls as appropriate for the target consumer of the report.

> [!NOTE]
> For embedded workspaces, use extensions to hide both the **Filters Pane** and **Tab** pages, for consistency.

You've now completed the task of extending the application form definition. For more information about how to use extensions to do customizations, see [Customize through extension and overlayering](../extensibility/customization-overlayering-extensions.md).

## Add X++ business logic to embed a viewer control

Follow these steps to add business logic that initializes the Microsoft Report Viewer control embedded in the **Reservation management** workspace.

1. Open the **FMClerkWorkspace** form designer to extend the design definition.
1. Press F7 to access the code behind the code definition.
1. Add the following X++ code.

    ```xpp
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
                // initialize the PBI report control using shared helper
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

1. Build the project to verify your changes.

You've now completed the task of adding business logic to initialize the embedded Microsoft Report Viewer control. The following illustration shows what the workspace looks like after these changes are applied.

:::image type="content" source="media/analytical-workspace-final.png" alt-text="Screenshot of report embedded in the workspace.":::

> [!NOTE]
> You can access the existing operational view by using the workspace tabs that appear below the page title.

## Reference

### PBIReportHelper.initializeReportControl method

This section provides information about the helper class that is used to embed a Power BI report (.pbix resource) in a form group control.

#### Syntax

```xpp
public static void initializeReportControl(
    str                 _resourceName,
    FormGroupControl    _formGroupControl,
    str                 _defaultPageName = '',
    boolean             _showFilterPane = false,
    boolean             _showNavPane = false,
    List                _defaultFilters = new List(Types::Class))
```

#### Parameters

| Name             | Description                                                                                                  |
|------------------|--------------------------------------------------------------------------------------------------------------|
| resourceName     | The name of the .pbix resource.                                                                              |
| formGroupControl | The form group control to apply the Power BI report control to.                                              |
| defaultPageName  | The default page name.                                                                                       |
| showFilterPane   | A Boolean value that indicates whether the filter pane should be shown (**true**) or hidden (**false**).     |
| showNavPane      | A Boolean value that indicates whether the navigation pane should be shown (**true**) or hidden (**false**). |
| defaultFilters   | The default filters for the Power BI report.                                                                 |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
