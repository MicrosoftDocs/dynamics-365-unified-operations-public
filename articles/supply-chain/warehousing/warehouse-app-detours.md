---
title: Configure detours for steps in mobile device menu items
description: Learn how to configure detours for menu items so that workers can park the current task, perform another task, and return to the original task without data loss.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 02/20/2024
ms.custom:
  - bap-template
ms.reviewer: kamaybac
ms.search.form: WHSMobileAppFlowStepListPage, WHSMobileAppFlowStepAddDetour, WHSMobileAppFlowStepDetourSelectFields, WHSMobileAppFlowStepSelectPromotedFields
---

# Configure detours for steps in mobile device menu items

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> The features that are described in this article apply only to the new Warehouse Management mobile app. They don't affect the old warehouse app, which is now deprecated.

This article describes how to configure detours for menu items so that workers can "park" the current task, perform another task, and then return to the original task without losing any information.

A detour is a separate menu item that can be opened from a step in a main task. At the end of the detour, the worker is returned to the place where they left the main task. During the configuration, you specify the menu item that should act as a detour. You also select which field values from the main task should automatically be forwarded (copied) to the detour and entered there. Therefore, you must understand where in the task flow you want the detour to be available to workers. You must also ensure that the information that must be copied to the detour is available for that step of the task flow.

## Configure a detour from a menu-specific override

Use the following procedure to set up a detour from a menu-specific override.

1. Create a menu-specific override for the relevant menu and step as described in [Customize step titles and instructions for the Warehouse Management mobile app](mobile-app-titles-instructions.md).
1. Find the combination of **Step ID** and **Menu item name** values that you want to edit, and then select the value in the **Step ID** column.
1. On the page that appears, on the **Available detours (menu items)** FastTab, you can specify the menu item that should act as a detour. You can also select which field values from the main task should automatically be copied to and from the detour. For examples that show how to use these settings, see the scenarios later in this article.

