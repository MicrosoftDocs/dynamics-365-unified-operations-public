---
title: Load has active appointments throughout shipment confirmation
description: Load has active appointments throughout shipment confirmation
author: perlynne
ms.date: 04/21/2021
ms.topic: troubleshooting
ms.search.form: WHSLoadTable_WHSShipConfirm,WHSLoadPlanningListPage_WHSShipConfirm,WHSLoadPlanningWorkbench_WHSShipConfirm,WHSTransportLoad_WHSShipConfirm,WHSShipPlanningListPage_WHSShipConfirm,WHSShipmentDetails_WHSShipConfirm,WHSWorkTable_WHSShipConfirm,WHSWorkTableListPage_WHSShipConfirm,Dialog_WHSOutboundShipConfirmController_WHSOutboundShipConfirm
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: lbc
ms.search.validFrom: 2021-04-21
ms.dyn365.ops.version: 10.0.18
---
<!-- KFM: Does this describe the issue the customer wants to solve? -->
# Load has active appointments throughout shipment confirmation

Error code: TRX2716

## Symptoms

The system displays the following error message:

> The calendar type %1 requires the appointment %2 to be checked in and out.

Therefore, the load can't be ship confirmed in current state. <!-- KFM: What is "ship confirmed"? Confirmed as shipped? Confirmed for shipment? -->

Active appointments for the load exist with a related appoint rule that requires driver check-in. <!-- KFM: Is this a symptom or a cause? -->

## Resolution

The load is currently in a state where shipment confirmation fails.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed
1. On the Action Pane, open the **Transportation** tab and, from the **Appointments** group, select **Appointment scheduling** and do one of the following:

    - Ensure that driver check-in/out is completed for appointment.
    - Complete or cancel the appointment.
    - Disable **Driver check-in required** for the related appointment rule.
