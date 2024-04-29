---
title: Software lifecycle policy and cloud releases
description: Learn about the lifecycle and support policies for the finance and operations online service, including dates and versions for application and platform releases.
author: hmahl
ms.author: sericks
ms.topic: article
ms.date: 09/29/2023
ms.reviewer: twheeloc
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-08-30
ms.search.form: SysAbout
ms.dyn365.ops.version: Platform update 2
---

# Software lifecycle policy and cloud releases

[!include [banner](../includes/banner.md)]

This article outlines the lifecycle and support policies for the finance and operations online service.

## Modern Lifecycle Policy

The finance and operations online service is covered by the Modern Lifecycle Policy. The Modern Lifecycle Policy covers products and services that are continuously serviced and supported. For more information about this policy, see [Modern Lifecycle Policy](https://support.microsoft.com/help/30881). Licensed customers must stay current with updates to the finance and operations online service in accordance with the following servicing and system requirements:

- Customers who purchase subscriptions of finance and operations apps experience continuous updates that are managed by Microsoft. Customers have the option to postpone one consecutive service update.
- Platform versions maintain backward compatibility with the application versions that are supported at the time of the platform release within the application support lifecycle. For more information about platform versions, see [What's new or changed in Platform updates](../get-started/whats-new-home-page.md).
- Critical fixes and non-critical updates are handled in the following way:

    - **Critical fixes** – Critical fixes include security fixes and any fixes that are required to adhere to the availability service level agreement (SLA) that the service supports. Critical fixes are available in the latest service update. In addition, to help protect customers and the online service, Microsoft might apply critical fixes directly to a customer's environment. If a critical fix must be applied, Microsoft notifies the customer about the required downtime window (if there will be any downtime) and applies the fix to the applicable environment. The critical fix updates the system to the latest update version.
    - **Non-critical updates** – Non-critical updates are made available through service updates and quality updates.

> [!IMPORTANT]
> Microsoft doesn't investigate, troubleshoot, or provide any fixes to issues on versions that have reached their end of service. For end-of-service dates by release, see [Targeted release schedule (dates subject to change)](../get-started/public-preview-releases.md#targeted-release-schedule-dates-subject-to-change).
>
> The Microsoft Support team can't take cases that are related to versions that are in their end of service. You must first update to the latest service update and then apply the latest quality update. At that point, if the issue  persists, you can report it. For more information, see [What happens to an environment that's running a finance and operations app version that's no longer supported](../../fin-ops/get-started/one-version.md#what-happens-to-an-environment-that-is-running-a-finance-and-operations-app-version-that-is-no-longer-supported).
>
> All environments are operated by Microsoft. All automatic processes that involve your environments, such as monitoring or self-healing, are as-is for supported versions.

## Dates and versions for application and platform releases

For details about dates and versions for releases, see the [What's new or changed in finance and operations apps home page](../../fin-ops/get-started/whats-new-changed.md).

> [!NOTE]
> - Service updates are cumulative and might include updates for some or all of the following components: platform, application, Financial Reporting, Commerce, and operating system updates.
> - Customers can pause, delay, or opt out of a service update by using the update settings in Microsoft Dynamics Lifecycle Services projects. However, this option is unavailable if any of their sandbox and production environments are more than one version behind the latest available update. For more information, see [Can the updates be delayed? What's the policy?](../../fin-ops/get-started/one-version.md#can-the-updates-be-delayed-what-is-the-policy)

## Downloadable virtual hard drive releases

For finance and operations apps, updates to the downloadable virtual hard drive (VHD) are released twice per year, concurrently with the major releases in April and October. Because the VHD is bundled with the latest service update, its release always follows the release of the associated service update for production use. You can expect the VHD update to be released after the generally available (self-update) date of the service update. For finance and operations release dates, see [Targeted release schedule (dates subject to change)](../get-started/public-preview-releases.md#targeted-release-schedule-dates-subject-to-change).

Use of the VHDs is subject to the [Software license terms](https://go.microsoft.com/fwlink/?linkid=851163).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
