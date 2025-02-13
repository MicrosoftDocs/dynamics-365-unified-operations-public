---
title: Register driver check-in and check-out for an appointment
description: Learn how to register a driver check-in and a driver check-out, and how to interpret the appointment status with an outline for selecting an appointment.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TMSDriverLogListPage, TMSDriverCheckIn
ms.topic: how-to
ms.date: 01/31/2025
ms.custom: 
  - bap-template
---

# Register driver check-in and check-out for an appointment

[!include [banner](../../includes/banner.md)]

This article describes how to register a driver check-in and a driver check-out, which represent a driver arriving at or leaving a facility. The procedures can be done either within the Finance and Operations user interface or on the Warehouse Mobile App. See [Set up mobile devices for warehouse work](/dynamics365/supply-chain/warehousing/configure-mobile-devices-warehouse) for how to add these menu items to the Warehouse Management mobile app.

This feature is used to keep track of whether loads have been picked up or dropped off, as well as whether carriers are arriving and departing within the agreed-upon appointments. It will calculate and show if carriers are late in checking in and/or out.

Before you start, an appointment must be set up for a load.

## Select an appointment

1. Go to **Transportation management** \> **Planning** \> **Dock appointment scheduling** \> **Driver check-in and check-out**.
2. Select an appointment.

## Register driver check-in

This can be done through the Finance and Operations user interface or the Warehouse Management mobile app:.

Via the web client:
1. Select **Driver check-in**.
2. Enter the **Actual start date/time at location** to reflect the actual time the driver checked in.
3. Optionally, select a **Shipping carrier** and **Location**, and enter a **Trailer number**, **Notes**, **Tractor number**, **Driver name**, **Driver license** and/or **Shipping container ID**.
5. Select **OK**.

Via Warehouse Management mobile app:
1. Select **Driver check-in**
2. Scan or enter the load or appointment ID
3. Select **Enter**

If the driver check-in was registered within the scheduled appointment window, then the status of the appointment will change to *Checked in*. 

## Register driver check-out

Once loading or unloading has finished and the driver has left the facility, you can register this by using the **Driver check-out** functionality. This can be done through the web client or the Warehouse Management mobile app.

Via web client:

1. Select **Driver check-out**.
2. Optionally, select or edit **Shipping carrier** and **Location**, and enter or edit a **Trailer number**, **Notes**, **Tractor number**, **Driver name**, **Driver license** and/or **Shipping container ID**.
3. Select **OK**.

Via Warehouse Management mobile app:
1. Select **Driver check-out**
2. Scan or enter the load or appointment ID
3. Select **Enter**

If driver check-in and check-out are done within or before the scheduled appointments, the appointment status will change to *Completed*.

## Appointment status

The **Appointment status** field indicates how actual driver check-in and check-out times compare to the scheduled times. The feature will also calculate and show if carriers are late in checking in and/or out.

Select **Display completed and canceled appointments** to show previous closed appointments.

| Status | Description |
|--------|-------------|
| *Waiting* | The driver hasn't checked in but isn't yet late. |
| *Checked in* | The driver checked in but hasn't checked out and isn't yet late checking out. |
| *Dropped trailer* | The driver checked in and selected the **Dropped trailer** option. |
| *Completed* | The driver checked in and checked out on time or ahead of schedule. |
| *Completed late* | The driver checked in and checked out, but after the scheduled deadline. |
| *Check out warning* | The driver checked in but hasn't checked out, and the alert interval hasn't yet expired. To specify the alert interval, go to **Transportation Management** \> **Setup** \> **Transportation Management parameters**, and then, on the **General** tab, on the **Driver check-in and check out** FastTab, set the **Alert interval** field. |
| *Late on check in* | The driver hasn't checked in and is now late. |
| *Late on check out* | The driver checked in but hasn't checked out, and the alert interval has now expired. |

These statuses help warehouse and transportation managers to:
1.	Track the status of ongoing shipments and be able to follow up with carriers on any loads that are deviating from the plan as well as to mitigate delays.
2.	Identify trends in timeliness of each carrier.
3.	Identify potential problems in own warehouse operations through late check-outs caused by delays in loading or unloading.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
