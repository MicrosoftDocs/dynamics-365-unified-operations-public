---
title: Global mobile device parameters
description: Learn how to set up mobile device settings on the Warehouse management parameters page with an outline on opening the Warehouse management parameters page.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHS
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Global mobile device parameters

[!include [banner](../includes/banner.md)]

This article explains how to set up global warehouse management parameters that affect how the system interacts with mobile devices.

For more information about how to set up warehouse workers, see [Manage warehouse worker](manage-warehouse-workers.md). For more information about license plate handling on mobile devices, see [License plate receiving via the Warehouse Management mobile app](warehousing-mobile-device-app-license-plate-receiving.md). For more information about the cycle counting processes, see [Cycle counting](cycle-counting.md) and [Cycle counting example scenarios](cycle-counting-scenarios.md).

## Open the Warehouse management parameters page

To open the **Warehouse management parameters** page, go to **Warehouse management \> Setup \> Warehouse management parameters**. You can then set the fields that are related to mobile device work.

## Global mobile device settings

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

## Inventory dimension display options

On the **Mobile device menu item display inventory dimensions** FastTab, you can use the **Display tracking dimension control for last on-hand** field to specify how the mobile app shows the *tracking dimension below location* control, including *batch below number* and *serial below number*. The setting has no impact on the display of *tracking dimension above location*, such as *batch above number* or *serial above number*.

This feature requires Supply Chain Management version 10.0.44 or later.

The setting of the **Display tracking dimension control for last on-hand** field applies to the entire work order type. Therefore, it affects all mobile device menu items that are used to process the work order type. Currently, this feature is supported only for sales orders. No other work order types (such as transfer orders and purchase orders) are supported.

Two options are available for this field:

- *Display tracking dimension control* – The mobile app always shows the tracking dimension below location control (batch below number or serial below number) when the work order type is processed.
- *Hide tracking dimension control* – The mobile app always hides the tracking dimension below location control (batch below number or serial below number) when the work order type is processed.

Consider the following scenario:

- You have a batch below item that is named *whsbb*.
- A sales order is placed for a quantity of two pieces of item *whsbb*.
- The available on-hand inventory for item *whsbb* is two pieces (the last batch in stock).

If the **Display tracking dimension control for last on-hand** field is set to *Hide tracking dimension control* (the default value), the following behavior occurs:

- The system automatically assigns the batch number behind the scenes and then proceeds.
- The mobile app doesn't show batch number control.
- The worker can't confirm or edit the batch number in the mobile app, even if batch number confirmation is enabled.

If the field is set to *Display tracking dimension control*, the following behavior occurs:

- The mobile app shows an *empty* batch number control.
- The user must manually enter the batch number.

You can override the default setting for any individual mobile device menu item that supports it by going to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**. Learn more in [Additional menu item options](configure-mobile-devices-warehouse.md#additional-menu-item-options).

> [!NOTE]
> This setting affects only menu items that process a supported work order type (currently only sales orders). Unsupported work order types (such as transfer orders and purchase orders) aren't affected.
