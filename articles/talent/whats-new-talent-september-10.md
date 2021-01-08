---
# required metadata

title: What's new or changed in Dynamics 365 Talent - Core HR (September 10, 2018)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent - Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 09/12/2018
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
ms.search.validFrom: 2018-09-06
ms.dyn365.ops.version: Talent September 10, 2018 update

---

# What's new or changed in Dynamics 365 Talent - Core HR (September 10, 2018)

**Build 8.1.138.0**

This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent: Core HR.

## Allow specific time of day on time-off requests (half days)

If leave and absence is set up so that time off is submitted in days, you can now also enable a half-day definition. Then, when users submit time-off requests, they can specify whether they are requesting the first half or the second half of the day off.

By default, this option is turned off. For employees to request the first half or second half of the day off, you must turn on this option in the **Leave and absence** area of Human resources parameters.

The security privilege for this feature is Maintain Human Resources Parameters.

## Validation of leave and absence entries

Depending on how leave is configured, employees who try to submit a time-off request that is longer than their work day receive a warning message. In other words, they are warned if they try to take more than a full day off on any given date.

This validation is always turned on. Any time that employees exceed the day threshold that is defined, they receive a warning in their time-off request.

## Additional fields for conditional statements in workflows

Additional fields have been added to conditional statements and placeholders for several workflows in Core HR.

The following fields have been added to the compensation, termination, and transfer workflows:

- EmploymentType
- LegalEntity
- AdjustedWorkerStartDate
- EmployerNoticeAmount
- EmployerUnitOfNotice
- TransitionDate
- WorkerNoticeAmount
- WorkerStartDate
- WorkerUnitOfNotice
- ProbationEndDate
- Position
- Union
- Department
- PositionType
- CompLocation
- Title
- Job
- JobType
- JobFamily
- JobFunction

The following fields have been added to the position workflow:

- Position
- Union
- Department
- PositionType
- CompLocation
- Title
- Job
- JobType
- JobFamily
- JobFunction

Fields in conditional statements and placeholders are available to all users who have access to configure the previously mentioned workflows.

## Navigation to Attract from personnel management

In personnel management, if Attract hasn't been set up, the **Candidates to hire** section directs users to get started with Attract instead of showing the message, "We didn't find anything to show here."

## Other changes

This release includes several additional bug fixes:

- When a contractor is hired, the **Compensation** tab should not be available on the request/action page.
- During the request termination process, you can't continue until all required fields contain data.
- Sort order and date display issues on the Personnel management analytics have been addressed.
