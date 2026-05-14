---
title: Work planner and time profiles
description: Learn about the work planner to shift work and print plans, including calculating and approving registrations in Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 05/14/2026
ms.topic: how-to
audience: Application User
ms.search.region: Global
---

# Work planner and time profiles

The work planner is a graphic tool that you use to plan shift work and print the plan.

## About work planner and time profiles

In the work planner, you select a predefined work time profile and then allocate the profile to one or more workers. Examples of profiles include day shift and night shift profiles. Profiles contain various elements included in a work day, such as standard work time, break time, and overtime. You save work planner entries in the profile calendar.

The profile calendar contains profile entries that differ from the standard work time profiles that you apply to a worker or a group of workers. Here are several examples of profile changes:

- A group of workers switch to the evening shift for a predefined period.

- A worker works on a Sunday or a national or regional holiday. Therefore, a special profile or a Sunday profile might be used.

You can create entries directly in the profile calendar or in the work planner. In the profile calendar, you can make one entry at a time in a list or one day at a time. You can also create profile changes for one worker or a profile group for a time period in the **Compose profile calendar** form. The work planner offers a graphic overview of profile selections for one or more workers.

## Calculating registrations

When registrations are calculated, they're verified against a worker's work time profile. The registrations that are calculated include work time, pay time, pay overtime, and absence time. Calculation is typically performed by a team leader or a supervisor. You can set up calculation groups for groups of workers to help make sure that the person calculating registrations can view information about only the workers on their team.

Before calculating registrations, you can override the work time profile for a specific worker.

If the registered time doesn't correspond to a worker’s work time profile, the calculation procedure creates errors, for example, a missing absence registration. The errors can be corrected and the registrations recalculated.

## Approving registrations

When all registrations have been calculated without errors, the registrations are ready to be approved. Approval is done by a worker other than the one in charge of calculating registrations, for example, a payroll administrator. You can set up approval groups for relevant groups of workers.

Before approving registrations, you can override pay agreements for individual workers and add manual premiums.

If you calculate overtime for specific workers, you can allocate the overtime to specific jobs during the day. This allocation is relevant if job cost is calculated based on worker pay.

During the process of approving a registration, you might need to enter additional information about absence registrations. If more absence information is needed, the system points it out during the approval process.

## Approving registrations by using workflow

It's possible to set up a workflow approval process that automatically approves registrations that comply with the rules set up in the workflow. If workflow approval is activated, the user who calculates registrations, for example, a team leader or a supervisor, submits the calculated registrations for approval. Through the workflow process, the appropriate approvals and tasks are created and they're assigned to the users and roles as identified in the workflow.

The approval workflow automates the approval process and allows users who have approval rights to approve many worker registrations at a time. Only deviations that aren't accepted in the approval workflow must be handled manually.

You can create two types of workflow approval in time and attendance:

- **Time and attendance days total workflow** – The workflow validates registrations against, for example, the expected number of work hours for the day.

- **Time and attendance journal registration workflow** – The workflow validates each registration type for the date of the registration. The following journal registration types are available. Time and attendance automatically select the registration types, depending on the worker’s registration:

  - Regarding registration in time and attendance and manufacturing execution:

    - **Clock in**
    - **Clock out**
    - **Absence**
    - **Break**
    - **Switch code**
    - **Project**
    - **Project activity**
    - **Indirect activity**

  - Regarding registration on production jobs in manufacturing execution:

    - **Queue before**
    - **Setup**
    - **Process**
    - **Overlap**
    - **Transport**
    - **Queue after**
    - **Start assistance**
    - **Stop assistance**

## Transferring registrations

When registrations have been approved, they can be transferred to a periodic payroll job.

A transferred registration is posted to an activity or job that it relates to, for example, a production order or a project. Also, payroll transactions are generated for each worker based on the registrations.

## Reversing registrations

