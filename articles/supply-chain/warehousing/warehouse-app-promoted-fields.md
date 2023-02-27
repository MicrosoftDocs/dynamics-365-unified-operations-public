---
title: Configure promoted fields for steps in the Warehouse Management mobile app
description: This article describes how to promote and highlight specific information for any step in the task flows for the Warehouse Management mobile app.
author: Mirzaab
ms.date: 08/09/2022
ms.topic: article
ms.search.form: WHSMobileAppFlowStepSelectPromotedFields, WHSMobileAppFlowStepListPage, WHSMobileAppFlowStepAddDetour, WHSMobileAppFlowStepDetourSelectFields
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mirzaab
ms.search.validFrom: 2021-10-15
ms.dyn365.ops.version: 10.0.23
---

# Configure promoted fields for steps in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> The features that are described in this article apply only to the new Warehouse Management mobile app. They don't affect the old warehouse app, which is now deprecated.

This article describes how to promote and highlight specific information for any step in the task flows for the Warehouse Management mobile app. This capability can help focus workers' attention on the most important fields as they work through a flow. For each step in every process, admins can select which fields to promote and which fields to highlight.

## Enable promoted fields in your system

If you're running Supply Chain Management version 10.0.28 or earlier, then before you can set up promoted fields, you must complete the following procedure to enable the required features and generate the required field names in the Warehouse Management mobile app. If you're running Supply Chain Management version 10.0.29 or later, the features are mandatory and can't be turned off, so you can skip this procedure.

1. Go to **System administration \> Workspaces \> Feature management**. (See [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) for more information about this page.)
1. Make sure that the *Warehouse app step instructions* feature is turned on for your system. This feature is a prerequisite for the *Warehouse app promoted fields* feature. As of Supply Chain Management version 10.0.29, it's mandatory and can't be turned off. For more information about the *Warehouse app step instructions* feature, see [Customize step titles and instructions for the Warehouse Management mobile app](mobile-app-titles-instructions.md).
1. Make sure that the *Warehouse app promoted fields* feature is turned on for your system. This is the feature described in this article. As of Supply Chain Management version 10.0.29, it's mandatory and can't be turned off.
1. Update the field names in the Warehouse Management mobile app by going to **Warehouse management \> Setup \> Mobile device \> Warehouse app field names** and selecting **Create default setup**. Repeat this step for each legal entity (company) where you use the Warehouse Management mobile app. For more information, see [Configure fields for the Warehouse Management mobile app](configure-app-field-names-priorities-warehouse.md).

## Configure promoted fields from a menu-specific override

Use the following procedure to set up promoted fields.

1. Create a menu-specific override for the relevant menu and step as described in [Customize step titles and instructions for the Warehouse Management mobile app](mobile-app-titles-instructions.md).
1. Find the combination of **Step ID** and **Menu item name** values that you want to edit, and then select the value in the **Step ID** column.
1. On the page that appears, on the **Select promoted fields** FastTab, select **Select fields** on the toolbar.
1. In the **Promoted fields** dialog box, select the fields that you want to promote. You can also highlight up to two of the selected fields. Highlighted fields will be shown in bold in the Warehouse Management mobile app. As you select fields, consider the fact that some screens might be large enough to show only the top one or two promoted fields. For an example that shows how to use these settings, see the scenario later in this article.

    > [!NOTE]
    > The **Available fields** list is limited to the fields that can appear for the menu item. However, other factors (such as item composition) determine whether a field actually appears in the Warehouse Management mobile app. If you've configured promoted fields, only the selected fields will appear on the main page of the Warehouse Management mobile app. However, workers can still view the remaining fields by tapping on the details page.

1. Select **OK** to apply your settings. Your selected fields are now listed on the **Select promoted fields** FastTab.

## Example scenario

### Enable sample data

To use the specified sample records and values to work through this scenario, you must be using a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. You must also select the **USMF** legal entity before you begin.

### Configure sales picking with promoted steps on the license plate step

In this procedure, you will set up promoted and highlighted fields for the **Sales picking** menu item in the license plate step.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device steps**.
1. Find the step ID that is named *LicensePlateId*, and select it.
1. On the Action Pane, select **Add step configuration**.
1. In the drop-down dialog box, use the **Menu item** field to find and select *Sales picking*.
1. Select **OK**.
1. The details page for the override that you just created appears. On the **Select promoted fields** FastTab, select **Select fields** on the toolbar.
1. In the **Promoted fields** dialog box, you can select the fields to promote and highlight. In the **Available fields** list, find and select the following fields, and use the buttons to move them to the **Selected fields** list:

    - Location
    - Item
    - Product name
    - Inventory status

1. Use the up arrow and down arrow buttons to customize the order of the fields in the **Selected fields** list. In the Warehouse Management mobile app, the fields will appear in the order that you set here.
1. Select the **Location** field, and then select **Highlight**.
1. Select **OK** to save the configuration.

### View the promoted fields in the Warehouse Management mobile app

In this procedure, you will open the Warehouse Management mobile app and go through the steps to view the fields that you promoted and highlighted in the previous procedure.

1. In Microsoft Dynamics 365 Supply Chain Management, create a sales order that will require a pick step to pick from a location that is license plate tracked. Then release the sales order to the warehouse. Make a note of the work ID that is generated.
1. Open the Warehouse Management mobile app, and sign in to warehouse 24. (In the standard demo data, sign in by using *24* as the user ID and *1* as the password.)
1. Select the **Outbound** menu, and then select the **Sales picking** menu item.
1. Follow the data entry instructions on the screen to enter the work ID that was generated in step 1.
1. On the step that contains the text **Scan a license plate**, you should see the changes that you made on the details page. The fields appear in the order that you set for the promoted fields, and the **Location** field is shown in bold.
