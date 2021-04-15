---
# required metadata

title: Load has active appointments throughout shipment confirmation
description: Load has active appointments throughout shipment confirmation
author: lbc@microsoft.com
manager: tfehr
ms.date: 4/15/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSLoadTable,WHSLoadPlanningListPage,WHSLoadPlanningWorkbench,WHSTransportLoad,WHSShipPlanningListPage,WHSShipmentDetails,WHSWorkTable,WHSWorkTableListPage
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

# Load has active appointments throughout shipment confirmation

Error code: TRX2716



## Symptoms
The load can't be ship confirmed in current state.

Active appointments for the load exist with related appoint rule requiring driver check-in.




## Resolution
Load is currently in a state where shipment confirmation fails.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed
1. On the Action Pane, open the **Transportation** tab and, from the **Appointments** group, select **Appointment scheduling** and do one of the following:

- Ensure that driver check-in/out is completed for appointment
- Complete/Cancel the appointment 
- Disable **Driver check-in required** for the related appointment rule



