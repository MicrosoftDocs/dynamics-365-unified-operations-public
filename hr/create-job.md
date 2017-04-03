---
# required metadata

title: Setting up the components of a job
description: This topic describes the conceptual elements that a job can include and provides examples of how you can use those elements in your organization. 
author: rschloma
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: HcmJob, HcmJobFunction, HcmJobTask, HcmTitle
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 31
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 269054
ms.assetid: 889a8fab-0eef-45c2-91fc-ff2f4d44d54f
ms.search.region: Global
# ms.search.industry: 
ms.author: shielas
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Setting up the components of a job

This topic describes the conceptual elements that a job can include and provides examples of how you can use those elements in your organization. 

Before you can create jobs, you must set up some reference information. You can create a job that has only a name. However, by including additional information, such as a job title, you provide default values for the positions that are assigned to the job. Additionally, some of the information that you enter can be used to filter compensation plans to specific jobs. If you want to set up eligibility that you can use to filter compensation plans to a specific job, you should set up job functions and job types before you set up jobs. By having these default values available, you will save time when you add positions to the job. 

Some job details, such as the job title, type, and function, are date-effective. If you create a job today but don't add these details until later, and you then look at the job as of the creation date, these details won't appear. Therefore, you should create some of this reference information before you require it. That way, you can add the information to new jobs when you create them.

## Job titles
Before you create jobs, you must set up titles for those jobs. Positions inherit job titles from the jobs that the positions are associated with. 

Maintain job titles using the **Titles** page, which you can open by using the Search function. On the **Titles **page, enter the titles that you plan to use for your jobs.

## Job types
You use job types to group similar jobs into categories. Job types aren't required. However, if you plan to use job types when you set up eligibility rules for compensation management, you should set up job types before you set up jobs. Some examples of job types are full-time and part-time, or salary and hourly pay. You maintain job types by using the **Job types** page. On the **Job types** page, enter a name and a brief description for the job type. In the **Exempt status** field, select one of the following options to indicate the Fair Labor Standards Act (FLSA) exempt status of jobs that have this job type:

-   **Exempt** – Jobs are exempt from overtime under the FLSA.
-   **Non-exempt** – Jobs aren't exempt from overtime under the FLSA.
-   **Does not apply** – FLSA coverage isn't applicable.

## Job functions
Job junctions describe high-level functional categories and relate high-level duties. Job functions aren't required. You can use job functions, together with job types, to filter compensation plans to specific jobs. You associate job functions and job types with compensation plans by setting up eligibility rules on the **Eligibility rules** page. You can then attach a set of levels to a compensation plan that apply to the specific combination of a job type and job function that you've defined through an eligibility rule. (These features apply to both fixed compensation plans and variable compensation plans.) However, if you plan to use job functions when you set up eligibility rules for compensation management, you should set up job functions before you set up jobs. The following table shows some examples of job functions.

| Job           | Job function      |
|---------------|-------------------|
| Sales manager | Mid-level Manager |
| Accountant    | Professionals     |

You maintain job functions by using the **Job functions** page. On the **Job functions** page, enter an identification code and a brief description for the job function.

## Job tasks
Job tasks describe the basic tasks that a worker who is in a position for a job must complete. The same job task can be added to multiple jobs, and to positions for the jobs that use those job tasks. The following table shows some examples of job tasks.

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
<li><strong>Perf-review</strong> – Review each salesperson's job performance.</li>
<li><strong>Abs-review</strong> – Approve or reject each salesperson's absence requests or registrations.</li>
</ul></td>
</tr>
<tr class="even">
<td>Accountant</td>
<td><strong>FIN-Report</strong> – Present weekly financial reports to the chief financial officer.</td>
</tr>
</tbody>
</table>

You maintain job tasks by using the **Job tasks** page. On the **Job tasks** page, enter a name and description for the job task. In the **Note** field, you can optionally enter additional information. The notes can be updated for a specific job without changing the notes that you entered here.

## Areas of responsibility
You use areas of responsibility to indicate the work roles, processes, and products that a worker who is in a position for a job is responsible for. For example, for a job that is named "Accountant," one area of responsibility might be "Financial reporting for product A." You maintain areas of responsibility by using the **Areas of responsibility** page, which you can find by using the Search function. On the **Areas of responsibility** page, enter a name and description for the responsibility. In the **Note** field, you can optionally enter additional information. The notes can be updated for a specific job without changing the notes that you entered here.

