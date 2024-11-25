---

# required metadata

title: Dynamics 365 Human Resources app for leave and absence
description: This article describes the Microsoft Dynamics 365 Human Resources app for leave and absence.
author: twheeloc
ms.date: 07/11/2024
ms.topic: overview
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-10-13
ms.dyn365.ops.version: Human Resources

---
# Dynamics 365 Human Resources app for leave and absence

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

The Human Resources app for leave and absence is integrated with Microsoft Dynamics 365 Human Resources. It helps organizations ensure that their employees can seamlessly request, edit, and cancel time off and leave of absence requests. Employees can view leave balances, upcoming leaves, and leave history in one app. Managers can also use the app to view requests, and approve or reject them.

The Human Resources app for leave and absence can be used in Microsoft Teams or in a web browser. It can be used on both mobile devices and desktop devices.

Administrators of an organization must install the Human Resources app and share it with Microsoft Teams before organization users can use it.

> [!IMPORTANT]
> Updates for the Human Resources app will be available. We don't recommend that you customize the app.

## Install the Human Resources app

Before you install the Human Resources app, the following prerequisites must be met:

- You must have a version 10.0.39 or later Dynamics 365 Human Resources environment, and the latest quality update must be installed.
- You must have a license to Dynamics 365 Human Resources or a Dynamics 365 Human Resources self service license assigned.
- The user who installs the app must have a system administrator role in both the Dynamics 365 Human Resources environment and Power Apps.
- For the notifications to work, you must install the **Microsoft flow approvals** app before you update or install.

    To install the **Microsoft flow approvals** app, follow these steps:

    1. In the appropriate environment's Power Platform admin center, go to **Dynamics 365 Apps**.
    1. Search for **Microsoft flow approvals**, and select **Install app**.
    1. Select the app, and then select **Next** to install it.

To install the Human Resources app for the first time, follow these steps.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as an admin.
2. Select **Environments**, search for your environment, and select it.
3. Follow these steps to confirm that the **Power Apps component framework for canvas apps** feature is enabled:

    1. Go to **Settings**, expand **Product**, and select **Features**.
    1. Search for **Power Apps component framework for canvas apps**, and enable it if it isn't already enabled.
    1. Select **Save**.

4. Select **Human Resources** to access the Human Resources app for leave and absence on AppSource, and then select **Get it now**.
5. You're redirected to Power Platform admin center.
6. Sign in to Power Platform admin center, select your environment, and then select **Install**.
7. To check the status of the installation, in Power Platform admin center, select **Environments**, select your environment, and then, in the **Resources** section, select **Dynamics 365 apps**. If the installation is successful, the **Status** column for Dynamics 365 Human Resources is changed to **Installed**. If the installation fails, try to install the app again by selecting **Retry installation** in Power Platform admin center.

## Update the Human Resources app

Use this procedure if the previous version of the Human Resources app is installed, and you must update it to the enhanced version.

1. In Power Platform admin center, select **Environments**, select your environment, and then, in the **Resources** section, select **Dynamics 365 apps**.
2. In the **Status** column for Dynamics 365 Human Resources, if an update is available, select it, and then select **Update**.
3. If the installation fails, try to install the app again by selecting **Retry installation** in Power Platform admin center.

## Embed the Human Resources app in Microsoft Teams

To embed the Human Resources app in Microsoft Teams, see [Embed a model-driven app as a personal app in Teams](/power-apps/teams/embed-model-driven-teams-personal). The Human Resources app can also be used in a web browser.

## Onboard users to the Human Resources app

1. Users of the app should have the following roles in Microsoft Power Platform:

    - Basic user
    - Finance and operations basic user
    - Human Resources Teams app user

2. End users should be assigned an employee role in the Dynamics 365 Human Resources environment.

## Create and manage leave requests by using the Human Resources app

### View available balances

1. Expand **Leave details**, and select **Available balances**.
2. For each leave plan that's assigned to the signed-in user, a tile shows the available balance. You can request leave directly from a tile by selecting the **Request** button.
3. If the HR administrator hid the leave balance for a leave plan, "- -" is shown as the balance value for the leave plan.

### Request leave

