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

Human Resources (preview) is an app that is integrated with Dynamics 365 Human Resources on the finance and operations environment. It is designed and developed for organizations to ensure their employees can 
request, edit, and cancel time off and leave of absence requests seamlessly. Employees can now view their leave balances, upcoming leaves and leave history using the same application. In addition to this, 
Managers can also efficiently view and approve or reject requests in one intuitive interface.

The application is designed to be used within Microsoft Teams or in a web browser and it provides an overall view of employees leave requests, leave balances, draft leave requests, leave requests taken in the 
past. The Human Resources app can be used both on Mobile and Desktop. Administrators of an organization would need to install the Human Resources app and share it to Microsoft Teams for the users of the 
organization to be able to use the same.

>[!Note:]
>There would be updates for the Human Resources app that are being made available that could fix possible bugs or could be feature enhancements and hence, its not encouraged to perform any customizations on the
>app as the updates might break them and would not work as expected. 

### Install Human Resources application

Pre-requisites
•	Dynamics 365 finance and operations environment should be of version 10.0.36 or above with latest quality update.
o	Please note to make sure the latest quality update is installed.
o	Follow the steps to update the quality updates.
•	License to Dynamics 365 Human Resources on a Dynamic 365 finance and operations environment
•	User who is installing the app for the organization needs to have system administrator roles in both Dynamic 365 Human Resources in Dynamics 365 finance and operations environment and in Microsoft Power Apps


