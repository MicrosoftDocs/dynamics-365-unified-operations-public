---
title: Work planner and time profiles
description: Learn about the work planner to shift work and print plans, including calculating and approving registrations in Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 01/24/2024
ms.topic: article
audience: Application User
ms.search.region: Global
---

# Work planner and time profiles

The work planner is a graphic tool that enables you to plan shift work and print the plan.

## About work planner and time profiles

In the work planner, you select a predefined work time profile and then allocate the profile to one or more workers. Examples are day shift and night shift profiles. Profiles contain various elements included in a work day, such as standard work time, break time, and overtime. Work planner entries are saved in the profile calendar.

The profile calendar contains profile entries that differ from the standard work time profiles that are applied to a worker or a group of workers. Here are several examples of profile changes:

  - A group of workers switch to the evening shift for a predefined period.

  - A worker works on a Sunday or a national/regional holiday. Therefore, a special profile or a Sunday profile may be used.

It's possible to create entries directly in the profile calendar, or in the work planner. In the profile calendar, you can make one entry at a time in a list or for one day at a time. You can also create profile changes for one worker or a profile group for a time period in the **Compose profile calendar** form. The work planner offers a graphic overview of profile selections for one or more workers.

## Calculating registrations

When registrations are calculated, they're verified against a worker's work time profile. The registrations that are calculated include work time, pay time, pay overtime, and absence time. Calculation is typically performed by a team leader or a supervisor. You can set up calculation groups for groups of workers to help make sure that the person calculating registrations can view information about only the workers on his or her team.

Before calculating registrations, you can override the work time profile for a specific worker.

If the registered time doesn't correspond to a worker’s work time profile, the calculation procedure will create errors, for example, a missing absence registration. The errors can be corrected and the registrations recalculated.

## Approving registrations

When all registrations have been calculated without errors, the registrations are ready to be approved. Approval is usually done by a worker other than the one in charge of calculating registrations, for example, a payroll administrator. You can set up approval groups for relevant groups of workers.

Before approving registrations, you can override pay agreements for individual workers and add manual premiums.

If overtime has been calculated for specific workers, the overtime can be allocated to specific jobs during the day. This is relevant if job cost is calculated based on worker pay.

During the process of approving a registration, you may have to enter additional information about absence registrations. If more absence information is needed, this will be pointed out during the approval process.

## Approving registrations using workflow

It's possible to set up a workflow approval process that automatically approves registrations that comply with the rules set up in the workflow. If workflow approval is activated, the user who calculates registrations, for example, a team leader or a supervisor, submits the calculated registrations for approval. Through the workflow process, the appropriate approvals and tasks are created and they're assigned to the users and roles as identified in the workflow.

The approval workflow automates the approval process and allows users who have approval rights to approve many worker registrations at a time. Only deviations that aren't accepted in the approval workflow must be handled manually.

Two types of workflow approval can be created in time and attendance:

  - **Time and attendance days total workflow** – The workflow validates registrations against, for example, the expected number of work hours for the day.

  - **Time and attendance journal registration workflow** – The workflow validates each registration type for the date of the registration. The following journal registration types are available. The registration types are automatically selected in time and attendance, depending on the worker’s registration:
    
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

After you calculate or approve registrations, you can view error descriptions on the **Error** tab in the **Calculate** form and the **Approve** form. For example, an error message may inform you that information about a worker’s absence time is missing.

## Update an absence registration

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**. In the **Calculate** dialog box, in the **Date** and **Calculation group** fields, enter the date and calculation group to calculate registrations for. Click **OK**.
2.  On the **Calculate** page, select the worker in the upper pane, and then, on the **Absence** tab, modify the absence registration that was entered during calculation. You can also press CTRL+N to create a new absence registration.
3.  Press CTRL+S to save absence records. The absence records are displayed in the lower pane on the **Overview** tab.
4.  Follow steps 1 through 3 for every worker for whom an absence registration is required.

> [!NOTE]
> When you calculate registrations for a group of workers, any missing absence records for the workers are created automatically. For those absence records, you only have to select the absence codes. Start times and end times are added automatically during calculation.

## Approve switch codes for a worker

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**. In the **Calculate** dialog box, in the **Date** and **Calculation group** fields, enter the date and calculation group to approve switch codes for. Click **OK**.
2.  On the **Calculate** page, select the worker in the upper pane, and then click **Switch code**.
3.  Select the **Approved** check box, and close the page.

