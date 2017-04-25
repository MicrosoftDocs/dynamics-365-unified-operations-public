---
# required metadata

title: Set up training courses
description: Human resources administrators and managers can use the courses features to maintain information about the training that's offered to workers.
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: HcmCourseType, HcmCourseTypeGroup, HRMCourseTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 7532
ms.assetid: a6950c29-8b3e-45b2-9084-ddfb1317ffaa
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up training courses

[!include[banner](includes/banner.md)


Human resources administrators and managers can use the courses features to maintain information about the training that's offered to workers.

 Set up prerequisites
---------------------

The following information is required and must be set up before you create courses.
-   **Course types**

The following information is optional information that you can specify for courses. If you know that you will be entering this information for courses, you should set up this information before you create course records.
-   **Classroom groups**
-   **Course groups**
-   **Course locations**
-   **Classrooms**
-   **Instructors**

## Course types
You can use course types to categorize courses according to the structure or content of the course. You can create course types on the **Course types** page. You must select a course type when you create a course record.

## Course setup type
The following table lists the three setup types for courses. Setup types determine the structure of the course.

<table>
<thead>
<tr class="header">
<th>Setup type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Standard</strong></td>
<td>Select this type for courses that will not have a daily agenda. This is the default setup type when you create a new course.</td>
</tr>
<tr class="even">
<td><strong>Agenda</strong></td>
<td>Select this type to plan the details of each day of a course that takes place over multiple days.</td>
</tr>
<tr class="odd">
<td><strong>Agenda + session</strong></td>
<td>Select this type for the more complex courses. For example, you can divide the agenda for the course into tracks and sessions.
<ul>
<li><strong>Track</strong> – Tracks are specific subject areas for a course.</li>
<li><strong>Sessions</strong> – Sessions divide up tracks and help identify specific processes or techniques that are relevant to the track.</li>
</ul></td>
</tr>
</tbody>
</table>

## Course tasks
For each course, you can complete the following tasks.
-   Register participants
-   Specify a registration deadline
-   Define the minimum and maximum number of participants
-   Assign a course location and classroom
-   Recommend hotels to course participants
-   Create a course description, which you can then advertise on Employee self service

  >**Note**
  >You can delete a course only if no one has registered for it. 
    
## Course statuses
The following table lists the possible course statuses and the actions that you can complete when the course has a specific status.

<table>
<thead>
<tr class="header">
<th>Status</th>
<th>Actions</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Created</strong></td>
<td><ul>
<li>Enter and modify course information.</li>
<li>Change the course status to <strong>Open</strong> so that workers can register for the course.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Open</strong></td>
<td><ul>
<li>Register participants for the course.</li>
<li>Remove participants from the course.</li>
<li>Confirm participants for the course.</li>
<li>Change the course status to <strong>Closed</strong> or <strong>Canceled</strong>.</li>
<li>Plan questionnaires for participants whose status is <strong>Confirmed</strong>.</li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>Closed</strong></td>
<td>You can reopen the course.</td>
</tr>
<tr class="even">
<td><strong>Canceled</strong></td>
<td>You can reopen the course.</td>
</tr>
</tbody>
</table>

## Course participants
Course participants are workers, applicants, or contact persons who participate in a training course or event. You can only register participants for open courses. The minimum and maximum number of participants that you can register for a course is defined on the **General** FastTab on the **Courses** page.

Workflow
--------

Employees who register for a course through the **Employee self service** page can have their registration routed through workflow for approval.  A workflow can be assigned to a course on the **General** FastTab on the **Courses** page.




