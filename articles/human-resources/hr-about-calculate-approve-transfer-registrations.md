---
title: Calculate, approve, and transfer registrations
description: Learn how to create and manage time and attendance registrations by calculating and transferring registrations in Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.date: 05/14/2026
ms.topic: article

audience: Application User
ms.search.region: Global
---

# Calculate, approve, and transfer registrations

You can create and manage time and attendance registrations. Registrations made by workers must be calculated, approved, and transferred daily. During that process, any registration errors can be corrected, missing registrations can be added, and incorrect registrations can be deleted.

> [!TIP]
>Time and attendance features can be used in manufacturing execution for time and attendance registrations in a production environment.

## Calculating registrations

When registrations are calculated, they're verified against a worker's work time profile. The registrations that are calculated include work time, pay time, pay overtime, and absence time. Calculation is typically performed by a team leader or a supervisor. You can set up calculation groups for groups of workers to help make sure that the person calculating registrations can view information about only the workers on their team.

Before calculating registrations, you can override the work time profile for a specific worker.

If the registered time doesn't correspond to a worker’s work time profile, the calculation procedure creates errors, such as a missing absence registration. You can correct the errors and recalculate the registrations.

## Approving registrations

When you calculate all registrations without errors, the registrations are ready to be approved. Usually, a worker other than the one in charge of calculating registrations, such as a payroll administrator, approves the registrations. Set up approval groups for relevant groups of workers.

Before approving registrations, you can override pay agreements for individual workers and add manual premiums.

The approval workflow is an automatic approval process. All registrations are validated against the rules in the approval workflow. Only deviations that aren't accepted in the workflow must be approved manually.

The worker responsible for calculating registrations, such as a team leader, initiates the approval process. The worker responsible for approving registrations, such as a payroll administrator, receives a message regarding the need for manual approval only when some registrations can't be approved according to the approval workflow.

If you calculate overtime for specific workers, you can allocate the overtime to specific jobs during the day. This allocation is relevant if job cost is calculated based on worker pay.

During the process of approving a registration, you might need to enter additional information about absence registrations. If more absence information is needed, the system points it out during the approval process.

## Approving registrations by using workflow

It's possible to set up a workflow approval process that automatically approves registrations that comply with the rules set up in the workflow. If workflow approval is activated, the user who calculates registrations, for example, a team leader or a supervisor, submits the calculated registrations for approval. Through the workflow process, the appropriate approvals and tasks are created and they're assigned to the users and roles as identified in the workflow.

The approval workflow automates the approval process and allows users who have approval rights to approve many worker registrations at a time. Only deviations that aren't accepted in the approval workflow must be handled manually.

You can create two types of workflow approval in time and attendance:

- **Time and attendance days total workflow** – The workflow validates registrations against, for example, the expected number of work hours for the day.

- **Time and attendance journal registration workflow** – The workflow validates each registration type for the date of the registration. The following journal registration types are available. Time and attendance automatically selects the registration types, depending on the worker’s registration:

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

After you approve registrations, transfer them to a periodic payroll job.

When you transfer a registration, you post it to an activity or job that it relates to, such as a production order or a project. The process also generates payroll transactions for each worker based on the registrations.

## Reversing registrations

Registrations that have been transferred can be reversed (rolled back). The task of reversing registrations can be done until the time when the payroll period's pay transfer is run. This means that payroll data has been transferred to an external file. The external file can be imported into a payroll system.

When you reverse registrations, the system withdraws all registrations and offsets and neutralizes any transactions posted on production orders or projects.

## Modify registrations before or after calculation

You can modify registrations made by workers before or after you calculate the registrations.

After you calculate or approve registrations, you can view error descriptions on the **Error** tab on the **Calculate** and the **Approve** pages. For example, an error message might inform you that information about a worker’s absence time is missing.

## Update an absence registration

1. Go to **Human resources** > **Common** > **Time and attendance** > **Calculate**. In the **Calculate** dialog box, enter the date and calculation group in the **Date** and **Calculation group** fields to calculate registrations for. Select **OK**.

1. On the **Calculate** page, select the worker in the upper pane, and then, on the **Absence** tab, modify the absence registration that was entered during calculation. You can also press **CTRL+N** to create a new absence registration.

1. Save the absence records. The absence records appear in the lower pane on the **Overview** tab.

1. Follow steps 1 through 3 for every worker for whom an absence registration is required.

> [!NOTE]
> When you calculate registrations for a group of workers, any missing absence records for the workers are created automatically. For those absence records, you only have to select the absence codes. Start times and end times are added automatically during calculation.

