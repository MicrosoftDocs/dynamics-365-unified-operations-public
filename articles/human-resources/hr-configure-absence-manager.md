---
# required metadata

title: Configure the Absence manager role
description: This article explains how to set up the Absence manager role for management of employee leave.
author: twheeloc
ms.date: 08/06/2026
ms.topic: how-to
# optional metadata

ms.search.form: LeavePlanFormPart, LeaveAbsenceWorkspace, LeaveAbsenceManager
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ajitchandran
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure the Absence manager role

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

In some organizations, people managers don't manage the leave for their team. Instead, an absence manager handles this process for team members across multiple departments and teams. Absence managers have the following capabilities for leave management:

- Review and approve time off, based on an alternate hierarchy.
- View team member balances.
- View the absence calendar.

## Turn on the feature

1. In the **System administration** workspace, select **Feature management**.
1. On the **Feature management** tab, enable the **Absence manager to manage leave** feature.

## Define a custom hierarchy

The absence manager functionality uses a custom hierarchy that you must configure.

1. In the **Organization administration** workspace, select **Position hierarchy types**.
1. Create a position hierarchy type named **Leave**.
1. In the **Leave and absence** workspace, under **Links**, select **Leave and Absence parameters**.
1. On the **General** tab, in the **Absence hierarchy** drop-down list, select the **Leave** hierarchy type that you created earlier. You must complete this Leave hierarchy association for every legal entity where you use the absence manager functionality.

After you define the hierarchy type, assign the position hierarchy report to the position.

1. In the **Organization Administration** workspace, select **All positions**.
1. Select the position to add the Leave hierarchy to.
1. On the **Relationships** tab, select **Add**.
1. In the **Hierarchy name** field, select **Leave**.
1. In the **Reports to position** field, select a position. The worker name automatically fills in after you select a position.

## Assign the Absence manager role to a user

Assign the Absence manager role to employees so they can approve or deny leave requests.

1. In the **System administration** workspace, select **Links**.
1. In the **Users** section, select the **Users** link.
1. In the list of users, select the user to assign the Absence manager role to.
1. On the **User's role** tab, select **Assign roles**.
1. In the list, select the **Absence manager** role. Then select **OK**.

    > [!IMPORTANT]
    > Make sure that you also assign the Employee role to the user that you're assigning the Absence manager role to. Otherwise, the worker can't use the feature.

1. After you create the Leave hierarchy, view it by following these steps:

    1. In the **Organization Administration** workspace, select **Position hierarchy**.
    1. In the **Hierarchy type** field, select **Leave**.

## Absence manager workspace

In the **Employee self service** workspace, the **Leave management** tab shows the absence information about the employees who are assigned to the absence manager in the Leave hierarchy. The absence manager has several options:

- Review time off requests.
- Submit a time off request on behalf of an employee.
- View all employees assigned to them as part of the leave hierarchy.
- View the absence manager calendar.

On the **Leave management** workspace, there are two tabs:

- **Time off requests**: This tab lists all the pending time off requests that the absence manager can approve. The absence manager can select multiple records and take action on them at the same time. If cross-company leave view is enabled, this list shows pending time off requests across all legal entities they access. Otherwise, it shows the pending time off requests for the legal entity currently selected.
- **All employees**: This tab lists all the employees that the absence manager is assigned to in the Leave hierarchy. Each employee has a couple of options:
  - **Request time off** -  Submit a new time off request for the selected employee.
  - **Time off** – View balances, approved time off, and time-off requests for the selected employee.

## Approve time-off requests

Absence managers can approve or deny time-off requests for employees.

> [!IMPORTANT]
> Before absence managers can approve or deny time off requests, configure the leave request workflow to assign leave request work items to them for review.
>
> 1. On **Human resource workflows**, select or create the leave request workflow.
> 1. Select the **Associate hierarchy** option, and then, in the **Hierarchy name** field, select **Leave**.
> 1. Update the workflow in the workflow designer. Under **Assignment type**, select the **Hierarchy** option, and then, on the **Hierarchy selection** tab, select **Configurable hierarchy**.
>
> For information about how to create the leave request workflow, see [Create a leave request workflow](hr-leave-and-absence-workflow.md).

1. In the **Employee self service** workspace, select the **Leave management** tab.
1. On the **Time off requests** tab, select the time off requests that you want to take action on. You can select multiple records in this list view.
1. Use the action buttons at the top of the grid to **Approve**, **Deny**, or **Delegate** the time off request.

Alternatively, use the **Time off requests** tile on the left to go to the list of all time off request work items.

## View time off in the calendar

Users in the Absence manager role can view time off requests in their calendar. Follow these steps to access the leave calendar.

> [!IMPORTANT]
> A system administrator must configure the view options for the absence manager calendar. On the **Leave and absence parameters** page, on the **Calendar** tab, you can hide or show birthdays, absences without details, leaves of absence, and pending leave requests. You can also filter the calendar view option by worker type.

1. In the **Employee self service** workspace, select **Leave management** and then **Absence manager calendar**.
1. In the **Date** field, enter the desired dates.
1. Update the view options as required.

The absence manager calendar shows all the records for the employees who report to the absence manager in the Leave hierarchy.

## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)
- [Create a leave request workflow](hr-leave-and-absence-workflow.md)
- [View team and company calendars](hr-employee-self-service-calendar.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
