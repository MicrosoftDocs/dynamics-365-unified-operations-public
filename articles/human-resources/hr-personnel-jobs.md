---
# required metadata

title: Set up the components of a job
description: This article describes the conceptual elements that a job can include and provides examples of how you can use those elements in your organization. 
author: twheeloc
ms.date: 05/08/2024
ms.topic: article
# optional metadata

ms.search.form: HcmJob, HcmJobFunction, HcmJobTask, HcmTitle, HcmPersonnelManagementWorkspace, HCMJobFamily
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.author: twheeloc

# ms.tgt_pltfrm: 
ms.assetid: 889a8fab-0eef-45c2-91fc-ff2f4d44d54f
ms.search.region: Global
# ms.search.industry: 
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Set up the components of a job


[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the conceptual elements that a job can include and provides examples of how you can use those elements in your organization. 

Before you can create jobs, you must set up some reference information. You can create a job that has only a name. However, by including additional information, such as a job title, you provide default values for the positions that are assigned to the job. Additionally, some of the information that you enter can be used to filter compensation plans to specific jobs. If you want to set up eligibility that you can use to filter compensation plans to a specific job, you should set up job functions and job types before you set up jobs. By having these default values available, you will save time when you add positions to the job. 

Some job details, such as the job title, type, and function, are date-effective. If you create a job today but don't add these details until later, and you then look at the job as of the creation date, these details won't appear. Therefore, you should create some of this reference information before you require it. That way, you can add the information to new jobs when you create them.

## Job titles
Before you create jobs, you must set up titles for those jobs. Positions inherit job titles from the jobs that the positions are associated with. 

Maintain job titles using the **Titles** page, which you can open by using the Search function. On the **Titles** page, enter the titles that you plan to use for your jobs.

## Job types
You use job types to group similar jobs into categories. Job types aren't required. However, if you plan to use job types when you set up eligibility rules for compensation management, you should set up job types before you set up jobs. Some examples of job types are full-time and part-time, or salary and hourly pay. You maintain job types by using the **Job types** page. On the **Job types** page, enter a name and a brief description for the job type. In the **Exempt status** field, select one of the following options to indicate the Fair Labor Standards Act (FLSA) exempt status of jobs that have this job type:

-   **Exempt** – Jobs are exempt from overtime under the FLSA.
-   **Non-exempt** – Jobs aren't exempt from overtime under the FLSA.
-   **Does not apply** – FLSA coverage isn't applicable.

## Job family
A job family is a group of jobs that involve similar work, and that require similar training, skills, knowledge, and expertise. A job family can be linked to a job on the **Job classification** FastTab of the **Jobs** page and on the **General** FastTab of the **All positions** page. Job families can be broad or specific, depending on your business and reporting requirements. Some examples of broad job families are **Skilled labor** and **Unskilled labor**. Some examples of specific job families are **Accounting**, **Manufacturing**, and **Sales**.

Maintain job families by using the **Job family** page, which you can open by using the search function. On the **Job family** page, enter a unique name for the family, and enter a detailed description that you plan to use for your jobs.

## Job functions
Job junctions describe high-level functional categories and relate high-level duties. Job functions aren't required. You can use job functions, together with job types, to filter compensation plans to specific jobs. You associate job functions and job types with compensation plans by setting up eligibility rules on the **Eligibility rules** page. You can then attach a set of levels to a compensation plan that apply to the specific combination of a job type and job function that you've defined through an eligibility rule. (These features apply to both fixed compensation plans and variable compensation plans.) However, if you plan to use job functions when you set up eligibility rules for compensation management, you should set up job functions before you set up jobs. The following table shows some examples of job functions.

| Job           | Job function         |
|---------------|----------------------|
| Sales manager | Mid-level Manager    |
| Accountant    | Professionals        |

You maintain job functions by using the **Job functions** page. On the **Job functions** page, enter an identification code and a brief description for the job function.

## Compensation
To assign a fixed compensation plan to an employee who has a position in a job, you must set compensation levels on the job. The **Compensation level** is used when minimum, midpoint, and maximum amounts are set in a compensation structure (compensation grid). When a fixed compensation plan is created, the compensation structure is selected. The compensation structure also includes the compensation level. When you're selecting a fixed compensation plan for an employee, the compensation levels that are available for selection depend on the job that the employee's position is associated with. For more information about how to set up compensation, see [Compensation plans](hr-compensation-overview.md).

## Job skills
Job skills describe the skills that are required to perform a job. A skill level must be associated with every job skill. The skill levels are user-defined. They indicate the level of knowledge or proficiency that is required for the skill. For example, companies might set up numeric levels, such as 1 through 5, where **1** indicates a beginner and **5** indicates an expert. Alternatively, companies might set up levels that are labeled **Beginner**, **Intermediate**, or **Expert**. After the skill level is set, the importance of the skill can also be set. For example, if an accountant is required to have a strong knowledge of Microsoft Excel, a skill that is named **Excel knowledge** can be created. The skill level can then be set to **Intermediate**, and the importance can be set to **Most**.

The skills that are on a job can be used in skill mapping. Skill mapping can compare the skill set that is required for a job and the skills that are associated with a worker. It can then determine a percentage match, based on overlapping skills. To learn more about skill mapping, see [Configure skills](hr-develop-skills.md). 

## Job tasks
Job tasks describe the basic tasks that a worker who is in a position for a job must complete. The same job task can be added to multiple jobs, and to positions for the jobs that use those job tasks. The following table shows some examples of job tasks.

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
<li><strong>Perf-review</strong> – Review each salesperson&#39;s job performance.</li>
<li><strong>Abs-review</strong> – Approve or reject each salesperson&#39;s absence requests or registrations.</li>
</ul></td>
</tr>
<tr class="even">
<td>Accountant</td>
<td><strong>FIN-Report</strong> – Present weekly financial reports to the chief financial officer.</td>
</tr>
</tbody>
</table>

You maintain job tasks by using the **Job tasks** page. On the **Job tasks** page, enter a name and description for the job task. In the **Note** field, you can optionally enter additional information. The notes can be updated for a specific job without changing the notes that you entered here.

## Areas of responsibility
You use areas of responsibility to indicate the work roles, processes, and products that a worker who is in a position for a job is responsible for. For example, for a job that is named "Accountant," one area of responsibility might be "Financial reporting for product A." You maintain areas of responsibility by using the **Areas of responsibility** page, which you can find by using the Search function. On the **Areas of responsibility** page, enter a name and description for the responsibility. In the **Note** field, you can optionally enter additional information. The notes can be updated for a specific job without changing the notes that you entered here.

## Steps for creating a job
Refer to the [Define new jobs](./hr-personnel-define-jobs.md) article for the step-by-step procedure for creating a new job. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
