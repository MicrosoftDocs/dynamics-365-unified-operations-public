---
title: Configure detours for steps in mobile device menu items
description: Configure detours for menu items to allow workers to park a current task to perform another one, and then return to the original task without losing any information.
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

# Configure detours for steps in mobile device menu items

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> The features that are described in this topic apply only to the new Warehouse Management mobile app. They do not affect the old warehouse app, which is now deprecated.

This topic describes how to configure detours for menu items, which allow workers to park a current task to perform another more important one, and then return to the original task without losing any information.

A detour is a separate menu item that can be launched from a step in a main task. At the end of the detour, the worker will return to where they left off in main task. During the configuration, you are asked to specify a menu item that should act as a detour, and to select which field values from the main task should automatically be forwarded to and populated in the detour. This means that you need to have an understanding of where in a task flow you want the detour to be available to the worker, and you need to make sure that the information you need to pass along to the detour is available for that step of the task flow.

## Enable detours on your system

Before you can configure detours for steps in mobile device menu items, you must complete the following procedure to enable the required features and generate the required warehouse app field names.

1. Go to **System administration \> Workspaces \> Feature management**.
1. In the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md), enable the feature that is listed in the following way:

    - **Module:** *Warehouse management*
    - **Feature name:** *Warehouse app step instructions*

    For more information about the *Warehouse app step instructions* feature, see [Customize step titles and instructions for the Warehouse Management mobile app](mobile-app-titles-instructions.md). This feature is a prerequisite for the *Warehouse management app detours* feature.

1. In the **Feature management** workspace, enable the feature that is listed in the following way:

    - **Module:** *Warehouse management*
    - **Feature name:** *Warehouse management app detours*

    This is the feature described in this topic.

1. Update the warehouse app field names by going to **Warehouse management \> Setup \> Mobile device \> Warehouse app field names** and selecting **Create default setup**. For more information see [Configure fields for the Warehouse Management mobile app](configure-app-field-names-priorities-warehouse.md).

1. Repeat the previous step for each legal entity (company) where you use the Warehouse Management mobile app.

## Configure a detour from a menu-specific override

Use the following procedure to set up a detour from a menu-specific override.

1. Start by creating a menu-specific override for the relevant menu and step as described in [Customize step titles and instructions for the Warehouse Management mobile app](mobile-app-titles-instructions.md)
1. Find the combination of **Step ID** and **Menu item name** values that you want to edit, and select the value in the **Step ID** column.
1. The page that opens includes a **Available detours (menu items)** FastTab. A detour is a separate menu item, which can be launched from a step in a main task. At the end of the detour, the worker will return to the main task. Here you can specify a menu item that should act as a detour, and select which field values from the main task should automatically be forwarded to and from the detour. See the scenarios provided later in this topic for examples of how to use these settings.

## Sample scenario 1: Sales picking with location inquiry as a detour

This scenario shows how to configure location inquiry as a detour in a worker-directed sales picking task flow. This detour will enable the worker to look up all the license plates on the location they are picking from and to pick the license plate they want to use to complete the pick. This could be useful if the barcode is damaged so that it is unreadable by the scanner device, or if the worker needs to look up what is actually on-hand in the system. Note that this scenario works only if you are picking from license plate controlled locations.

### Enable sample data

To work through this scenario using the specified sample records and values, you must be using a system where the standard demo data is installed. You must also select the USMF legal entity before you begin.

### Create a menu-specific override and configure the detour for scenario 1

In this procedure, you will configure a detour for the menu item **Sales picking** in the license plate step.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device steps**.
1. Find the **Step ID** named *LicensePlateId* and select it.
1. On the Actions Pane, select **Add step configuration** to open a drop-down dialog box and then use the **Menu item** field to find and select *Sales picking*.
1. Select **OK** in the drop-down dialog box. The details page opens for the override you just created.
1. Expand the **Available detours (menu items)** FastTab.
1. Select **Add** from the **Available detours (menu items)** FastTab toolbar.
1. In the **Add detour** dialog, select **Location inquiry**. This is the detour that will be made available in the Warehouse Management mobile app.
1. Select **OK**.
1. On the **Available detours (menu items)** FastTab, select the detour you just added and then select **Select fields to send** from the toolbar.
1. Use the **Select fields to send** dialog to configure what information to send to and from the detour. For this scenario, you are allowing workers to use the location they are supposed to pick from as input to the location inquiry detour. In the **Send from sales picking** section, select **Add** from the toolbar to add a new row and then make the following settings for it:
    - **Copy from Sales Picking:** *Location*
    - **Paste in Location Inquiry:** *Location*
1. For this scenario, because the detour is configured on the license plate step, it would be useful for the worker to bring back the license plate from the inquiry back to the main flow. In the **Bring back from location inquiry** section, select **Add** from the toolbar to add a new row and then make the following settings for it:
    - **Copy from Location Inquiry:** *License plate*
    - **Paste in Sales Picking:** *License plate*
