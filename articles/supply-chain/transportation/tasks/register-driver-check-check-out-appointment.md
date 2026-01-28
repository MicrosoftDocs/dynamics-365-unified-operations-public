---
title: Register driver check-in and check-out for an appointment
description: Learn how to register a driver check-in and a driver check-out, and how to interpret the appointment status with an outline for selecting an appointment.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TMSDriverLogListPage, TMSDriverCheckIn
ms.topic: how-to
ms.date: 02/14/2025
ms.custom: 
  - bap-template
---

# Register driver check-in and check-out for an appointment

[!include [banner](../../includes/banner.md)]

This article describes how to register driver check-in and check-out events, which represent drivers arriving to or leaving from a facility. The events can be registered using either the web client or the Warehouse Management mobile app. To learn how to add the required menu items to the Warehouse Management mobile app, go to [Set up mobile devices for warehouse work](/dynamics365/supply-chain/warehousing/configure-mobile-devices-warehouse).

This feature lets you keep track of whether loads have been picked up or dropped off, and to confirm whether carriers are arriving and departing within the agreed-upon appointments. It calculates and shows whether carriers are late when checking in and/or out.

Before you start, an appointment must be set up for a load.

## Select or open an appointment

To select or open an appointment in the web client, follow these steps:

1. Go to **Transportation management** \> **Planning** \> **Dock appointment scheduling** \> **Driver check-in and check-out**.
1. Set the **Display completed and canceled appointments** check box as needed, depending on whether you'd like to see previous closed appointments in the grid.
1. Select an appointment.

## Register driver check-in

You can register driver check-in using either the web client or the Warehouse Management mobile app.

To check in a driver using the web client, follow these steps:

1. Select an appointment, as described previously.
1. On the Action Pane, select **Driver check-in**.
1. Enter the **Actual start date/time at location** to reflect the actual time the driver checked in.
1. Fill out the fields on the **The driver's information** dialog as needed.
1. Select **OK**.

To check in a driver using the Warehouse Management mobile app, follow these steps:

1. Select **Driver check-in**.
2. Scan or enter the load or appointment ID.
3. Select **Enter**.

If the driver check-in was registered within the scheduled appointment window, then the **Appointment status** changes to *Checked in*.

## Register driver check-out

After loading or unloading has finished and the driver has left the facility, you can check out the driver using either the web client or the Warehouse Management mobile app.

To check out a driver using the web client, follow these steps:

1. Select an appointment, as described previously.
1. On the Action Pane, select **Driver check-out**.
1. Fill out the fields on the **The driver's information** dialog as needed.
1. Select **OK**.

To check out a driver using the Warehouse Management mobile app, follow these steps:

1. Select **Driver check-out**
2. Scan or enter the load or appointment ID
3. Select **Enter**

If driver check-in and check-out are done within or before the scheduled appointments, the **Appointment status** changes to *Completed*.

## Appointment status

For each record listed on the **Driver check-in and check-out** page, the **Appointment status** field indicates how actual driver check-in and check-out times compare to the scheduled times. The feature also calculates and shows if carriers were late checking in and/or out.

> [!TIP]
> Select the **Display completed and canceled appointments** check box to display closed appointments in the grid.

The following table describes the possible **Appointment status** that an appointment can have.

| Appointment status | Description |
|--------|-------------|
| *Waiting* | The driver hasn't checked in but isn't yet late. |
| *Checked in* | The driver checked in but hasn't checked out and isn't yet late checking out. |
| *Dropped trailer* | The driver checked in and selected the **Dropped trailer** option. |
| *Completed* | The driver checked in and checked out on time or ahead of schedule. |
| *Completed late* | The driver checked in and checked out, but after the scheduled deadline. |
| *Check out warning* | The driver checked in but hasn't checked out, and the alert interval hasn't yet expired. To specify the alert interval, go to **Transportation Management** \> **Setup** \> **Transportation Management parameters**, and then, on the **General** tab, on the **Driver check-in and check out** FastTab, set the **Alert interval** field. |
| *Late on check in* | The driver hasn't checked in and is now late. |
| *Late on check out* | The driver checked in but hasn't checked out, and the alert interval has now expired. |

These statuses help warehouse and transportation managers to do the following tasks:

1. Track the status of ongoing shipments, follow up with carriers on loads that deviated from the plan, and  mitigate delays.
1. Identify trends in the timeliness of each carrier.
1. Identify potential problems in your own warehouse operations that are resulting in late check-outs caused by delays in loading or unloading.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
