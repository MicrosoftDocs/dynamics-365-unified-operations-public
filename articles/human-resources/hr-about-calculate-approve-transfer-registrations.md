---
title: Calculate, approve, and transfer registrations
description: Learn how to create and manage time and attendance registrations by calculating and transferring registrations in Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.date: 01/24/2024
ms.topic: article

audience: Application User
ms.search.region: Global
---

# Calculate, approve, and transfer registrations

You can create and manage time and attendance registrations. Registrations made by workers must be calculated, approved, and transferred daily. During that process, any registration errors can be corrected, missing registrations can be added, and incorrect registrations can be deleted.

> [!TIP]
>Time and attendance features can be used in manufacturing execution for time and attendance registrations in a production environment.

## Calculating registrations

When registrations are calculated, they're verified against a worker's work time profile. The registrations that are calculated include work time, pay time, pay overtime, and absence time. Calculation is typically performed by a team leader or a supervisor. You can set up calculation groups for groups of workers to help make sure that the person calculating registrations can view information about only the workers on his or her team.

Before calculating registrations, you can override the work time profile for a specific worker.

If the registered time does not correspond to a worker’s work time profile, the calculation procedure will create errors, such as a missing absence registration. The errors can be corrected and the registrations recalculated.

## Approving registrations

When all registrations have been calculated without errors, the registrations are ready to be approved. Approval is usually done by a worker other than the one in charge of calculating registrations, for example, a payroll administrator. You can set up approval groups for relevant groups of workers.

Before approving registrations, you can override pay agreements for individual workers and add manual premiums.

The approval workflow is an automatic approval process. All registrations are validated against the rules in the approval workflow. Only deviations that aren't accepted in the workflow must be approved manually.

The worker who is responsible for calculating registrations, for example, a team leader, initiates the approval process. The worker who is responsible for approving registrations, for example, a payroll administrator, receives a message regarding the need for manual approval only when some registrations couldn't be approved according to the approval workflow.

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

After you calculate or approve registrations, you can view error descriptions on the **Error** tab on the **Calculate** and the **Approve** pages. For example, an error message may inform you that information about a worker’s absence time is missing.

## Update an absence registration

1.  Go to **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**. In the **Calculate** dialog box, in the **Date** and **Calculation group** fields, enter the date and calculation group to calculate registrations for. Click **OK**.

2.  On the **Calculate** page, select the worker in the upper pane, and then, on the **Absence** tab, modify the absence registration that was entered during calculation. You can also press **CTRL+N** to create a new absence registration.

3.  Save the absence records. The absence records are displayed in the lower pane on the **Overview** tab.

4.  Follow steps 1 through 3 for every worker for whom an absence registration is required.

> [!NOTE]
> When you calculate registrations for a group of workers, any missing absence records for the workers are created automatically. For those absence records, you only have to select the absence codes. Start times and end times are added automatically during calculation.

## Approve switch codes for a worker

1.  Go to **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**. In the **Calculate** dialog box, in the **Date** and **Calculation group** fields, enter the date and calculation group to approve switch codes for. Click **OK**.

2.  On the **Calculate** page, select the worker in the upper pane, and then click **Switch code**.

3.  Select **Approved** and close the page.

## Add a missing clock-out registration

1.  Go to **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**. In the **Calculate** dialog box, in the **Date** and **Calculation group** fields, enter the date and calculation group to add clock-out registrations for. Click **OK**.

2.  In the **Calculate** form, select the worker in the upper pane, and then click **Clock-in and out** \> **Missing clock-out**.

3.  In the **Clock out** section, select the date and time for the clock-out registration.

4.  Select the **Create lines** check box, and then click **OK**.

## Clock out all workers in a calculation group

1.  Go to **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**. In the **Calculate** dialog box, in the **Date** and **Calculation group** fields, enter the date and calculation group to calculate registrations for. Click **OK**.
2.  On the **Calculate** page, click **Clock-in and out** \> **Clock out workers**.
3.  In the **Profile date** field, select the clock-out date. Click **OK**.

> [!NOTE]
> All workers in the selected calculation group are clocked out according to their work time profile.

## Transfer time and attendance registrations 

Registrations must be transferred to journals, such as production or project journals.

After workers’ registrations are approved, and no errors occur, you can transfer the registrations. You can transfer registrations in one of the following ways:

  - Transfer registrations by using a workflow.
  - Transfer registrations by using a batch job.
  - Transfer registrations manually for an approval group.
  - Transfer registrations manually for one worker at a time.

## Transfer registrations using a workflow

If an approval workflow is set up to approve registrations based on a set of predefined rules, all approved registrations are transferred to the appropriate journals. Only deviations that aren't accepted in the workflow are handled manually. This means that approval and transferal of those registrations is performed by the worker responsible for approving registrations, for example, a payroll administrator.

## Transfer registrations using a batch job

1.  Go to **Human resources** \> **Common** \> **Time and attendance** \> **Approve**.
2.  Select the approval date in the **Date** field.
3.  Select your group in the **Approval group** field.
4.  Click **Update** and then **Transfer**.
5.  Start the batch job.

## Transfer registrations for all workers in an approval group

1.  Go to **Human resources** \> **Common** \> **Time and attendance** \> **Approve**.
2.  Select the approval date in the **Date** field.
3.  Select your group in the **Approval group** field.
4.  Click **Update** and **Transfer**.
5.  Click **OK**.

> [!NOTE]
> You can only transfer registrations that have been calculated and approved without errors.

To view a list of worker registrations that contain errors in the registration lines, click **Display errors**. The **Error** tab provides information about the type of error.

## Transfer registrations for one worker

When an error is found in a worker registration, you can transfer the registration after you have corrected the error.

1.  On the **Approve** page, select the worker in the upper pane.
2.  Select **Transferred** for the worker.

## Reverse a transferred registration

You can reverse transferred registrations for a worker before payroll information for the period is exported to the payroll system. 

To reverse transferred registrations for a worker, follow these steps:

1.  On the **Approve** page, select the worker in the upper pane.
2.  Clear the **Transferred** checkbox.

## Correct errors and add registrations

1.  Go to **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**. In the **Calculate** dialog box, in the **Date** and **Calculation group** fields, enter the date and calculation group to calculate registrations for. Click **OK**.
2.  On the **Calculate** page, select the worker in the upper pane. In lower pane, click the registration to modify, or press **CTRL+N** to add a new line.
3.  Enter information for the registration line.
4.  To recalculate the worker’s registrations, in the upper pane, on the **Overview** tab, select **Calculated**.

> [!IMPORTANT]
> Don't create a new journal line for a clock-out registration if a worker didn't clock out. To create missing clock-out registrations, click **Clock-in and out**, and then select the appropriate option. Only these two options make sure that the clock-out registration is entered in the **Raw registrations** table. Raw registrations determine whether the worker is clocked in or clocked out.

## See also

[Time and attendance information](hr-about-time-and-attendance-information.md)

[Communicate with and deploy assignments to workers](hr-communicate-and-deploy-assignments.md)

[Register time for workers](hr-register-time.md)
