---
# required metadata

title: Courses overview
description: Human resources administrators and managers can use the courses features to maintain information about courses available to workers.
author: twheeloc
ms.date: 08/26/2021
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

Dynamics 365 Human Resources provides a solution for your organization’s learning needs. The solution offers two learning course paths, **Virtual** and **Instructor-led**. 

**Virtual learning** is a learning experience enhanced utilizing online resources. Instructor-led training is when an instructor facilitates a training session for a 
group of workers or learners.  

In our learning module, Human Resource professionals, administrators, training managers, and managers can create and assign both learning course paths to workers.  

> [!Note] 
> To use **Virtual courses**, enable **Course enhancements** in **Feature management**.    

## Set up Virtual courses

To configure **Virtual courses**, enable the **Course enhancements** feature in **Feature management**.  
Go to **Courses > New** and set **Virtual** to **Yes**. After the feature is enabled, a **Course link** is required. 
The **Course status** will be set to **Open**. The **Allow employee to self-register** will be set to **Yes** and can be changed to **No**. 

After the **Virtual course enhancements** are enabled in **Feature management**:  
 - A due date must be defined for course assignment
 - A **Course link** is required 
 - **Employee self service** will show an employees overview in **Courses**. User can view **Overdue**, **Due soon**, and **Assigned** courses 
 - Workers can complete virtual courses and self-attest to those virtual courses 


## Set up Instructor-led courses

**Instructor-led** courses don't need to be configured before using.  

The following information is optional and can be specified for courses. If this information will be entered for courses, it should be set up before 
the course records are created: 
 - **Course type**
 - **Classroom groups**
 - **Course groups**
 - **Course locations**
 - **Classrooms**
 - **Instructors**
 - **Course types** 

You can use **Course types** to categorize courses according to the structure or content of the course. You can create **Course types** on the **Course types** page.  

The minimum and maximum number of participants that you can register for a course is defined on the **General** FastTab on the **Courses** page. 

### Course setup type 

**Setup types** determine the structure of the course and there are three **Setup types** for courses: 

|**Setup type**|**Description**|
|--------------|------------------|

|**Standard** | This course type doesn't have a daily agenda. This is the default setup type when you create a new course.|
|**Agenda**| Select this type to plan the details of each day of a course that takes place over multiple days.| 
| **Agenda + session**| <p>Select this type for the more complex courses. For example, you can divide the agenda for the course into tracks and sessions:</p><ul><li>
**Track** – Tracks are specific subject areas for a course.</li><li>**Sessions** – Sessions divide up tracks and help identify specific processes or techniques that are 
relevant to the track.</li></ul><p>| 

### Course tasks 
For each course, complete the following tasks: 
 - Register participants
 - Specify a registration deadline
 - Define the minimum and maximum number of participants 
 - Assign a course location and classroom 
 - Recommend hotels to course participants 
 - Create a course description, which you can be posted on **Employee self service** 

>[!NOTE]
> You can only delete a course if no one has registered for it. 
 

### Course statuses 

The following table lists course statuses and the actions to complete for a specific status: 
 
|Status|Actions| 
|------|--------|

 |**Created**| </p><ul><li>Enter and modify course information</li><li>Change the course status to **Open** so that workers can register for the course</li></ul><p>| 
|**Open**|</p><ul><li>Register participants for the course</li><li>Remove participants from the course</li><li>Confirm participants for the course</li><li>Change
the course status to **Closed** or **Canceled** for participants whose status is **Confirmed**</p><ul><li>|
|**Closed**|You can reopen the course.| 
|**Canceled**|You can reopen the course.| 

### Course participants 
Course participants are workers who participate in a training course or event. You can only register participants for open courses.  

### Workflow 

Employees who register for a course through the **Employee self service** page can have their registration routed through workflow for approval. You can assign a 
workflow to a course on the **General** FastTab on the **Courses** page. 

 