Steps to install Human Resources for the first time
1.	In the Power Platform admin center (https://admin.powerplatform.microsoft.com), after logging in as the admin, select ‘Environments’ from the left navigation panel and search for your environment and select it by clicking on it. 
2.	As a pre-requisite, you need to make sure to enable ‘Power Apps component framework for canvas apps’ using the following steps, 
After choosing the correct environment as mentioned in Step 1
a.	Go to ‘Settings’.
b.	Expand ‘Product’ section and click on ‘Features’
c.	Search for section ‘Power Apps component framework for canvas apps’ and enable it using the toggle button (Allow publishing of canvas apps with code components) and click on ‘Save’
3.	Click the link Human Resources App V2 to access the V2 app.
a.	Click on ‘Get it now’. This will be redirected to Power Platform Admin Center installation page. 
b.	Sign in using the same user and select your environment and click on ‘Install’.
c.	Wait until the installation is completed and the Status changes to ‘Installed’ from ‘Installing’ - for Dynamics 365 Human Resources.
d.	Status could be checked under Environments >> (Environment name) >> Dynamics 365 apps (under Resources section) in Power Platform Admin Center.
e.	If installation fails, try installing again using the ‘Retry installation’ option in the Power Platform admin center.
Note: Check the Mandatory Checks section after installation.

### Update the Human Resources app 
Note : This section would also help if you have installed a previous version Human Resources app and if you need to update it to the enhanced version of the Human Resources app,
1.	Go to Power Platform Admin Center >> Environments >> (Environment name) >> Dynamics 365 apps (under Resources section)
2.	Check for Update available in the status column for Dynamics 365 Human Resources and select on it and click on ‘Update’ to update the app. 
3.	If installation fails, try installing again using the ‘Retry installation’ option in the Power Platform admin center.
Steps to embed the Human Resources app to Microsoft Teams: Use the documentation Embed a model-driven app as personal app in Teams to add the Human Resources app to Microsoft Teams.

Note: The Human Resource app can also be used on a browser without having to be added to Microsoft Teams
 
### Onboard users to Human Resources app:

1.	End users of the app should have the following roles in the Power Platform,
a.	Basic User
b.	Finance and Operations Basic User
c.	Human Resources Teams App User

2.	End users should be assigned with employee role in the D365 Human Resources finance and operation environment. 


### Create, update, and cancel leave requests using the Human Resources app

View Available Balances
1.	Expand Leave Details on the left pane and click on Available Balances
2.	This would show the available balances tiles for the various leave plans assigned to the user logged in.
3.	You could also request leaves directly from the tiles using the Request button present in each tile

Request Leaves
1.	Leave requests can be created either from the Available Balances tiles shown in the previous section or using the ‘+Request Time off’ button on the top right corner. 
2.	Click the ‘+Request Time Off’ button and a new screen will appear where the details like Leave Type, Reason Code (if mandatory), Start Date and End Date must be entered.
3.	Click ‘+Add’ button.
4.	The number of days selected would appear in the Selected Dates section.
5.	Click on Edit Days present in the Selected Dates section to update the details of the dates i.e. if you need to change the number of hours or request for half day leaves etc.
6.	Click on Edit Day if you need to change the number of hours or request for half day leaves or use the bin icon on the date tiles to remove a particular date from the date range. 
7.	Click ‘Save’ once all the changes are updated.
8.	Add any comments and attachments if needed and click on ‘Next’.
9.	Review all the details of the leave request that you are requesting and click on ‘Submit’.
10.	Leave request can also be saved as draft using the ‘Save as draft’ option or the action can be cancelled by clicking on ‘Cancel’ button.
11.	You can also view the drafts, or the leave request submitted in the Upcoming Leaves section.


Edit Leave requests
1.	Select the leave request to be edited, click on Edit Leave.
2.	Update the leave request as needed and submit the same.
Note: If there is an approval workflow associated with the leave type, then it will go for an approval again.
3.	To edit a single day in a leave request with more than one day, select the edit icon present in the tile beside the day that needs to be edited, update the details, and submit the request.


Cancel Leave requests
1.	Select the leave request to be cancelled, click on Delete Leave, and then click on Request Cancellation.
2.	To cancel a single day in a leave request with more than one day, select the ‘X’ icon present in the tile beside the day that needs to be edited and submit the request.


Create Leave of absence requests
1.	On the top right corner of the screen, click on the drop down beside ‘+ Request Time off’, there would be an option ‘+ Request Leave of Absence’.
2.	Select the ‘Leave Type’, enter the ‘Start Date’, ‘End Date’ and update the other details like comments, attachments.


View Upcoming requests
1.	Expand Leave Details on the left pane and click on Upcoming Requests
2.	This section will show all the draft leave requests in an ascending order of dates followed by the future leave requests in ascending order. 


View History
1.	Expand Leave Details on the left pane and click on History.
2.	This section will show all the leave that has an end date in the past.  


Approve or Reject leave requests: Managers can now approve or reject leave requests of their direct reports using this functionality on the Human Resources app.
1.	This functionality is for users with HR Manager role, HR Absence manager role. 
2.	Expand the My team section and click on Pending requests to see if there are any open leave requests that are awaiting an approval.
3.	Click on the leave request and click on Approve or Reject the request.

Troubleshooting: 
This section is for the Administrators of the organization who has installed the application.
• If installation fails, make sure Finance and Operations virtual entity solution is installed with 
updates if available. 
• If there is any data discrepancy that you experience, try to refresh the app and that should 
update the latest data.
• Incase you are not able to run a process using the app i.e. either submit a leave request or approve a leave request, it also could be that the entity is not refreshed. To solve this follow the below steps,
a. Go to Maker Portal (https://make.powerapps.com) 
b. Click on Tables on the left pane >> Select All >> and search for the table ‘Available 
Finance and Operations Entity’ >> click on Edit 
c. In the section Available Finance and Operations Entity columns and data, search 
for the entity ‘EssWorkflowWorkItemEntity’ and click on it to open it in edit mode.
d. Select the ‘EssWorkflowWorkItemEntity’ and click on ‘Edit row using form’ which 
opens a new section.
e. Goto General >> Click the checkbox beside Refresh >> Click Save
f. Follow similar steps c,d and e for the below entities aswell,
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

Supported languages
•	The Human Resources app supports all languages Power Apps supports and can be found here.  

Where can I ask questions or submit feedback about the app? 
•	The Human Resources App Viva Engage (Yammer) group is a great place to exchange tips, check on issues, submit feedback to Microsoft. Yammer group includes Microsoft partners, customers, experts, and employees.

