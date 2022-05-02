---
title: Global mobile device parameters
description: This topic explains how to set up mobile device settings on the Warehouse management parameters page.
author: Mirzaab
ms.date: 08/13/2021
ms.topic: article
ms.search.form: WHS
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mirzaab
ms.search.validFrom: 2021-08-13
ms.dyn365.ops.version: 10.0.18
---

# Global mobile device parameters

[!include [banner](../includes/banner.md)]

This topic explains how to set up global warehouse management parameters that affect how the system interacts with mobile devices.

For more information about how to set up warehouse workers, see [Manage warehouse worker](manage-warehouse-workers.md). For more information about license plate handling on mobile devices, see [License plate receiving via the Warehouse Management mobile app](warehousing-mobile-device-app-license-plate-receiving.md). For more information about the cycle counting processes, see [Cycle counting](cycle-counting.md) and [Cycle counting example scenarios](cycle-counting-scenarios.md).

## Open the Warehouse management parameters page

To open the **Warehouse management parameters** page, go to **Warehouse management \> Setup \> Warehouse management parameters**. You can then set the fields that are related to mobile device work, as described in the next section of this topic.

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
