---
# required metadata

title: What's new or changed in Dynamics 365 Talent - Core HR (August 2018)
description: This topic describes features that are new or changed in Microsoft Dynamics 365 Talent - Core HR.
author: andreabichsel
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
ms.reviewer: anbichse
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-08-27
ms.dyn365.ops.version: Talent August 2018 update

---

# What's new or changed in Dynamics 365 Talent - Core HR (August 2018)

**Build 8.1.104**

This topic describes features that are either new or changed in Dynamics 365 Talent: Core HR.

## View expiring records in Manager self-service

You can now view expiring records in Manager self-service. New options allow you to configure what information will be available for managers to view. These options include:

-   Certificates

-   Identification numbers

-   Probation periods

-   Screenings

-   Tests

This feature also gives you the ability to specify the range of days in which to look for expiring records.

## Configurable transfer actions

You can configure by role the options that will be available during the entry of a
transfer request. This feature provides additional flexibility across the
roles in an organization.

For example, managers requesting employee transfers may not have access to suggest or enter compensation amounts or select the task lists that will be associated with the transfer request. Managers can create and submit transfer requests, but can't enter compensation or task list assignments. In this same configuration, HR can assign the new compensation values and assign any additional checklists to be completed because of the transfer completing.

By default, the new configuration options are set to not change the capabilities prior to this update.

## Leave and absence

There are now additional Date fields available in Leave and Absence.

With this feature, you can set the accrual period basis at the plan level to
use specific employee dates. Dates other than the plan start
date can be used during the leave accrual process. Options for employee-specific
dates include the following values:

-   Custom (available prior to this update)

-   Anniversary date

-   Original hire date

-   Seniority date

-   Worker’s adjusted start date

-   Worker’s start date

When configured to use one of the employee-specific dates, the enrollment
process will use the specified date to calculate the accrual periods. The
accrual period basis is also displayed on the employee’s plan enrollment to help
you understand what’s being used during the accrual process.

## Microsoft Word integration

Document templates have been enabled throughout Core HR. This feature allows you to create letters and reports based on Word templates that you create.

Additional information about this feature is available in the
[Office integration tutorial](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/office-integration/office-integration-tutorial?toc=/dynamics365/unified-operations/talent/toc.json).


## Other fixes

This release also includes a number of bug fixes, the addition of new entities, fixes to
existing entities, and localized label changes.
