---
# required metadata

title: Configure the Absence manager role
description: This article explains how to set up the Absence manager role for management of employee leave.
author: twheeloc
ms.date: 08/25/2021
ms.topic: article
ms.prod: 
ms.technology: 

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
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure the Absence manager role


[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

In some organizations, people managers might not manage the leave for their team. Instead, an absence manager might handle this process for team members across multiple departments and teams. Absence managers have the following capabilities for leave management:

- Review and approve time off, based on an alternate hierarchy.
- View team member balances.
- View the absence calendar.

## Turn on the feature

1. In the **System administration** workspace, select **Feature management**.
2. On the **Feature management** tab, enable the **Absence manager to manage leave** feature.

## Define a custom hierarchy

The absence manager functionality uses a custom hierarchy that must be configured.

1. In the **Organization administration** workspace, select **Position hierarchy types**.
2. Create a position hierarchy type that is named **Leave**.
3. In the **Leave and absence** workspace, under **Links**, select **Leave and Absence parameters**.
4. On the **General** tab, in the **Absence hierarchy** drop-down list, select the **Leave** hierarchy type that you created earlier. This Leave hierarchy association must be completed for every legal entity where the absence manager functionality will be used.

After the hierarchy type is defined, the position hierarchy report must be assigned to the position.

1. In the **Organization Administration** workspace, select **All positions**.
2. Select the position to add the Leave hierarchy to.
3. On the **Relationships** tab, select **Add**.
4. In the **Hierarchy name** field, select **Leave**.
5. In the **Reports to position** field, select a position. The worker name is automatically filled in after you select a position.

## Assign the Absence manager role to a user

The Absence manager role must be assigned to employees to enable them to approve or deny leave requests.

1. In the **System administration** workspace, select **Links**.
2. In the **Users** section, select the **Users** link.
3. In the list of users, select the user to assign the Absence manager role to.
4. On the **User's role** tab, select **Assign roles**.
5. In the list, select the **Absence manager** role. Then select **OK**.

    > [!IMPORTANT]
    > Make sure that the Employee role has also been assigned to the user that you're assigning the Absence manager role to. Otherwise, the worker won't be able to use the feature.

6. After you've created the Leave hierarchy, you can view it by following these steps:

    1. In the **Organization Administration** workspace, select **Position hierarchy**.
    2. In the **Hierarchy type** field, select **Leave**.

## Absence manager workspace

In the **Employee self service** workspace, the **Leave management** tab shows the absence information about the employees who are assigned to the absence manager in the Leave hierarchy. There are a few options available to the absence manager: 
 - Review time off requests.</br>
 - Submit a time off request on behalf of an employee.</br>
 - View all employees assigned to them as part of the leave hierarchy.</br>
 - View the absence manager calendar.</br>

On the **Leave management** workspace, there are two tabs:
 - **Time off requests**: This tab will list all the pending time off requests that the absence manager can approve. The absence manager can select multiple records and take action on them at the same time. If cross-company leave view is enabled, this list will show pending time off requests across all legal entities they have access to. Otherwise, it will show the pending time off requests for the legal entity currently selected. </br>
 - **All employees**: This tab will list all the employees that are assigned to the absence manager in the Leave hierarchy. There are a couple of options available for each employee:
    - **Request time off** -  Submit a new time off request for the selected employee.</br>
    - **Time off** – View balances, approved time off, and time-off requests for the selected employee.</br>

## Approve time-off requests

Absence managers can approve or deny time off requests for employees. 

> [!IMPORTANT]
> Before absence managers can approve or deny time off requests, the leave request workflow must be configured to assign leave request work items to them for review.
>
> 1. On the **Human resource workflows** page, select or create the leave request workflow.
> 2. Select the **Associate hierarchy** option, and then, in the **Hierarchy name** field, select **Leave**.
> 3. Update the workflow in the workflow designer. Under **Assignment type**, select the **Hierarchy** option, and then, on the **Hierarchy selection** tab, select **Configurable hierarchy**.
>
> For information about how to create the leave request workflow, see [Create a leave request workflow](hr-leave-and-absence-workflow.md).

1. In the **Employee self service** workspace, select the **Leave management** tab.
2. On the **Time off requests** tab, select the time off requests that you want to take action on. You can select multiple records in this list view.
3. Use the action buttons at the top of the grid to Approve, Deny or Delegate the time off request. 

Alternatively, the user can also use the **Time off requests** tile on the left to navigate to the list of all time off request work items. 

## View time off in the calendar

Users in the Absence manager role can view time off requests in their calendar. Follow these steps to access the leave calendar.

> [!IMPORTANT]
> A system administrator must configure the view options for the absence manager calendar. On the **Leave and absence parameters** page, on the **Calendar** tab, there are options to hide or show birthdays, absences without details, leaves of absence, and pending leave requests. There is also an option to filter the calendar view option by worker type.

1. In the **Employee self service** workspace, select **Leave management** and then **Absence manager calendar**.
2. In the **Date** field, enter the desired dates.
3. Update the view options as required.

The absence manager calendar shows all the records for the employees who report to the absence manager in the Leave hierarchy.

## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)
- [Create a leave request workflow](hr-leave-and-absence-workflow.md)
- [View team and company calendars](hr-employee-self-service-calendar.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
