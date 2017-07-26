---
# required metadata

title: Workforce management overview
description: 
author: shalabhjainmsft
manager: AnnBe
ms.date: 7/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 260624
ms.assetid: a4f9d315-9951-451c-8ee6-37f9b3b15ef0
ms.search.region: global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2017-07-30
ms.dyn365.ops.version: Retail July 2017 update

---

# Workforce management overview

[!include[banner](includes/banner.md)]
	
## Introduction
Workforce management (WFM) service leverages the familiar Point of Sale clients - Modern POS and Cloud POS - to empower store managers to easily manage their workforce. The WFM service uses the extension framework to download the relevant packages in POS. These packages are downloaded when the POS is closed and reopened. When Microsoft releases new features for WFM, the POS app needs to be closed and reopened. Using this service, the store managers can easily create and publish weekly work schedule for their stores. The store workers can quickly view their schedules, along with the schedule of their colleagues, to know who will be working with them during the assigned shifts. They can also create requests for absence, shift swap, and shift offer, all of which trigger a defined workflow. During the shift, the store workers can leverage the clock in and clock out capability, built in the POS clients, which sends the data to the HQ for payroll processing. The clock in and clock out feature is an existing capability of POS. The following link provides more details about the setup and supported scenarios
[Clock in and clock out]( https://docs.microsoft.com/en-us/dynamics365/operations/retail/retail-time-attendance).

## Supported scenarios
The following section provides additional details on the supported scenarios:

* __Schedule creation and publish__ - The WFM service leverages the POS permissions configured in the HQ to determine if a worker has store manager privileges. Only a store manager can create and publish schedules using the Schedule management operation. They can copy and paste an existing work shift from one worker to another to quickly create the schedule. Additionally, they can import the schedule from any of the previous weeks to the current week to create the schedule. If the schedule is not published, then the schedule is in a draft state, which is visually different than the schedule in the published schedule. Store managers can publish the schedule by clicking the **Publish** button for any week. After the schedule is published for a week, then any further changes, such as adding, editing, or deleting work shifts or absences are automatically published. The store workers can only view the schedule for the published weeks.

* __Create and approve requests__ - The store workers can create three types of requests:
  - Request absence 
  - Request shift swap
  - Request shift offer 

  These requests can be created using the Schedule requests operation. Each request follows a defined workflow and the workers can easily see the current status of their requests. Absence requests are automatically sent to the store manager for approval. If there are multiple store managers, all managers will be able to view the request, but only one of manager will be able to approve or reject the request. The absence types are configured in the retail HQ using the **Leave and absence types** form in the Retail module. After the store manager approves or rejects the request, it moves to the **History** tab of the Schedule requests operation. For shift swap and offer requests, the request first goes to the worker to whom the request is sent. Only after this worker has approved the request can the store manager view the request. For example, if the worker rejects the shift swap or offer request then the manager will not be able to view it. The worker who created the request also has an option to cancel the request before the manager approves or denies it.  
	
* __Display the active store workers in the schedule view__ - When a worker is added to a store, such as by associating to the store's employee address book, then this worker will be available for scheduling in the WFM service. This is achieved by running a recurring batch job named **Process worker data for workforce management** in HQ. This job prepares the store-worker associations that will be sent to the Common Data Service (CDS). The same is true for removing a worker from a store scenario. However, the removed worker will still be displayed for the past, current, and future weeks if there is an active work shift or absence assigned to the removed worker. Thus, unless these work shifts and absences are deleted, the removed worker will be displayed for these weeks.
