---
title: Configure promoted fields for steps in the Warehouse Management mobile app
description: This topic describes how to promote and highlight certain information for any step in the task flows for the Warehouse Management mobile app.
author: MarkusFogelberg
ms.date: 10/15/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mafoge
ms.search.validFrom: 2021-10-15
ms.dyn365.ops.version: 10.0.23
---

# Configure promoted fields for steps in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> The features that are described in this topic apply only to the new Warehouse Management mobile app. They do not affect the old warehouse app, which is now deprecated.

This topic describes how to promote and highlight certain information for any task-flow step in the Warehouse Management mobile app. This can help focus workers' attention on the most important fields as they work through a flow. Admins can choose precisely which fields to promote and which to highlight for each step in each process.

## Enable promoted fields on your system

Before you can set up your promoted fields, you must complete the following procedure to enable the required features and generate the required warehouse app field names.

1. Go to **System administration \> Workspaces \> Feature management**.
1. In the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md), enable the feature that is listed in the following way:

    - **Module:** *Warehouse management*
    - **Feature name:** *Warehouse app step instructions*

    For more information about the *Warehouse app promoted fields* feature, see [Customize step titles and instructions for the Warehouse Management mobile app](mobile-app-titles-instructions.md). This feature is a prerequisite for the *Warehouse app promoted fields* feature.

1. In the **Feature management** workspace, enable the feature that is listed in the following way:

    - **Module:** *Warehouse management*
    - **Feature name:** *Warehouse app promoted fields*

    This is the feature described in this topic.

1. Update the warehouse app field names by going to **Warehouse management \> Setup \> Mobile device \> Warehouse app field names** and selecting **Create default setup**. For more information see [Configure fields for the Warehouse Management mobile app](configure-app-field-names-priorities-warehouse.md).

1. Repeat the previous step for each legal entity (company) where you use the Warehouse Management mobile app.

## Configure promoted fields from a menu-specific override

Use the following procedure to set up promoted fields.

1. Start by creating a menu-specific override for the relevant menu and step as described in [Customize step titles and instructions for the Warehouse Management mobile app](mobile-app-titles-instructions.md)
1. Find the combination of **Step ID** and **Menu item name** values that you want to edit, and select the value in the **Step ID** column.
1. On the page that opens, expand the **Select promoted fields** FastTab.
1. Select **Select fields** from the **Select promoted fields** FastTab toolbar.
1. Use the **Promoted fields** dialog to identify the fields you want to promote. You can also highlight up to two of the selected fields. Highlighted fields will be shown in bold in the Warehouse Management mobile app. Take into consideration that smaller screens might only show the top one or two promoted fields (depending on the size of the screen). See the scenario provided later in this topic for an example of how to use these settings.

    > [!NOTE]
    > The available field list is limited to the fields that could appear for that menu item, but there could be other factors (such as item composition) that decide whether the field is actually populated on the Warehouse Management mobile app. If you have configured promoted fields, only the selected fields will appear on the main page of the Warehouse Management mobile app. The worker can still view the rest of the fields by tapping on the details page.

1. Select **OK** to apply your settings. Your selected fields are now listed on the **Select promoted fields** FastTab

## Example scenario

### Enable sample data

To work through this scenario using the specified sample records and values, you must be using a system where the standard demo data is installed. You must also select the USMF legal entity before you begin.

### Sales picking with promoted steps on the license plate step

In this procedure, you will configure a detour for the menu item **Sales picking** in the license plate step.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device steps**.
1. Find the **Step ID** named *LicensePlateId* and select it.
1. On the Actions Pane, select **Add step configuration** to open a drop-down dialog box and then use the **Menu item** field to find and select *Sales picking*.
1. Select **OK** in the drop-down dialog box. The details page opens for the override you just created.
1. Expand the **Select promoted fields** FastTab.
1. Select **Select fields** from the **Select promoted fields** FastTab toolbar.
1. The **Promoted fields** dialog opens. Here you can select the fields to promote and highlight. In the **Available fields** column, find the following fields and use the buttons to move them to the **Selected fields** column:
    - **Location**
    - **Item**
    - **Product name**
    - **Inventory status**.
1. Use the up and down buttons to customize the order of the fields in the **Selected fields** list. The order shown here is the order that they will be shown in the Warehouse Management mobile app.
1. Select the **Location** field and then select **Highlight**.
1. Select **OK** to save the configuration.

### View the promoted fields on the Warehouse Management mobile app

In this procedure, you will open the Warehouse Management mobile app and go through the steps to see the fields you promoted and highlighted in the previous procedure.

1. In Supply Chain Management, create a sales order that will require a pick step to pick from a location that is license plate tracked. Then release the sales order to the warehouse and make a note of the work ID generated.
1. Open the Warehouse Management mobile app and sign in to warehouse 24. (In the standard demo data, sign in by using 24 as the user ID and 1 as the password.)
1. Select the **Outbound** menu and then the **Sales picking** menu item.
1. Follow the data entry instructions on the screen to input the work ID that you prepared in step 1.
1. On the step that says **Scan a license plate**, you can see the changes in the details page. The fields shown are in the order of the configured promoted fields, and the **Location** field is highlighted in bold.
