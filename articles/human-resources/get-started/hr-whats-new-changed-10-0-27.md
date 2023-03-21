---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources 10.0.27 (July 2022)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Human Resources version 10.0.27 preview release.
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

# What's new or changed in Dynamics 365 Human Resources 10.0.27 (July 2022)

[!include [banner](../../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Human Resources version 10.0.27. This version has a build number of 10.0.1227 and is available on the following schedule:

- **Preview of release:** April 2022
- **General availability of release (self-update):** June 2022
- **General availability of release (auto-update):** July 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature name | Overview | Release status |
|----|----|----|
| Recruit job candidates\* | This feature enables recruiting functionality, including recruiting requests and candidate profiles. Hiring managers can use **Manager self service** or **Personnel management** to create a recruiting request for a new worker. The feature also includes candidate records that are shown in **Personnel management**. | Preview |
| Absence manager to manage leave | This feature enables an absence manager role to be assigned to users so that they can manage leave requests and balances across departments and teams. | General availability (GA) |
| Balance adjustment reason code and comment (Leave) | This feature enables Human resources to include reason codes and comments when leave balances are adjusted. | GA |
| Buy and sell leave | This feature lets users buy and sell leaves. | GA |
| Configure leave units per leave type\*\* | This feature lets administrators configure leave units (hours or days) for each leave type. By default, the leave units from the leave parameters configuration at the legal entity level will be used for the leave types in that legal entity. | GA |
| Configure multiple leave types on a single leave plan\*\* | This feature enables leave types to be defined per row instead of per plan in the leave accrual schedule. | GA |
| Configure required attachment for leave requests | This feature lets admins configure attachments that are required when leave requests are submitted for specific leave types. | GA |
| Cross company leave view | This feature lets employees and managers view their leave records across all legal entities where they are employed. | GA |
| Leave accrual auditing | This feature can be used to audit leave and absence accruals and deletions. | GA |
| Leave accrual deletion | This feature can be used to delete leave accruals. | GA |
| Leave accrual for a single company or a single plan | This feature enables leave accruals to be processed for a specific company or leave plan. | GA |
| Leave accrual holiday corrections | This feature can be used to subtract holidays from balances when time off is accrued. | GA |
| Leave accrual rounding | This feature can be used to round prorated leave accruals. | GA |
| Leave accrual transaction auditing | This feature can be used to audit leave and absence accrual transactions. | GA |
| Leave and absence accrual suspension | This feature enables a worker's leave accruals to be suspended for a specified date range. | GA |
| Leave and absence calendar | This feature lets users view employee time off in a calendar view. | GA |
| Leave and absence calendar enhancements | This feature lets users view the leave and absence calendar enhancements. | GA |
| Leave balance view enhancements | This feature provides more insight into leave balances so that employees and managers can find answers for themselves. | GA |
| Leave carry-forward rules | This feature enables carry-forward balances to be transferred to another leave type and expiration rules to be defined for leave plan balances. | GA |
| Leave request workflow experience enhancements | This feature enables a more intuitive leave request workflow experience for users. | GA |
| Update time off enhancements (Leave) | This feature enables details of approved time off to be updated. It also adds a new page that shows the time-off requests that are associated with the time off for a specific calendar day. | GA |
| Use an employee's FTE for accruals (Leave) | This feature enables an employee's position full-time equivalency to be used when a leave and absence accrual is calculated. | GA |
| Configure multiple compensation levels per job\*\* | This feature enables multiple compensation levels to be defined per job. | GA |
| Human Resources user experience enhancements | This feature brings enhancements to user experience flows across several Human resources modules. | GA |
| Streamlined employee entry | This feature enables efficient entry of employee and employment data. You can quickly update work history information for past, active, and future employees and contractors. The feature also provides more intuitive navigation options. | GA |
| Task management | This feature enables custom checklists and tasks to be created for onboarding, offboarding, and position changes for employees. | GA |
| Benefits management | This feature enables benefits management. | GA |
| Enable eligibility rules using custom fields in benefits management | (Preview) This feature enables custom fields on the worker, job, and employment (and related tables) to be included in eligibility rules for benefits management. | GA |

\* Human resources user experience enhancements must be turned on in Feature management.

\*\* Recruiting process management must be turned on in Feature management.

## Enabling the Human resources user experience enhancements feature

When you use the **Feature management** workspace to enable the Human resources capabilities as part of the infrastructure merge, the **Human resources user experience enhancements** feature must be enabled.

The following features must be enabled before the **Human resources user experience enhancements** feature:

- Managers can view performance-related information for extended reports
- Task management
- Future-dated worker transfer with cross company compensation
- Configure multiple compensation levels per job\*
- Filter active positions

\* This feature can't be turned off after it has been enabled.

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature name | More information |
|--------------|------------------|
| Display tasks on default dashboard | A new option has been added to show the task list on the default dashboard. The task management feature must be on for the option to be shown. |
| People search and people hub | The **People** search and people hub are now available when the **Human Resources User Experience** switch is on. The user must have the **View the people hub workspace** privilege to see the people hub. |

## Known issues

| Issue summary | More information |
|---------------|------------------|
| Signing limits won't work with multiple compensation levels. | When the **Multiple compensation levels** feature is turned on, and the **Signing limit** parameter is set to **Compensation level**, the signing limits won't be processed. Issue #670843. |
| The wrong leave type is being used to determine the half-day definition | If multiple leave types use the same name for different companies, the half-day definition isn't correctly enabled. Issue #660494. |
| A main account can't be specified on the earning code. | When the **Human Resources user experience enhancement** feature is turned on, the main account and the **Accounting** tab for the earning code aren't available. Issue #667727. |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance 10.0.27 includes platform updates. To learn more, see [Platform updates for version 10.0.27 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-27.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=673217).

## LCS updates

| Feature name | Overview | Release status |
|----|----|----|
| Deploy Dynamics 365 Human Resources by using Finance and Operations LCS projects | If you've purchased the minimum required licenses for Dynamics 365 Human Resources, you can now deploy new LCS projects and environments by using the **Implementation** project type and selecting **Finance and operations** as the product in LCS. For more information, see [Provision Human Resources in the finance and operations infrastructure](../hr-admin-setup-provision-fo.md). | June 2022 |
| Prevention of deploying production environments in Human Resources LCS projects | If you have an existing Human Resources LCS project, you can no longer deploy a production environment in it. Instead, you must create a new finance and operations LCS project and follow the standard process to deploy a production environment. | June 2022 |

