---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources July 26, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for July 26, 2021.
author: marcelbf
ms.date: 07/12/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form:
# ROBOTS:
audience: Application User
# ms.devlang:
ms.search.scope: Human Resources
# ms.tgt_pltfrm:
ms.custom:
ms.assetid:
ms.search.region: Global
# ms.search.industry:
ms.author: marcelbf
ms.search.validFrom: 2021-07-26
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources July 26, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4384.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| ## [s360] Migrate to MSAL from ADAL - Due September 30, 2021 - (584168) | | |
| ## Integrate benefit reason codes into core hr reason codes (Part 4 - Forced integration) - (570459) This deliverable is about creating a forced integration pattern given the lack of manual upgrades occurring in Part 3 of this upgrade | | |    
| ## Restrict access to the Ready to Pay menu item on the Worker forms. - (598852) | | |
| ## Regular translation checkins for supported HCM languages - (394249) | | |
| ## Design feedback: Add a link for "Pending time off requests" under the summary view - (592117) | | |
| ## Design feedback: new absence manager workspace view - (596441) | | |
| ## [Payroll] - Payroll position entity should have a relation to hcmpositionhierarchy entity - (598851) | | |
| ## [Payroll] - Employee payroll entity must have a relation to bank accounts entity - (598403) | | |
| ## PU44 Uptake/Validation - (593816) | | |
| ## Migration service internal end-to-end (V0) - (589862) | | |


### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| ## Leave workflow enhancement returns incorrect work item for a leave request - (600377) | | |
| ## Payroll address validation failing for Ready to Pay - (600422) | | |
| ## Tiles that were added to Employee Self Service workspace are now missing, and tiles can no longer be added to it. - (602272) | | |
| ## Half-day definition selection field enabled for full day leave requests - (600711) | | |
| ## ACCRUAL RATE UNITS DISPLAYING HRS INSTEAD OF DAYS  - (602208) | | |
| ## Absence manager calendar is empty when accessed from the tile - (602010) | | |
| ## Ceridian payroll integration resets to incremental refresh and needs to always be full refresh. - (601226) | | |
| ## Worker benefit plans- tab sequence - (594783) | | |
| ## Scale out VM count in Europe Clusters - (601016) | | |


## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers) | [Payroll integration API](hr-admin-integration-payroll-api-introduction.md)|
|  Enable an absence manager to manage leave | [Enable an absence manager to manage leave](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-absence-manager-manage-leave) | [Configure absence manager role](https://go.microsoft.com/fwlink/?linkid=2168107)|
|  Configure attachment requirement per leave type | [Configure attachment requirement per leave type](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/mandate-attachments-specific-leave-types) |[Configure leave and absence types](https://go.microsoft.com/fwlink/?linkid=2168108)|
|  Configure leave units per leave type | [Configure leave units per leave type](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/configure-leave-units-per-leave-type) |[Configure leave and absence types](https://go.microsoft.com/fwlink/?linkid=2168215)|
| Enable employees to be marked as ready to be paid | [Enable employees to be marked as ready to be paid](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-employees-be-marked-as-ready-pay) | [Ready to pay](/dynamics365/human-resources/hr-compensation-payroll) |

## Coming soon

| Feature | Details |
| --- | --- |
| Platform update 10.0.20 (44) | Platform update 10.0.20 is scheduled to begin rolling out with the service release on July 26, 2021. For more information, see [Platform updates for version 10.0.20 of Finance and Operations apps (August 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-20). |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