## Approve switch codes for a worker

1. Go to **Human resources** > **Common** > **Time and attendance** > **Calculate**. In the **Calculate** dialog box, enter the date and calculation group in the **Date** and **Calculation group** fields to approve switch codes for. Select **OK**.

1. On the **Calculate** page, select the worker in the upper pane, and then select **Switch code**.

1. Select **Approved** and close the page.

## Add a missing clock-out registration

1. Go to **Human resources** \> **Common** \> **Time and attendance** \> **Calculate**. In the **Calculate** dialog box, in the **Date** and **Calculation group** fields, enter the date and calculation group to add clock-out registrations for. Select **OK**.

1. In the **Calculate** form, select the worker in the upper pane, and then select **Clock-in and out** > **Missing clock-out**.

1. In the **Clock out** section, select the date and time for the clock-out registration.

1. Select the **Create lines** check box, and then select **OK**.

## Clock out all workers in a calculation group

1. Go to **Human resources** > **Common** > **Time and attendance** > **Calculate**. In the **Calculate** dialog box, enter the date and calculation group in the **Date** and **Calculation group** fields to calculate registrations for. Select **OK**.
1. On the **Calculate** page, select **Clock-in and out** > **Clock out workers**.
1. In the **Profile date** field, select the clock-out date. Select **OK**.

> [!NOTE]
> All workers in the selected calculation group are clocked out according to their work time profile.

## Transfer time and attendance registrations

You must transfer registrations to journals, such as production or project journals.

After you approve workers’ registrations and no errors occur, you can transfer the registrations. You can transfer registrations in one of the following ways:

- Transfer registrations by using a workflow.
- Transfer registrations by using a batch job.
- Transfer registrations manually for an approval group.
- Transfer registrations manually for one worker at a time.

## Transfer registrations by using a workflow

If an approval workflow is set up to approve registrations based on a set of predefined rules, all approved registrations are transferred to the appropriate journals. Only deviations that aren't accepted in the workflow are handled manually. This means that approval and transferal of those registrations is performed by the worker responsible for approving registrations, for example, a payroll administrator.

## Transfer registrations by using a batch job

1. Go to **Human resources** > **Common** > **Time and attendance** > **Approve**.
1. Select the approval date in the **Date** field.
1. Select your group in the **Approval group** field.
1. Select **Update** and then **Transfer**.
1. Start the batch job.

## Transfer registrations for all workers in an approval group

1. Go to **Human resources** > **Common** > **Time and attendance** > **Approve**.
1. Select the approval date in the **Date** field.
1. Select your group in the **Approval group** field.
1. Select **Update** and **Transfer**.
1. Select **OK**.

> [!NOTE]
> You can only transfer registrations that are calculated and approved without errors.

To view a list of worker registrations that contain errors in the registration lines, select **Display errors**. The **Error** tab provides information about the type of error.

## Transfer registrations for one worker

When you find an error in a worker registration, you can transfer the registration after you correct the error.

1. On the **Approve** page, select the worker in the upper pane.
1. Select **Transferred** for the worker.

## Reverse a transferred registration

You can reverse transferred registrations for a worker before you export payroll information for the period to the payroll system.

To reverse transferred registrations for a worker, follow these steps:

1. On the **Approve** page, select the worker in the upper pane.
1. Clear the **Transferred** checkbox.

## Correct errors and add registrations

1. Go to **Human resources** > **Common** > **Time and attendance** > **Calculate**. In the **Calculate** dialog box, enter the date and calculation group in the **Date** and **Calculation group** fields to calculate registrations for. Select **OK**.
1. On the **Calculate** page, select the worker in the upper pane. In the lower pane, select the registration to modify, or press **CTRL+N** to add a new line.
1. Enter information for the registration line.
1. To recalculate the worker’s registrations, in the upper pane, on the **Overview** tab, select **Calculated**.

> [!IMPORTANT]
> Don't create a new journal line for a clock-out registration if a worker didn't clock out. To create missing clock-out registrations, select **Clock-in and out**, and then select the appropriate option. Only these two options ensure that the clock-out registration is entered in the **Raw registrations** table. Raw registrations determine whether the worker is clocked in or clocked out.

## See also

[Time and attendance information](hr-about-time-and-attendance-information.md)

[Communicate with and deploy assignments to workers](hr-communicate-and-deploy-assignments.md)

[Register time for workers](hr-register-time.md)
