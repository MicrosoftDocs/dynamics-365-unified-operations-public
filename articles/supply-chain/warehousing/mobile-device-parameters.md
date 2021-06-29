---

# required metadata

title: Mobile device settings Warehouse management parameters
description: This topic explains how to set up  Mobile device settings on the WH parameters form
author: ivanhuber
ms.date: c
ms.topic: article

# optional metadata

ms.search.form: WHS
audience: Application User
# ms.devlang:
ms.reviewer: karlmaybach
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
ms.author: ivanhuber
ms.search.validFrom: 2021-06-25
ms.dyn365.ops.version: 10.0.18

---

# Mobile device settings on the Warehouse management parameters form

This topic explains how to set up global warehouse management parameters so that they support operations via Mobile device. This topic provides general information. For detailed information that is related to the Warehouse worker setup, see [Manage warehouse worker](manage-warehouse-workers.md); the Mobile device license plate handling, see [License plate receiving via the Warehouse Management mobile app](warehousing-mobile-device-app-license-plate-receiving.md); the Cycle counting processes, see [Cycle counting](cycle-counting.md) and [Cycle counting example scenarios](cycle-counting-scenarios.md).

## Open the Warehouse management parameters page

To open the **Warehouse management parameters** page, go to **Warehouse management > Setup > Warehouse management parameters**. You can then set the fields related to Mobile device works as described in the next section of this topic.

## The Mobile device fasttab in the General tab 

The following table describes the available fields on the **Mobile device** fasttab in the **General** tab of the **Warehouse management parameters** page.

| Field | Description |
| --- | --- |
| Mobile device note type | Select the type of information that is displayed to a user during sales order picking. |
| Scanned quantity limit | Enter the maximum quantity of items that can be scanned by a mobile device for each session. |
| Use mobile device session logging | A Warehouse worker login history, can be found on the **Work user sessions** screen |
| Number of stored errors | Amount of records that are stored by the system, can be found on the **Work user sessions** screen |
| Default warehouse transfer journal | The journal that is used during movement from one warehouse to another using a mobile device. If you want to use the Warehouse transfer mobile device menu, the transfer journal selected should have the Voucher draw field set to Posting. |
| Allow purchase order line registration when in external review | It is possible to perform purchase order line registration on the mobile device when the purchase order approval status equal in external review. Select the *Yes* option to allow registration using the mobile device when the Purchase order approval status is in external review. Select *No* to block the registration when the purchase order approval status is in external review. |
| Enable RSAT support | Enables the warehouse app task validator, which logs and validates each step taken by the warehouse app. This can significantly slow down system performance, so you should only enable this during testing, and never enable it on a production environment. |

> [!NOTE]
> The **Scanned quantity limit** field does not allow exceeding the specified value only for the *Adjustment in* **Work creation process** type.
