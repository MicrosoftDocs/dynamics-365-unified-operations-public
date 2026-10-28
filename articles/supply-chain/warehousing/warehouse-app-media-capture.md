---
title: Capture photos and videos by using Warehouse Management mobile app detours (preview)
description: Learn how workers can capture photos and videos in the Warehouse Management mobile app and attach them to records in Supply Chain Management.
author: pefreita
ms.author: pefreita
ms.reviewer: kamaybac
ms.search.form: WHSRFMenuItem, WHSRFMenu, WHSMobileAppFlowStepListPage, WHSMobileAppFlowStepAddDetour, WHSMobileAppFlowStepDetourSelectFields, DocuParameters
ms.topic: how-to
ms.date: 10/27/2026
ms.custom:
  - bap-template
ai-usage: ai-assisted
---

# Capture photos and videos by using Warehouse Management mobile app detours (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Warehouse workers often need to document what they see on the warehouse floor, such as a damaged pallet, a mislabeled license plate, or the condition of goods at receipt. The media capture feature lets workers take photos and record videos in the Warehouse Management mobile app and attach them to records in Microsoft Dynamics 365 Supply Chain Management, without leaving the task that they're working on.

Media capture runs as a detour. A worker starts it from a step in a mobile device flow, finds one or more records, captures or selects the media files, and uploads them. The app then returns the worker to the step where they started. The uploaded media files are stored as standard document management attachments, so anyone who has access to the record in Supply Chain Management can view them on the **Attachments** pane.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use media capture, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.50 or later.
- The feature that's named *(Preview) Media capture in the warehouse mobile app* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- The Warehouse Management mobile app must be installed and set up. Learn more in [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md).
- The mobile devices that workers use must have a camera or access to stored media files.

## How media capture works

When a worker opens a media capture menu item, the app uses the query set up on that menu item to find the records that the media files should be attached to. The process works in the following way:

- **Search for records** – Any query range that has a blank **Criteria** value becomes a search field that the worker fills in. If the detour sends values from the main flow, the app fills in the matching search fields automatically. The worker must enter a value in every search field before searching. By default, values must match exactly. To search for a pattern, the worker can include an asterisk (`*`) wildcard character, such as *WMA\**.
- **Collect records** – If a search finds exactly one record, the app adds it to the worker's list. If a search finds several records, the worker selects the ones to add. A search returns up to 100 records at a time, and the worker can page through the results or narrow the filter. The worker can run several searches to build up the list, and remove records from it, before capturing any files. The list can hold up to 100 records. Searches only return records from the worker's current legal entity.
- **Capture and upload files** – The worker takes photos, records videos, or selects existing files on the device, and then uploads them. Each file is attached to every record on the list.

Workers can upload the following file types:

- JPEG images (*.jpg*)
- PNG images (*.png*)
- MP4 videos (*.mp4*)

Supply Chain Management checks that the content of each file matches its file type. If any file in an upload isn't valid, none of the files are attached. Attachments use the default document type for files. The notes for each attachment show the worker who uploaded it.

## Allow MP4 video attachments

Document management only accepts the file extensions that are listed on the **File types** tab of the **Document management parameters** page. If MP4 isn't on that list, workers can't upload videos. You don't need to create a separate document type for videos. Learn more about file types in [Configure document management](../../fin-ops-core/dev-itpro/organization-administration/configure-document-management.md#configure-file-types).

To allow workers to upload MP4 videos, follow these steps:

1. Go to **Organization administration** > **Document management** > **Document management parameters**.
1. On the **File types** tab, add a row and set **File extension** to *mp4*. Don't include the period.
1. Save your changes.

If an MP4 upload failed before you made this change, the worker can try the upload again.

## Create a media capture menu item

Each media capture menu item identifies one type of record that files can be attached to, such as license plates, items, or purchase orders. The menu item uses a query to find those records, in the same way as a data inquiry menu item. Learn more about how to set up these queries in [Query data by using Warehouse Management mobile app detours](warehouse-app-data-inquiry.md).

To create a media capture menu item, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu items**.
1. On the Action Pane, select **New**.
1. Set the following fields:

    - **Menu item name** – Enter a unique name for the menu item.
    - **Title** – Enter the title that workers see in the mobile app.
    - **Mode** – Select *Indirect*.
    - **Activity code** – Select *(Preview) Media capture*.
    - **Use process guide** – This option is automatically set to *Yes* because media capture requires the process guide framework.
    - **Table name** – Select the table that contains the records that workers attach media files to.
    - **Show filter page** – Select when workers see the page where they search for records. Select *Always* to always show it. Select *Only when filters can be changed* to skip it when every search field already has a value, either from fixed query criteria or from the main flow. In this case, the app runs the search immediately.
    - **Barcode data policy** – This field isn't used by media capture menu items. Scanned GS1 barcodes aren't parsed into the search fields, so leave it blank.

1. On the Action Pane, select **Edit query**.
1. In the query editor, on the **Range** tab, add a row for each field that workers should search by, and leave **Criteria** blank for those rows. You can also add rows that have fixed criteria to limit which records workers can find. The table that you selected in the **Table name** field must be the root data source of the query. Don't group the query, and sort it only by fields from that table.
1. Select **OK** to close the query editor.
1. On the Action Pane, select **Field list** and choose the fields that appear on each record card in the app. Workers use these fields to identify the records that they select.
1. Save the menu item.

## Add the menu item to a mobile device menu

Workers can use a menu item, including one used as a detour, only if it's in a menu assigned to their mobile device user account. If you want workers to open media capture only as a detour, hide the menu item in the menu. Learn more in [Set up mobile device menus](configure-mobile-devices-warehouse.md#mobile-device-menu).