1. Select **OK**.

The detour is now fully configured, so a button to initiate **Location inquiry** will appear on the license plate step for the **Sales picking** menu item.

### Complete a sales pick on mobile device and use the detour

In this procedure, you will use the Warehouse Management mobile app to complete a sales pick using the detour to find a license plate to use to complete the pick step.

1. In Supply Chain Management, create a sales order that will require a pick step to pick from a location that is license plate tracked. Then release the sales order to the warehouse and make a note of the work ID generated.
1. Open the Warehouse Management mobile app and sign in to warehouse 24. (In the standard demo data, sign in by using 24 as the user ID and 1 as the password.)
1. Select the **Outbound** menu and then the **Sales picking** menu item.
1. Follow the data entry instructions on the screen to input the work ID that you prepared in step 1.
1. On the step that says **Scan a license plate**, open the actions menu and you will see a new button that says **Location inquiry**. A detour is also recognizable on the icon itself, which shows an arrow in the top-left corner to indicate that it is a detour.
1. Select on **Location inquiry**.
1. In the next screen, the detour has started and you are asked to confirm the location that was copied from the main flow.
1. Next you will see the list of the available license plates in the location. Tap on the one you want to bring back, then select the back icon.
1. You are now taken back to the sales picking main flow, and the license plate has been copied back. You are asked to confirm it to proceed to the next step.
1. You can now proceed to complete the rest of the standard flow by entering the requested data entry instructions.

The warehouse work is now complete. The worker was able to launch a detour to do a secondary task of location inquiry without losing their place in the task, and they brought back the information needed to complete the task.

## Sample scenario 2: Item inquiry with movement and adjustment detours

This scenario shows how to configure movement and adjustments as multiple detours in the location inquiry task flow. You could replace location inquiry with a license plate inquiry or item inquiry as needed. This will give workers the ability to do a lookup of a specific location, and immediately from the inquiry complete tasks from the inquiry task flow. This could be useful in situations where a worker finds inventory discrepancies when arriving at a location compared to what is registered in the system, and therefore needs to adjust or move goods.

### Enable sample data

To work through this scenario using the specified sample records and values, you must be using a system where the standard demo data is installed. You must also select the USMF legal entity before you begin.

### Create a menu-specific override and configure the detour for scenario 2

In this procedure, you will configure a detour for the menu item "Sales picking" in the license plate step.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device steps**.
1. Find and select the **Step ID** named *LocationInquiryList*. (If you want to this same procedure for an item or license plate inquiry, select a row with **Step ID** *ItemInquiryList* or *LPInquiryList*, respectively.)
1. On the Actions Pane, select **Add step configuration** to open a drop-down dialog box and then use the **Menu item** field to find and select *Location inquiry*.
1. Select **OK** in the drop-down dialog box. The details page opens for the override you just created.
1. Expand the **Available detours (menu items)** FastTab.
1. Select **Add** from the **Available detours (menu items)** FastTab toolbar.
1. In the **Add detour** dialog, select **Movement**. This is the detour that will be made available in the Warehouse Management mobile app.
1. Select **OK**.
1. On the **Available detours (menu items)** FastTab, select the detour you just added and then select **Select fields to send** from the toolbar.
1. Use the **Select fields to send** dialog to configure what information to send to and from the detour. For this scenario, we are expecting the worker to look for license plate controlled locations, so it would be helpful to copy the license plate from the inquiry to the **Movement** detour. In the **Send from sales picking** section, select **Add** from the toolbar to add a new row and then make the following settings for it:
    - **Copy from Location Inquiry:** *Location*
    - **Paste in Movement:** *Loc / LP*
1. In this detour, we are not expecting any information to be copied back as the main flow was an inquiry where no additional steps are needed.
1. Select **OK**.

The detour is now fully configured, so a button to initiate **Movement** will appear on the license plate step for the **Location inquiry** menu item.

### Do a location inquiry on mobile device and use the detour

In this procedure, you will conduct a location inquiry using the Warehouse Management mobile app, and then do the detour to complete a movement of goods.

1. Open the Warehouse Management mobile app and sign in to warehouse 24. (In the standard demo data, sign in by using 24 as the user ID and 1 as the password.)
1. Select the **Inventory** menu and then the **Location inquiry** menu item.
1. Enter a location to inquire on, for example *FL-001*.
1. When the list is shown, long-press on one of the cards in the list to open the available detours.
1. Select **Movement**.
1. Notice that the license plate has been copied from the card you selected and you are now asked to confirm it.
1. From here you can follow the standard task flow to complete the movement. After the work is complete, open the actions menu and select **Cancel**.
1. You are now back on the **Location inquiry** page. Note that the values are not automatically updated, so you need to manually refresh the page to see the changes from the movement detour.
