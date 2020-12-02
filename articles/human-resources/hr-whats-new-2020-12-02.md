---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources December 2, 2020
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: marcelbf
manager: AnnBe
ms.date: 12/2/2020
ms.topic: article
ms.prod:
ms.service: dynamics-human-resources
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
ms.author: jcart
ms.search.validFrom: 2020-12-02
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources December 2, 2020"

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3794.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Regular translation checkins for supported HCM languages | - | 394249 |
| PU40+ Build Errors | - | 528010 |
| Breaking changes resolution for BusinessProcess module | - | 523493 |
| Candidate Profile V1 UI implementation | - | 444051 |
| Add recruiting request form to security role | - | 447078 |
| Provide capability to add new address from recruiting request location | - | 473588 | 
| Finalize the Candidate Model re-using Person entity and test end to end insert flow. | - | 483250 | 
| Keyvaults need soft delete setting applied. | - | 520494 | 

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

#HCM & HCMFabric Bugs

| Issue number | Issue | Description |
| --- | --- | --- |
| 517364 | Benefit Self service Recently created beneficiaries do not appear in the designees table | |
| 525958 | Multiple entries exist for table with the same name on Reference Type lookup | |
| 508461 | Incorrect forecast balance when carry-forward feature is enabled | |
| 509982 | Balance expiration batch job doesn't bring balance to 0 | |
| 485085 | Add more fields to BenefitPlanEmployeeDesigneeEntity | |
| 514087 | BenefitEligibilityProcessResult should include datetime that was used in processing | |
| 526903 | Benefit Enrollment fails for plans with dependents when Auto-select designees is turned on in HR shared parameters | |
| 513558 | Leave forms emits compiler warnings with BPErrorFormDesignPatternUnspecified | |
| 525011 | Populate assignment start/end date for candidate transfer & new hire scenarios | |
| 525957 | Candidate status doesn't update on internal candidates when transfer is completed | |
| 521922 | Show absence without detail parameter not working on team calendar view | |
| 528172 | Improve error message on Format Exception for CDS. | |
| 527316 | Title changes for Job/Positions/Worker notifications do not sync with the 2.2.4.1 Solution | |
| 512275 | Remove the color options from leave and absence parameters | |
| 437112 | Misleading error message text during employee position assignment | |
| 527816 | Performance issues on EssLeaveRequestCalendar form | |
| 523158 | BenefitPeriodMigrationUpgrade and BenefitPlanMigrationUpgrade not executing | |
| 523178 | Platform flighting not working correctly for FeatureManagement and in Dev/Int environments | |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- | --- |
| Feature name or short description | Release plan title and link | Doc title and link |

## Coming soon

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