To add the media capture menu item to a menu, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu**.
1. On the list pane, select the menu assigned to the workers who need media capture. Then, on the Action Pane, select **Edit**.
1. In the **Available menus and menu items** column, select your media capture menu item, and then select the right arrow to move it to the **Menu structure** column.
1. Optional: To hide the menu item, right-click it in the **Menu structure** column, and then select **Hide**.
1. On the Action Pane, select **Save**.

## Add the menu item as a detour

To make media capture available during a task, add the media capture menu item as a detour on a step of that task. The worker can open media capture from that step and return to it when they finish.

To add media capture as a detour, follow these steps:

1. Create a menu-specific override for the step and menu item where workers can capture media. Learn how in [Add menu-specific overrides](mobile-app-titles-instructions.md#add-menu-specific-overrides).
1. On the details page for the override, on the **Available detours (menu items)** FastTab, select **Add**.
1. In the **Add detour** dialog, select your media capture menu item, and then select **OK**.
1. Optional: To fill in the search fields for the worker, select the detour, and then select **Select fields to send**. In the **Select fields to send** dialog, add a row that copies a field from the main flow to a matching search field in the media capture flow. If you select the **Auto submit** checkbox for the row, the app runs the search automatically when the worker opens the detour. Auto submit never uploads files. The worker always confirms the upload.
1. Save your changes.

Learn more about detours in [Configure detours for steps in mobile device menu items](warehouse-app-detours.md).

## Example scenario: Capture media during sales picking

This scenario shows how to let workers attach photos and videos to a license plate while they pick a sales order. For example, a worker might find a damaged carton during picking and photograph it before they continue.

### Enable sample data

To work through this scenario, use a system that has the standard demo data installed, and select the *USMF* legal entity. Learn more in [Deploy a demo environment](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md).

### Create a license plate media capture menu item

This procedure creates a media capture menu item that finds license plates by their ID.

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu items**.
1. On the Action Pane, select **New**.
1. Set the following fields:

    - **Menu item name** – Enter *Media capture*.
    - **Title** – Enter *Media capture*.
    - **Mode** – Select *Indirect*.
    - **Activity code** – Select *(Preview) Media capture*.
    - **Table name** – Select *WHSLicensePlate*.

1. On the Action Pane, select **Edit query**.
1. In the query editor, on the **Range** tab, add a row where **Field** is *License plate* and **Criteria** is blank.
1. Select **OK**.
1. Save the menu item.
1. Add the *Media capture* menu item to the menu that's assigned to user *24*, as described in [Add the menu item to a mobile device menu](#add-the-menu-item-to-a-mobile-device-menu).

### Add the detour to sales picking

This procedure makes the media capture menu item available at the license plate step of the *Sales picking* menu item. It also sends the current license plate to the detour, so the worker doesn't have to enter it again.

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device steps**.
1. If you don't see any steps, and you're working with *USMF* demo data, select **Create default setup** on the Action Pane and then reload the page.
1. Find and select the step ID *LicensePlateId*.
1. On the Action Pane, select **Add step configuration**.
1. In the **Add step configuration** drop-down dialog, set **Menu item** to *Sales picking*, and then select **OK**.
1. On the details page for the new override, on the **Available detours (menu items)** FastTab, select **Add**.
1. In the **Add detour** dialog, select *Media capture*, and then select **OK**.
1. On the **Available detours (menu items)** FastTab, select the *Media capture* detour that you created earlier, and then select **Select fields to send** on the toolbar.
1. In the **Select fields to send** dialog, in the **Send from sales picking** section, select **Add**. Then set the following fields for the new row:

    - **Copy from Sales Picking** – Select *License plate*.
    - **Paste in Media Capture** – Select *License plate*.
    - **Auto submit** – Select this checkbox.

1. Select **OK**.

The *Media capture* detour is now available at the license plate step of the *Sales picking* menu item.

### Pick a sales order and capture media

This procedure shows how a worker uses the detour during picking.

1. In Supply Chain Management, create a sales order that picks inventory from a license plate–controlled location in warehouse *24*. Release the order to the warehouse, and make a note of the work ID.
1. Sign in to the Warehouse Management mobile app as a worker for warehouse *24*. In the demo data, use *24* as the user ID and *1* as the password.
1. Select **Outbound** > **Sales picking**, and enter or scan the work ID.
1. On the license plate step, open the action menu and select **Media capture**.
1. The app searches for the license plate that the sales picking flow sent. If it doesn't find a license plate, enter a license plate ID, or enter part of an ID with a wildcard, such as *WMA\**. Then select **Search**. If the search finds several license plates, select the ones that you want to attach files to.
1. When the list shows the license plates that you want, select **Take a photo**.
1. Add one or more files by selecting either of the following options:

    - **Camera** – Take a photo or record a video.
    - **Gallery** – Select a file that's already on the device.

1. Select **Upload**. The app attaches the files to every license plate on the list and returns you to the sales picking flow.
1. Complete the remaining sales picking steps.

## View captured media in Supply Chain Management

To view the uploaded files, open the record that the worker attached files to and select the **Attachments** button in the upper-right corner of the page. The attachments pane lists the photos, videos, and other files that were uploaded for the record.

> [!NOTE]
> In Supply Chain Management version 10.0.50, you can download attached MP4 video files. However, you can't preview or play them directly in the browser.

## Related information

- [Configure detours for steps in mobile device menu items](warehouse-app-detours.md)
- [Query data by using Warehouse Management mobile app detours](warehouse-app-data-inquiry.md)
- [Customize step titles and instructions for the Warehouse Management mobile app](mobile-app-titles-instructions.md)
- [Create and configure mobile device menu items](configure-mobile-devices-warehouse.md)
- [Configure document management](../../fin-ops-core/dev-itpro/organization-administration/configure-document-management.md)