## Add a missing clock-out registration

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**. In the **Calculate** dialog box, in the **Date** and **Calculation group** fields, enter the date and calculation group to add clock-out registrations for. Click **OK**.
2.  In the **Calculate** page, select the worker in the upper pane, and then click **Clock-in and out** \> **Missing clock-out**.
3.  In the **Clock out** section, select the date and time for the clock-out registration.
4.  Select the **Create lines** checkbox, and then click **OK**.

## Clock out all workers in a calculation group

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**. In the **Calculate** dialog box, in the **Date** and **Calculation group** fields, enter the date and calculation group to calculate registrations for. Click **OK**.
2.  In the **Calculate** page, click **Clock-in and out** \> **Clock out workers**.
3.  In the **Profile date** field, select the clock-out date, and then click **OK**.

> [!NOTE]
> All workers in the selected calculation group are clocked out according to their work time profile. Also, you can create a batch job that clocks out all workers in a calculation group. 

## Correct errors and add registrations

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**. In the **Calculate** dialog box, in the **Date** and **Calculation group** fields, enter the date and calculation group to calculate registrations for. Click **OK**.
2.  In the **Calculate** page, select the worker in the upper pane. In lower pane, click the registration to modify, or press CTRL+N to add a new line.
3.  Enter information for the registration line.
4.  To recalculate the worker’s registrations, in the upper pane, on the **Overview** tab, select the **Calculated** checkbox.

> [!IMPORTANT]
> Don't create a new journal line for a clock-out registration if a worker didn't clock out. To create missing clock-out registrations, click **Clock-in and out**, and then select the appropriate option. Only these two options make sure that the clock-out registration is entered in the **Raw registrations** table. Raw registrations determine whether the worker is clocked in or clocked out.

## Calculate time and attendance for workers 

You can calculate time and attendance registrations for workers in the following ways:

  - Calculate registrations for all workers who are assigned to a calculation group.
  - Calculate registrations for a specific worker.
  - Calculate registrations by using a batch job.

You can use the **Day view** and **Week view** filters as follows:

  - **Day view** – View registrations for all workers for a selected weekday.
  - **Week view** – View registrations for a selected worker for a selected week.

## Calculate registrations for all workers in a calculation group

You can calculate registrations for all workers in a calculation group by navigating to the **Calculate** option in the **Time and attendance** menu. You can select the week or date to calculate registrations for in the **Week** and/or **Date** fields. In the **Calculation group** field, select the calculation group to calculate registrations for, then select **Update** and **Calculate** in the **Calculate** page.

In the **Calculates jobs** page, verify that the calculation group is selected in the **Calculation group** field. If you use a workflow for approvals, select **Submit to workflow** in the **Calculates jobs** page.

> [!NOTE]
> If registrations contain errors because of missing information or for other reasons, you must correct the registrations, and then calculate the registrations again. To view the worker registrations that contain errors, click **Display errors**. The **Error** tab displays information about the type of error.

## Calculate registrations for one worker at a time

You can calculate registrations for a specific worker. Typically, you calculate registrations for a worker after you have corrected registration errors for that worker.

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**.
2.  In the **Week** or **Date** field, select the week or date to calculate registrations for.
3.  In the **Calculation group** field, select the calculation group to calculate registrations for, and then click **OK**.
4.  In the **Calculate** page, select the worker in the upper pane and click **Select**.
5.  Select the **Calculated** checkbox for the registration.
6.  Click **Close**.

## Reverse calculated registrations

You can reverse the registrations that have been calculated for a worker. However, you can't reverse calculated registrations after payroll information for the period has been exported to the payroll system. Also, if registrations have been approved, you can reverse the calculated registration only on the **Approve** page.

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**.
2.  In the **Week** or **Date** field, select the week or date to calculate registrations for.
3.  In the **Calculation group** field, select the calculation group to calculate registrations for, and then click **OK**.
4.  In the **Calculate** page, select the worker in the upper pane and click **Select**.
5.  Clear the **Calculated** checkbox for the registration.
6.  Click **Close**.

> [!TIP]
> If you have changed the registrations, and you want to restore the original values, delete all lines, and then click **Restore lines**.

## Calculate registrations by using a batch job

To calculate registrations, navigate to the **Time and attendance** page and access the **Week** or **Date** fields to select the week or date to calculate registrations for.

Then, select the calculation group to calculate registrations for in the **Calculation group** field. On the **Calculate** page, select **Update**, and then **Calculate**. Start the batch job by following prompts in the **Batch** tab's **Calculates jobs** page.

