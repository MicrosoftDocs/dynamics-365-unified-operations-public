---
title: Create models and data model elements overview
description: In this tutorial, you'll use Visual Studio's Dynamics 365 menu to create a new model named Fleet Management tutorial.
author: josaw1
ms.author: josaw
ms.topic: overview
ms.date: 03/30/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 1b7789f4-12c1-480b-bb39-c354b5b03276
---

# Create models and data model elements overview

[!include [banner](../includes/banner.md)]

In this tutorial, use Visual Studio's Dynamics 365 menu to create a new model named **Fleet Management tutorial**. You also create and edit new model elements.

## Prerequisites

This tutorial requires that you have access to an environment and that you're provisioned as an administrator.

## Keywords

- **Model** - You configure your model to refer to two other models. This configuration enables your model to reference metadata and code elements that are in other packages.
- **Project** - You create a project and then associate your project to your new model. You add elements to your project, which are also added to your model. Specifically, you add an extended data type (EDT). You also add a table that you populate with fields and a method.
- **Designer** - Each time you add an item to your project, a designer is displayed that is tailored to the item type you selected. The **Properties** window adjusts each time a different node of the designer is highlighted. You make updates in the designers and in the **Properties** window.
- **EDT** - Extended data type.

## Create the Fleet Management tutorial model

1. Start Visual Studio by selecting **Run as administrator**.
1. From the **Dynamics 365** menu, select **Model Management &gt; Create model** to open the **Create model** wizard.
1. Enter the following values for model parameters.

    | Property               | Value                                                                                                                    |
    |------------------------|--------------------------------------------------------------------------------------------------------------------------|
    | **Model name**         | FleetMgmntTutorial                                                                                                       |
    | **Model publisher**    | Microsoft Corp                                                                                                           |
    | **Layer**              | isv                                                                                                                      |
    | **Model description**  | This tutorial shows how to build the Fleet Management application by using the Microsoft Dynamics AX  development tools. |
    | **Model display name** | Fleet Management Tutorial                                                                                                |

    > [!NOTE]
    > Your model name must be **FleetMgmntTutorial**. Don't use any other name. In other tutorials, you import a project that overwrites model elements in this model. If the model you create in this tutorial isn't named **FleetMgmntTutorial**, you might not be able to correctly import the project in other tutorials.

1. Select **Next** to go to the next page, and then select **Create New Package**. The model you're creating has its own package and builds its own .NET assembly.

    :::image type="content" source="./media/package_datamodel.png" alt-text="Screenshot of the Select package page." lightbox="./media/package_datamodel.png":::

1. Select **Next** to go to the **Select referenced models** step.
1. Select **Application Platform** and **Application Foundation** as referenced models.

    :::image type="content" source="./media/referencemodels_datamodel.png" alt-text="Screenshot of the Select referenced models page." lightbox="./media/referencemodels_datamodel.png":::

    > [!IMPORTANT]
    > Verify that you select the correct referenced models.

1. Select **Next** to go to the **Summary** step.
1. Verify the information on the summary page, and then select the **Create new project** and **Make this my default model for new projects** check boxes.

    :::image type="content" source="./media/summary_datamodel.png" alt-text="Screenshot of the Summary of data model page." lightbox="./media/summary_datamodel.png":::

1. Select **Finish**. The **New Project** dialog box opens.
1. Under **Templates**, select **Dynamics 365**.
1. Select the **Unified Operations** template.
1. Enter the following values in the fields in the dialog box.

    | Property     | Value           |
    |--------------|-----------------|
    | **Name**     | FMTDataModel    |
    | **Location** | C:\\FMLab       |
    | **Solution** | Add to solution |

    :::image type="content" source="./media/newproject_datamodel.png" alt-text="Screenshot of the New project dialog." lightbox="./media/newproject_datamodel.png":::

1. Select **OK** to create the project.

## Create the FMTAddress extended data type

1. In **Solution Explorer**, right-click **FMTDataModel**, point to **Add**, and then select **New Item**.
1. Under **Dynamics 365 Items**, select **Data Types**.
1. Select **EDT String**.
1. In the **Name** field, enter **FMTAddress**, and then select **Add**.

    :::image type="content" source="./media/newitem_datamodel.png" alt-text="Screenshot of adding a new data type." lightbox="./media/newitem_datamodel.png":::

    This step adds a new EDT model element to the project and opens the EDT designer for the new element, as shown in the following illustration.

    :::image type="content" source="./media/edtelement_datamodel.png" alt-text="Screenshot of FMTAddress added to the project." lightbox="./media/edtelement_datamodel.png":::

1. Select the root node of **FMTAddress** in the designer.
1. In the **Properties** window, in the **Appearance** section, set the following properties.

    | Property        | Value              |
    |-----------------|--------------------|
    | **Help Text**   | Check online help. |
    | **Label**       | Address            |
    | **String Size** | 75                 |

    :::image type="content" source="./media/edtproperty_datamodel.png" alt-text="Screenshot of the Properties window for FMTAddress." lightbox="./media/edtproperty_datamodel.png":::

1. Press **Ctrl+S** to save the EDT.

## Add existing model

