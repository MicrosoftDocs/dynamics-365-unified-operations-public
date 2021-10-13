---
title: Configure promoted fields for steps in the mobile device
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

# Configure promoted fields for steps in the mobile device

[!include [banner](../includes/banner.md)]

This topic describes how to promote and highlight certain information for any step in the task flows for the Warehouse Management mobile app. This can help focus workers' attention on the most important fields as they work through a flow. Admins can choose precisely which fields to promote and which to highlight for each step in each process.

## Prerequisites

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

To configure promoted fields, you must first create a menu-specific override as described in [Add menu-specific overrides](mobile-app-titles-instructions.md#add-menu-specific-overrides).

Find the combination of Step ID and Menu item name values that you want to edit, and select the value in the Step ID column. The page that is opened has a tab **Select promoted fields**. Using this setup you can decide which fields to promote on the details card on the main page of the warehouse app. You can add fields to the selected column to promote them. You can also highlight up to two of the selected fields. Highlighted fields will be shown in bold in the warehouse app. Take into consideration that smaller screens might only show the top one or two promoted fields depending on the size of the screen.

The available field list is limited to the fields that could appear for that menu item, but there could be other factors such as item composition that decides whether the field is actually populated on the warehouse app or not. If you have configured promoted fields, only the selected fields will show in the main page on the mobile app. The user can still view the rest of the fields by tapping on the details page.

## Example scenario

### Enable sample data

To work through this scenario using the specified sample records and values, you must be using a system where the standard demo data is installed. You must also select the USMF legal entity before you begin.

### Sales picking with promoted steps on the license plate step

In this procedure, you will configure a detour for the menu item "Sales picking" in the license plate step.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device steps**.
1. Find the **Step ID** named **LicensePlateId** and select it.
1. In the **Actions Pane** select **Add step configuration**.
1. In the **Menu item** selection select, find and select **Sales picking**.
1. The details page for the override you just created will open.
1. Open the FastTab **Select promoted fields**.
1. Select **Select fields**.
1. Here you can select the fields to promote and highlight. In the **Available fields** column find and add the following fields: Location, Item, Product name, Inventory status. Select Location and select **Highlight**. The order of the selected fields here is the order that they will be shown in the warehouse app.
1. Select **OK** to save the configuration.

### View the promoted fields on the warehouse mobile app

In this procedure you will go through the steps to see the promoted fields in the warehouse app. Note that you are expected to have prepared a sales order, released it to warehouse and it should have a pick step to pick from a location that is license plate tracked.

1. Use your mobile device to sign in to warehouse 24. (In the standard demo data, sign in by using 24 as the user ID and 1 as the password.)
1. Select the **Outbound** menu and then the **Sales picking** menu item.
1. Follow the data entry instructions on the screen to input the Work ID number you have prepared.
1. On the step that says **Scan a license plate**, you can see the changes in the details page. The fields shown are in the order of the configured promoted fields, and the **Location** field will be highlighted in bold as per the setup.
