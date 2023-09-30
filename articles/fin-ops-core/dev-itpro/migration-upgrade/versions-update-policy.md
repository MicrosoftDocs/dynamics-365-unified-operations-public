---
# required metadata

title: Software lifecycle policy and cloud releases
description: This article outlines the lifecycle and support policies for the finance and operations online service.
author: hmahl
ms.date: 09/29/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysAbout
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2

---

# Software lifecycle policy and cloud releases

[!include [banner](../includes/banner.md)]

This article outlines the lifecycle and support policies for the finance and operations online service.

## Modern Lifecycle Policy
The finance and operations online service is covered by the Modern Lifecycle Policy. The Modern Lifecycle Policy covers products and services that are serviced and supported continuously. For more information about this policy, see [Modern Lifecycle Policy](https://support.microsoft.com/help/30881). Licensed customers must stay current with updates to the finance and operations online service in accordance with the following servicing and system requirements:

- Customers purchasing subscriptions of finance and operations apps will experience continuous updates managed by Microsoft. Customers have the option to postpone one consecutive service update.

- Platform versions maintain backward compatibility with the application versions that are supported at the time of the platform release within the application support lifecycle. For more information about platform versions, see [What's new or changed in Platform updates](../get-started/whats-new-home-page.md).

- Critical fixes and non-critical updates are handled in the following way:

    - **Critical fixes** – Critical fixes include security fixes and any fixes that are required to adhere to the availability service level agreement (SLA) that the service supports. Critical fixes are available in the latest service update. In addition, to help protect the customer and the online service, Microsoft may apply critical fixes directly to a customer's environment. If a critical fix must be applied, Microsoft notifies the customer about the required downtime window (if there will be any downtime) and applies the fix to the applicable environment. The critical fix updates the system to the latest update version.

    - **Non-critical updates** – Non-critical updates are made available through service updates and quality updates.          

> [!IMPORTANT]
> Microsoft won't investigate, troubleshoot, or provide any fixes to issues on versions that reached their end of service. See the [Targeted release schedule](public-preview-releases.md#targeted-release-schedule-dates-subject-to-change) for end of service dates by release.
> 
> The Microsoft support team can't take cases relating to versions in end of service. You must first update to the latest service update and then apply the latest quality update. If the issue still persists, you can then report it. For more information, see [What happens to an environment that is running a finance and operations app version that is no longer supported](../../fin-ops/get-started/one-version.md#what-happens-to-an-environment-that-is-running-a-finance-and-operations-app-version-that-is-no-longer-supported).
>
> All environments are operated by Microsoft. All automatic processes around your environments, such as monitoring or self-healing, are also as-is for supported versions.

## Dates and versions for application and platform releases

To see details on dates and versions for releases, see the [What's new or changed in finance and operations apps home page](../../fin-ops/get-started/whats-new-changed.md).

> [!NOTE]
> - Service updates are cumulative in nature and may include updates for some or all of the following components:  platform, application, Financial Reporting, Commerce, and operating system updates. 
> - Customers can pause, delay, or opt out of a service update using the update settings in Lifecycle Services projects, provided that all their sandbox and production environments are no more than one version behind the latest available update. For more information, refer to [Can the updates be delayed? What is the policy?](../../fin-ops/get-started/one-version.md#can-the-updates-be-delayed-what-is-the-policy)

## Downloadable virtual hard drive (VHD) releases

For finance and operations apps, updates to the downloadable VHD are released twice per year, concurrent with the major releases in April and October. The VHD is bundled with the latest service update, and therefore its release always follows the release of the associated service update for production use. You can expect the VHD update to be released after the generally available (self-update) date of the service update. Finance and operations release dates are published in the [Targeted release schedule](public-preview-releases.md#targeted-release-schedule-dates-subject-to-change).

Use of the VHDs is subject to the [Software license terms](https://go.microsoft.com/fwlink/?linkid=851163).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
