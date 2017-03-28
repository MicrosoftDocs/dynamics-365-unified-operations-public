---
# required metadata

title: Time and attendance registration
description: Time registration workers can enter different types of time registrations, for example, clock in, clock out, register indirect activities, and absence registration. This article describes registrations, their calculation, approval, and the use of workflow to add structure and automated approval to the process of approving timesheets. 
author: YuyuScheller
manager: AnnBe
ms.date: 2016-02-24 15 - 27 - 06
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: HcmWorker, JmgCalcApprovePickDialog, JmgGroupApprove, JmgGroupCalc, JmgGroupSigningTable, JmgRegistration, JmgTimeCalcParmeters, WorkflowTableListPageRnr
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 31
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 53351
ms.assetid: 885b0cdf-53d7-4cb4-92fe-da1b9e32b39f
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yuyus
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Time and attendance registration

Time registration workers can enter different types of time registrations, for example, clock in, clock out, register indirect activities, and absence registration. This article describes registrations, their calculation, approval, and the use of workflow to add structure and automated approval to the process of approving timesheets. 

Registrations
-------------

In companies that use Time and attendance, workers must register the time that they spend at work, as well as their attendance. Some companies may only require workers to register clocking-in and clocking-out times. In other companies, workers may also be required to register time consumption on the actual activities they perform as well as the breaks they take. The intended users of Time and attendance are:
-   Workers, who are required to register time and attendance at regular intervals, for example daily, weekly or bi-weekly.
-   Supervisors, managers, and payroll officers who calculate, approve, and transfer worker registrations for further processing.

| **Note**                                                                                                                                                                                                                                                    |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| If you run Time and attendance together with Manufacturing execution, all registrations on projects, project activities, indirect activities, absence codes, and overtime and flex time will be recorded and are used to calculate payroll in both modules. |

## Time registrations workers
To be able to register time and absence, workers must be set up as time registration workers in the company they are employed in.

After setup, the workers can enter different types of registrations.

-   Clocking in- and out when arriving or leaving work.
-   Time and item consumption on production jobs.
-   Time used on a machine on the shop floor, if the machine has been defined as a resource.

| **Note**                                                                                                                                                                                                                      |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| A worker can be automatically assigned the time registrations that are made on a particular machine on the shop floor, if the worker chooses to work as an assistant to the machine when he or she starts the production job. |

-   Time registrations on projects and project activities.
-   Registering project fees and item consumption via the respective project fee journals and project item journals.
-   Planned absence.
-   Absence when arriving late to work or leaving earlier than planned.
-   Work breaks, either manually registered or automatically calculated by the system.
-   Indirect activities, which are non-productive activities a worker might engage in during a workday. Examples of these activities include meetings or cleaning their workspace.
-   Overtime, which can be registered either as extra hours, flextime, or overtime.

## Adding clockout registrations
If a worker forgets to clock-out at the end of their workday, the missing registration can be added by running a batch job. The system will compare the clock-in time and the clock-out time according to the associated profile of the worker, and automatically insert the missing clock-out registration to match the profile’s end time. Both the clock-in and clock-out registrations are vital for the subsequent calculation and approval of time registrations before they can be transferred to payroll.

## Calculating registrations
When a registration worker is assigned a calculation group that typically relates to a specific team, shift, or work group. The team manager or supervisor typically validates the registrations made by the workers, and is therefore also the responsible person to run the calculation for the respective calculation groups on a daily basis. As part of the calculation process the team manager or supervisor is able to:
-   Correct erroneous registrations. For example, change switch codes and adjust feedback on production jobs.
-   Add missing registrations. For example, create clock-out registrations and create absence transactions.
-   Delete incorrect registrations.

Because the registered time must match the worker’s time profile prior to calculating the registrations, you must override the work time profile for any worker who has an exception to his standard work time profile. In the case, where the worker profile is day shift, and the worker has agreed to work a night shift with no overtime pay, the team manager or supervisor must override the default worker profile in order to calculate the working time at the standard night rate and not as overtime. The calculation will also display an error if an absence registration is missing. It must be added before the calculation can be completed.

## Approving registrations
Just as you assign a calculation group to a time registration worker, you must assign an approval group as well. Typically the group will be specific to a team, shift, or work group. You must approve the time registrations that were calculated correctly – this means doing a calculation without errors – before pay items can be generated that afterward can be transferred to a payroll system. The payroll administrator will typically do the approval of registrations, and prior to the approval he is able to:
-   Override pay agreements for individual workers.
-   Add manual premiums.
-   Enter additional information about absence registrations.

| **Note**                                                                                                                                                                             |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| If overtime has been calculated for specific workers, the overtime can be allocated to specific jobs during the day. This is relevant if job cost is calculated based on worker pay. |

## Approving registrations using workflow
You can set up a workflow approval process that automatically approves registrations which comply with workflow rules, leaving only deviations to be handled manually. If workflow approval is activated, the team manager or supervisor submits the calculated registrations for approval. The workflow process will generate the appropriate approvals and tasks, and then assign them to the right users and roles as identified in the workflow. There are two workflow approvals for time and attendance.

| Workflow                                  | Purpose                                                                                                   | Registration type                                                                                                                                                                                                                                     |
|-------------------------------------------|-----------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Time and attendance days total            | The workflow validates registrations against, for example, the expected number of work hours for the day. |                                                                                                                                                                                                                                                       |
| Time and attendance journal registration. | The workflow validates each registration type for the date of the registration.                           | Time and attendance • Clock-in • Clock-out • Absence • Break • Switch code • Project • Project activity • Indirect activity Production jobs • Queue before • Setup • Process • Overlap • Transport • Queue after • Start assistance • Stop assistance |

 

## Transferring approved registrations
After approval of the registrations you can transfer them to a periodic payroll job. A transferred registration is posted to an activity or job that it relates to, for example, a production order or a project. Payroll transactions are generated for each worker based on the registrations.  

## Reversing transferred registrations
The task of reversing transactions – rolling them back – can be done until the time when the payroll period’s pay transfer is run. This means that payroll data has been transferred to an external file. When reversed, all registrations are withdrawn, and any transactions posted on production orders or projects are offset and neutralized.

| **Note**                                                 |
|----------------------------------------------------------|
| The external file can be imported into a payroll system. |

## Registrations in electronic timecards
Workers with job tasks that do not require immediate feedback, as is the case with production jobs, but who work on project activities, can benefit from using the electronic timecard. Electronic timecards offer the flexibility to enter registrations any time and in the best way for your business schedule – daily, weekly, or when a worker is in the office again after being away. To use electronic timecards or these workers, you must specify, Use timecard, in the worker details. Electronic timecards enable the worker to register:

-   Date
-   Registration type
-   Job reference, such as project, indirect activity, or production order
-   Job identification
-   Time consumption
-   Project fees
-   Project items