> [!NOTE]
> If you use a workflow for approvals, select the **Submit to workflow** checkbox.

## Modify registrations before or after approval 

You can change worker registrations during the approval process. Click **Human resources** \> **Common** \> **Time and attendance** \> **Approve**.

Examples of changes include the following:

  - Edit an absence registration.
  - Apply changes to a pay agreement by overriding the standard pay agreement for the worker.
  - Add premium lines, such as mileage, to worker registrations.
  - Allocate overtime to specific jobs.

> [!NOTE]
> You can make additional changes during the calculation process. Modify registrations before or after calculation.

## Change an absence registration

Change absence registrations by entering changes on the **Approve** page. Select the worker, then navigate to the **Absence** tab to begin making changes for the absence registration.

> [!NOTE]
> Only the **Absence job** and **Pay units** fields can be edited during approval.

## Override a pay agreement

You can override the pay agreement for a specific worker to generate the correct pay for the day.

1.  In the **Approve** page, select the worker.
2.  Click **Override**, and then select **Override pay agreement**.
3.  Click **Retrieve pay agreement**.
4.  Enter the changes to the pay agreement lines for the day.

## Add manual premium lines

You can add manual premium lines by selecting the worker and navigating to the **Premium lines** option in the **Approve** page. After creating a new premium line with **CTRL+N**, you can select the premium to add in the **Premiums** field. Additionally, you can enter the number and price of units to add in the **Price** field. Lastly, you can select the cost to be assigned to a specific job in the **Transaction ID** field.

## Allocate overtime

Overtime can be allocated to the relevant jobs performed during the work day.

1.  In the **Approve** form, select the worker.
2.  Click **Overtime allocation**.
3.  In the **Percent** box, enter a percentage for each job.

> [!NOTE]
> Total allocation for a work day must always be 100 percent.

## About adding clock-out registrations 

If workers forget to clock out at the end of their work day, you can create clock-out registrations for them by running a batch job. This helps make sure that calculations include all clock-out registrations. You must run the batch job before you calculate information about worker registrations.

## Adding clock-out registrations

On the specified date, the batch job searches for clock-out registrations. When a missing registration is found, the following occurs:

  - If a worker doesn't have a clock-in registration before the profile end time, and no registrations exist after the end time, the batch job adds a clock-out registration at the profile end time.

  > [!NOTE]
   > The profile end time is the end of the work day according to the worker’s work time profile. For example, if a day profile is set up with an expected clock-in time at 07:00 and an expected clock-out time at 15:00, then 15:00 is the profile end time.

  - If a clock-in registration or a job registration is after the end time specified on the workers profile, then the worker has worked overtime. In this case, the batch job doesn't add a clock-out registration.

> [!NOTE]
> You can also create clock-out registrations for a worker in the **Calculate** and the **Approve** pages.

## Add clock-out registrations for workers 

A supervisor or manager can insert missing clock-out registrations for workers who forgot to make those registrations. Missing clock-out registrations can be inserted by running a batch job for a group of workers, or for one worker at a time.

> [!NOTE]
> It is also possible to make clock-in registrations for workers, but it is more likely that a missing registration for a worker is a clock-out registration.

## Clock out an individual worker or group of workers

To clock out a single worker:

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**.
2.  Select the worker, and then click **Clock-in and out** \> **Missing clock-out**.
3.  In the **Clock out** section, insert the **Date** and **Time** for the clock-out registration.
4.  To create a clock out registration record in the raw registrations table, select the **Create lines** checkbox.

To clock out a group of workers:

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Approve**.
2.  Click **Clock-in and out** \> **Clock out workers**.
    
      - If you want to clock out all the workers in the selected calculation group or approval group, enter the profile date for the clock-out registration and then click **OK**.    
      - If you want to clock out specific workers, click **Select** and then select the relevant workers.    
      - If you want to set up the clock-out registration as a batch job, select the **Batch** tab, and create the batch job.

> [!NOTE]
> You can also clock out workers by setting up a batch job. Click **Human resources** &gt; **Periodic** &gt; **Time and attendance** &gt; **Clock out workers**.

## Approve time and attendance registrations 

After each work day, workers’ registrations must be calculated and approved. You can approve registrations after they have been calculated, and no errors occurred during calculation. You can approve registrations by using one of the following:

  - A workflow
  - A batch job
  - Manually for an approval group
  - Manually for one worker at a time
