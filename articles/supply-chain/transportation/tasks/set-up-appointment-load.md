---
title: Set up an appointment for a load
description: Learn how to set up and plan a dock appointment for a load typically done by transportation coordinators, including a step-by-step process. 
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: WHSLoadPlanningWorkbench, TMSAppointment, WHSOutboundLoadPlanningWorkbench, WHSInboundLoadPlanningWorkbench
ms.topic: how-to
ms.date: 02/12/2025
ms.custom: 
  - bap-template
---

# Set up an appointment for a load

[!include [banner](../../includes/banner.md)]

This procedure shows how to set up and plan a dock appointment for an inbound or an outbound load. The appointment reflects a date and time agreed with the carrier for picking up or dropping off a load based on a sales, purchase, or transfer order. Scheduling an appointment can be done after the load has been created and is typically done by a transportation coordinator.

This feature enables transportation and warehouse managers to keep track of appointments and plan ahead to make sure that there's enough capacity to handle upcoming arrival of trucks for loading and unloading.

1. Go to one of the following pages, depending on whether you're setting up an appointment for an inbound or outbound load:
    - **Transportation management** \> **Planning** \> **Inbound load planning workbench**.
    - **Transportation management** \> **Planning** \> **Outbound load planning workbench**.
1. Select a load you want to create an appointment for. If the load doesn't appear in the list, clear the **Hide shipped and received** check box. This is especially relevant for creating an appointment for an inbound load that has already been shipped from the vendor's site.
1. From the **Loads** toolbar, select **Transportation** \> **Appointment scheduling**.
1. On the Action Pane, select **New**.
1. In the **Appointment rule** field, enter or select a value. This represents the physical loading or unloading dock in your warehouse that you want to schedule the appointment for. Configure your appointment rules by going to **Transport management** \> **Setup** \> **Appointment scheduling** \> **Appointment rules**. Define parameters such as how many docks there are per warehouse and whether they can receive inbound and/or outbound loads.
1. Select a **Planned start date/time at location** value using the local time zone at the facility. This is an appointment that has been agreed upon separately with the carrier. The **Planned end date/time at location** value is automatically populated based on the value defined in the **Duration** field of the selected appointment rule. This is the time frame during which you expect the carrier to arrive at the dock door, the warehouse to complete loading or unloading, the warehouse to print any shipping documentation, and the driver to depart. The **Planned start date/time** and the **Planned end date and time** fields represent the appointment in the system's time zone and are automatically populated based on the selected **Planned start date/time at location**.
1. Select **Save**.
1. Select **Update status**.
1. Select **Firm**.
1. Select **Save**.
1. Close the page.

After the appointment has been scheduled, the appointment status changes to *Waiting*, which indicates that the driver has yet to check in.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
