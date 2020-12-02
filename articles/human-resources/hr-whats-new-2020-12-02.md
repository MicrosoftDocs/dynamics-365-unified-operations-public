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

#HCM & HCMFabric Deliverables

## Release: D365HR Release Tracking - 2020-11-30 - (532031)
## Regular translation checkins for supported HCM languages - (394249)
## Release: D365HR Release Tracking - 2020-11-23 - (529321)
## PU40+ Build Errors - (528010)
## [Fusion] - Breaking changes resolution for BusinessProcess module - (523493)
## Release: D365HR Release Tracking - 2020-11-16 - (527157)
## Candidate Profile V1 UI implementation - (444051)
## Add recruiting request form to security role - (447078)
## Provide capability to add new address from recruiting request location - (473588)
## Finalize the Candidate Model re-using Person entity and test end to end insert flow. - (483250)
## Release: D365HR Release Tracking - 2020-11-30 - (532031)
## Release: D365HR Release Tracking - 2020-11-23 - (529321)
## Release: D365HR Release Tracking - 2020-11-16 - (527157)
## Release: D365HR Release Tracking - 2020-11-09 - (524854)
## Release: D365HR Release Tracking - 2020-11-02 - (522491)
## Release: D365HR Release Tracking - 2020-10-26 - (520210)
## [s360] Keyvaults need soft delete setting applied. - (520494)
## Release: D365HR Release Tracking - 2020-10-19 - (517735)

| Feature | Release plan | Documentation |
| --- | --- | --- | --- |
| Feature name or short description | Release plan title and link | Doc title and link |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

#HCM & HCMFabric Bugs

## Benefit Self service - Recently created beneficiaries do not appear in the designees table - (517364)
## Multiple entries exist for table with the same name on Reference Type lookup - (525958)
## Incorrect forecast balance when carry-forward feature is enabled  - (508461)
## Balance expiration batch job doesn't bring balance to 0 - (509982)
## Add more fields to BenefitPlanEmployeeDesigneeEntity - (485085)
## BenefitEligibilityProcessResult should include datetime that was used in processing - (514087)
## Benefit Enrollment fails for plans with dependents when Auto-select designees is turned on in HR shared parameters - (526903)
## Leave forms emits compiler warnings with BPErrorFormDesignPatternUnspecified  - (513558)## Populate assignment start/end date for candidate transfer & new hire scenarios - (525011)
Date manipulation code in `HcmWorkerTransfer` currently prevents us from setting correct start/end assignment dates for candidates who are internal transfers within `HcmWorkerTransferEventHandler_HcmIntegration`. We need to determine the purpose of said date manipulation code and refactor the `HcmWorkerTransfer` form to allow our event handler to set the start/end assignment dates from a candidate, e.g. `candidate.AvailabilityDate` and `DateTimeUtil::maxValue()`.
    ## Candidate status doesn't update on internal candidates when transfer is completed - (525957)
When a transfer is completed (i.e. the Change position or Continue button is clicked on the Transfer work to a new position assignment page), the Status on the candidate record must change to Hired.
    
## Show absence without detail parameter not working on team calendar view - (521922)
## Improve error message on Format Exception for CDS. - (528172)
## Title changes for Job/Positions/Worker notifications do not sync with the 2.2.4.1 Solution - (527316)
## Remove the color options from leave and absence parameters - (512275)## Misleading error message text during employee position assignment  - (437112)
In case a user tries to enter a worker position assignment for a
position which is not active yet (HcmPositionWorkerAssignment.ValidFrom <
HcmPositionDuration.ValidFrom) the system gives correctly an error message. 
    
## Performance issues on EssLeaveRequestCalendar form - (527816)
## BenefitPeriodMigrationUpgrade and BenefitPlanMigrationUpgrade not executing - (523158)
## Platform flighting not working correctly for FeatureManagement and in Dev/Int environments - (523178)

| LCS support number | Description |
| --- | --- |
| LCS number and link | Description |


## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- | --- |
| Feature name or short description | Release plan title and link | Doc title and link |

## Coming soon

The following new features and bug fixes are scheduled for future releases.

### New features

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/).

### Bug fixes

| LCS support number | Description |
| --- | --- |
| Number and link | Description |

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
