--- 
# required metadata 
 
title: Register driver check-in and check-out for an appointment
description: This procedure shows how to register a driver check-in and a driver check-out. 
author: Weijiesa
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TMSDriverLogListPage, TMSDriverCheckIn
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: weijiesa
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Register driver check-in and check-out for an appointment

[!include [banner](../../includes/banner.md)]

This procedure shows how to register a driver check-in and a driver check-out. This is typically done by a transportation coordinator. You can use this procedure in the USMF demo data company. Before you start, there must be an appointment set up for a load. To create an appointment, you can run the "Set up an appointment for a load" procedure as a prerequisite.


## Select an appointment
1. Go to Transportation management > Planning > Dock appointment scheduling > Driver check-in and check-out.
2. Select an appointment.

## Register driver check-in
1. Click Driver check-in.
2. In the Trailer number field, type a value.
3. In the Driver name field, type a value.
4. In the Driver license field, type a value.
5. Click OK.

## Register driver check-out
1. Click Driver check-out.
2. Click OK.

## Appointment status
The appointment status varies based on the actual driver check-in and check-out times in comparison to the predefined deadline, accurately reflecting the current circumstances.

| Appointment status| Description |
|---|---|
| <p>Checked In</p> | Driver checked-in but not check-out, the remain left time does not exceed the scheduled deadline. |
| <p>In progress</p> | Trailer already dropped. |
| <p>Complete</p> | Driver check-in and check-out processes are successfully executed and concluded ahead of schedule. |
| <p>Completed Late</p> | Driver check-in and check-out processes are successfully executed, but the complete time exceed the scheduled deadline. |
| <p>Late warning</p> | Driver checked-in, the remaining time small than the Alert interval value. To setup Alert interval, go to **Transportation Management > Setup > Transportation Management parameters > General** , Fast tab: Driver check-in and check out. |
| <p>Late check in</p> | Driver checked-in, the remaining time does not exceed the scheduled deadline. |
| <p>Pending</p> | Driver not checked-in, the remaining time does not exceed the scheduled deadline. |
| <p>Late on check in</p> | Driver not checked-in, the remaining time has exceed the scheduled deadline. |




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
