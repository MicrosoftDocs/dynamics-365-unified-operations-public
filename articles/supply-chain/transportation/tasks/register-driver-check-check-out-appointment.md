---
title: Register driver check-in and check-out for an appointment
description: This article shows how to register driver check-in and a driver check-out and how to interpret the appointment status.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form: TMSDriverLogListPage, TMSDriverCheckIn
ms.topic: how-to
ms.date: 11/17/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template 
---
# Register driver check-in and check-out for an appointment

[!include [banner](../../includes/banner.md)]

This procedure shows how to register a driver check-in and a driver check-out. This procedure is typically done by a transportation coordinator. Before you start, there must be an appointment set up for a load.

## Select an appointment

1. Go to **Transportation management > Planning > Dock appointment scheduling > Driver check-in and check-out**.
2. Select an appointment.

## Register driver check-in

1. Select **Driver check-in**.
2. In the **Trailer number** field, type a value.
3. In the **Driver name** field, type a value.
4. In the **Driver license** field, type a value.
5. Select **OK**.

## Register driver check-out

1. Select **Driver check-out**.
2. Select **OK**.

## Appointment status

The **Appointment status** indicates how actual driver check-in and check-out times compare to the scheduled times.

| Status| Description |
|---------|---------|
| *Waiting* | The driver didn't checked in and isn't late. |  
| *Checked in* | Driver checked in but didn't check out and isn't yet late checking out. |
| *Dropped trailer* | The driver checked in and selected the **Dropped trailer** option. |
| *Completed* | The driver checked in and checked out on time or ahead of schedule. |
| *Completed late* | The driver checked in and checked out but after the scheduled deadline. |
| *Check out warning* | The driver checked in but didn't check out and the **Alert interval** value didn't expire yet. To set the **Alert interval**, go to **Transportation Management > Setup > Transportation Management parameters**, open the **General** tab and expand the **Driver check-in and check out** FastTab.|
| *Late on check in* | The driver didn't check in yet and is now late. |
| *Late on check out* | The driver checked in but didn't check out yet and the **Alert interval** has expired. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
