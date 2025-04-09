---
title: Global mobile device parameters
description: Learn how to set up mobile device settings on the Warehouse management parameters page with an outline on opening the Warehouse management parameters page.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 08/13/2021
ms.reviewer: kamaybac
ms.search.form: WHS
---

# Global mobile device parameters

[!include [banner](../includes/banner.md)]

This article explains how to set up global warehouse management parameters that affect how the system interacts with mobile devices.

For more information about how to set up warehouse workers, see [Manage warehouse worker](manage-warehouse-workers.md). For more information about license plate handling on mobile devices, see [License plate receiving via the Warehouse Management mobile app](warehousing-mobile-device-app-license-plate-receiving.md). For more information about the cycle counting processes, see [Cycle counting](cycle-counting.md) and [Cycle counting example scenarios](cycle-counting-scenarios.md).

## Open the Warehouse management parameters page

To open the **Warehouse management parameters** page, go to **Warehouse management \> Setup \> Warehouse management parameters**. You can then set the fields that are related to mobile device work, as described in the next section of this article.

## Mobile device FastTab on the General tab

The global mobile device settings are found on the **Mobile device** FastTab on the **General** tab of the **Warehouse management parameters** page. The following fields are available.

| Field | Description |
|---|---|
| Mobile device note type | Select the type of information that is shown to workers during sales order picking. |
| Scanned quantity limit | Enter the maximum item quantity that a worker can scan during each session by using a mobile device menu item that has a **Work creation process** value of *Adjustment in*. This field doesn't affect scans that are done by using any other type of menu item. |
| Use mobile device session logging | Set this option to *Yes* to keep a log of worker sign-in history. To view the log, go to **Work users sessions \> Inquiries and reports \> Mobile device logs \> Work user sessions**. |
| Number of stored errors | Enter the maximum number of error records that the system should store. To view the error log, go to **Work users sessions \> Inquiries and reports \> Mobile device logs \> Work user sessions**. |
| Default warehouse transfer journal | Select the journal that is used when workers use a mobile device to move products from one warehouse to another. |
| Allow purchase order line registration when in external review | Set this option to *Yes* if workers should be able to use a mobile device to register order lines for purchase orders that have an **Approval status** value of *In external review*. Set this option to *No* to prevent workers from registering lines for purchase orders that are in external review. |
| Enable RSAT support | The field enables the Warehouse Management mobile app task validator, which logs and validates each step that the app performs. Because this process can significantly slow down system performance, you should enable the validator only during testing. You should never enable it in a production environment. |

## Mobile device menu item display inventory dimensions FastTab on the General tab

In this fast tab, you can configure how **tracking dimension below location** is displayed in the mobile app, including **batch below number** and **serial below number**. It has no impact on tracking dimension above location, such as batch above number or serial above number display.

The **Display tracking dimension control for last on-hand** setting applies to the entire **work order type**, meaning it affects all mobile device menu items if they are used to process this work order type. Currently, this feature is supported only for **sales orders** — other work order types (e.g. transfer order, purchase order) are not supported. The setting has two options:

- **Display tracking dimension control**. The mobile app always displays the tracking dimension below location control (batch below number or serial below number) when processing this work order type.
- **Hide tracking dimension control**. The mobile app always hides the tracking dimension below location control (batch below number or serial below number) when processing this work order type.

Consider the following scenario:

- A batch below item whsbb.
- A sales order is placed for whsbb with a quantity of 2 eaches.
- The available on-hand inventory for whsbb is 2 eachs (the last batch in stock).

If the setting is configured to **Hide tracking dimension control** (Default configuration):

- The system will automatically assign the batch number behind the scene and proceed.
- The mobile app will not display batch number control.
- User can not confirm or edit batch number in the mobile app, even if batch number confirmation is enabled.

If the setting is configured to **Display tracking dimension control**:

- The mobile app will display an **empty** batch number control.
- The user must manually enter the batch number.

To configure this setting for an individual mobile device menu item, navigate to the **mobile device menu item** \> set the **Display tracking dimension control for last on-hand** field, where you can override the setting here. Similarly, it will only take effect if the menu item is used to process the supported work order type (currently only sales order). For more details, see <a href="configure-mobile-devices-warehouse.md#additional-menu-item-options">Additional menu item options</a>.
