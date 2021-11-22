---
title: You can't confirm a shipment because of an issue with the calendar
description: You can't confirm a shipment because of an issue with the calendar
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

# You can't confirm a shipment because of an issue with the calendar

Error code: TRX2716

## Symptoms

When you try to confirm a shipment, the system shows the following error message:

> The calendar type %1 requires the appointment %2 to be checked in and out.

Therefore, you can't confirm the shipment for the load.

## Cause

Active appointments for the load exist. For example, there is a rule that requires driver check-in. Therefore, the load is currently in a state where shipment confirmation fails.

## Resolution

You must investigate and fix any issues with the active appointments that are linked to the load.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the shipment can't be confirmed for.
1. On the Action Pane, on the **Transportation** tab, in the **Appointments** group, select **Appointment scheduling**.
1. Follow one of these steps:

    - Make sure that driver check-in/check-out is completed for the appointment.
    - Complete or cancel the appointment.
    - Disable the **Driver check-in required** option for the related appointment rule.
