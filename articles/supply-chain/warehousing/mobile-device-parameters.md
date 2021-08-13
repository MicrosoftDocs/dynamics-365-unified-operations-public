---
title: Global mobile device parameters
description: This topic explains how to set up mobile device settings on the Warehouse management parameters page
author: ivanhuber
ms.date: 08/13/2021
ms.topic: article
ms.search.form: WHS
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: ivanhuber
ms.search.validFrom: 2021-08-13
ms.dyn365.ops.version: 10.0.18
---

# Global mobile device parameters

[!include [banner](../includes/banner.md)]

This topic explains how to set up global warehouse management parameters that affect the way the system interacts with mobile devices.

For more information about how to set up warehouse workers, see [Manage warehouse worker](manage-warehouse-workers.md). For more information about mobile device license plate handling, see [License plate receiving via the Warehouse Management mobile app](warehousing-mobile-device-app-license-plate-receiving.md). For more information about the cycle counting processes, see [Cycle counting](cycle-counting.md) and [Cycle counting example scenarios](cycle-counting-scenarios.md).

## Open the Warehouse management parameters page

To open the **Warehouse management parameters** page, go to **Warehouse management > Setup > Warehouse management parameters**. You can then set the fields related to Mobile device works as described in the next section of this topic.

## The Mobile device FastTab on the General tab

The global mobile device settings are found on the **Mobile device** FastTab of the **General** tab of the **Warehouse management parameters** page. The following settings are available here:

| Field | Description |
| --- | --- |
| **Mobile device note type** | Select the type of information displayed to workers during sales order picking. <!--KFM: more info is needed here. What does each value do? What is the **Name** column for? --> |
| **Scanned quantity limit** | Enter the maximum quantity of items that a work can scan during each session using a mobile device menu item that has its **Work creation process** set to *Adjustment in*. This setting does not affect scans made with any other type of menu item. |
| **Use mobile device session logging** | Set to *Yes* to keep a log of worker sign-in history. To view the log, go to **Work users sessions \> Inquiries and reports \> Mobile device logs \> Work user sessions**. |
| **Number of stored errors** | Enter the maximum number of error records that should be stored by the system. To view the error log, go to **Work users sessions \> Inquiries and reports \> Mobile device logs \> Work user sessions**. |
| **Default warehouse transfer journal** | Select the journal to use when workers are moving products from one warehouse to another with the help of a mobile device. If you want to use the Warehouse transfer mobile device menu <!--KFM: what is the "Warehouse transfer mobile device menu"? -->, the transfer journal selected must have its **Voucher draw** field set to *Posting*. |
| **Allow purchase order line registration when in external review** | Set this to *Yes* to allow workers to use a mobile device to register order lines for purchase orders that have an **Approval status** of *In external review*. Set this to *No* to block workers from registering lines for purchase orders that are in external review. |
| **Enable RSAT support** | Enables the Warehouse Management mobile app task validator, which logs and validates each step taken by the  app. This can significantly slow down system performance, so you should only enable this during testing, and never enable it on a production environment. |

