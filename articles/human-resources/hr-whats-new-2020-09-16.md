---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (September 16, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 9/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2020-09-08
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (September 8, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3557. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## New Platform functionality (Platform 37)
Saved views is generally available with this release. 

### Uptake new Default Financial Dimensions grid and dialog pattern throughout D365HR - (469495)

This release updates the user interface when adding default financial dimensions on the position actions form.  The dimensions grid has been updated and a new dialogue has been introduced.

### Benefits screens don’t take into consideration the Restrict access to worker information parameter - (393384)

With this release, if the Restrict access to worker information is set to yes in Advanced access in Human Resources Shared parameters, benefit screens will only show the appropriate workers. 
### Calendar Generation Options are not available in the WorkCalendarEntity - (477055)

With this release the following fields were added to the WorkCalendar entity:
-	Default ending time
-	Default starting time
-	Is Friday working day
-	Is Monday working day
-	Is Saturday working day
-	Is Sunday working day
-	Is Thursday working day
-	Is Tuesday working day
-	Is Wednesday working day
-	Work calendar holiday ID

### LeaveBankTransactionV1 Entity not populating actual reasoncodeID value - (477823)

This release includes the reason code in the LeaveBankTransactionV1 entity. 

### Saving of task recording in LCS isn’t possible - (492923)

With this release, task recordings can now be saved. 

### Data loss while publishing data using Excel Connector with the entity HcmWorkerContactEntity - (427620)

With this release, data is published successfully from the HCMWorkerContactEntity. 

### Personnel action for a Contractor incorrectly hides compensation fast tab after saving - (482494)

This release corrects the issue where adding a worker type of contractor, the compensation fast tab was not visible in the Worker Actions form. With this fix, the interface will display the compensation fast tab in this scenario.  

### No error thrown on attempting to complete hire action if fixed compensation action is set, but level and plan are blank - (482497)

With this release, level and plan are now marked as mandatory in the user experience along with providing an error message. 

### When creating new benefit plan, plan type field is no longer a drop list - (488768)

With this release, the plan type field is now a drop list. 

### Removal of custom fields from HR does not alert that CDS custom field is also not removed - (481408)

With this release, system administrators will receive a notification if a custom field is deleted from Dynamics 365 Human Resources. 

### Terminate employee process experiencing performance issues - (479877)

With this release, the application will behave as expected and not change the selected company after appearing to lock for a period of time. 

### Identification numbers expiring for my team – manager is able to add a Number column - (485317)

With this release, managers can’t add the number column through personalization. 

### Identification numbers expiring for my team – manager is able to remove the data range filter - (485321)

With this release, managers can’t remove the filter from identification numbers expiring. 

### Hover over position assigned to employee is empty in case the position in "reports to" is not assigned to any worker - (433328)

With this release, even if the reports to field is empty, the position details are still displayed when hovering over the position. 

### Information regarding the Benefit plan not available in ESS for user only with Employee role. - (481676)

With this release, employees can view benefit plan information. 

### An employee registered to a course from another company cannot see the next registered course in his employee self-service - (429048)

With this release, employees can see all registered courses. 

### Filter Professional Certificates page - (451501)

This release updates the user interface to have additional viewing options to restrict to the current legal entity, by worker status and by worker type. 

## In Preview

### Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see:

- [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) in the Dynamics 365 2020 release wave 1 plan
- [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841) in Human Resources documentation

### Human Resources app in Teams preview features
 
-  **Notifications**: Submitters and approvers of time-off requests will be notified in the Human Resources app in Teams. Approvers will be able to approve or deny time-off requests. Submitters will be notified if the request was approved or denied. For more information, see:
   - [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/employee-leave-absence-experience-teams) in the Dynamics 365 2020 release wave 2 plan
   - [Enable notifications for the Human Resources app in Teams](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-teams-leave-app#enable-notifications-for-the-human-resources-app-in-teams) in Human Resources documentation
   - [Turn Teams notifications on or off for individual users](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-teams-leave-app#turn-teams-notifications-on-or-off-for-individual-users) in Human Resources documentation
   - [Teams notifications](https://docs.microsoft.com/dynamics365/human-resources/hr-teams-leave-app#teams-notifications) in Human Resources documentation
   - [View your team's leave calendar](https://docs.microsoft.com/dynamics365/human-resources/hr-teams-leave-app#view-your-teams-leave-calendar) in Human Resources documentation
 
- **Manager time-off calendar**: Managers will be able to see approved and pending time off for their direct reports in a calendar view. This view provides an easy understanding of when their team members are away from work. For more information, see:
   - [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/employee-leave-absence-experience-teams) in the Dynamics 365 2020 release wave 2 plan
   - [View your team's leave calendar](https://docs.microsoft.com/dynamics365/human-resources/hr-teams-leave-app#view-your-teams-leave-calendar) in Human Resources documentation

### Configuration option to position Work items assigned to me list (477004)

A new option is now available to position the **Work items assigned to me** list in the right-hand column of the dashboard. With this change, all work items and to do lists display in the same area. Enable this functionality by turning on **Preview - Workflow experience enhancements** in Feature management. For more information about turning on preview features, see [Manage features](hr-admin-manage-features.md).

This feature also promotes the workflow options that appear in the personnel actions forms. Workflow options also appear above the action fast tab for quick access. For more information, see: 

- [Organization and personnel management workflow experience enhancements](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/organization-personnel-management-workflow-experience-enhancements) in the Dynamics 365 2020 release wave 2 plan

![Work items assigned to me](./media/hr-workflow-work-items-assigned-to-me.png)

![Workflow items quick access](./media/hr-workflow-quick-access.png)

### Leave and absence calendar

Additional calendar options for leave and absence calendars [View team and company calendars] (https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-employee-self-service-calendar)

## Coming Soon

### Checklist entities included in Common Data Service

Checklist entities for Onboarding, Offboarding, Transfers, and Business processes will be available soon in Common Data Service.

### Benefits management reason codes

Benefits management reason codes will soon be combined with existing reason codes in Human Resources. If you created reason codes in Benefits management that are over 15 characters, you must change the name of the reason code in the Benefits management **Reason codes** form to be 15 characters or less. After you update the name, the reason code will appear under the existing reason code form in Personnel management. This change will be available in the future and won't affect existing functionally.

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
