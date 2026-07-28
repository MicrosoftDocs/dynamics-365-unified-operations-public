---
title: Warehouse Management mobile app release schedule
description: View the targeted release schedule for the Warehouse Management mobile app, and learn how you can plan your own validation and update process around it.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.topic: concept-article
ms.date: 07/27/2026
ms.search.form:
ms.custom:
  - bap-template
---

# Warehouse Management mobile app release schedule

[!include [banner](../includes/banner.md)]

Microsoft doesn't force version upgrades for the Warehouse Management mobile app. You can decide when a new version reaches each of your devices, and you can stay on your preferred version for as long as you like. However, Microsoft normally supports each release for one year. Version 4 and later releases follow a rolling 12-month support window, with each release eligible for support cases only while its publication date falls within the previous 12 months. For details, see [Support policy for the Warehouse Management mobile app](warehouse-app-support-info.md#version-4-and-later-support-policy). Therefore, you should plan for at least one update per device per year.

For most deployments, you should install the app from an app store and let it update automatically. This approach is the simplest way to receive security fixes, platform compatibility updates, and bug fixes. It keeps devices inside the support window without extra effort. If your organization wants to validate a release before it reaches production devices, use the release schedule in this article to plan that validation.

## Targeted release schedule (dates subject to change)

Each release becomes available in Microsoft App Center first. Progressive rollout to the app stores (Microsoft Store, Google Play, and the Apple App Store) starts later. Because rollout is gradual, a release might not appear on every device on the date that rollout begins. Availability in each store can take several additional days to reach all users. iOS releases can arrive later still because of Apple App Store review times.

The following table lists the current and scheduled releases of the Warehouse Management mobile app. It includes the following columns:

- The **Availability in Microsoft App Center** column indicates when you can download the release for evaluation or for manual distribution. This date is also the publication date that determines support eligibility under the 12-month support window.
- The **App store rollout begins** column indicates when progressive rollout to the app stores starts.

| Release version | Availability in Microsoft App Center | App store rollout begins | Status |
|---|---|---|---|
| 4.1.5.0 | August 11, 2026 | August 25, 2026 | Planned |
| 4.1.4.0 | May 28, 2026 | Complete | Released |
| 4.1.3.0 | May 18, 2026 | Complete | Released |
| 4.1.2.0 | May 6, 2026 | Complete | Released |
| 4.1.1.0 | April 30, 2026 | Complete | Released |

For a list of features and fixes included in each release, see [What's new or changed in the Warehouse Management mobile app](warehouse-app-whats-new.md). For releases before version 4.1.1.0, see [Warehouse Management mobile app release notes archive](warehouse-app-whats-new-archive.md).

> [!NOTE]
> Microsoft App Center remains available for downloading Warehouse Management mobile app packages. If that changes, Microsoft will communicate the change and the replacement distribution method in advance through [What's new or changed in the Warehouse Management mobile app](warehouse-app-whats-new.md).

## Plan your own update process

The schedule gives you a window between App Center availability and app store rollout that you can use for validation. How you use that window is up to you. Every organization has a different device fleet, mobile device management (MDM) solution, and internal change management policy, so develop the process that fits your organization best. The following points are a starting point, not a required process.

- **Track upcoming releases** – Check this schedule and [What's new or changed in the Warehouse Management mobile app](warehouse-app-whats-new.md) so that no version reaches your devices unannounced.
- **Review the release notes** – Compare each release against the flows, device models, scanners, and authentication configuration that matter most to your operation.
- **Test on a small set of pilot devices** – Download the release from [Microsoft App Center](install-configure-warehouse-management-app.md#download-the-app-from-microsoft-app-center) during the window before store rollout begins, and install it on devices that represent your real hardware mix. Preview builds are also available in App Center for earlier evaluation, but they're intended for evaluation only and aren't covered by the support window.
- **Use your MDM solution to control timing** – On Android, Managed Google Play in Microsoft Intune lets you set a different app update mode (*Default*, *High Priority*, or *Postponed*) for each group that the app is assigned to. For details, see [Update a Managed Google Play app](/intune/app-management/deployment/add-managed-google-play#update-a-managed-google-play-app). On Windows, you can deploy a specific MSIX package from Microsoft App Center as a line-of-business app. For details, see [Add a Windows line-of-business app to Microsoft Intune](/intune/intune-service/apps/lob-apps-windows). On iOS, the app is available only through the Apple App Store, so this type of version control isn't available.
- **Report problems that you find** – If validation uncovers a regression, open a support case with a supported version so that the issue can be fixed in a current release.

## Things to keep in mind

- **Stay within the support window** – Holding a version indefinitely eventually moves devices outside the rolling 12-month support window for version 4 and later releases. Learn more in [Support policy for the Warehouse Management mobile app](warehouse-app-support-info.md#version-4-and-later-support-policy).
- **Security and platform fixes ship in current releases** – Older releases don't receive backported fixes, and operating system updates can break older builds.
- **Back-end compatibility isn't guaranteed indefinitely** – Supply Chain Management services evolve over time, so a version that you hold for a long time might eventually stop working correctly.
- **Manual distribution adds ownership** – If you take devices off the store update path, your organization becomes responsible for delivering every subsequent update, including security fixes. Make sure that you have a reliable mechanism to get the latest version onto your devices. The Warehouse Management mobile app is for your internal business use only. You may not republish or distribute it externally in any app store or similar distribution service.

## Related information

- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md)
- [Support policy for the Warehouse Management mobile app](warehouse-app-support-info.md)
- [What's new or changed in the Warehouse Management mobile app](warehouse-app-whats-new.md)
- [Migrate the Warehouse Management mobile app from V3 to V4](warehouse-app-migrating-from-v3-v4.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
