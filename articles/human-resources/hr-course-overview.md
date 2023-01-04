---
# required metadata

title: Courses overview
description: This article explains how Human Resources administrators and managers can use the courses features to maintain information about courses that are available to workers.
author: twheeloc
ms.date: 01/04/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmCourseType, HcmCourseTypeGroup, HRMCourseTable, HcmLearningWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7532
ms.assetid: a6950c29-8b3e-45b2-9084-ddfb1317ffaa
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Courses overview

Microsoft Dynamics 365 Human Resources provides a solution for your organization's learning needs. This solution offers two learning course paths: *virtual* and *instructor-led*.

*Virtual learning* is a learning experience that is enhanced through online resources. In *instructor-led training*, an instructor facilitates a training session for a group of workers or learners.

In our learning module, Human Resources professionals, administrators, training managers, and managers can create and assign both learning course paths to workers.

> [!NOTE]
> To use virtual courses, you must enable the **Course enhancements** feature in Feature management.
> *Virtual learning* is available in Dynamics 365 Human Resources (merged infrastructure). 

## Set up virtual courses

To configure virtual courses, you must enable the **Course enhancements** feature in Feature management. Go to **Courses \> New**, and set the **Virtual** option to **Yes**. After the feature is enabled, a course link is required. The **Course status** field will be set to **Open**. The **Allow employee to self-register** option will be set to **Yes** but can be set to **No**.

After the **Course enhancements** feature is enabled in Feature management, the following changes occur:

- A due date must be defined for course assignment.
- A course link is required.
- **Employee self service** will show an employee overview in **Courses**. User can view courses that are overdue, due soon, and assigned.
- Workers can complete virtual courses and self-attest to them.

## Set up instructor-led courses

Instructor-led courses don't have to be configured before they are used.

The following information is optional and can be specified for courses. If this information will be entered for courses, it should be set up before the course records are created:

- Course type
- Classroom groups
- Course groups
- Course locations
- Classrooms
- Instructors
- Course types

You can use *course types* to categorize courses according to their structure or content. You can create course types on the **Course types** page.

The minimum and maximum number of participants that you can register for a course is defined on the **General** FastTab of the **Courses** page.

### Course setup type 

*Setup types* determine the structure of the course. There are three setup types for courses.

| Setup type | Description |
|------|--------|
| Standard | Courses of this setup type don't have a daily agenda. It's the default setup type when you create a new course. |
| Agenda | Select this setup type to plan the details of each day of a course that takes place over multiple days. |
| Agenda + session | <p>Select this setup type for more complex courses. For example, you can divide the agenda for the course into *tracks* and *sessions*:</p><ul><li>*Tracks* are specific subject areas for a course.</li><li>*Sessions* divide up tracks, and help identify specific processes or techniques that are relevant to a track.</li></ul> |

### Course tasks

For each course, complete the following tasks:

- Register participants.
- Specify a registration deadline.
- Define the minimum and maximum number of participants.
- Assign a course location and classroom.
- Recommend hotels to course participants.
- Create a course description, which can be posted on **Employee self service**.

> [!NOTE]
> You can delete a course only if no one has registered for it.

### Course statuses

The following table lists course statuses and the actions that are completed for each.

| Status | Actions |
|------|--------|
| Created | <ul><li>Enter and modify course information.</li><li>Change the course status to **Open**, so that workers can register for the course.</li></ul> | 
| Open | <ul><li>Register participants for the course.</li><li>Remove participants from the course.</li><li>Confirm participants for the course.</li><li>Change the course status to **Closed** or **Canceled** for participants whose status is **Confirmed**.</li></ul>|
| Closed | You can reopen the course. |
| Canceled | You can reopen the course. |

### Course participants

*Course participants* are workers who participate in a training course or event. You can register participants only for open courses.

### Workflow

Employees who register for a course through the **Employee self service** page can have their registration routed through a workflow for approval. You can assign a 
workflow to a course on the **General** FastTab of the **Courses** page.
