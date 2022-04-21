---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources 10.0.27 (June 2022) 
description: This topic describes features that are either new or changed in the Dynamics 365 Human Resources version 10.0.27 preview release.
author: twheeloc
ms.date: 04/07/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2022-04-22 
ms.dyn365.ops.version: 10.0.27

---

# Preview of Dynamics 365 Human Resources 10.0.27 (June 2022)

[!include [banner](../../includes/preview-banner.md)]

This topic lists features that are new or changed for Microsoft Dynamics 365 Human Resources version 10.0.27. This version has a build number of 10.0.1227 and is 
available as follows:


- **Preview of release**: April 2022
- **General availability of release (self-update)**: May 2022
- **General availability of release (auto-update)**: June 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this topic to include features that made it into the build after this topic 
was initially published.

| Feature name | Overview | Release status  |
|----|----|----|
|Recruit job candidates*|     |Preview     | 
|Absence manager to manage leave	|This feature enables users to be assigned an absence manager role who can manage leave requests and balances across departments and teams.	|GA|
|Balance adjustment reason code and comment (Leave)|	This feature allows human resources to include reason codes and comments when adjusting leave balances.|	GA|
|Buy and sell leave	|This feature allows users to buy and sell leaves.|	GA|
|Configure leave units per leave type**	|This feature enables administrators to configure leave units (hours or days) for each leave type. The leave types in that legal entity will be defaulted to the leave units from the leave parameters configuration at the legal entity level.	|GA|
|Configure multiple leave types on a single leave plan**|	This feature allows for leave types to be defined per row in the leave accrual schedule instead of per plan.	|GA|
|Configure required attachment for leave requests	|This feature enables admins to configure attachment to be required when submitting leave requests for specific leave types.	|GA|
|Cross company leave view|	This feature gives employees and managers the ability to see their leave records across all legal entities in which they are employed.|	GA|
|Leave accrual auditing|	This feature can be used to audit leave and absence accruals and deletions.|	GA|
|Leave accrual deletion|	This feature can be used to delete Leave Accruals.	|GA|
|Leave accrual for a single company or a single plan	|This feature allows processing leave accruals for a specific company or leave plan.|	GA|
|Leave accrual holiday corrections	|This feature can be used to subtract holidays from balances when accruing time off.	|GA|
|Leave accrual rounding	|This feature can be used to round prorated Leave Accruals.|	GA|
|Leave accrual transaction auditing|	This feature can be used to audit leave and absence accrual transactions.	|GA|
|Leave and absence accrual suspension|	This feature allows suspending a worker's leave accruals for a specified date range.|	GA|
|Leave and absence calendar|	This feature allows users to see employee time off in a calendar view.	|GA|
|Leave and absence calendar enhancements	|This feature allows users to see the leave and absence calendar enhancements.	|GA|
|Leave balance view enhancements	|This feature provides more insight into leave balances so employees and managers can find answers themselves.|	GA|
|Leave carry-forward rules	|This feature allows transferring carry-forward balance to another leave type and defining expiration rules for leave plan balance.|	GA|
|Leave request workflow experience enhancements	|This feature enables a more intuitive leave request workflow experience for users.|	GA|
|Update time off enhancements (Leave)	|This feature allows updating details of approved time off. It also adds a new page to view the time off requests that are associated with the time off for a particular calendar day.|	GA|
|Use an employee's FTE for accruals (Leave)	|This feature allows an employee's position full time equivalency to be used when calculating a leave and absence accrual.|	GA|
|Configure multiple compensation levels per job** 	|This feature allows for multiple compensation levels to be defined per job.|	GA|
|Human Resources user experience enhancements|	This feature brings enhancements to user experience flows across several Human Resources modules.|	GA|
|Streamlined employee entry|	This feature allows for efficient entry of employee and employment data. You can quickly update work history information for past, active, and future employees and contractors along with more intuitive navigation options.	|GA|
|Task management|	This feature provides the ability to create custom checklists and tasks for onboarding, offboarding and position changes for employees.|	GA|
|Benefits management| 	This feature enables benefits management.|	GA|
|Enable eligibility rules using custom fields in benefits management|	(Preview) This feature allows custom fields on the Worker, Job, Employment (and related tables) to be included in Eligibility Rules for Benefits Management.|	Preview|


* Human resources user experience enhancements must be turned on in Feature management.
* Recruiting process management must be turned on in Feature management.

## Enabling Human resources user experience enhancements feature

When using **Feature management** workspace to enable the Human resources capabilities as part of the infrastructure merge, the **Human resources user experience enhancements** (HRUX) feature must be enabled. 
The following features are required to be enabled prior to enabling the HRUX feature: 
 - Managers can view performance-related information for extended reports
 - (Preview) Task management
 - Future-dated worker transfer with cross company compensation
 - Configure multiple compensation levels per job**
 - Filter active positions
 
** Feature cannot be turned off once it has been enabled. 


## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these enhancements provides an incremental improvement to an existing feature. 
Because they are only enhancements, they are not listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). 

| Feature name | More information |  
|--------------|------------------|
| Display tasks on default dashboard     |A new option has been added to view the task list on the default dashboard. The task management feature must be on for the option to display.           | 
|  People search and people hub  | The **People** search and people hub are now available when the **Human Resources User Experience** switch is on. The user must have the **View the people hub workspace** privilege to see the **People hub**.  |
|Display tasks on default dashboard|	A new option has been introduced to view the task list on the default dashboard. The task management feature must be on for the option to display.|
|People search and people hub|	The people search and people hub are now available when the **Human resources user experience** switch is on. The user must have the **View the people hub workspace** privilege to see the **People hub**. |



## Known issues

| Issue summary | More information |
|---------------|------------------|
|Signing limits will not to work with multiple compensation levels|When the **Multiple compensation levels** feature is turned on, and the **Signing limit** parameter is set to **Compensation level**, the signing limits will not process. Issue #670843|
|Wrong leave type being used to determine half day definition	|When there are multiple leave types with the same name for different company, the half-day definition is not correctly enabled. Issue #660494|
|Main Account can’t be specified on the Earning code	|When the Human Resources user experience enhancement feature is turned on, the main account and the accounting tab for the earning code is not available. Issue #667727|
|Signing limits will not work with multiple compensation levels |When the **Multiple compensation levels** feature is turned on, and **Signing limit** parameters are set to the **Compensation level**, signing limits will not process. Issue #670843|

## Additional resources

### Platform updates for Finance and Operations apps
Dynamics 365 Finance 10.0.27 includes platform updates. To learn more, see [Platform updates for version 10.0.27 of Finance and Operations apps](../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-27.md). 

### Bug fixes 
For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=673217). 

