---
title: Configure detours for steps in mobile device menu items
description: This article describes how to configure detours for menu items so that workers can park the current task, perform another task, and then return to the original task without losing any information.
author: Mirzaab
ms.date: 09/01/2022
ms.topic: article
ms.search.form: WHSMobileAppFlowStepListPage, WHSMobileAppFlowStepAddDetour, WHSMobileAppFlowStepDetourSelectFields, WHSMobileAppFlowStepSelectPromotedFields
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mirzaab
ms.search.validFrom: 2021-10-15
ms.dyn365.ops.version: 10.0.30
---

# Configure detours for steps in mobile device menu items

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> The features that are described in this article apply only to the new Warehouse Management mobile app. They don't affect the old warehouse app, which is now deprecated.

This article describes how to configure detours for menu items so that workers can "park" the current task, perform another task, and then return to the original task without losing any information.

A detour is a separate menu item that can be opened from a step in a main task. At the end of the detour, the worker is returned to the place where they left the main task. During the configuration, you specify the menu item that should act as a detour. You also select which field values from the main task should automatically be forwarded (copied) to the detour and entered there. Therefore, you must understand where in the task flow you want the detour to be available to workers. You must also ensure that the information that must be copied to the detour is available for that step of the task flow.

## Enable detours in your system

Before you can configure detours for steps in mobile device menu items, you must complete the following procedure to enable the required features and generate the required field names in the Warehouse Management mobile app.

1. Go to **System administration \> Workspaces \> Feature management**.
1. Make sure that the *Warehouse app step instructions* feature is turned on for your system. As of Supply Chain Management version 10.0.29, this feature is turned on by default. For more information about the *Warehouse app step instructions* feature, see [Customize step titles and instructions for the Warehouse Management mobile app](mobile-app-titles-instructions.md). This feature is a prerequisite for the *Warehouse management app detours* feature.
1. Turn on the following features, which provide the functionality described in this article:
    - *Warehouse management app detours*<br>(As of Supply Chain Management version 10.0.29, this feature is turned on by default.)
    - *Multi-level detours for the Warehouse Management mobile app*
    - *Auto-submit detour steps for the Warehouse Management mobile app*
1. If the *Warehouse management app detours* and/or *Multi-level detours for the Warehouse Management mobile app* features were't already turned on, update the field names in the Warehouse Management mobile app by going to **Warehouse management \> Setup \> Mobile device \> Warehouse app field names** and selecting **Create default setup**. For more information, see [Configure fields for the Warehouse Management mobile app](configure-app-field-names-priorities-warehouse.md).
1. Repeat the previous step for each legal entity (company) where you use the Warehouse Management mobile app.

## Configure a detour from a menu-specific override

Use the following procedure to set up a detour from a menu-specific override.

1. Create a menu-specific override for the relevant menu and step as described in [Customize step titles and instructions for the Warehouse Management mobile app](mobile-app-titles-instructions.md).
1. Find the combination of **Step ID** and **Menu item name** values that you want to edit, and then select the value in the **Step ID** column.
1. On the page that appears, on the **Available detours (menu items)** FastTab, you can specify the menu item that should act as a detour. You can also select which field values from the main task should automatically be copied to and from the detour. For examples that show how to use these settings, see the scenarios later in this article.

## <a name="scenario-1"></a>Sample scenario 1: Sales picking where a location inquiry acts as a detour

This scenario shows how to configure a location inquiry as a detour in a worker-directed sales picking task flow. This detour will enable workers to look up all the license plates in the location that they are picking from and pick the license plate that they want to use to complete the pick. This type of detour might be useful if the bar code is damaged and therefore unreadable by the scanner device. Alternatively, it might be useful if a worker must learn what is actually on hand in the system. Note that this scenario works only if you're picking from license plate–controlled locations.

### Enable sample data

To use the specified sample records and values to work through this scenario, you must be using a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. You must also select the **USMF** legal entity before you begin.

### Create a menu-specific override and configure the detour for scenario 1

In this procedure, you'll configure a detour for the **Sales picking** menu item in the license plate step.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device steps**.
1. Find the step ID that is named *LicensePlateId*, and select it.
1. On the Action Pane, select **Add step configuration**.
1. In the drop-down dialog box, use the **Menu item** field to find and select *Sales picking*.
1. Select **OK**.
1. The details page for the override that you just created appears. On the **Available detours (menu items)** FastTab, select **Add** on the toolbar.
1. In the **Add detour** dialog box, select **Location inquiry** as the detour that will be made available in the Warehouse Management mobile app.
1. Select **OK**.
1. On the **Available detours (menu items)** FastTab, select the detour that you just added, and then select **Select fields to send** on the toolbar.
1. In the **Select fields to send** dialog box, specify the information that should be sent to and from the detour. In this scenario, you're enabling workers to use the location that they're supposed to pick from as input for the location inquiry detour. Therefore, in the **Send from sales picking** section, select **Add** on the toolbar to add a row to the grid. Then set the following values for the new row:

    - **Copy from Sales Picking:** *Location*
    - **Paste in Location Inquiry:** *Location*
    - **Auto submit:** *Selected* (the page will be refreshed with the pasted *Location* value)

1. Because the detour in this scenario is configured on the license plate step, it will be useful if workers can bring the license plate from the inquiry back to the main flow. Therefore, in the **Bring back from location inquiry** section, select **Add** on the toolbar to add a row to the grid. Then set the following values for the new row:

    - **Copy from Location Inquiry:** *License plate*
    - **Paste in Sales Picking:** *License plate*
    - **Auto submit:** *Cleared* (no auto update will occur when returning from the detour with a *License plate* value)

