---

# required metadata

title: Dynamics 365 Human Resources (preview) app
description: This article describes the Microsoft Dynamics 365 Human Resources (preview) app.
author: twheeloc
ms.date: 11/25/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-10-13
ms.dyn365.ops.version: Human Resources

---
# Dynamics 365 Human Resources (preview) app

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]
[!include [preview banner](../includes/preview-banner.md)]

The Human Resources (preview) app is integrated with Microsoft Dynamics 365 Human Resources in a finance and operations environment. It helps organizations ensure that their employees can seamlessly request, edit, and cancel time off and leave of absence requests. The app provides an overall view of employee leave requests, leave balances, draft leave requests, and the leave requests for leave that was taken in the past. Managers can also use the app to view requests, and approve or reject them.

The Human Resources app can be used in Microsoft Teams or in a web browser. It can be used on both mobile devices and desktop devices. 

Administrators of an organization must install the Human Resources app and share it with Microsoft Teams before organization users can use it.

> [!IMPORTANT]
> Updates for the Human Resources app will be available. We don't recommend that you customize the app.

## Install the Human Resources app

Before you install the Human Resources app, the following prerequisites must be met:

- You must have a version 10.0.36 or later Dynamics 365 finance and operations environment, and the latest quality update must be installed.
- You must have a license to Dynamics 365 Human Resources in a finance and operations environment.
- The user who installs the app must have a system administrator role in both the Dynamics 365 Human Resources environment and Power Apps.

To install the Human Resources app for the first time, follow these steps.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as an admin.
1. Select **Environments**, search for your environment, and select it.
1. Follow these steps to confirm that the **Power Apps component framework for canvas apps** feature is enabled:

    1. Go to **Settings**, expand **Product**, and select **Features**.
    1. Search for **Power Apps component framework for canvas apps**, and enable it if it isn't already enabled.
    1. Select **Save**.

1. Select **Human Resources App V2**, and then select **Get it now**.
1. Sign in to Power Platform admin center, select your environment, and then select **Install**.
1. To check the status of the installation, in Power Platform admin center, select **Environments**, select your environment, and then, in the **Resources** section, select **Dynamics 365 apps**. If the installation is successful, the value in the **Status** column for Dynamics 365 Human Resources is changed to **Installed**. If the installation fails, try to install the app again by selecting **Retry installation** in Power Platform admin center.

## Update the Human Resources app

Use this procedure if the previous version of the Human Resources app is installed, and you must update it to the enhanced version.

1. In Power Platform admin center, select **Environments**, select your environment, and then, in the **Resources** section, select **Dynamics 365 apps**.
1. In the **Status** column for Dynamics 365 Human Resources, if an update is available, select it, and then select **Update**.
1. If the installation fails, try to install the app again by selecting **Retry installation** in Power Platform admin center.

For information about how to embed the Human Resources app in Microsoft Teams, see [Embed a model-driven app as personal app in Teams](../../power-apps/teams/embed-model-driven-teams-personal.md). The Human Resource app can also be used in a web browser.

## Onboard users to the Human Resources app

- Users of the app should have the following roles in Microsoft Power Platform:

    - Basic user
    - Finance and operations basic user
    - Human Resources Teams app user

- End users should be assigned an employee role in the Dynamics 365 Human Resources environment.

## Create and manage leave requests by using the Human Resources app

### View available balances

- Expand **Leave details**, and select **Available balances**.

    For each leave plan that's assigned to the signed-in user, a tile shows the available balance. You can request leave directly from a tile by selecting the **Request** button.

### Request leave

1. Select either the **Request** button on an available balance tile or the **Request time off** button. A new page contains **Leave type**, **Reason code**, **Start date**, and **End date** fields that must be set.
1. Select **Add**.
1. The selected number of days appears in **Selected dates**. Select **Edit days present** to update the details of the dates. For example, you might have to change the number of hours or a request for half-day leave.
1. Select **Edit day** to change the number of hours or a request for half-day leave. To remove a specific date from the date range, select the **Delete** (trashcan) button on the date tile. 
1. When you've finished making changes, select **Save**.
1. Add any comments and attachments that are required, and then select **Next**.
1. Review the details of the leave request. If everything looks correct, select **Submit**. Alternatively, you can save the leave request as a draft by selecting **Save as draft**. To cancel the action of creating a leave request, select **Cancel**. You can view draft and submitted leave requests in **Upcoming leaves**.

### Edit a leave request

1. Select the leave request that you want to edit, and then select **Edit leave**.
1. Update the leave request, and then submit it. If an approval workflow is associated with the leave type, it's submitted for approval again.

    To edit a single day in a leave request that includes more than one day, select the **Edit** button on the tile next to that day, and update the details. Then submit the request.

### Cancel a leave request

1. Select the leave request that you want to cancel, and then select **Delete leave**.
1. Select **Request cancellation**.

    To cancel a single day in a leave request that includes more than one day, select the **X** button on the tile next to that day, and then submit the request.

### Create a leave of absence request

1. Select **Request time off** or **Request leave of absence**.
1. Select the leave type, enter the start and end dates, and update the other details.

### View upcoming requests

- Expand **Leave details**, and select **Upcoming requests**.

    The app shows all draft leave requests in order of ascending date, followed by future leave requests in order of ascending date.

### View leave history

- Expand **Leave details**, and select **History**.

    The app shows all leaves that have an end date in the past.

### Approve or reject a leave request

Users who have the HR Manager or HR Absence manager role can use the Human Resources app to approve or reject leave requests for their direct reports on their team.

1. Expand **My team**, and select **Pending requests** to view open leave requests that are awaiting approval.
1. Select a leave request, and then select **Approve** or **Reject**.

## Troubleshooting

This section is for administrators of an organization that has installed the app.

- If installation fails, confirm that the finance and operations virtual entity solution and any available updates are installed.
- If you experience any data discrepancy, refresh the app to update it with the latest data.
- If you can't submit a leave request or approve a leave request, follow these steps:

    1. Sign in to the [Power Apps maker portal](https://make.powerapps.com/).
    1. Select **Tables**, and then select **Select all**.
    1. Search for the **Available finance and operations entity** table, and then select **Edit**.
    1. Under **Available finance and operations entity columns and data**, search for the **EssWorkflowWorkItemEntity** entity, and select it to edit it.
    1. Select **EssWorkflowWorkItemEntity**, and then select **Edit row using form**.
    1. Go to **General**, select the **Refresh** checkbox, and then select **Save**.
    1. Repeat steps d through f for each of the following entities:

        - EssLeaveBalanceEntity
        - EssLoaRequestEntity
        - EssLeaveRequestAttachmentEntity
        - MssLeaveRequestAttachmentEntity
        - EssLeaveRequestDetailEntity
        - EssTimeOffDetailApproverEntity
        - EssLoaRequestDetailApproverEntity
        - EssLeaveRequestHeaderEntity
        - EssLeaveTypeEntity
        - EssLeaveTypeReasonCodeEntity
        - MssHRTeamsAppPendingLoaEntity
        - MssHRTeamsAppPendingTimeoffEntity
        - EssWorkCalendarDayEntity
        - EssWorkerDetailEntity

### Submitting questions or feedback about the Human Resources app

The Human Resources App Viva Engage (Yammer) group is a great place to exchange tips, check on issues, and submit feedback to Microsoft. The group includes Microsoft partners, customers, experts, and employees.

### Supported languages

The Human Resources app supports all languages that Power Apps supports.
