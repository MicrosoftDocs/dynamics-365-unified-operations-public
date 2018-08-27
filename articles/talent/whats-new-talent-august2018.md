---
# required metadata

title: What's new or changed in Dynamics 365 for Talent Core HR (August 2018)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 08/27/2018
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
ms.search.validFrom: 2018-08-27
ms.dyn365.ops.version: Talent August 2018 update

---

# What's new or changed in Dynamics 365 for Talent Core HR, (August 2018)

**Build 8.1.104**

[!include [banner](https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/live/articles/fin-and-ops/includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for
Talent Core HR.

## Expiring records: manager self service

View expiring records in Manager self-service. New options are now available to
configure what information will be available for managers to view. These
include:

-   Certificates

-   Identification numbers

-   Probation periods

-   Screenings

-   Tests

This feature also gives you the ability to specify the range of days to look for
expiring records.

## Configurable transfer actions

Configure by role the options that will be available during the entry of a
transfer request. This feature will provide additional flexibility across the
roles in an organization.

For Example: Managers requesting employee transfers may not have access to
suggest or enter compensation amounts or select the task lists that will be
associated with the transfer request. In this case Managers can create and
submit transfer requests but are not allowed to enter compensation or task list
assignments. In this same configuration, HR will be able to assign the new
compensation values as well as assign any additional checklists to be completed
as a result of the transfer completing.

By default, the new configuration options are set to not change the capabilities
prior to this update.

## Leave and absence

Use additional Date fields in Leave and Absence

With this feature you can now set the accrual period basis at the plan level to
use specific employee dates. This allows for dates other than the plan start
date to be used during the leave accrual process. Options for employee specific
dates include following values:

-   Custom (Available prior to this update)

-   Anniversary date

-   Original hire date

-   Seniority date

-   Worker’s adjusted start date

-   Worker’s start date

When configured to use one of the employee specific dates, the enrollment
process will use the specified date to calculate the accrual periods. The
accrual period basis is also displayed on the employee’s plan enrollment to help
you understand what’s being used during the accrual process.

## Microsoft Word integration

Document templates have been enabled throughout Core HR. This feature enables
scenarios for creating letters and reports based on Word templates you create.

Full documentation is available
[here](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/office-integration/office-integration-tutorial?toc=/dynamics365/unified-operations/talent/toc.json).


## Other Fixes

This release includes a number of bug fixes, additional entities, fixes to
entities and localized label changes.
