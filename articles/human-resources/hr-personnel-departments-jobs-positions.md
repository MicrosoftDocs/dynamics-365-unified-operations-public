---
# required metadata

title: Organize your workforce by using departments, jobs, and positions
description: This article describes conceptual information about departments, jobs, and positions, which are organizational elements that are maintained within Human resources. 
author: twheeloc
ms.date: 08/13/2026
ms.topic: how-to
# optional metadata

ms.search.form: HcmJob, HcmPosition, OMOperatingUnit, HcmPersonnelManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: eb5dcacb-a5fe-451d-b30a-7ef14da65d81
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Organize your workforce by using departments, jobs, and positions

[!INCLUDE [banner](../includes/banner.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Human resources maintains departments, jobs, and positions as organizational elements. This article describes conceptual information about these elements.

The following example is used to illustrate the concepts described in this article.

|**Department**|**Position**|**Job**|
|---|---|---|
|**Sales**|Sales manager (East)|Sales manager|
|**Sales**|Sales manager (West)|Sales manager|
|**Sales**|Sales manager (Central)|Sales manager|
|**Accounting**|Accounting supervisor|Accounting manager|
|**Accounting**|Accounting-A|Accountant|
|**Human resources**|HR manager (East)|HR manager|
|**Human resources**|HR manager (West)|HR manager|
|**Human resources**|HR manager (Central)|HR manager|

## Departments

A department is an operating unit that represents a category or functional area of an organization. Each department is responsible for a specific area of the organization, such as sales or accounting. Use departments to report on functional areas. Departments might have profit and loss responsibility. A department might include a group of cost centers. Sales, accounting, and human resources are some examples of departments in an organization.

## Jobs and positions

A job is a collection of tasks and responsibilities that a person who performs the job must complete. A position is an individual instance of a job. Positions that are associated with a job require the same areas of responsibility, job tasks, job functions, skills, education information, and certificates that are required for the job.

### Job tasks

Create job tasks that describe the basic tasks a worker in a position for that job must complete. Add the same job task to multiple jobs, and positions for those jobs inherit those job tasks. The following table lists examples of job tasks.

| Job           | Job task                                                |
|---------------|-------------------------------------------------------------|
| Sales manager | Perf-review – Review each salesperson’s job performance.    |
| Accountant    | Abs-review – Approve or reject each salesperson’s absence requests or registrations. |

### Job functions

Job functions are like job tasks. A job function describes one or more tasks, duties, or responsibilities that are assigned to a job. Assign job functions to jobs and use them to set up and implement eligibility rules for compensation plans. The following table lists examples of job functions.

| Job           | Job function                                                |
|---------------|-------------------------------------------------------------|
| Sales manager | Mng-people – Manage people who report to you.               |
| Accountant    | FIN-Review – Maintain financial data for a set of accounts. |

### Job types

Use job types to classify similar jobs into categories. Assign job types, just like job functions, to jobs and use them to set up and implement eligibility rules for compensation plans. The following list includes some examples of job types:

- Full-time
- Part-time
- Salary
- Hourly pay

### Areas of responsibility

Use areas of responsibility to show the work roles, processes, and products that a worker in a position for that job is responsible for. For example, an area of responsibility for a job titled "Accountant" might be "Financial reporting for Product A."

## Positions

Positions are an important element of the lower level of an organization hierarchy. A position is an individual instance of a job. For example, the position "Sales manager (East)" is one of the positions that's associated with the job "Sales manager." Positions exist in a department and are assigned to workers.

### Position creation and maintenance

- You can view a history of position-related system changes in an easy-to-access list page.
- You can create reason codes that your users can select when they create or modify positions.
- You can create personnel action types and assign a number sequence to personnel actions.
- You can set up workflow so that position additions and changes require approval.

### Position duration

Every position has a length of time that the position is effective. This length of time is referred to as duration. For example, summer positions might have a duration of May 1, 2025, until August 31, 2025.

### Worker assignments

When you assign a worker to a position, you fill that position. You can assign workers to multiple positions, but only one worker can be assigned to a position at the same time.

### Reporting relationships

Positions are important elements of the lower level of an organization hierarchy. On the **Position** page, you can specify the position that a position reports to. When you assign a worker to a position that reports to another position, you create a reporting relationship between the workers who are assigned to the two positions. For example, position “Accountant-A” reports to position “Accounting Supervisor”. Ana Bowman is assigned to position “Accounting Supervisor” and Felix Henderson is assigned to position “Accountant-A”. This means that Felix Henderson reports to Ana Bowman.

If your organization uses a matrix hierarchy or another custom hierarchy, you can set up position hierarchy types and then add reporting relationships to positions for each hierarchy type that you set up. For example, Olivia Wilson is a general manager at Adventure Works and is assigned to the “General Manager” position. Olivia manages the development of a product that is used to clean widgets. Olivia requires an accountant to help with the finances for developing the product. Therefore, Olivia has recruited Felix Henderson to be the accountant. Felix reports directly to Ana Bowman, but also works with Olivia Wilson on work related to the finances for developing the widget cleaner.

For the previous example, you would complete the following tasks to set up the working relationship between Felix Henderson and Ana Bowman:

1. Create a custom position hierarchy type called “Widget” to create a hierarchy that includes positions responsible for working on the widget cleaner product.
1. Assign the General Manager position to be the position that the Accountant-A position reports to in the Widget hierarchy.

Use the **Position hierarchy** page to view the reporting structure of positions. If you have multiple position hierarchies, you can view the hierarchy for each hierarchy type in the **Position hierarchy**. Also, you can search for a position by position ID or by the name of the worker who is assigned to the position. The **Position hierarchy** is an organizational hierarchy.

## Date-effective records

For some records, you can specify future changes to the record. The following information is date-effective.

| Records | Date-effective information |
|---|---|
| Jobs | <ul><li>Some detailed job information</li><li>Job classification information</li><li>Compensation information</li></ul> |
| Positions | <ul><li>Some detailed position information</li><li>Worker assignments</li><li>Position durations</li><li>Position hierarchies</li></ul> |

[!INCLUDE[footer-include](../includes/footer-banner.md)]
