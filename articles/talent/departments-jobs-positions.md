---
# required metadata

title: Organize your workforce using departments, jobs, and positions
description: Departments, jobs, and positions are organizational elements that are maintained within Human resources. This topic describes conceptual information about these elements. 
author: rschloma
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: HcmJob, HcmPosition, OMOperatingUnit
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail

# ms.tgt_pltfrm: 
ms.custom: 87933
ms.assetid: eb5dcacb-a5fe-451d-b30a-7ef14da65d81
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Talent July 2017 update

---

# Organize your workforce using departments, jobs, and positions

[!include[banner](includes/banner.md)]

[!include[retail name](includes/retail-name.md)]


Departments, jobs, and positions are organizational elements that are maintained within Human resources. This topic describes conceptual information about these elements. 

The following example is used to illustrate the concepts described in this topic.

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

 
 Departments
------------

A department is an operating unit that represents a category or functional area of an organization that is responsible for a specific area of the organization, such as sales or accounting. A department is used to report on functional areas and may have profit and loss responsibility. Also, a department might include a group of cost centers. Sales, accounting, and human resources are some examples of departments in an organization.

## Jobs and positions
A job is a collection of tasks and responsibilities that are required of a person who performs a job. A position is an individual instance of a job. Areas of responsibility, job tasks, job functions, skills, education information, and certificates that are required for a job are also required for positions that are associated with a job.
### Job tasks

You can create job tasks that describe the basic tasks that a worker in a position for that job must complete. The same job task can be added to multiple jobs, and positions for those jobs will inherit those job tasks. Examples of job tasks are listed in the following table.

<table>
<thead>
<tr class="header">
<th>Job</th>
<th>Job task</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Sales manager</td>
<td><ul>
<li><span class="input">Perf-review</span> – Review each salesperson’s job performance.</li>
<li><span class="input">Abs-review</span> – Approve or reject each salesperson’s absence requests or registrations.</li>
</ul></td>
</tr>
<tr class="even">
<td>Accountant</td>
<td><span class="input">FIN-Report</span> – Present weekly financial reports to chief financial officer.</td>
</tr>
</tbody>
</table>

### Job functions

Job functions are like job tasks. A job function describes one or more tasks, duties or responsibilities that are assigned to a job. Job functions can be assigned to jobs and used to set up and implement eligibility rules for compensation plans. Examples of job functions are listed in the following table.

| Job           | Job function                                                |
|---------------|-------------------------------------------------------------|
| Sales manager | Mng-people – Manage people who report to you.               |
| Accountant    | FIN-Review – Maintain financial data for a set of accounts. |

### Job types

Use job types to classify similar jobs into categories. Job types, just like job functions, can be assigned to jobs and used to set up and implement eligibility rules for compensation plans. Some examples of job types are included in the following list:
-   Full-time
-   Part-time
-   Salary
-   Hourly pay

### Areas of responsibility

Use areas of responsibility to indicate the work roles, processes, and products that a worker in a position for that job would be responsible for. An example of an area of responsibility for a job titled “Accountant” might be “Financial reporting for Product A”.

Positions
----------

Positions are an important element of the lower level of an organization hierarchy. A position is an individual instance of a job. For example, the position, “Sales manager (East),” is just one of the positions that is associated with the job, “Sales manager.” Positions exist in a department and are assigned to workers.
### Position creation and maintenance

-   You can view a history of position-related system changes in an easy-to-access list page.
-   You can create reason codes that your users can select when they create or modify positions.
-   You can create personnel action types and assign a number sequence to personnel actions.
-   You can set up workflow so that position additions and changes can require approval.

### Position duration

Every position has a length of time that the position is effective. This length of time is referred to as duration. For example, summer positions might have duration of May 1, 2015 until August 31, 2015.

### Worker assignments

When you assign a worker to a position, you fill that position. You can assign workers to multiple positions, but only one worker can be assigned to a position at the same time.

### Reporting relationships

Positions are important elements of the lower level of an organization hierarchy. In the Position form, you can specify the position that a position reports to. When you assign a worker to a position that reports to another position, you create a reporting relationship between the workers who are assigned to the two positions. For example, position “Accountant-A” reports to position “Accounting Supervisor”. Kim Akers is assigned to position “Accounting Supervisor” and Sanjay Patel is assigned to position “Accountant-A”. This means that Sanjay Patel reports to Kim Akers. 

If your organization uses a matrix hierarchy or another custom hierarchy, you can set up position hierarchy types and then add reporting relationships to positions for each hierarchy type that you set up. For example, Lori Penor is a general manager at Adventure Works and is assigned to the “General Manager” position. Lori manages the development of a product that is used to clean widgets. Lori requires an accountant to help her with the finances for developing the product. Therefore, she has recruited Sanjay Patel to be her accountant. Sanjay reports directly to Kim Akers, but also works with Lori Penor on his work related to the finances for developing the widget cleaner. 

For the previous example, you would complete the following tasks to set up the working relationship between Sanjay Patel and Lori Penor:
1.  Create a custom position hierarchy type called “Widget” to create a hierarchy that includes positions responsible for working on the widget cleaner product.
2.  Assign the General Manager position to be the position that the Accountant-A position reports to in the Widget hierarchy.

Use the position hierarchy to view the reporting structure of positions. If you have multiple position hierarchies, you can view the hierarchy for each hierarchy type in the position hierarchy. Also, you can search for a position by position ID or by the name of the worker who is assigned to the position. The position hierarchy is an organizational hierarchy.

## Date effective records
For some records, you can specify future changes to the record. The following information is date effective.

<table>
<thead>
<tr class="header">
<th>Records</th>
<th>Date effective information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Jobs</td>
<td><ul>
<li>Some detailed job information</li>
<li>Job classification information</li>
<li>Compensation information</li>
</ul></td>
</tr>
<tr class="even">
<td>Positions</td>
<td><ul>
<li>Some detailed position information</li>
<li>Worker assignments</li>
<li>Position durations</li>
<li>Position hierarchies</li>
</ul></td>
</tr>
</tbody>
</table>

You can modify the information mentioned in the previous table for a position or a job and specify a date when the modifications to the position or job should take effect. For example, a position can only be assigned to one worker, but Sanjay Patel, who is assigned to the position Accountant-A, will be leaving in two weeks. Joe Healy will replace Sanjay Patel when he leaves. Even though Sanjay is still assigned to his position, you can assign Joe Healy to the same position so that the assignment is effective only after Sanjay’s last day.