Registrations that have been transferred can be reversed (rolled back). The task of reversing registrations can be done until the time when the payroll period's pay transfer is run. This means that payroll data has been transferred to an external file. The external file can be imported into a payroll system.

When reversed, all registrations are withdrawn, and any transactions posted on production orders or projects are offset and neutralized.

## Modify registrations before or after calculation

You can modify registrations made by workers before or after you calculate the registrations.

After you calculate or approve registrations, you can view error descriptions on the **Error** tab in the **Calculate** form and the **Approve** form. For example, an error message might inform you that information about a worker’s absence time is missing.

## Update an absence registration

1. Select **Human resources** > **Common** > **Time and attendance** > **Calculate**. In the **Calculate** dialog box, enter the date and calculation group to calculate registrations for in the **Date** and **Calculation group** fields. Select **OK**.
1. On the **Calculate** page, select the worker in the upper pane. On the **Absence** tab, modify the absence registration that you entered during calculation. You can also press CTRL+N to create a new absence registration.
1. Press CTRL+S to save absence records. The absence records are displayed in the lower pane on the **Overview** tab.
1. Follow steps 1 through 3 for every worker for whom an absence registration is required.

> [!NOTE]
> When you calculate registrations for a group of workers, any missing absence records for the workers are created automatically. For those absence records, you only have to select the absence codes. Start times and end times are added automatically during calculation.

## Approve switch codes for a worker

1. Select **Human resources** > **Common** > **Time and attendance** > **Calculate**. In the **Calculate** dialog box, enter the date and calculation group in the **Date** and **Calculation group** fields to approve switch codes for. Select **OK**.
1. On **Calculate**, select the worker in the upper pane, and then select **Switch code**.
1. Select the **Approved** checkbox, and close the page.

## Add a missing clock-out registration

1. Select **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**. In the **Calculate** dialog box, in the **Date** and **Calculation group** fields, enter the date and calculation group to add clock-out registrations for. Select **OK**.
1. In the **Calculate** page, select the worker in the upper pane, and then select **Clock-in and out** > **Missing clock-out**.
1. In the **Clock out** section, select the date and time for the clock-out registration.
1. Select the **Create lines** checkbox, and then select **OK**.

## Clock out all workers in a calculation group

1. Select **Human resources** > **Common** > **Time and attendance** > **Calculate**. In the **Calculate** dialog box, enter the date and calculation group to calculate registrations for in the **Date** and **Calculation group** fields. Select **OK**.
1. In the **Calculate** page, select **Clock-in and out** > **Clock out workers**.
1. In the **Profile date** field, select the clock-out date, and then select **OK**.

> [!NOTE]
> All workers in the selected calculation group are clocked out according to their work time profile. You can also create a batch job that clocks out all workers in a calculation group.

## Correct errors and add registrations

1. Select **Human resources** > **Common** > **Time and attendance** > **Calculate**. In the **Calculate** dialog box, enter the date and calculation group to calculate registrations for in the **Date** and **Calculation group** fields. Select **OK**.
1. In the **Calculate** page, select the worker in the upper pane. In the lower pane, select the registration to modify, or press CTRL+N to add a new line.
1. Enter information for the registration line.
1. To recalculate the worker’s registrations, in the upper pane, on the **Overview** tab, select the **Calculated** checkbox.

> [!IMPORTANT]
> Don't create a new journal line for a clock-out registration if a worker didn't clock out. To create missing clock-out registrations, select **Clock-in and out**, and then select the appropriate option. Only these two options ensure that the clock-out registration is entered in the **Raw registrations** table. Raw registrations determine whether the worker is clocked in or clocked out.

## Calculate time and attendance for workers

You can calculate time and attendance registrations for workers in the following ways:

- Calculate registrations for all workers who are assigned to a calculation group.
- Calculate registrations for a specific worker.
- Calculate registrations by using a batch job.

Use the **Day view** and **Week view** filters as follows:

- **Day view** – View registrations for all workers for a selected weekday.
- **Week view** – View registrations for a selected worker for a selected week.

## Calculate registrations for all workers in a calculation group

You can calculate registrations for all workers in a calculation group by navigating to the **Calculate** option in the **Time and attendance** menu. You can select the week or date to calculate registrations for in the **Week** and/or **Date** fields. In the **Calculation group** field, select the calculation group to calculate registrations for, then select **Update** and **Calculate** in the **Calculate** page.

In the **Calculates jobs** page, verify that the calculation group is selected in the **Calculation group** field. If you use a workflow for approvals, select **Submit to workflow** in the **Calculates jobs** page.

> [!NOTE]
> If registrations contain errors because of missing information or other reasons, you must correct the registrations, and then calculate the registrations again. To view the worker registrations that contain errors, select **Display errors**. The **Error** tab displays information about the type of error.

## Calculate registrations for one worker at a time

You can calculate registrations for a specific worker. Typically, you calculate registrations for a worker after you correct registration errors for that worker.

1. Select **Human resources** > **Common** > **Time and attendance** > **Calculate**.
1. In the **Week** or **Date** field, select the week or date to calculate registrations for.
1. In the **Calculation group** field, select the calculation group to calculate registrations for, and then select **OK**.
1. In the **Calculate** page, select the worker in the upper pane and select **Select**.
1. Select the **Calculated** checkbox for the registration.
1. Select **Close**.

## Reverse calculated registrations

You can reverse the registrations that have been calculated for a worker. However, you can't reverse calculated registrations after payroll information for the period has been exported to the payroll system. Also, if registrations have been approved, you can reverse the calculated registration only on the **Approve** page.

1. Select **Human resources** > **Common** > **Time and attendance** > **Calculate**.
1. In the **Week** or **Date** field, select the week or date to calculate registrations for.
1. In the **Calculation group** field, select the calculation group to calculate registrations for, and then select **OK**.
1. In the **Calculate** page, select the worker in the upper pane and select **Select**.
1. Clear the **Calculated** checkbox for the registration.
1. Select **Close**.

> [!TIP]
> If you change the registrations and want to restore the original values, delete all lines, and then select **Restore lines**.

## Calculate registrations by using a batch job

To calculate registrations, go to the **Time and attendance** page and access the **Week** or **Date** fields to select the week or date to calculate registrations for.

Then, select the calculation group to calculate registrations for in the **Calculation group** field. On the **Calculate** page, select **Update**, and then **Calculate**. Start the batch job by following prompts in the **Batch** tab's **Calculates jobs** page.

> [!NOTE]
> If you use a workflow for approvals, select the **Submit to workflow** checkbox.

## Modify registrations before or after approval

You can change worker registrations during the approval process. Select **Human resources** > **Common** > **Time and attendance** > **Approve**.

Examples of changes include the following:

- Edit an absence registration.
- Apply changes to a pay agreement by overriding the standard pay agreement for the worker.
- Add premium lines, such as mileage, to worker registrations.
- Allocate overtime to specific jobs.

> [!NOTE]
> You can make additional changes during the calculation process. Modify registrations before or after calculation.

## Change an absence registration

Change absence registrations by entering changes on the **Approve** page. Select the worker, and then go to the **Absence** tab to begin making changes for the absence registration.

> [!NOTE]
> During approval, you can edit only the **Absence job** and **Pay units** fields.

## Override a pay agreement

You can override the pay agreement for a specific worker to generate the correct pay for the day.

1. On the **Approve** page, select the worker.
1. Select **Override**, and then select **Override pay agreement**.
1. Select **Retrieve pay agreement**.
1. Enter the changes to the pay agreement lines for the day.

## Add manual premium lines

