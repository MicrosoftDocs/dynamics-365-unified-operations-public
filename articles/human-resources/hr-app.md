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

## Dynamics 365 Human Resources (preview) app 

Human Resources (preview) is an app that integrates with Dynamics 365 Human Resources on the finance and operations environment. It's designed and developed for organizations to ensure their employees can 
request, edit, and cancel time off and leave of absence requests seamlessly. Employees can view their leave balances, upcoming leaves and leave history. Managers can also view and approve or reject requests.

The application is used within Microsoft Teams or in a web browser and provides an overall view of employees leave requests, leave balances, draft leave requests, leave requests taken in the past. The Human Resources app can be used both on mobile and desktop. Administrators of an organization need to install the Human Resources app and share it to Microsoft Teams for the organization users to use.

>[!Note:]
>There will be updates for the Human Resources app that will be available, it's not recommended to customize the app.  

### Install Human Resources 

Before you install the Human Resources app, the following prerequisites are required:
 - Dynamics 365 finance and operations environment version 10.0.36 or later with latest quality update.
 - Confirm the latest quality update is installed and follow the steps to install the quality update.
 - License to Dynamics 365 Human Resources on a Dynamics 365 finance and operations environment.
 - The user who is installing the app for the organization needs to have system administrator roles in both Dynamic 365 Human Resources in Dynamics 365 finance and operations environment and in Microsoft Power Apps.


