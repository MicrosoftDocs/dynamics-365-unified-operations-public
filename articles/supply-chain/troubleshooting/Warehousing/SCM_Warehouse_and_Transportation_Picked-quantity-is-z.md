---
# required metadata

title: Picked quantity is zero throughout shipment confirmation.
description: Picked quantity is zero throughout shipment confirmation.
author: lbc@microsoft.com
manager: tfehr
ms.date: 4/15/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSLoadTable_WHSShipConfirm,WHSLoadPlanningListPage_WHSShipConfirm,WHSLoadPlanningWorkbench_WHSShipConfirm,WHSTransportLoad_WHSShipConfirm,WHSShipPlanningListPage_WHSShipConfirm,WHSShipmentDetails_WHSShipConfirm,WHSWorkTable_WHSShipConfirm,WHSWorkTableListPage_WHSShipConfirm,Dialog_WHSOutboundShipConfirmController_WHSOutboundShipConfirm
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: lbc@microsoft.com
ms.assetid: 
ms.search.region: Global
ms.author: lbc@microsoft.com

---

# Picked quantity is zero throughout shipment confirmation.

Error code: LoadLineWarningUpdatedToZero

The system displays the following error message:

> Load line for item %1 and shipment %2 has been updated to have zero quantity due to underdelivery setup allowing not to ship any quantities for this item.

## Symptoms
The load or shipment can't be ship confirmed in current state.

The calculation if picked quantity is within delivery percentage limit is based on picked quantity, load line quantity and the under delivery percentage.  If the result of the calculation has picked load line quantity zero then it will not be allowed to ship confirm. Example if work has been cancelled and the under delivery percentage is 100 on the load line then the error show up.




## Resolution
Load or shipment is currently in a state where shipment confirmation fails. Navigate to related orders for the load / shipment ensuring the work is completed or cancelled.

There are several forms where we have shipments and loads, so a couple are described here:

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed
1. Open the **Load lines** tab and select the load line for the item that exceeds the under delivery
1. Adjust the **Underdelivery** field percentage or **Quantity** field value to fulfill the requirement to ship confirm.

- Alternative pick more quantities from the related work.