Add manual premium lines by selecting the worker and going to the **Premium lines** option in the **Approve** page. After creating a new premium line by using **CTRL+N**, select the premium to add in the **Premiums** field. Enter the number and price of units to add in the **Price** field. Select the cost to assign to a specific job in the **Transaction ID** field.

## Allocate overtime

Allocate overtime to the relevant jobs performed during the work day.

1. In the **Approve** form, select the worker.
1. Select **Overtime allocation**.
1. In the **Percent** box, enter a percentage for each job.

> [!NOTE]
> Total allocation for a work day must always be 100 percent.

## About adding clock-out registrations

If workers forget to clock out at the end of their work day, you can create clock-out registrations for them by running a batch job. This helps make sure that calculations include all clock-out registrations. You must run the batch job before you calculate information about worker registrations.

## Add clock-out registrations

On the specified date, the batch job searches for clock-out registrations. When a missing registration is found, the following occurs:

- If a worker doesn't have a clock-in registration before the profile end time, and no registrations exist after the end time, the batch job adds a clock-out registration at the profile end time.

  > [!NOTE]
   > The profile end time is the end of the work day according to the worker’s work time profile. For example, if a day profile is set up with an expected clock-in time at 07:00 and an expected clock-out time at 15:00, then 15:00 is the profile end time.

- If a clock-in registration or a job registration is after the end time specified on the worker's profile, then the worker has worked overtime. In this case, the batch job doesn't add a clock-out registration.

> [!NOTE]
> You can also create clock-out registrations for a worker in the **Calculate** and the **Approve** pages.

## Add clock-out registrations for workers

A supervisor or manager can insert missing clock-out registrations for workers who forgot to make those registrations. To insert missing clock-out registrations, run a batch job for a group of workers or for one worker at a time.

> [!NOTE]
> You can also make clock-in registrations for workers, but it's more likely that a missing registration for a worker is a clock-out registration.

## Clock out an individual worker or group of workers

To clock out a single worker:

1. Select **Human resources** > **Common** > **Time and attendance** > **Calculate**.
1. Select the worker, and then select **Clock-in and out** > **Missing clock-out**.
1. In the **Clock out** section, enter the **Date** and **Time** for the clock-out registration.
1. To create a clock out registration record in the raw registrations table, select the **Create lines** checkbox.

To clock out a group of workers:

1. Select **Human resources** > **Common** > **Time and attendance** > **Approve**.
1. Select **Clock-in and out** > **Clock out workers**.

      - To clock out all the workers in the selected calculation group or approval group, enter the profile date for the clock-out registration and then select **OK**.
      - To clock out specific workers, select **Select** and then select the relevant workers.
      - To set up the clock-out registration as a batch job, select the **Batch** tab, and create the batch job.

> [!NOTE]
> You can also clock out workers by setting up a batch job. Select **Human resources** &gt; **Periodic** &gt; **Time and attendance** &gt; **Clock out workers**.

## Approve time and attendance registrations

After each work day, workers’ registrations must be calculated and approved. You can approve registrations after they have been calculated, and no errors occurred during calculation. You can approve registrations by using one of the following:

- A workflow
- A batch job
- Manually for an approval group
- Manually for one worker at a time

## Approve registrations by using a workflow

The approval workflow is an automatic approval process. All registrations are validated against the rules in the approval workflow. Only deviations that aren't accepted in the workflow must be approved manually.

The worker who is responsible for calculating registrations, for example, a team leader, initiates the approval process. The worker who is responsible for approving registrations, for example, a payroll administrator, receives a message regarding the need for manual approval only when some registrations couldn't be approved according to the approval workflow.

1. Select **Human resources** > **Common** > **Time and attendance** > **Approve**.
1. Select the approval date in the **Date** field.
1. Select your group in the **Approval group** field.
1. In the **Approve** page, select the worker in the upper pane, on the **Overview** tab.
1. Select the **Action** button. If the worker’s registrations are ready for approval, the **Approve** and **Reject** options are available.

      - To approve, select **Approve**.
      - To reject, select **Reject**, and add a note explaining why the registrations are rejected.