1. Select either the **Request** button on the **Available balance** tile or the **Request time off** button. A new page contains **Leave type**, **Reason code**, **Start date**, and **End date** fields that must be set.
2. Select **Add**.
3. The selected number of days appears in **Selected dates**. To update the details of the dates, select **Edit days present**, and then follow these steps:

    - To change the number of hours or a request for half-day leave, select **Edit day**.
    - To remove a specific date from the date range, select the **Delete** (trashcan) button on the date tile.

4. After you finish making changes, select **Save**.
5. Add any comments and attachments that are required, and then select **Next**.
6. Review the details of the leave request. If everything looks correct, select **Submit**. Alternatively, you can save the leave request as a draft by selecting **Save as draft**. To cancel the action of creating a leave request, select **Cancel**. You can view draft and submitted leave requests in **Upcoming leaves**.
7. To request and submit a leave of absence, select **Request leave of absence**.
8. Select the leave type, enter the start and end dates, add any comments, and submit the request

### Edit a leave request

1. Select the leave request that you want to edit, and then select **Edit leave**.
2. Update the leave request, and then submit it. If an approval workflow is associated with the leave type, it's submitted for approval again.

To edit a single day in a leave request that includes more than one day, select the **Edit** button on the tile next to that day, and update the details. Then submit the request.

### Cancel a leave request

1. Select the leave request that you want to cancel, and then select **Delete leave**.
2. Select **Request cancellation**.

To cancel a single day in a leave request that includes more than one day, select the **X** button on the tile next to that day, and then submit the request.

### View upcoming requests

- Expand **Leave details**, and select **Upcoming requests**. The app shows all approved future leave requests in order of ascending date.

### View pending leaves

- Expand **Pending leaves** to view the leave requests that have a status of **Submitted**, **In review**, and **Draft**.

### View leave history

- Expand **Leave details**, and select **History**.

    The app shows all leaves that have an end date in the past.

### Approve or reject a leave request

Users who have the HR Manager or HR Absence manager role can use the Human Resources app to approve or reject leave requests for their direct reports on their team.

1. Expand **My team**, and select **Pending requests** to view open leave requests that are awaiting approval.
2. Select a leave request, and then select **Approve** or **Reject**.

### Notifications to managers, users, and approver delegates

If you must send a team's notifications to users who approve leave requests, the notifications are sent to both Outlook and Teams. For the team's application, confirm that the Approvals app is installed in the end user's Microsoft Teams. For Outlook, no additional setup is required. You can also approve or reject leave requests directly from Outlook.

There are three new connection references. All the connection references are part of the default solution. Customers can update or edit the connections in the connection reference. These actions will not create an unmanaged version of the Human Resources Teams app.

> [!NOTE]
> All the connection references must be linked with the system administrator connection, because the system administrator runs the flows on behalf of the users.

- **new_HRDataverseSysAdminAccess** – This connection reference connects to Dataverse events and tables. It should have the system administrator role in Dataverse.
- **new_HRFinOpsSysAdminAccess** – This connection reference connects to Dynamics 365 Human Resources tables and actions. It should have the system administrator role in Dynamics 365 Human Resources.
- **new_HRSysAdminNotificationAccess** – This connection reference sends approval notifications to Teams and Outlook. It expects the connection to be the same as **new_HRDataverseSysAdminAccess**.

### Limitation on using the Approval connection

- The **Approve** action remains active in Outlook and Teams for a maximum of 28 days.
- The Approval connection requires that both the sender ID and the receiver ID are available in Microsoft Entra ID. If either ID isn't available in Microsoft Entra ID, the flow doesn't work.

### Uninstall the Human Resources app

If the Human Resources app must be uninstalled, follow these steps.

1. Open [Power Apps](https://make.powerapps.com/).
2. Select the Dataverse environment.
3. Go to **Solutions**, and select **Managed solutions**.
4. Delete the Human Resources solution.
5. Delete the following solutions: 

    - Custom components for Human Resource App 
    - Human Resources App Entities 
    - Human Resources App Flows 
    - HCM Application Anchor Solution

### Supported languages

The Human Resources app supports all languages that Power Apps supports.

### Submitting questions or feedback about the Human Resources app

- The Human Resources App Viva Engage (Yammer) group is a great place to exchange tips, check on issues, and submit feedback to Microsoft. The group includes Microsoft partners, customers, experts, and employees.
- In addition, support requests can be submitted.
