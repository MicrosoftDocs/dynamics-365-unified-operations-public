---
# required metadata

title: Workforce management overview
description: This topic describes how you can use the Workforce management (WFM) service to take advantage of the familiar point of sale (POS) clients, Modern POS and Cloud POS, so that store managers can easily manage their workforce.
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
	
The Workforce management (WFM) service takes advantage of the familiar point of sale (POS) clients, Modern POS and Cloud POS, to let store managers easily manage their workforce. The WFM service uses the extension framework to download the relevant packages in the POS. These packages are downloaded when the POS is closed and reopened. Therefore, when Microsoft releases new features for WFM, the POS app must be closed and reopened.

By using this service, store managers can easily create and publish weekly work schedule for their stores. Store workers can then quickly view their own schedules and the schedules of their colleagues. In that way, they can learn who will be working with them during the assigned shifts. Store workers can also create requests for absence, shift swap, and shift offer. All these requests trigger a defined workflow.

During a shift, store workers can take advantage of the clock-in and clock-out feature that is built into the POS clients. The data is then sent to the headquarters (HQ) for payroll processing. The clock-in and clock-out feature is an existing capability of the POS. For more information about the setup and supported scenarios, see [Clock in and clock out](retail-time-attendance.md).

## Supported scenarios
This section provides more information about the supported scenarios.

- **Create and publish schedules** – The WFM service uses the POS permissions that are configured in the HQ to determine whether a worker has store manager privileges. Only store managers can create and publish schedules by using the Schedule management operation. They can quickly create a schedule by copying and pasting an existing work shift from one worker to another worker. They can also create a schedule by importing the schedule from any previous week to the current week.

    If a schedule isn't published, it's in a draft state and looks different than a published schedule. Store managers can publish a schedule by clicking the **Publish** button for any week. After the schedule is published for a week, any changes are automatically published. Examples of changes include the addition or deletion of work shifts or absences, or edits to work shifts or absences. Store workers can view only schedules that have been published for various weeks.
    
- **Create and approve requests** – Store workers can create three types of request:

    - Request absence
    - Request shift swap
    - Request shift offer

    These requests can be created by using the Schedule requests operation. Each request follows a defined workflow, and workers can easily see the current status of their requests.
    
    Absence requests are automatically sent to the store manager for approval. If there are multiple store managers, all managers can view a given request, but only one manager can approve or reject it. The absence types are configured in the retail HQ by using the **Leave and absence types** page in the **Retail** module. After the store manager approves or rejects a request, it's moved to the **History** tab for the Schedule requests operation.
    
    A shift swap or shift offer request first goes to the worker that the request was sent to. The store manager can view the request only after this worker has approved it. Therefore, if the worker rejects the shift swap or shift offer request, the manager can't view it. The worker who created the request can also cancel it before the manager approves or denies it.

- **Show the active store workers in the schedule view** – When a worker is added to a store by, for example, associating him or her with the store's employee address book, the worker becomes available for scheduling in the WFM service. A recurring batch job that is named **Process worker data for workforce management** is run in the HQ. This job prepares the store-worker associations that will be sent to the Common Data Service (CDS).

    The same process is used when a worker is removed from a store. However, the worker who is removed is still shown for past, current, and future weeks if an active work shift or absence is assigned to that worker. Therefore, unless these work shifts and absences are deleted, the removed worker will continue to be shown for these weeks.