Add the other required model element files to the current model and project. Use the **Add existing item** feature to quickly complete this step.

1. In **Solution Explorer**, right-click **FMTDataModel**, point to **Add**, and then select **Existing Item**.
1. Browse to `C:\FMLab\EDT\`.

    :::image type="content" source="./media/existingitem_datamodel.png" alt-text="Screenshot of the Add existing items dialog." lightbox="./media/existingitem_datamodel.png":::

1. Press **Ctrl+A** to select all of the files, and then select **Add**.

## Create the FMTCustomer table

1. In **Solution Explorer**, right-click **FMTDataModel**, and then select **Add &gt; New Item**.
1. In the left pane, expand **Installed**, expand **Dynamics 365 Items**, and then select **Data Model**.
1. In the list of artifacts, select **Table**.
1. In the **Name** field, enter **FMTCustomer**, and then select **Add**. The table designer opens.

   :::image type="content" source="./media/add_datamodel.png" alt-text="Screenshot of adding a table to the data model." lightbox="./media/add_datamodel.png":::

### Add fields to the FMTCustomer table

In the table designer for FMTCustomer, add several fields to the table.

:::image type="content" source="./media/addfields_datamodel.png" alt-text="Screenshot of adding fields to the table.":::

1. To add each field, right-click **Fields**, select **New**, and then choose a type. As you add each field, specify the field name and other values in the **Properties** window, as described in the following table.

    | Type       | Field name     | Property values                                                             |
    |------------|----------------|-----------------------------------------------------------------------------|
    | **Date**   | CCExpiryDate   | Extended Data Type = FMTCCExpiryDate                                        |
    | **String** | Address        | Extended Data Type = FMTAddressHelp Text = Help text for the address field. |
    | **String** | CellPhone      | Extended Data Type = Phone                                                  |
    | **String** | CreditCardNum  | Extended Data Type = FMTCreditCardNum                                       |
    | **String** | DriversLicense | Extended Data Type = FMTDriversLicense                                      |
    | **String** | Email          | String Size = 80Label = Email                                               |
    | **String** | FirstName      | Extended Data Type = FirstName                                              |
    | **String** | LastName       | Extended Data Type = LastName                                               |
    | **String** | License        | String Size = 100Label = License                                            |
    | **String** | Thumbnail      | String Size = 100Label = Thumbnail                                          |

    > [!TIP]
    > For all new fields in the table that reference an EDT, create the field by dragging the EDT element from **Solution Explorer** or **Application Explorer** and dropping it on the **Fields** node of the **FMTCustomer** table in the designer.

    :::image type="content" source="./media/administratorarrow_datamodel.png" alt-text="Screenshot of Solution Explorer with data model." lightbox="./media/administratorarrow_datamodel.png":::

1. Press **Ctrl+S** to save the new fields on the table.

### Add fields to field groups

1. Prepare to add some of the fields to the **AutoSummary** field group by selecting the fields in the following list. To select multiple fields, hold down the Ctrl key while you click each field:
    - **Address**
    - **CCExpiryDate**
    - **CellPhone**
    - **CreditCardNum**
    - **DriversLicense**
    - **Email**
    - **FirstName**
    - **LastName**

1. Expand the **Field Groups** node.
1. Drag the selected fields to the **AutoSummary** node.
1. Use the same technique to add the fields **FirstName**, **LastName**, and **CellPhone** to the **AutoReport** field group.
1. Save the table.

### Add a method

1. Add the X++ method named **fullName** to the **FMTCustomer** table by right-clicking the **Methods** node, and then clicking **New Method**.
1. In the code editor, replace the default method code with the following code.

    > [!TIP]
    > When you type "this.", choose the field from the IntelliSense list.

    ```xpp
    public display FMTName fullName()
    {
        return this.FirstName + ' ' + this.LastName;
    }
    ```

1. Save the code.

## Update the FMTAddress EDT

1. In **Solution Explorer**, expand the **FMTDataModel** project.
1. Right-click **FMTAddress**, and then select **Open**. The **EDT designer** opens.
1. In the **EDT designer**, select **FMTAddress**.
1. In the **Properties** window, in the **Reference Table** field, select **FMTCustomer**. **Tip:** Select the drop-down list, and then type the prefix "FMT" in the search box. This action filters the drop-down list to only show tables that contain "FMT" in their name. Select the **FMTCustomer** table from the list of filtered entries.

    :::image type="content" source="./media/searchfmt_datamodel.png" alt-text="Screenshot of updating the FMTAddress EDT in the Properties window." lightbox="./media/searchfmt_datamodel.png":::

1. Save the EDT.

## Build the FMTDataModel project and the Fleet Management tutorial model

1. In **Solution Explorer**, right-click **FMTDataModel**, and then select **Rebuild**.
1. To do a full build of the entire model, on the **Dynamics 365** menu, select **Build models**.
1. Clear the check box for all models except for **Fleet Management Tutorial**.
1. On the **Options** tab, select the **Run Best practice checks** check box. Note that other options are available.
1. On the **Models** tab, select **Build**.
1. Select **Close**  in the dialog box.
1. On the **Window** menu, select **Close All Documents**, to close all open documents.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
