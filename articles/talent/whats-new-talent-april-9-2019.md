---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (April 9, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
manager: AnnBe
ms.date: 4/9/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-04-09
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 for Talent (April 9, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Changes in Attract

### Lifecycle Services (LCS) integration with report a problem
In Attract and Onboard, problems logged by end users through the report a problem feature now automatically create support issues in the customer's LCS project. Admins can then triage the issues and submit them to Microsoft when needed. This is consistent with how Core HR handles end user support issues.

### Relevance search
Using the search under the Talent pools section, you can now search over your entire candidate database for particular skills, names or educational background. You no longer need to specify what section of the candidate's profile you want to search through. We search the entire profile and highlight all the matches we find. We also search over all documents available for a candidate and intelligently rank the search results. You can also filter the results by source or whether they are a silver medalist. Learn more [here](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/attract-talent-pools#search-and-view-candidate-profiles).

### Prospect recommendations
We can help kickstart sourcing for a job as soon as the job is activated by making intelligent candidate recommendations from your organization's candidate database in Attract. The recommendations will include the skills and education information that we identified when searching for relevant prospects. These recommendations will appear in the Prospects tab under a job, if it is enabled in the job's hiring process. Learn more [here](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/intelligent-recommendations#prospect-recommendations).

### Interviewer availability statuses
Interview schedulers will soon be able to view out of office, working elsewhere statuses for interviewers, thus helping them schedule times which may work better for interviewers.

### Candidate interview experience: save calendar invites
Candidates will now be able to download and save their interview events via an ics file to their personal calendars. This ics file is sent along with the interview summary e-mail sent to the candidate.

## Changes in Onboard

### Lifecycle Services (LCS) integration with report a problem
In Attract and Onboard, problems logged by end users through the report a problem feature now automatically create support issues in the customer's LCS project. Admins can then triage the issues and submit them to Microsoft when needed. This is consistent with how Core HR handles end user support issues.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2225.

### Percent of basis variable plans load incorrect amount (308254)
With this week’s release, a change has been made to correct an issue when loading variable compensation awards using percent of bases plans.
 
### Talent - Date picker on Last day worked doesn’t work correctly (301831)
This change corrects the issue: When users edit the Employment end date and the date is selected using the calendar control a day is added to the selection.

###  Limit personnel action types by the action taken (290094)
This change will limit the action types that appear when taking specific actions. For example: when a new position is requested only the new position actions will appear in the list of actions to select. Previously, both new and edit actions were available. 

### Transferring an employee with compensation in a second legal entity (288603)
This release will now allow compensation to be ended in a second legal entity if the transfer is for a cross company transfer.

### Unable to select compensation for a future Employment during a transfer (288606) 
When transferring an employee to a new legal entity you are now able to set compensation for the new legal entity during the transfer process.

### User is not able to assign compensation during position assignment (293600)
Adding a new position assignment will now allow for setting up fixed compensation records. 

## In preview

### Allow reason codes to be specified on leave types (244754)
Organizations might need additional information about time-off requests. You can now specify reason codes for leave types and enable employees to select a reason code on their time-off requests.

### Require reason codes for certain leave types on time-off requests (244756)
Organizations might require reason codes for specific leave types when employees submit time-off. This might be due to company policy or regulatory requirements. You can now specify which leave types require a reason code, and you can require employees to provide a reason code for the leave type on their time-off requests.

### Provide leave and absence transaction list for HR (170943)
Being able to track employee time off and understand how time off is being calculated helps HR to not only answer employee questions, but also ensure accurate time off awards are being given to employees. A new view into the transactions (grants, accruals, adjustments and requests) for HR is now available to see why balances are what they are. 

## Coming soon

### Improvements to the user interface for duplicate employee check (257821)
With this change, duplicates are detected as you enter name fields, and a status displays the number of duplicates found. You can select the provided link to open a new page to evaluate whether to use the detected match. To avoid interrupting data entry, the duplicates form doesn't automatically open.

###  Email support for alerts
With Platform update 25, users can create alert rules that automatically send email notifications to contacts when triggered by an event. 