> [!IMPORTANT]
> Workers can only access menu items that are included in the menu that is assigned to their [mobile device user account](mobile-device-work-users.md) (or a submenu of that menu). This also applies to menu items that are intended for use as [detours](warehouse-app-detours.md), but which you might not want workers to access directly from the menu. In this case, you should add the detour items to the relevant menus and then hide the items. For details about how to hide menu items, see [Mobile device menu](configure-mobile-devices-warehouse.md#mobile-device-menu)

## <a name="scenario-1"></a>Sample scenario 1: Sales picking where a location inquiry acts as a detour

This scenario shows how to configure a location inquiry as a detour in a worker-directed sales picking task flow. This detour will enable workers to look up all the license plates in the location that they are picking from and pick the license plate that they want to use to complete the pick. This type of detour might be useful if the bar code is damaged and therefore unreadable by the scanner device. Alternatively, it might be useful if a worker must learn what is actually on hand in the system. This scenario works only if you're picking from license plate–controlled locations.

### Enable sample data

To use the specified sample records and values to work through this scenario, you must be using a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. You must also select the **USMF** legal entity before you begin.

### Create a menu-specific override and configure the detour for scenario 1

In this procedure, you'll configure a detour for the **Sales picking** menu item in the license plate step.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device steps**.
1. Find the step ID that is named *LicensePlateId*, and select it.
1. On the Action Pane, select **Add step configuration**.
1. In the drop-down dialog, use the **Menu item** field to find and select *Sales picking*.
1. Select **OK**.
1. The details page for the override that you just created appears. On the **Available detours (menu items)** FastTab, select **Add** on the toolbar.
1. In the **Add detour** dialog, select **Location inquiry** as the detour that will be made available in the Warehouse Management mobile app.
1. Select **OK**.
1. On the **Available detours (menu items)** FastTab, select the detour that you just added, and then select **Select fields to send** on the toolbar.
1. In the **Select fields to send** dialog, specify the information that should be sent to and from the detour. In this scenario, you're enabling workers to use the location that they're supposed to pick from as input for the location inquiry detour. Therefore, in the **Send from sales picking** section, select **Add** on the toolbar to add a row to the grid. Then set the following values for the new row:

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
1. In the drop-down dialog, use the **Menu item** field to find and select *Location inquiry*.
1. Select **OK**.
1. The details page for the override that you just created appears. On the **Available detours (menu items)** FastTab, select **Add** on the toolbar.
1. In the **Add detour** dialog, select **Movement** as the detour that will be made available in the Warehouse Management mobile app.
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
1. You're returned to the **Location inquiry** page. The values aren't automatically updated. Therefore, you must manually refresh the page to see the changes from the movement detour.

## <a name="scenario-3"></a>Sample scenario 3: Movement by template with a data inquiry detour

This scenario shows how to configure movement by template with a data inquiry detour. 

### Enable sample data

To use the specified sample records and values to work through this scenario, you must be using a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. You must also select the **USMF** legal entity before you begin.

In this procedure, you'll configure a data inquiry detour for the **Movement by template** menu item in the **Scan location or license plate** step.

### Configure an Item data inquire mobile device menu item for scenario 3

To create the **Item data inquire** mobile device menu item, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. On the Action Pane, select **New** to add a mobile device menu item.
1. Set the following values for the new menu item:

    - In the **Menu item name** field, enter *Item data inquire*.
    - In the **Title** field, look up the inventory dimensions by items.
    - In the **Mode** field, select *Indirect*.

1. On the **General** FastTab, set the following values:

    - In the **Activity code** field, select *Data inquiry*.
    - In the **Use process guide** field, ensure that *Yes* is selected. (*Yes* is the default value.)
    - In the **Table name** field, select *InventSum*, because you want to look up inventory dimensions from this table.

1. You must now select the fields that appear on the cards on the **Inquiry list** page. On the Action Pane, select **Field list**.
1. On the **Field list** page, set the following values:

    - **Display field 1:** *ItemId* (This field will appear as the header for each card.)
    - **Display field 2:** *InventColorId*
    - **Display field 3:** *InventSizeId*
    - **Display field 4:** *WMSLocationId*

1. On the Action Pane, select **Save**.
1. Close the page.

> [!NOTE]
> The **Item data inquire** mobile device menu item must be added to mobile device menu before it can be used as part of a detour process. 

### Create a menu-specific override and configure the detour for scenario 3

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device steps**.
1. Find and select the step ID that is named *LocOrLP*.
1. On the Action Pane, select **Add step configuration**.
1. In the dropdown dialog, in the **Menu item** field, select *Movement by template*.
1. Select **OK**.
1. The details page for the override that you just created appears. On the **Available detours (menu items)** FastTab, select **Add** on the toolbar.
1. In the **Add detour** dialog, select **Item data inquiry** as the detour that will be available in the Warehouse Management mobile app.
1. Select **OK**.
1. On the **Available detours (menu items)** FastTab, select the detour that you just added.
1. In the **Bring back from Items data inquiry** section, select **Add** on the toolbar to add a row to the grid. Then set the following values for the new row:

    - **Copy from Items Inquiry:** *Item number*
    - **Paste in Movement by template:** *Item*
    - **Auto submit:** *Yes*

1. Select **Add** on the toolbar to add another row to the grid. Then set the following values for the new row:

    - **Copy from Items Inquiry:** *Size*
    - **Paste in Movement by template:** *Size*
    - **Auto submit:** *Yes*

1. Select **Add** on the toolbar to add another row to the grid. Then set the following values for the new row:

    - **Copy from Items Inquiry:** *Color*
    - **Paste in Movement by template:** *Color*
    - **Auto submit:** *Yes*

1. Select **Add** on the toolbar to add another row to the grid. Then set the following values for the new row:

    - **Copy from Items Inquiry:** *Location*
    - **Paste in Movement by template:** *Loc / LP*
    - **Auto submit:** *No*

1. Select **OK**.

The detour is now fully configured. A button to start the **Item data inquiry** detour now appears in the **Scan location or license plate** step for the **Movement by template** menu item.

### Create a new product master item T-Shirt and add on-hand for scenario 3

Create a new *T-shirt* product master item that has size and color variants. Add one on-hand entry for one specific size and color of this item for warehouse 24.

### Do a movement by template on a mobile device and use the detour

In this procedure, you'll use the Warehouse Management mobile app to do a movement by template. You'll then complete the movement by using the detour to find the item, color, size, and location.

1. Open the Warehouse Management mobile app, and sign in to warehouse 24. (In the standard demo data, sign in by using *24* as the user ID and *1* as the password.)
1. Select the **Movement by template** menu item.
1. In the first step that contains the text **Scan location or license plate**, select **Item data inquiry**. 
1. The detour is started, and the first detour step is **Item number**. Specify *T-shirt*, and then confirm the entry.
1. Select the card that contains information about the location, color, and size of the existing on-hand entry. You're returned to the movement by template flow and receive a "Work completion" message.

Note that the detour was configured to auto-submit only the item, size, and color. The system also auto-populated the location and quantity. This behavior occurred because the system could determine the size, location, and quantity from the specified color, based on the on-hand data distribution. The detour contained three auto-submit controls that corresponded to three **OK** buttons. Because a default location and a default quantity were entered after the return from the detour, they were automatically confirmed.

> [!NOTE]
> Multi-level detours enable you to define multi-level detours (detours within detours), which will allow workers to jump from an existing detour two a second one and then back again. The feature supports two levels of detours out of the box and, if necessary, you can customize your system to support three or more levels of detours by creating code extensions on the `WHSWorkUserSessionState` table.
>
> Auto-submit detour steps can make it faster and easier for workers to complete detour flows in the Warehouse Management mobile app. It enables some flow steps to be skipped by letting the app populate detour data on the back end and then move automatically to the next step by auto submitting the page, as shown in [Sample scenario 1: Sales picking where a location inquiry acts as a detour](#scenario-1) earlier in the article.
>
> Essentially, the number of auto-submits corresponds to the number of times that the **OK** button is selected. If a mobile app flow has defaulting mechanics, auto-submit for detours can cause variations in behavior, based on the on-hand data composition. An example is shown in [Sample scenario 3: Movement by template with data inquiry detour](#scenario-3).
