---
# required metadata

title: Configure absence manager role
description: This topic describes setting up the absence manager role for managing employees' leave.
author: hasrivas
ms.date: 07/14/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LeavePlanFormPart, LeaveAbsenceWorkspace , LeaveAbsenceManager
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: hasrivas
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure absence manager role

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!include [preview feature](./includes/preview-feature.md)]

In some organizations, a people manager might not be managing the leave for their team. Instead, an absence manager might handle this process for team members across multiple departments and teams. Absence managers will be able to manage leave with the following capabilities:

- Review and approve time off based on an alternate hierarchy.
- View team member balances.
- View the absence calendar.


## Enable feature 

1.  In the **System Administration** workspace, select **Feature management**.

2.  From the **Feature management** tab, enable the **Absence manager to manage leave** feature.


## Define new custom hierarchy
This absence manager capability uses a custom hierarchy that needs to be configured.

1.  In the **Organization Administration** workspace, select **Position hierarchy types**.

2.  Create a new position hierarchy type named **Leave**.

3.  Go to **Leave and Absence** workspace, under **Links**, select **Leave and Absence parameters**. In the general tab select **Absence hierarchy**, from the dropdown select the hierarchy type **Leave** created in the previous step. This leave hierarchy assoication needs to be completed for each leagal entity where the absence manager capability will be used. 

Once the hierarchy type is defined then the position hierarchy report will be assigned to the position.

1.  In the **Organization Administration** workspace, select **All positions.**

2.  Select the position you want to add this **Leave hierarchy**.

3.  Under **Relationships** tab, select Add.

- In the hierarchy name, select from the dropdown Leave.</br>

= In the Reports to position, select a position from the dropdown.</br>

The worker name will complete automatically once you select a position from the reports to position tab.

## Assign the Absence manager role to a user
The Absence manager role needs to be assigned in order to allow an employee to approve or deny leave requests.

1.  In the **System Administrator** workspace, select **Links**.

2.  Under **Users** section, select **Users** link.

3.  From the list of users, select the user you want to assign the Absence manager role.

4.  In the **User's role** tab, select **+Assign roles**.

5.  From the list, select the Absence manager role, and select ok. Make sure the user you want to assign with the Absence manager role has also been assigned the Employee role. If not, the worker will not be able to use this feature.


Once you created the Leave hierarchy, you can check how it looks like following these steps:

1.  In the **Organization Administration** workspace, select **Position hierarchy**.

2.  In the hierarchy type box select **Leave**.


## Absence manager features 
Once the system administrator assigns the absence manager role to an user, this user will be able to perform different activities related to absence for the employees assigned in Leave hierarchy.

In the **Employee Self-Service** workspace, select the **Absence manager** tab. You will find the absence information about the employees assigned to you in Leave hierarchy.

In the Absence manager section there are two tabs, Summary and Absence.

-   **Summary** you will find information about leave balances, a list of the balances for the different leave plans for the employees.

-   **Absence** tab, select **Details**, and then **Time off**. In this section you will find three tabs: balances, approved time off, and time off request.


## Approve time off request
The absence manager can approve or deny time off request for employees, only if the workflow has been edited to perform this action, review the following documentation to check how to create a leave request workflow. If needed, the absence manager can also create requests on behalf of the employee.

In The **Employee Self-Service** workspace, select the **Absence manager** tab.

In the **Absence** tab, click on the desired employee. Select **Details** \> **Time off**

You will find the time off request, select the **Approval** option. A dropdown will open and you can approve or cancel the time off request.

-   Cancel status mean that the request has been denied.

-   Completed status means the request has been approved.

## See time off in calendar 
From the Absence manager role, users are able to see time-off requests in calendar. Follow these steps to access the Leave calendar.

1.  Log in the system as Manager with the Absence manager role.

2.  In the **Employee Self-Service** workspace, select **Absence manager** and then **Absence manager calendar.**

3.  In the date box, enter the desired dates

4.  All the records for the employee/s reporting to the manager in the absence hierarchy will show in **Absence manager calendar**.


## See also

[Leave and absence overview](hr-leave-and-absence-overview.md)</br>
[Create a leave request workflow](hr-leave-and-absence-workflow.md)</br>
[View team and company calendars](hr-employee-self-service-calendar.md)</br>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
