---
# required metadata

title: Courses overview
description: This article explains how Human Resources administrators and managers can use the courses features to maintain information about courses that are available to workers.
author: twheeloc
ms.date: 03/20/2023
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

Microsoft Dynamics 365 Human Resources provides a solution for your organization's learning needs. This solution offers two learning course paths: *virtual* and *in-person*.

*Virtual learning* is a learning experience that is enhanced through online resources. For *in-person training* or *instructor-led training*, an instructor facilitates a training session for a group of workers or learners.

In our learning module, Human Resources professionals, administrators, training managers, and managers can create and assign both learning course paths to workers.

> [!NOTE]
> To use virtual courses, you must enable the **Course enhancements** feature in Feature management.

## Set up virtual courses

To configure virtual courses, you must enable the **Course enhancements** feature in Feature management. Go to **Courses \> New**, and set the **Virtual** option to **Yes**. After the feature is enabled, a course link is required. The **Course status** field will be set to **Open**. The **Allow employee to self-register** option will be set to **Yes** but can be set to **No**. You can use the **Cost** section to associate a cost with the course or the participant. The default cost is **None**.

After the **Course enhancements** feature is enabled in Feature management, the following changes occur:

- On the **Participants** page, a due date must be defined for course assignment.
- A course link is required.
- **Employee self service** will display an employee overview in **Courses**. User can view courses that are overdue, due soon, and assigned.
- Workers can complete virtual courses and self-attest to them.

## Set up in-person courses

Go to **Courses \> New**, select **In-person**, and complete the page. In-person courses require a start date and time, and also a minimum and maximum number of participants. When you create a new course, you can save it as a draft, so that you can make changes. You can use the **Cost** section to associate a cost with the course or the participant. The default cost is **None**.

You can specify the following optional information for courses. If you know that you will be entering this information for courses, you should set it up before you create course records.

- Course template
- Classroom groups
- Course groups
- Course locations
- Classrooms
- Instructors

### Course tasks

For each course, complete the following tasks:

- Register, assign, and manage participants.
- Define a virtual or in-person course.
- Define the cost per course or participant (if applicable).
- Specify a registration deadline.
- Define the minimum and maximum number of participants.
- Assign a course location and classroom.
- Recommend hotels to course participants.
- Create a course description that will be shown in **Employee self service**.

> [!NOTE]
> You can delete a course only if no one has registered for it.

### Workflow

Employees who register for a course through the **Employee self service** page can have their registration routed through a workflow for approval. You can assign a 
workflow to a course on the **General** FastTab of the **Courses** page.
