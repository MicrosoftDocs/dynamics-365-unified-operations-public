---
# required metadata

title: Use cases for business events
description: This article provides use cases for business events.
author: twheeloc
ms.date: 03/03/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HRMParameters, EssWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: ["51941", "intro-internal"]
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resources

---

# Use cases for business events

[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article provides use cases for business events.

The following table lists and describes potential uses cases for business events. This list isn't exhaustive. Some of these use cases might not yet have been implemented either by Microsoft or other organizations. These use cases are meant to provide ideas and to help you understand business events.

| Business process | Use case | Value |
|------------------|----------|-------|
| Personnel management – Position change | When a workflow item is created for a position action, the individual who's assigned to the approval should be notified, so that they can review the position change or creation and take the appropriate action. | This business event will notify individuals when they have a position action to approve. The individual can then approve, reject, or delegate the request. | 
| Personnel management – Hire action | When a workflow item is created for a hire action, the individual who's assigned to the approval should be notified, so that they can review the new hire. | This business event will notify individuals when they have a hire action to approve. The individual can then approve, reject, or delegate the request. |
| Task Management | When a task is assigned to an individual during the onboarding, offboarding, or transition process, that individual should be notified, so that they can see what must be done. | This use case will help users correctly monitor and manage all their tasks and complete them on time. |
| Leave and absence | When employees submit a leave request, their manager should be notified for approval. | This use case will help employees notify their manager when a leave request is submitted and awaiting their approval. The manager can then approve, reject, or delegate the request. |
| Leave and absence | When a manager approves, rejects, or delegates a leave request, the employee is notified. | This use case will help employees be notified when a manager approves, rejects, or delegates a leave request that they submitted. | 
| Leave and absence | When employees return from a leave of absence, their manager will be notified. | This use case will help managers be notified when an employee confirms the end date of a leave of absence and plans to return. | 
| Leave and absence | When an employee cancels their time off request, their manager will be notified. | This use case will notify managers when employees cancel their time off requests. |
| Learning – Course assignment | The training manager often relies on manual intervention to alert individuals when a course has been assigned. Automation of this process should increase training manager and/or HR admin productivity. | By using business events, the training department will be able to streamline and easily manage course assignment and tracking. Therefore, this use case will help eliminate manual intervention, errors, and decreased communication between HR and employees. |
| Learning – Course completion | Many organizations manually track training courses and communicate internally and externally. Validation of course completion will create efficiencies. | By using business events, the training department will be able to streamline and easily manage course assignment and tracking. Therefore, this use case will help eliminate manual intervention, errors, and decreased communication between HR and employees. |
| Performance management | When a goal is assigned to an employee, that employee should be notified so that they can see what goals must be achieved. | This use case will help users effectively manage all their goals. |
