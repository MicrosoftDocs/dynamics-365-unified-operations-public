---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources 10.0.36 (October 2023)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Human Resources version 10.0.36 preview release.
author: twheeloc
ms.date: 07/28/2023
ms.topic: whats-new
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
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.36

---

# What's new or changed in Dynamics 365 Human Resources 10.0.36 (October 2023)

[!include [banner](../../includes/preview-banner.md)]

This article lists features that are new or changed for Dynamics 365 Human Resources version 10.0.36. This version has a build number of 10.0.1695 and is available on the following schedule:

- **Preview of release:** July 2023
- **General availability of release (self-update):** September 2023
- **General availability of release (auto-update):** October 2023

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature name | More information |
|--------------|------------------|
| Configure working time for service level agreements in Case management | When this feature is enabled, it helps organizations determine service level agreements (SLAs), based on the working time that's set in the calendar. When this feature is disabled, calendar days are considered even if the working time is set. |

## Features turned on by default in this release

The following table lists the features that are turned on by default or are now mandatory in version 10.0.36. Most features that have been turned on automatically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory. This change is made to ensure that customers are using current functionality. In this way, as enhancements are added, they can build on the current functionality. Features will never be automatically enabled in less than one year, unless they're determined to be essential.

| Feature name | Enable date | Feature state | Module |
|--------------|-------------|---------------|--------|
| Payroll integration | July 22, 2023 | Mandatory | Human Resources |
| Years of service calculation | July 22, 2023 | Mandatory | Human Resources |
| Advanced address maintenance | July 23, 2023 | On by default | Global address book |
| Enable translation for the Country/Region component of the Russian address format | July 23, 2023 | Mandatory | Global address book |
| Disable Russian address format validation | July 23, 2023 | Mandatory | Global address book |
| (Russia) Import addresses from the State address register (GAR) | July 23, 2023 | On by default | Global address book (Tax) |
| Benefits bulk update page redesign | July 23, 2023 | Moved from preview to GA | Human Resources |
| Cross company compensation view | July 23, 2023 | On by default | Human Resources |
| Recruiting process management | July 23, 2023 | On by default | Human Resources |
| Custom links in Manager self service | July 23, 2023 | Mandatory | Human Resources |
| Allow proration of benefit plan contributions | July 23, 2023 | Moved from preview to GA | Human Resources |
| Benefits Compare Selections | July 23, 2023 | Moved from preview to GA | Human Resources |
| View all workers without employments|  | Mandatory| Personnel Management| 
|Worker header control| |On by default |Personnel Management |
|Years of service calculation| |Mandatory |Personnel Management| 
|Workflow experience enhancements| |Mandatory |Personnel Management| 
|Set job description on the **Position** and **Forecast position** pages be read-only|	7/22/2023|	On by default|	Human Resources|
|Absence manager to manage leave|	7/22/2023|	Mandatory	|Human Resources|
|Configure required attachment for leave requests|	7/22/2023|	Mandatory|	Human Resources|
|Cross company leave view	|7/22/2023	|Mandatory|	Human Resources|
|Leave accrual auditing	|7/22/2023|	Mandatory|	Human Resources|
|Leave accrual deletion	|7/22/2023	|Mandatory	|Human Resources|
|Leave accrual for a single company or a single plan	|7/22/2023|	Mandatory|	Human Resources|
|Leave accrual holiday corrections	|7/22/2023	|Mandatory|	Human Resources|
|Leave accrual rounding	|7/22/2023|	Mandatory|	Human Resources|
|Leave accrual transaction auditing	|7/22/2023|	Mandatory|	Human Resources|
|Leave and absence calendar	|7/22/2023|	Mandatory|	Human Resources|
|Leave and absence calendar enhancements	|7/22/2023|	Mandatory	|Human Resources|
|Leave balance view enhancements	|7/22/2023	|Mandatory	|Human Resources|
|Leave request workflow experience enhancements	|7/22/2023|	Mandatory|	Human Resources|
|Update time off enhancements (Leave)	|7/22/2023|	Mandatory|	Human Resources|
|Use an employee's FTE for accruals (Leave)|	7/22/2023|	Mandatory|	Human Resources|
|Inclusion of weekends and holidays for leave and absence|	7/22/2023|	Released|	Human Resources|
|Hide leave balances	|7/22/2023|	Released|	Human Resources|
|Absence manager to manage leave of absence requests|	7/22/2023|	Released|	Human Resources|
|View all workers without employment|	7/22/2023|	Mandatory|	Human Resources|
|Worker header control	|7/22/2023|	On by default|	Human Resources|
|Payroll integration|	7/22/2023|	Mandatory|	Human Resources|
|Years of service calculation|7/22/2023|	Mandatory	|Human Resources|
|Advanced address maintenance|	7/23/2023|	On by default	|Global Address Book|
|Enable translation for the Country/Region component of the Russian address format	|7/23/2023|	Mandatory	|Global Address Book|
|Disable Russian address format validation	|7/23/2023|	Mandatory	|Global Address Book|
|(Russia) Import addresses from the State Address Register (GAR)	|7/23/2023|	On by default	|Global Address Book (Tax)|
|**Benefits bulk update** page redesign|	7/23/2023|	Moved from Preview to Generally available|	Human Resources|
|Cross company compensation view	|7/23/2023|	On by default|	Human Resources|
|Recruiting process management	|7/23/2023|	On by default	|Human Resources|
|Custom links in Manager self service	|7/23/2023|	Mandatory|	Human Resources|
|Allow proration of benefit plan contributions	|7/23/2023|	Moved from Preview to Generally available|	Human Resources|
|Benefits compare selections	|7/23/2023|	Moved from Preview to Generally available|	Human Resources|



## Features removed from Feature management

The following table lists the features that have been removed from Feature management in version 10.0.36.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
|Filter active positions |The related functionality is enabled out of the box. | Personnel Management| 
|Managers can view performance-related information for extended reports |The related functionality is enabled out of the box.| Manager self service |
|Future dated worker transfer with cross-company compensation| The related functionality is enabled out of the box. |Compensation |
|Human resources user experience enhancements| The related functionality is enabled out of the box.| Human resources | 


## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Human Resources version 10.0.36 includes platform updates. To learn more, see [Platform updates for version 10.0.36 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-36.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=831854).
