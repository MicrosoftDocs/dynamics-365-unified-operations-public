---
# required metadata

title: What's new or changed in Dynamics 365 for Talent Core HR (September 10, 2018)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 09/06/2018
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
ms.search.validFrom: 2018-09-06
ms.dyn365.ops.version: Talent September 10, 2018 update

---

# What's new or changed in Dynamics 365 for Talent: Core HR (September 10, 2018)

[!include [banner](includes/banner.md)]

**Build 8.1.138.0**

This topic describes features that are either new or changed in Core HR.

## Allow specific time of day on time off requests (half day)

If leave and absence is setup to have time off submitted in days, you can now
also enable a half day definition. This option will let users specify if they
will be requesting the first half or the second half of the day when submitting
time off requests.

By default, this option isn’t enabled. In order to allow employees to request
the first half or second half of the day, you’ll need to enable this option in
the Leave and absence area of Human resources parameters.

The security privilege for this feature is: Maintain Human Resources Parameters

## Leave and absence entry validation

When an employee tries to submit a time off request that is longer than their
work day, they’ll receive a warning message. Depending on how leave is
configured, employees will be warned if they attempt to take more than a full
day off on any given date.

This validation is always enabled. Any time an employee goes over the day
threshold defined, they will receive the warning in their time off request.

## Additional fields in workflow for conditional statements

Additional fields have been added to conditional statements and placeholders for
several workflows within Core HR.

Compensation, termination and transfer workflow have the following fields added:

• EmploymentType

• LegalEntity

• AdjustedWorkerStartDate

• EmployerNoticeAmount

• EmployerUnitOfNotice

• TransitionDate

• WorkerNoticeAmount

• WorkerStartDate

• WorkerUnitOfNotice

• ProbationEndDate

• Position

• Union

• Departement

• PositionType

• CompLocation

• Title

• Job

• JobType

• JobFamily

• JobFunction

Position workflow has the following additions:

• Position

• Union

• Departement

• PositionType

• CompLocation

• Title

• Job

• JobType

• JobFamily

• JobFunction

Fields within conditional statements and place holders are available to all
users that have access to configure the workflows mentioned above.

## Navigation to Attract from personnel management

In personnel management, if Attract has not been set up, the candidates to hire
section will direct users to get started with Attract instead of showing the
message “We didn’t find anything to show here”.

## Other changes

This release includes several additional bug fixes.

-   When hiring a contractor, the compensation tab should not be available on
    the request/action form

-   During the request termination process you can’t continue until all required
    fields contain data

-   Sort order and date display issues have been addressed on the Personnel
    management analytics

-   Other misc. fixes
