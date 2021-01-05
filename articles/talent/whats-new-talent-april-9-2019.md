---
# required metadata

title: What's new or changed in Dynamics 365 Talent (April 9, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 04/09/2019
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
# ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-04-09
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (April 9, 2019)

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract

### Lifecycle Services (LCS) integration with 'report a problem'
In Attract and Onboard, issues logged by end users using the report a problem feature now automatically create support issues in the customer's LCS project. Admins can then triage the issues and submit them to Microsoft when needed. This is consistent with how Core HR handles end user support issues.

### Relevance search
In talent pools, you can now search your entire candidate database for particular skills, names, or educational background. You no longer need to specify which section of a candidate's profile you want to search through. Attract searches the entire profile and highlights all the matches found. Attract also searches all documents that are available for a candidate and intelligently ranks the search results. In addition, you can filter the results by source or by whether they are a silver medalist. For more information, see [Search and view candidate profiles](https://docs.microsoft.com/dynamics365/unified-operations/talent/attract-talent-pools#search-and-view-candidate-profiles).

### Prospect recommendations
Attract can help kickstart sourcing for a job as soon as you activate it by making intelligent candidate recommendations from your organization's candidate database. The recommendations include the skills and education information identified while searching for relevant prospects. These recommendations appear on the **Prospects** tab under a job, if you enable it during the job's hiring process. For more information, see [Prospect recommendations](https://docs.microsoft.com/dynamics365/unified-operations/talent/intelligent-recommendations#prospect-recommendations).

### Interviewer availability statuses
Interview schedulers will soon be able to view **Out of office, working elsewhere** statuses for interviewers, to help schedule times that might work better for interviewers.

### Candidate interview experience: Save calendar invites
Candidates can now download and save their interview events to their personal calendars using an .ics file attached to the interview summary email sent to the candidate.

## Changes in Onboard

### Lifecycle Services (LCS) integration with report a problem
In Attract and Onboard, issues logged by end users using the report a problem feature now automatically create support issues in the customer's LCS project. Admins can then triage the issues and submit them to Microsoft when needed. This is consistent with how Core HR handles end user support issues.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2225.

### Percent of basis variable plans load incorrect amount
This week’s release corrects an issue when loading variable compensation awards using percent of basis plans.
 
### Date picker on Last day worked doesn’t work correctly
This change corrects the issue: When users edit the **Employment end date** and select the date using the calendar control, a day is added to the selection.

###  Limit personnel action types by the action taken
This change limits the action types that appear when taking specific actions. For example, when a new position is requested, only the new position actions appear in the list of actions to select. Previously, both new and edit actions appeared. 

### Transferring an employee with compensation in a second legal entity
This release allows compensation to be ended in a second legal entity if the transfer is for a cross-company transfer.

### Unable to select compensation for a future employment during a transfer
When transferring an employee to a new legal entity, you can now set compensation for the new legal entity during the transfer process.

### User isn't able to assign compensation during position assignment
Adding a new position assignment now allows setting up fixed compensation records. 

## In preview

### Allow reason codes to be specified on leave types
Organizations might need additional information about time-off requests. You can now specify reason codes for leave types and enable employees to select a reason code on their time-off requests.

### Require reason codes for certain leave types on time-off requests
Organizations might require reason codes for specific leave types when employees submit time off. This might be due to company policy or regulatory requirements. You can now specify which leave types require a reason code, and you can require employees to provide a reason code for the leave type on their time-off requests.

### Provide leave and absence transaction list for HR
Tracking employee time off and understanding how time off is calculated not only helps HR answer employee questions, but also ensures accurate time off awards for employees. HR now has a new view into the transactions (grants, accruals, adjustments, and requests) to see the reasons behind balances. 

## Coming soon

### Improvements to the user interface for duplicate employee check
With this change, duplicates are detected as you enter name fields, and a status displays the number of duplicates found. You can select the provided link to open a new page to evaluate whether to use the detected match. To avoid interrupting data entry, the duplicates form doesn't automatically open.

###  Email support for alerts
With Platform update 25 for Finance and Operations, users can create alert rules that automatically send email notifications to contacts when triggered by an event. 
