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

## Glossary

**Work shift** - This defines a period where workers are scheduled to work 

**Shift swap request** - This is a request by a worker to another worker for exchanging their work shifts. Once the request is approved then the shifts are exchanged.

**Shift offer request** - This is a request by a worker to another worker for transferring one's shift to another worker. Once the request is approved, the requester's shift is transferred to another worker.   
	
## Introduction
Workforce management (WFM) service leverages the familiar Point of Sale clients i.e. Modern POS and Cloud POS to light up features, that empower the store managers to easily manage their workforce.  The WFM service uses the extension framework to download the relevant packages in POS. These packages are downloaded whenever the POS is closed and re-opened. Thus, when Microsoft releases new features for WFM the POS app needs to be closed and reopened. Using this service, the store managers can easily create and publish weekly work schedule for their stores. The store workers can quickly view their schedules, along with the schedule of their colleagues, to know who will be working with them during the assigned shifts. They can also create requests for absence, shift swap and shift offer which trigger a defined workflow. During the shift, the store workers can leverage the clock in and clock out capability, built in the POS clients, which sends the data to the HQ for payroll processing. The clock in and clock out feature is an existing capability of POS and the below link provides more details about the setup and supported scenarios:
[Clock in and clock out]( https://docs.microsoft.com/en-us/dynamics365/operations/retail/retail-time-attendance)

## Supported scenarios
The below section provides additional details on the supported scenarios:

* __Schedule creation and publish__ - The WFM service leverages the POS permissions configured in the HQ to determine if a worker has the store manager privileges or not. Only the store managers can create and publish schedules using the "Schedule management" operation. They can copy and paste an existing work shift from one worker to another to quickly create the schedule. Additionally, they can import the schedule from any of the previous weeks to current week to create the schedule. If the schedule is not published, then the schedule is in draft state, which can be easily visually differentiated from the schedule in the published schedule. Store managers can publish the schedule by pressing the "Publish" button for any week. Once the schedule is published for a week, then any further changes i.e. adding, editing and deleting work shifts or absences are automatically published. The store workers can view the schedule only for the published weeks.

* __Create and approve requests__ - The store workers can create three types of requests 1. Request absence 2. Request shift swap 3. Request shift offer. These requests can be created using the "Schedule requests" operation. Each request follows a defined workflow and the workers can easily see the current status of their requests. Absence requests are automatically sent to the store manager for approval. In case of multiple store managers, all of managers will be able to view the request, but only one of them will be able to approve or reject the request. The absence types available to choose are configured in the retail HQ using the new "Leave and absence types" form added to the Retail module. Once the store manager approves or rejects the request, it moves to the history tab of the 'Schedule requests' operation. For the shift swap and offer requests, the request first goes to the worker to whom the request is sent. Only after this worker has approved the request can the store manager view the request i.e. if the worker rejects the shift swap or offer request then the manager will not be able to view it.  The worker who created the request also has an option to cancel the request before the manager approves or denies it.  
	
* __Display the active store workers in the schedule view__ - When a worker is added to a store i.e. by associating to the store's employee address book, then this worker will be available for scheduling in the WFM service. This is achieved by running a recurring batch job named 'Process worker data for workforce management' in HQ. This job prepares the store-worker associations which will be sent to CDS. The same is true for removing a worker from a store scenario. However, the removed worker will still be displayed for the past, current and future weeks which has an active work shift or absence assigned to the removed worker. Thus, unless these work shifts and absences are deleted, the removed worker will still be displayed for such weeks.
