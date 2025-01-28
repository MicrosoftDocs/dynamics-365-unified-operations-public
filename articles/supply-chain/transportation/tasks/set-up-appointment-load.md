--- 
title: Set up an appointment for a load
description: Learn how to set up and plan a dock appointment for a load typically done by transportation coordinators, including a step-by-step process. 
author: lisascholz91
ms.author: lisascholz
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: kamaybac 
ms.search.form: WHSLoadPlanningWorkbench, TMSAppointment, WHSOutboundLoadPlanningWorkbench, WHSInboundLoadPlanningWorkbench
---

# Set up an appointment for a load

[!include [banner](../../includes/banner.md)]

This procedure shows how to set up and plan a dock appointment for an inbound or an outbound load. The appointment reflects a date and time that has been agreed upon with the carrier for picking up or dropping off a load based on a sales, purchase or transfer order. Scheduling an appointment can be done after the load has been created and is typically done by a transportation coordinator.

The feature is for transportation and warehouse managers to keep track of appointments and be able to plan ahead to make sure that there is enough capacity to handle upcoming arrival of trucks for loading and unloading. 

1. Go to one of the following pages, depending on whether you are setting up an appointment for an inbound or outbound load:
    - **Transportation management > Planning > Inbound load planning workbench**.
    - **Transportation management > Planning > Outbound load planning workbench**.
1. Select a load you want to create an appointment for. If the load does not appear in the list, clear the **Hide shipped and received** check box. This is especially relevant for creating an appointment for an inbound load that has already been shipped from the vendor's site.
1. From the **Loads** toolbar, select **Transportation**  \> **Appointment scheduling**.
1. On the Action Pane, select **New**.
1. In the **Appointment rule** field, enter or select a value. This represents a physical loading or unloading dock in your warehouse that you want to schedule the appointment for. Appointment rules can be configured in **Transport management > Setup > Appointment scheduling > Appointment rules** and define parameters such as how many docks there are per warehouse and whether they can receive inbound and/or outbound loads.
1. Select a **Planned start date/time at location** in the local time zone of the facility. This is an appointment that has been agreed upon separately with the carrier. The **Planned end date/time at location** is automatically populated based on the value defined in the **Duration** field of the selected Appointment Rule. This is the time frame in which you expect the carrier to arrive at the dock door, for the warehouse to complete loading or unloading, print any shipping documentation, and depart. The **Planned start date/time** and the **Planned end date and time** fields represent the appointment in UTC time zone and is automatically populated based on the selected **Planned start date/time at location**.
1. Select **Save**.
1. Select **Update status**.
1. Select **Firm**.
1. Select **Save**.
1. Close the page.

After the appointment has been scheduled, the appointment status changes to 'Waiting', indicating that the driver has yet to check in.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
