---
title: Build the Rental Charge Type form
description: Learn about building rental charge type forms, including prerequisites, key concepts, and overviews on various forms.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/09/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9b4f244c-f058-416c-b3c2-6f4ca29c8db8
---

# Build the Rental Charge Type form

[!include [banner](../includes/banner.md)]

In this lab, you create a Simple List form. A Simple List form can show reference or secondary data that has six or fewer fields. For example, the form that you create lists and describes the types of rental charges.

## Prerequisites

For this tutorial, you need to access the environment by using Remote Desktop and be provisioned as an administrator on the instance. For more information, see [Access Instances](../dev-tools/access-instances.md).

## Overview

To create the form, start from the existing form, **FmtChargeType**. This form uses the Simple List pattern. The following illustration shows the **FmtChargeType** form with the required controls from the Simple List pattern.

:::image type="content" source="./media/rentalcharge1.png" alt-text="Screenshot of FmtChargeType form.":::

Adhering to the form pattern ensures that this Simple List form has the same structure and layout as other Simple List forms.

## Key concepts

- Create a Simple List form by using a pattern.
- Bind a table to the form.
- Add controls to the form.
- View the form by using Visual Studio and a browser.

## Setup

### Import the tutorial project and transactional data

Use Visual Studio to import the tutorial project. The tutorial project includes the artifacts that you use to complete this tutorial. Use Visual Studio to open the FMTutorial project and load the data for the tutorial. You use the FMTDataHelper class to load data for the Fleet Management tutorial. If this tutorial is the first tutorial you're working on, review [Access Microsoft Instances](../dev-tools/access-instances.md) and make sure you provision your administrator user if you're working on a local VM.

1. Download the Fleet Management sample from <https://github.com/Microsoft/FMLab>, save it to **C:\\**, and unzip it.
1. On the desktop, double-click the Visual Studio shortcut to open the development environment.
1. On the **Finance and operations** menu, select **Import Project**.
1. In the **Import Project** window, next to the **Filename** text box, select the ellipsis button.
1. In the **Select the file to import** window, browse to `C:\FMLab`, select `FMTutorialDataModel.axpp`, and then select **Open**.
1. In the **Project file location** text box, enter `C:\FMLab`.
1. Select the **Overwrite Elements** option, and the **Current solution** radio button. The following illustration shows the completed **Import Project** dialog box.

    :::image type="content" source="./media/rentalcharge2.png" alt-text="Screenshot of completed Import Project dialog box.":::

1. Select **OK**.
1. In **Solution Explorer**, expand **Classes**. Under the **FMTutorial** project, right-click **FMTDataHelper**, and then select **Set as Startup Object**.
1. On the **Build** menu, select **Rebuild Solution**. Use the rebuild to make sure that all of the files in the project are built regardless of timestamps. You can view the build progress in the **Output** window.
1. After the build completes, press **Ctrl+F5** to run the project. The browser opens and runs the class that imports the data.

## Open the FMTutorial project

Use Visual Studio to open the FMTutorial project. If you have Visual Studio open and already loaded the FMTutorial project, you can continue to the next section.

1. If the development environment isn't already open, on the desktop, double-click the Visual Studio shortcut to open the development environment.
2. On the **File** menu, select **Open** &gt; **Project/Solution**.
3. In the **Open Project** dialog box, browse to `C:\FmLab\FMTutorial`, select the **FMTutorial** solution, and then select **Open**.
4. The FMTutorial project appears in **Solution Explorer**.

## Use a template to create the form

Use Visual Studio to create the **FmtChargeType** form. Use a template for building the Simple List form. Add a data source to the form and add fields to the data grid.

1. In **Solution Explorer**, right-click the **FMTutorial** project, point to **Add**, and then select **Existing Item**.
1. In the **Add Existing Item** window, browse to `C:\FmLab`, select **AxForm_FmtChargeType**, and then select **Add**. The **FmtChargeType** form appears at the bottom of the **FMTutorial** project in **Solution Explorer**.
1. In **Solution Explorer**, double-click **FmtChargeType**. The form opens in the Form designer.
1. Add the **FmtChargeType** table as the data source for the form. Right-click **Data Sources**, and then select **New Data Source**. A data source node is added.
1. Select the data source node from the previous step. In the **Properties** window, populate the following properties with the specified values.

    | **Property** | **Value**|
    |--------------|------|
    | Table        | FMTChargeType|
    | Name         | FMTChargeType *Be sure to specify the value for the Table property first. This property automatically updates to use that same value.* |

    The following illustration shows **Data Sources** after you add the **FMTChargeType** table.

    :::image type="content" source="./media/rentalcharge3.png" alt-text="Screenshot of Data Sources after you add FMTChargeType table.":::

1. In the Form designer, select **Design**. In the **Properties** window, populate the following properties with the specified values.

    | **Property** | **Value**                                                                    |
    |--------------|------------------------------------------------------------------------------|
    | Caption      | Rental charge types *This is the label that appears at the top of the form.* |
    | Data Source  | FMTChargeType *Use this property to specify the data source for the form.*   |

1. In the Form designer, select **Design** > **Grid**.
1. Bind the FMTChargeType data source to the grid that appears in the simple list form. In the **Properties** window, in **Data Source**, enter **FMTChargeType**.
1. You have to specify the data source before you add fields to the grid. You can then use the fields from the data source to add columns to the grid. Add two fields from the data source to the grid. The fields you add appear as columns on the Simple List form. Expand the FMTChargeType data source **Fields** node in the left pane. Press **Ctrl** and then select the following fields:
    - ChargeType
    - Description

1. Drag the selected fields to **Design** > **Grid** in the right pane. The following illustration shows the grid after the grid node is expanded and the two fields are added.

    :::image type="content" source="./media/rentalcharge4.png" alt-text="Screenshot showing grid after the grid node is expanded.":::

1. In the Form designer, select **Design** > **CustomFilterGroup** > **QuickFilter**.
1. In the **Properties** window, select **TargetControl**, and then select **Grid** to bind the **QuickFilter** control to the grid on the form.
1. Select **File** > **Save** **FmtChargeType**.

## View the form

Use Visual Studio to build and run the **FmtChargeType** form.

1. In **Solution Explorer**, right-click the **FmtChargeType** form, and then select **Set as Startup Object**.
1. Press Ctrl+F5 to build and run the form.
1. The form opens in Microsoft Edge.
1. To add a rental charge type, select **New** in the Action Pane at the top of the form. Add the following information.

    | **Rental Charge Type** | **Description** |
    |------------------------|-----------------|
    | cleaning               | Cleaning fee    |

1. In the Action Pane, select **Save**.
1. Refresh the browser to see the new record in the list.
1. The form opens in view mode. Select **Edit** in the Action Pane to switch the form into edit mode. To return to view mode, select **Options** and then **Read mode**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
