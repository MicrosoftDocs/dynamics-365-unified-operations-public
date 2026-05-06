---
title: Support policy for the Warehouse Management mobile app
description: Learn about the support policies that apply to the Warehouse Management mobile app, including the V3 end-of-support milestone in May 2026 and the rolling 12-month support window for V4 and later releases that starts on May 1, 2027.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.topic: conceptual
ms.date: 04/28/2026
ms.custom:
  - bap-template
---

# Support policy for the Warehouse Management mobile app

This article describes the support policies for the Warehouse Management mobile app. The policy that applies to you depends on the version you are running:

- **Version 3 (V3)** reaches end of support in May 2026. After that date, Microsoft no longer accepts support cases for V3. Migrate to V4 before May 2026 to keep support coverage.
- **Version 4 (V4) and all later releases** follow a rolling 12-month support window starting May 1, 2027. After that date, a release is eligible for support cases only if its publication date is within the previous 12 months. This rule applies to every V4 release. It also applies to later major, minor, and patch versions.

These policies help keep the app secure, reliable, and compatible with current platforms. By focusing on recent releases, Microsoft can:

- Deliver security fixes faster.
- Keep up with changes in Apple, Google, and Microsoft platforms.
- Provide a consistent baseline for troubleshooting.

Older releases of the app continue to function. The policies define when Microsoft accepts support cases. They don't affect service availability or sign-in.

## Version 3 support policy

V3 of the Warehouse Management mobile app reaches end of support in May 2026. For details, see the [Migration to V4 Guide](warehouse-app-migrating-from-v3-v4.md). Migrate devices to V4 before that date to keep support coverage.

V3 runs on the *Xamarin* framework. Xamarin is no longer supported, so Microsoft can't ship new features or bug fixes for V3.

### Scope of support after May 2026

Back-end APIs stay compatible with V3 during the migration period. This compatibility lets V3 clients keep running while you move to V4. The compatibility duration isn't guaranteed and may end as Supply Chain Management services change.

- **No new releases** – Microsoft can't build, patch, or ship updates for V3. The Xamarin framework is deprecated.
- **Support cases** – Microsoft no longer accepts support cases for the V3 client.

Devices that stay on V3 after May 2026 follow this V3 policy. The 12-month rolling window doesn't apply to V3.

### Examples of out-of-scope scenarios

The following table lists examples of issues that Microsoft no longer investigates for V3.

- **Authentication and identity (Microsoft Entra ID)** – V3 uses legacy authentication libraries that Microsoft no longer maintains.
    - **Unsupported** – Failures with modern Microsoft Authentication Library (MSAL) flows, *Device not compliant* errors, and new conditional access policies in Microsoft Entra ID.
    - **Resolution** – Migrate to V4 to use current authentication protocols.

- **Client-side performance and connectivity** – The V3 networking stack and libraries are frozen at their current versions.
    - **Unsupported** – Local latency, connection drops, or timeouts caused by the outdated V3 libraries.
    - **Note** – If a performance issue is verified as a server-side or service-wide problem, Microsoft still investigates it as part of standard cloud service support.

- **Operating system (OS) compatibility** – Apple and Google release new OS versions often. Legacy apps often break on those new OS versions.
    - **Unsupported** – Crashes, UI glitches, or launch failures on mobile OS versions released after the final V3 release.
    - **Resolution** – Use V4 for ongoing OS compatibility. V4 is built on the latest software development kits (SDKs).

## Version 4 and later support policy

Starting **May 1, 2027**, V4 and every later release follow a rolling 12-month support window. On or after that date, a release is eligible for support cases only if its publication date is within the previous 12 months. The window is evaluated on the date the support case is opened.

This rule applies to every release from V4 onward. It applies to major, minor, and patch versions equally.

### How publication date is defined

The publication date of a release is the date the release first becomes available on Microsoft App Center. Releases on the Microsoft Store, Google Play, and the Apple App Store can appear later. iOS releases often arrive later because of store review times. Even so, the Microsoft App Center date is always the date that determines support eligibility.

Each V4 and later release, starting with version 4.1.1.0, lists its publication date in [What's new or changed in the Warehouse Management mobile app](warehouse-app-whats-new.md).

### Examples

- A release published on *April 30, 2026* is eligible for support cases until *April 30, 2027*. Because that date falls before May 1, 2027, the release becomes ineligible on May 1, 2027 (the date the policy takes effect).
- A release published on *June 15, 2026* is eligible for support cases until *June 15, 2027*.
- A release published on *August 1, 2027* is eligible for support cases until *August 1, 2028*.

There's no grace period after the 12-month boundary. Update the device to a supported release before you open a support case.

### Why the 12-month window matters

The 12-month window is critical for keeping the app secure and reliable. It lets Microsoft:

- Ship security fixes on a current code base. Backporting across many legacy builds slows fix delivery.
- Keep up with platform changes from Apple, Google, and Microsoft. OS updates, authentication libraries, and store policies often break older releases.
- Diagnose issues against a known, well-tested baseline. This approach makes root-cause analysis faster and more accurate.
- Focus engineering work on changes that help all customers. Issues already fixed in newer releases don't need reinvestigation.

### Scope of the 12-month window

- **Support cases** – Microsoft accepts and investigates support cases only when the device runs a V4 or later release with a publication date within the previous 12 months. For older releases, update to a supported version before opening a case.
- **Critical production outages** – Microsoft might still investigate severity-1 incidents that block widespread production operations. The team reviews these cases individually. The standard guidance is still to update to a supported release first. This exception isn't a substitute for staying current.
- **Preview builds** – Preview and beta builds from Microsoft App Center aren't part of the 12-month window. Use them only for evaluation. Report issues through the [preview feedback channel](warehouse-app-whats-new.md).
- **App availability** – The app keeps running on any installed version. Microsoft doesn't block out-of-window clients, and back-end services don't reject their connections. However, Supply Chain Management services change over time. Older releases might eventually stop working with newer back-end behavior. Compatibility for out-of-window releases isn't guaranteed.
- **Security and platform fixes** – Critical fixes ship in current releases. Devices on older releases don't get those fixes.

### How to identify the installed version

To check which version is installed, open the app. The version appears on the sign-in screen or in **Settings**. Compare it to the publication dates in [What's new or changed in the Warehouse Management mobile app](warehouse-app-whats-new.md).

### How to stay within the support window

- Turn on autoupdate in your app store, or push updates through Microsoft Intune or another mobile device management (MDM) solution. For details, see [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md).
- Track release dates in [What's new or changed in the Warehouse Management mobile app](warehouse-app-whats-new.md). Every V4 and later release, starting with 4.1.1.0, has a publication date.
- Update devices at least once a year. This practice keeps every device inside the 12-month support window.

## Related information

- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [Migrate the Warehouse Management mobile app from V3 to V4](warehouse-app-migrating-from-v3-v4.md)
- [What's new or changed in the Warehouse Management mobile app](warehouse-app-whats-new.md)
- [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md)
