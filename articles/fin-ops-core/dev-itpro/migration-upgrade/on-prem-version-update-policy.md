---
title: Software lifecycle policy and on-premises releases
description: This article outlines the lifecycle and support policies for Microsoft Dynamics 365 Finance + Operations (on-premises) releases.
author: faix
ms.date: 12/14/2021
ms.topic: article
ms.prod: dynamics-365
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: osfaixat
ms.search.validFrom: 2017-07-15
ms.dyn365.ops.version: Platform update 2
ms.search.form: SysAbout
ms.service: 
search.app:
  - financeandoperationsonprem-docs
---

# Software Lifecycle Policy for Microsoft Dynamics 365 Finance + Operations (on-premises)

[!include [banner](../includes/banner.md)]

This article outlines the lifecycle and support policies for Microsoft Dynamics 365 Finance + Operations (on-premises) releases.

## Product life time

The product life time of Finance + Operations (on-premises) software ends **December 2027**. Licensed customers who are in compliance with this policy are entitled to product support. Product support is available at a minimum through December 31, 2027.

## Modern Lifecycle Policy

Finance + Operations (on-premises) software is covered by the Modern Lifecycle Policy. The Modern Lifecycle Policy rules products and services that are serviced and supported continuously. For more information about this policy, see [Modern Lifecycle Policy](https://support.microsoft.com/help/30881/modern-lifecycle-policy).  

Licensed customers must regularly update their deployment of the Finance + Operations (on-premises) software. The servicing policy requires that you maintain the Software Assurance (SA) or the Enhancement Plan and it requires that you deploy the update releases provided through the [continuous service updates](on-prem-version-update-policy.md#continuous-service-updates).

> [!NOTE]
> If you want to use the Fixed Support Lifecycle Policy (5+5), you must downgrade to Microsoft Dynamics AX 2012 R3. If you instead lapse on your SA or the Enhancement Plan, you will only be eligible for the perpetual license rights to Microsoft Dynamics AX 2012 R3 and must uninstall Microsoft Dynamics 365 for Finance + Operations (on-premises).

## On-premises software update policies

As a customer, you are in full control of your on-premises deployments and must actively follow this policy. You are in control of installing updates in your on-premises environments.

Microsoft will support your deployment of Finance + Operations (on-premises) software only if you keep the deployed software current according to this policy.

Critical fixes and non-critical updates are handled in the following way:

- **Critical fixes** – Critical fixes include security fixes and any fixes that are required to support reliability and availability. Critical fixes will be made available in the latest platform update version.
- **Non-critical updates** – Customers must update to the most current Finance + Operations platform and financial reporter version to deploy non-critical updates.

## Finance + Operations (on-premises) release dates

### Continuous service updates

Since November 2018, on-premises service updates are released continuously. For more information about version numbers and availability dates, see [Software lifecycle policy and cloud releases](versions-update-policy.md). For more information about One Version service updates, see [One Version service updates FAQ](../../../fin-ops-core/fin-ops/get-started/one-version.md).

Every service update release has a specific expiration date after which the release isn't entitled to receive support.

#### Continuous combined releases (Application and Platform)

With [Continuous service updates](on-prem-version-update-policy.md#continuous-service-updates), application and platform are released together. The [One Version schedule](../../fin-ops/get-started/public-preview-releases.md#targeted-release-schedule-dates-subject-to-change) specifies the dates for early access, public release, and expiration of the release.

| Product | Deployment options | Application version | Release or expiration dates|
|--------|-----------------------|-----------------------|------------------------|
| Finance + Operations | Base deployment + Service update | 10.0.38 | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |
| Finance + Operations | Service update | 10.0.37 | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |
| Finance + Operations | Service update | 10.0.36 | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |
| Finance + Operations | Base deployment + Service update | 10.0.35 | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |
| Finance + Operations | Service update | 10.0.34 | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |
| Finance + Operations | Service update | 10.0.33 | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |
| Finance + Operations | Base deployment + Service update | 10.0.32 | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |
| Finance + Operations | Service update | 10.0.31 | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |
| Finance + Operations | Service update | 10.0.30 | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |
| Finance + Operations | Base deployment + Service update | 10.0.29  | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |
| Finance + Operations | Service update | 10.0.28 | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |
| Finance + Operations | Service update | 10.0.27* | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |
| Finance + Operations | Base deployment + Service update | 10.0.26*  | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |
| Finance + Operations | Service update | 10.0.25* | [One Version schedule](../../fin-ops/get-started/public-preview-releases.md?#targeted-release-schedule-dates-subject-to-change) |

\* Expired version. All customers must be on the latest version of Finance + Operations according to the [Modern Lifecycle Policy](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

### Older application releases

  > [!NOTE]
  > Older platform releases have passed the expiration date and are no longer supported. Extension requests cannot be logged since January 1, 2019.
  >
  > Customer who are not following the [Modern Lifecycle Policy](https://support.microsoft.com/help/30881/modern-lifecycle-policy) and the [Continuous service updates](on-prem-version-update-policy.md#continuous-service-updates) may not be entitled to receive support after the expiration date of the deployed application version. Expired versions will be removed from LCS at some point where after servicing and deployment of such versions from LCS may not be possible.

| Product          | Application version |Public availability| Expiration date |
|------------------|---------|---------|---------|
| Finance + Operations (on-premises) |10.0  (10.0.8) |Mar 2019 | Jun 2019 |
| Finance + Operations (on-premises) |8.1 (8.1.136) | Nov 2018 | Apr 2019     |
| Finance + Operations, Enterprise edition (on-premises) | 7.3 (7.3.11971) | Mar 2018 | Apr 2020* |
| Finance + Operations, Enterprise edition (on-premises) | July 2017 (7.2.11792) | Jun 2017 | Apr 2019 |

\* All customers must be on the latest version of Finance + Operations. The deadline for this requirement was April 30, 2019. In the transition to [Continuous service updates](on-prem-version-update-policy.md#continuous-service-updates), we had given exemptions for customers who had unfulfilled [extension requests](../extensibility/extensibility-home-page.md) that had been submitted to Microsoft. Those customers could stay on version 7.3 until April 2020. For more information, see [One Version service updates FAQ](../../../fin-ops-core/fin-ops/get-started/one-version.md).

#### Older platform releases

> [!NOTE]
> Older platform releases have passed the expiration date and are no longer supported. Extension requests cannot be logged since January 1, 2019.

| Platform release          |Build Number         | Availability          | Expiration date   |
|------------------|----------------------|------------------|--------------|
|  Platform update 20 | 7.0.5030  | November 2018  | February 2019 |
|  Platform update 15 | 7.0.4841  | June 2018  | September 2018 |
|  Platform update 12 | 7.0.4709.41182  | March 2018  | June 2018 |
|  Platform update 11 | 7.0.4679.35176 | October 2017 | April 2018 |
|  Platform update 10 | 7.0.4641.16233 | August 2017 | April 2018 |
|  Platform update 9 | 7.0.4612.35162 | August 2017 | April 2018 |
|  Platform update 8 | 7.0.4565.1612 | July 2017 | April 2018 |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
