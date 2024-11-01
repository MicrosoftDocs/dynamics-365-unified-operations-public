---
title: Register driver check-in and check-out for an appointment
description: Learn how to register a driver check-in and a driver check-out, and how to interpret the appointment status with an outline for selecting an appointment.
author: lisascholz
ms.author: lisascholz
ms.topic: how-to
ms.date: 11/17/2023
ms.custom: bap-template 
ms.reviewer: kamaybac
ms.search.form: TMSDriverLogListPage, TMSDriverCheckIn
---

# Register driver check-in and check-out for an appointment

[!include [banner](../../includes/banner.md)]

This article describes how to register a driver check-in and a driver check-out. The procedures are typically done by a transportation coordinator. Before you start, an appointment must be set up for a load.

## Select an appointment

1. Go to **Transportation management** \> **Planning** \> **Dock appointment scheduling** \> **Driver check-in and check-out**.
2. Select an appointment.

## Register driver check-in

1. Select **Driver check-in**.
2. In the **Trailer number** field, enter a value.
3. In the **Driver name** field, enter a value.
4. In the **Driver license** field, enter a value.
5. Select **OK**.

## Register driver check-out

1. Select **Driver check-out**.
2. Select **OK**.

## Appointment status

The **Appointment status** field indicates how actual driver check-in and check-out times compare to the scheduled times.

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

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
