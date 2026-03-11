---
title: Support policy for V3 of the Warehouse Management mobile app
description: Learn about the support policies that apply to Warehouse Management mobile app V3 after it reaches its end of support in May 2026. The article includes information about compatibility, requirements, and the timeline.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 03/11/2026
ms.custom:
  - bap-template
---

# Support policy for V3 of the Warehouse Management mobile app

As announced in the [Migration to V4 Guide](warehouse-app-migrating-from-v3-v4.md), version 3 (V3) of the Warehouse Management mobile app reaches its official end of support in May 2026.

V3 is based on the *Xamarin* framework, which is no longer supported, so Microsoft can't provide any new features or bug fixes for V3. It's replaced by version 4 (V4), which uses a more modern architecture that provides enhanced security, stability, and performance.

This article describes the support policies that apply to V3 after the May 2026 end of support milestone.

## Scope of support after May 2026

The back-end APIs remain compatible for a transitional period to prevent immediate service disruption, but the V3 client application itself is legacy.

- **No new releases** – Microsoft can't build, patch, or release updates for V3 because the underlying Xamarin framework is deprecated.
- **Incident management (ICMs)** – Microsoft support teams no longer accept or investigate incidents (ICMs) related specifically to the V3 client software.

## Examples of out-of-scope scenarios

The following list provides examples of issues that Microsoft no longer investigates for V3.

- **Authentication and identity (Microsoft Entra ID)** – V3 uses legacy authentication libraries that Microsoft no longer maintains.
    - **Unsupported** – Failures related to modern Microsoft Authentication Library (MSAL) flows, *Device not compliant* errors, and new conditional access policies enforced by Microsoft Entra ID.
    - **Resolution** – You must migrate to V4 to use current and secure authentication protocols.

- **Client-side performance and connectivity** – The networking stack and libraries within V3 are frozen at their current versions.
    - **Unsupported** – Issues regarding local latency, connection drops, or timeouts originating from the outdated client-side libraries.
    - **Note** – If a performance issue is verified to be a server-side or service-wide latency issue, Microsoft continues to investigate it as part of standard cloud service support.

- **Operating system (OS) compatibility** – Because Apple (iOS) and Google (Android) continually release new operating system versions, legacy apps often encounter breaking changes.
    - **Unsupported** – Crashes, UI glitches, or failure to launch on mobile OS versions released after 2025.
    - **Resolution** – Continued compatibility is only guaranteed for the V4 application, which is built on the latest software development kits (SDKs).