1. Select **OK**.

The detour is now fully configured. A button to start the **Location inquiry** detour will now appear on the license plate step for the **Sales picking** menu item.

### Complete a sales pick on a mobile device and use the detour

In this procedure, you'll complete a sales pick by using the Warehouse Management mobile app. You'll use the detour that you just configured to find the license plate that you'll use to complete the pick step.

1. In Microsoft Dynamics 365 Supply Chain Management, create a sales order that will require a pick step to pick from a location that is license plate tracked. Then release the sales order to the warehouse. Make a note of the work ID that is generated.
1. Open the Warehouse Management mobile app, and sign in to warehouse 24. (In the standard demo data, sign in by using *24* as the user ID and *1* as the password.)
1. Select the **Outbound** menu, and then select the **Sales picking** menu item.
1. Follow the data entry instructions on the screen to enter the work ID that was generated in step 1.
1. On the step that contains the text **Scan a license plate**, open the actions menu. You should see a new button that is labeled **Location inquiry**. An arrow in the upper-left corner indicates that the button will start a detour. Select **Location inquiry**.
1. The detour is started. On the next page, confirm the location that was copied from the main flow.
1. In the list of available license plates in the location, tap on the license plate that you want to copy back to the main flow. Then select the **Back** button.
1. You're returned to the sales picking main flow, and the license plate has been copied back to it from the detour. Confirm the value to continue to the next step.
1. You can now complete the rest of the standard flow by entering the requested data entry instructions.

The warehouse work is now completed. The worker successfully opened a detour to perform a secondary task (location inquiry) without losing their place in the main task, and brought back the information that was required to complete the main task.

## Sample scenario 2: Item inquiry with movement and adjustment detours

This scenario shows how to configure movement and adjustments as multiple detours in the location inquiry task flow. This capability can be useful in situations where a worker arrives at a location, finds that the inventory in the location differs from what is registered in the system, and must therefore adjust or move goods.

You can replace the location inquiry with a license plate inquiry or an item inquiry as you require.

### Enable sample data

To use the specified sample records and values to work through this scenario, you must be using a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. You must also select the **USMF** legal entity before you begin.

### Create a menu-specific override and configure the detour for scenario 2

In this procedure, you'll configure a detour for the **Sales picking** menu item in the license plate step.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device steps**.
1. Find and select the step ID that is named *LocationInquiryList*.

    > [!NOTE]
    > To use an item inquiry instead of a location inquiry, select a row where the step ID is named *ItemInquiryList*. To use a license plate inquiry, select a row where the step ID is named *LPInquiryList*.

1. On the Action Pane, select **Add step configuration**.
1. In the drop-down dialog box, use the **Menu item** field to find and select *Location inquiry*.
1. Select **OK**.
1. The details page for the override that you just created appears. On the **Available detours (menu items)** FastTab, select **Add** on the toolbar.
1. In the **Add detour** dialog box, select **Movement** as the detour that will be made available in the Warehouse Management mobile app.
1. Select **OK**.
1. On the **Available detours (menu items)** FastTab, select the detour that you just added, and then select **Select fields to send** on the toolbar.
1. In the **Select fields to send** dialog, specify the information that should be sent to and from the detour. In this scenario, you're expecting workers to look for license plate–controlled locations. Therefore, it will be helpful to copy the license plate from the inquiry to the **Movement** detour. In the **Send from sales picking** section, select **Add** on the toolbar to add a row to the grid. Then set the following values for the new row:

    - **Copy from Location Inquiry:** *Location*
    - **Paste in Movement:** *Loc / LP*
    - **Auto submit:** *Cleared* (no auto update will occur)

    In this detour, you aren't expecting any information to be copied back, because the main flow was an inquiry where no additional steps are required.

1. Select **OK**.

The detour is now fully configured. A button to start the **Movement** detour will now appear on the license plate step for the **Location inquiry** menu item.

### Do a location inquiry on a mobile device and use the detour

In this procedure, you'll do a location inquiry by using the Warehouse Management mobile app. You'll then use the detour to complete a movement of goods.

1. Open the Warehouse Management mobile app, and sign in to warehouse 24. (In the standard demo data, sign in by using *24* as the user ID and *1* as the password.)
1. Select the **Inventory** menu, and then select the **Location inquiry** menu item.
1. Enter a location to inquire about, such as *FL-001*.
1. When the list appears, tap and hold on one of the cards in it to show the available detours.
1. Select **Movement**.
1. Notice that the license plate has been copied from the card that you selected. Confirm the value.
1. You can now follow the standard task flow to complete the movement. After the work is completed, open the actions menu, and select **Cancel**.
1. You're returned to the **Location inquiry** page. Note that the values aren't automatically updated. Therefore, you must manually refresh the page to see the changes from the movement detour.

> [!NOTE]
> The *Multi-level detours for the Warehouse Management mobile app* feature enables you to define multi-level detours (detours within detours), which will allow workers to jump from an existing detour two a second one and then back again. The feature supports two levels of detours out of the box and, if necessary, you can customize your system to support three or more levels of detours by creating code extensions on the `WHSWorkUserSessionState` table.
>
> The *Auto-submit detour steps for the Warehouse Management mobile app* feature can make it faster and easier for workers to complete detour flows in the Warehouse Management mobile app. It enables some flow steps to be skipped by letting the app populate detour data on the back end and then move automatically to the next step by auto submitting the page, as shown in [*Sample scenario 1: Sales picking where a location inquiry acts as a detour*](#scenario-1).