To install Human Resources for the first time, follow these steps:
1.	In the Power Platform admin center (https://admin.powerplatform.microsoft.com), log in as the admin.
2.	Select **Environments** and search for your environment and select it. 
3.	Confirm that **Power Apps component framework for canvas apps**.  
After choosing the correct environment as mentioned in Step 1
    a.	Go to **Settings**, expand **Product** section and click **Features**.      	
    b.	Search for **Power Apps component framework for canvas apps** and enable it.
  	 c. Click **Save**.
4.	Click **Human Resources App V2**.
5.	Click **Get it now** and sign into the Power Platform Admin Center installation page. 
6.	Select your environment and click **Install**.
7.	After the installation is completed and the status changes to **Installed** for Dynamics 365 Human Resources. You can check the status by going to the Power Platform Admin Center. **Environments** > **(Environment name)** > **Dynamics 365 apps** (under Resources section). If the installation fails, try installing again using **Retry installation** in the Power Platform admin center.

>[!Note:]
>Check the Mandatory Checks section after installation.

### Update the Human Resources app 

This section will also help if the previous version Human Resources app is installed and you need to update it to the enhanced version.

1.	Go to Power Platform Admin Center. **Environments** > **(Environment name)** > **Dynamics 365 apps** (under Resources section).
2.	Check for available updates in the **Status** column for Dynamics 365 Human Resources. Select it and click **Update**. 
3.	If installation fails, try installing again using **Retry installation** option in the Power Platform admin center.

To embed the Human Resources app in Microsoft Teams, see (Embed a model-driven app as personal app in Teams)[../../power-apps/teams/embed-model-driven-teams-personal.md).
The Human Resource app can also be used on a browser. 
 
### Onboard users to Human Resources app

To onboard users to the Human Resources app, follow these steps:
1.	Users of the app should have the following roles in Power Platform:
 - Basic user
 - Finance and operations basic user
 - Human Resources Teams app user
2.	End users should be assigned with employee role in the Dynamics 365 Human Resources finance and operations environment. 


### Create, update, and cancel leave requests using the Human Resources app

View Available Balances
1.	Expand **Leave details** and click **Available balances**.
2.	This displays the available balances tiles for the various leave plans assigned to the user logged in.
3.	You could also request leaves directly from the tiles using the **Request** button present in each tile.

To request leave, follow these steps: 
1.	Leave requests can be created either from the **Available balances** tile or the **+Request time off** button. 
2.	Click **+Request time off**. A new page displays details like **Leave type**, **Reason code**, **Start date** and **End date** must be entered.
3.	Click **+Add**.
4.	The number of days selected appear in **Selected dates**.
5.	Click **Edit days present** in the **Selected dates** section to update the details of the dates. For example, if you need to change the number of hours or request for half day leaves.
6.	Click **Edit day** to change the number of hours, request for half day leaves or use the bin icon on the date tiles to remove a particular date from the date range. 
7.	Click **Save** after all the changes are updated.
8.	Add any comments and attachments if needed and click **Next**.
9.	Review the details of the leave request and click **Submit**.
10.	Leave requests can be saved as draft using the **Save as draft** option or the action can be cancelled by clicking **Cancel**.
11.	You can also view the drafts, or the leave request submitted in **Upcoming leaves**.


To edit leave requests, follow these steps:
1.	Select the leave request, click **Edit leave**.
2.	Update the leave request as needed and submit. If there is an approval workflow associated with the leave type, then it will be submitted for approval again.
3.	To edit a single day in a leave request with more than one day, select the edit icon in the tile beside the day that needs to be edited, update the details, and submit the request.


To cancel leave requests, follow these steps:
1.	Select the leave request to be cancelled, click **Delete leave**.
2.	Click **Request cancellation**.
3.	To cancel a single day in a leave request with more than one day, select **X** in the tile beside the day that needs to be edited and submit the request.


To create leave of absence requests, follow these steps:
1.	Click **+ Request time off** or **+ Request leave of absence**.
2.	Select the **Leave type**, enter the **Start date**, **End date** and update the other details.


To view upcoming requests:
1.	Expand **Leave details** and click **Upcoming requests**.
2.	All the draft leave requests will be displayed in an ascending order of dates followed by the future leave requests in ascending order. 


To view leave History:
1.	Expand **Leave details** and click **History**.
2.	All leaves that have an end date in the past will be displayed.  


Managers can now approve or reject leave requests for their direct reports using the Human Resources app. Users with HR Manager role, HR Absence manager role can approve or reject leave requests for their team. 

To approve or reject leave requests: 
Managers can now approve or reject leave requests for their direct reports using the Human Resources app. Users with HR Manager role, HR Absence manager role can approve or reject leave requests for their team. 
1. Expand **My team** and click **Pending requests** to view open leave requests that are awaiting an approval.
2.	Click the leave request and click **Approve** or **Reject**.

### Troubleshooting

This section is for the Administrators of the organization who has installed the application.
 - If the installation fails, confirm the finance and operations virtual entity solution is installed with updates if available.
 - If you experience any data discrepancy, refresh the app and to update the latest data.
 - If you're not able to either submit a leave request or approve a leave request, it could be that the entity isn't refreshed. Follow these steps:
a. Go to the Maker Portal (https://make.powerapps.com) 
b. Click **Tables** > **Select all**. Search for the **Available finance and operations entity**, click **Edit**. 
c. In **Available finance and operations entity columns and data**, search for **EssWorkflowWorkItemEntity** entity and click on it to open it in edit mode.
d. Select **EssWorkflowWorkItemEntity** and click **Edit row using form**.
e. Go to **General**. Select **Refresh** checkbox and click **Save**.
f. Follow c, d and e steps for the following entities:
•	EssLeaveBalanceEntity
•	EssLoaRequestEntity 
•	EssLeaveRequestAttachmentEntity                    
•	MssLeaveRequestAttachmentEntity
•	EssLeaveRequestDetailEntity
•	EssTimeOffDetailApproverEntity
•	EssLoaRequestDetailApproverEntity
•	EssLeaveRequestHeaderEntity
•	EssLeaveTypeEntity
•	EssLeaveTypeReasonCodeEntity
•	MssHRTeamsAppPendingLoaEntity
•	MssHRTeamsAppPendingTimeoffEntity
•	EssWorkCalendarDayEntity
•	EssWorkerDetailEntity

Where can I ask questions or submit feedback about the app? 
The Human Resources App Viva Engage (Yammer) group is a great place to exchange tips, check on issues, submit feedback to Microsoft. Yammer group includes Microsoft partners, customers, experts, and employees.

#### Supported languages
The Human Resources app supports all languages Power Apps supports and can be found here. 