## Approve registrations by using a batch job

You can approve registrations by using a batch job. To do this procedure:

1. Select **Human resources** > **Common** > **Time and attendance** > **Approve**.
1. Select the approval date in the **Date** field.
1. Select your group in the **Approval group** field.
1. Select **Update** and **Approve**.
1. Start the batch job.

To approve registrations for all workers in an approval group:

1. Select **Human resources** > **Common** > **Time and attendance** > **Approve**.
1. Select the approval date in the **Date** field.
1. Select your group in the **Approval group** field.
1. Select **Update** and **Approve**.
1. Select **OK**.

> [!NOTE]
> If the approval process returns errors on some registrations, such as missing information, you must edit those registrations and approve them again.

> [!TIP]
> To see a list of worker registrations that contain errors in the registration lines, select **Display errors**. The **Error** tab provides information about the type of error.

## Approve registrations for one worker at a time

Typically, you approve registrations for an individual worker after you correct errors for that worker.

1. On the **Approve** page, select the worker in the upper pane.
1. Select the **Approved** checkbox for the worker.

## Reverse an approval

You can reverse approved registrations for a worker until payroll information for the period is exported to the payroll system. To reverse approved registrations for a worker, follow these steps:

1. On the **Approve** page, select the worker in the upper pane.
1. Clear the **Approved** checkbox.

> [!TIP]
> If you have made several corrections to the registrations, and, therefore, must restore the lines to their original value, delete all lines, and then select **Restore lines**.

You must transfer registrations to journals, such as production or project journals.

After you approve workers’ registrations and no errors occur, you can transfer the registrations. You can transfer registrations in one of the following ways:

- Transfer registrations by using a workflow.
- Transfer registrations by using a batch job.
- Transfer registrations manually for an approval group.
- Transfer registrations manually for one worker at a time.

## Transfer registrations by using a workflow

If an approval workflow is set up to approve registrations based on a set of predefined rules, all approved registrations are transferred to the appropriate journals. Only deviations that aren't accepted in the workflow are handled manually. This means that approval and transferal of those registrations is performed by the worker responsible for approving registrations, for example, a payroll administrator.

## Transfer registrations using a batch job

1. Select **Human resources** > **Common** > **Time and attendance** > **Approve**.
1. Select the approval date in the **Date** field.
1. Select your group in the **Approval group** field.
1. Select **Update** and then **Transfer**.
1. Start the batch job. For more information, see [Transfer registrations (class form)](https://technet.microsoft.com/library/aa548840\(v=ax.60\)).

## Transfer registrations for all workers in an approval group

1. Select **Human resources** > **Common** > **Time and attendance** > **Approve**.
1. Select the approval date in the **Date** field.
1. Select your group in the **Approval group** field.
1. Select **Update** and **Transfer**.
1. Select **OK**.

> [!NOTE]
> You can only transfer registrations that are calculated and approved without errors.

> [!TIP]
> To view a list of worker registrations that contain errors in the registration lines, select **Display errors**. The **Error** tab provides information about the type of error.

## Transfer registrations for one worker

When you find an error in a worker registration, you can transfer the registration after you correct the error.

1. On the **Approve** page, select the worker in the upper pane.
1. Select the **Transferred** checkbox for the worker.

## Reverse a transferred registration

You can reverse transferred registrations for a worker before payroll information for the period is exported to the payroll system. To reverse transferred registrations for a worker, complete the following steps:

1. On the **Approve** page, select the worker in the upper pane.
1. Clear the **Transferred** checkbox.

## See also

[Calculate, approve, and transfer registrations](hr-about-calculate-approve-transfer-registrations.md)

[Update time and attendance information](hr-update-time-and-attendance-information.md)

[Communicate with and deploy assignments to workers](hr-communicate-and-deploy-assignments.md)
