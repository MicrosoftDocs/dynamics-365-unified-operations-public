---
# required metadata

title: Use cases for business events
description: This article provides Human resources use cases for business events.
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
ms.collection: get-started
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resources

---

# Use cases for Human resources business events


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article provides use cases for business events in Human resources.

The following are potential uses cases for business events. These use cases aren't an exhaustive list of the potential use cases. Some of these use cases may not have been implemented yet either by Microsoft or other organizations. These use cases are meant to provide ideas and help with understanding business events. 

|Business process| Use case| Value| 
|---------------|----------|-------|
|Personnel management – Position change |When a workflow item has been created for a position action, the individual assigned to the approval should be notified so they can review the position change or creation and take the appropriate action.|This business event will notify individuals when they have a position action to approve. The individual can either approve, reject or delegate the request.| 
|Personnel management – Hire action |When a workflow item has been created for a hire action, the individual assigned to the approval should be notified so they can review the new hire. |This business event will notify individuals when they have a hire action to approve. The individual can either approve, reject or delegate the request. |
|Task Management |When a task is assigned to an individual during the onboarding, offboarding, or transition processes, the individual should be notified so that they can see what needs to be done. |This use case will assist users in properly monitoring and managing all of their tasks and completing them on time. |
|Leave and absence |When employees raise a leave request, their manager should be notified for approval. |This use case will help employees notify their managers when a leave request is raised and is waiting for their approval. Their managers can either approve/reject/delegate the requests. |
|Leave and absence |When manager approves, rejects, or delegates a leave request, the employee is notified of the same. |This use case will help employees get notified when a manager approves/ rejects/ delegates a leave request they raised.| 
|Leave and absence |When employees return from a leave of absence, their manager will be notified.|This use case will help managers get a notification when an employee confirms the end date and plans to return after a leave of absence. | 
|Leave and absence |When an employee cancels their time off request, their manager will be notified. |This use case will notify managers when an employee cancels their time off requests. |
|Learning- Course assignment |The training manager frequently relies on manual intervention to alert individuals when a course has been assigned. Automating this process should increase training manager and/or HR admin productivity. | Using business events, the training department would be able to streamline and easily manage course assignment and tracking. This removes manual intervention, errors, and decreased communication between HR and employees. |
|Learning- Course completion |Many organizations manually track training courses and communicate internally and externally. Validating course completion will create efficiencies.  |Using business events, the training department would be able to streamline and easily manage course assignment and tracking. This removes manual intervention, errors, and decreased communication between HR and employees. |
|Performance management |When a goal is assigned to an employee then they should be notified so that they can see what goals need to be achieved. |This use case will assist users to manage all of their goals effectively. |

 