## Approve registrations using a workflow

The approval workflow is an automatic approval process. All registrations are validated against the rules in the approval workflow. Only deviations that aren't accepted in the workflow must be approved manually.

The worker who is responsible for calculating registrations, for example, a team leader, initiates the approval process. The worker who is responsible for approving registrations, for example, a payroll administrator, receives a message regarding the need for manual approval only when some registrations couldn't be approved according to the approval workflow.

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Approve**.
2.  Select the approval date in the **Date** field.
3.  Select your group in the **Approval group** field.
4.  In the **Approve** page, select the worker in the upper pane, on the **Overview** tab.
5.  Click the **Action** button. If the worker’s registrations are ready for approval, the **Approve** and **Reject** options are available.
    
      - To approve, click **Approve**.    
      - To reject, click **Reject**, and insert a note explaining why the registrations are rejected.

## Approve registrations using a batch job

You can approve registrations using a batch job. To do this:

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Approve**.
2.  Select the approval date in the **Date** field.
3.  Select your group in the **Approval group** field.
4.  Click **Update** and **Approve**.
5.  Start the batch job.

To approve registrations for all workers in an approval group:

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Approve**.
2.  Select the approval date in the **Date** field.
3.  Select your group in the **Approval group** field.
4.  Click **Update** and **Approve**.
5.  Click **OK**.

> [!NOTE]
> If the approval process returns errors on some registrations, for example because of missing information, you must edit those registrations and approve again.

> [!TIP]
> To see a list of worker registrations that contain errors in the registration lines, click **Display errors**. The **Error** tab provides information about the type of error.

## Approve registrations for one worker at a time

You typically must approve registrations for an individual worker after you have corrected errors for that worker.

1.  In the **Approve** page, select the worker in the upper pane.
2.  Select the **Approved** checkbox for the worker.

## Reverse an approval

Approved registrations for a worker can be reversed until payroll information for the period has been exported to the payroll system. Do the following to reverse approved registrations for a worker:

1.  In the **Approve** page, select the worker in the upper pane.
2.  Clear the **Approved** checkbox.

> [!TIP]
> If you have made several corrections to the registrations, and, therefore, must restore the lines to their original value, delete all lines, and then click **Restore lines**.

Registrations must be transferred to journals, such as production or project journals.

After workers’ registrations are approved, and no errors occur, you can transfer the registrations. You can transfer registrations in one of the following ways:

  - Transfer registrations by using a workflow.
  - Transfer registrations by using a batch job.
  - Transfer registrations manually for an approval group.
  - Transfer registrations manually for one worker at a time.

## Transfer registrations using a workflow

If an approval workflow is set up to approve registrations based on a set of predefined rules, all approved registrations are transferred to the appropriate journals. Only deviations that aren't accepted in the workflow are handled manually. This means that approval and transferal of those registrations is performed by the worker responsible for approving registrations, for example, a payroll administrator.

## Transfer registrations using a batch job

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Approve**.
2.  Select the approval date in the **Date** field.
3.  Select your group in the **Approval group** field.
4.  Click **Update** and then **Transfer**.
5.  Start the batch job. For more information, see [Transfer registrations (class form)](https://technet.microsoft.com/library/aa548840\(v=ax.60\)).

## Transfer registrations for all workers in an approval group

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Approve**.
2.  Select the approval date in the **Date** field.
3.  Select your group in the **Approval group** field.
4.  Click **Update** and **Transfer**.
5.  Click **OK**.


> [!NOTE]
> You can only transfer registrations that have been calculated and approved without errors.

> [!TIP]
> To view a list of worker registrations that contain errors in the registration lines, click **Display errors**. The **Error** tab provides information about the type of error.

## Transfer registrations for one worker

When an error is found in a worker registration, you can transfer the registration after you have corrected the error.

1.  In the **Approve** page, select the worker in the upper pane.
2.  Select the **Transferred** checkbox for the worker.

## Reverse a transferred registration

You can reverse transferred registrations for a worker before payroll information for the period is exported to the payroll system. Do the following to reverse transferred registrations for a worker:

1.  In the **Approve** page, select the worker in the upper pane.
2.  Clear the **Transferred** checkbox.

## See also

[Calculate, approve, and transfer registrations](hr-about-calculate-approve-transfer-registrations.md)

[Update time and attendance information](hr-update-time-and-attendance-information.md)

[Communicate with and deploy assignments to workers](hr-communicate-and-deploy-assignments.md)
