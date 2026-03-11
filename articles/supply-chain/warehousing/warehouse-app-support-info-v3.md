---
title: Support Guidance for Warehouse Management App
description: Learn support dates and conditions of Warehouse Management v3 to migrate from Warehouse Management. The article includes information about compatibility, requirements, and the timeline.
author: Nsayginer
ms.author: Nsayginer
ms.topic: how-to
ms.date: 03/11/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Support Guidance for Warehouse Management App (V3/Xamarin) 

As previously announced in the [Migration to V4 Guide](warehouse-app-migrating-from-v3-v4.md)., the Xamarin-based version (V3) of the Warehouse Management mobile app will reach its official **End of Support (EOS) in May 2026**. 

This transition ensures that all users benefit from the enhanced security, stability, and performance offered by the modern  architecture of V4. After the May 2026 milestone, the following support policies will go into effect.  

### Scope of Support After May 2026 

While the back-end APIs will remain compatible for a transitional period to prevent immediate service disruption, the V3 client application itself is considered **legacy**. 

- **No New Releases**: We can no longer build, patch, or release updates for the V3 app due to the deprecation of the underlying *Xamarin* framework. 

- **Incident Management (ICMs)**: Support teams will no longer accept or investigate incidents (ICMs) related specifically to the V3 client software. 

### Examples of Out-of-Scope Scenarios 

To help your IT teams prepare, the following are examples of issues that will **no longer be investigated** for the V3 application: 

- **Authentication and Identity (Microsoft Entra ID)**

  The V3 application utilizes legacy authentication libraries that are no longer being maintained. 
  
    - **Unsupported**: Failures related to modern MSAL (Microsoft Authentication Library) flows, "Device not compliant" errors, or new conditional access policies enforced by Microsoft Entra ID. 
  
    - **Resolution**: Users must migrate to V4 to utilize current, secure authentication protocols. 

- **Client-Side Performance and Connectivity** 

  The networking stack and libraries within V3 are frozen at their current versions. 
  
    - **Unsupported**: Issues regarding local latency, connection drops, or timeouts originating from the outdated client-side libraries. 
  
    - **Note**: If a performance issue is verified to be a **server-side** or service-wide latency issue, Microsoft will continue to investigate as part of standard cloud service support. 

- **Operating System (OS) Compatibility** 

  As Apple (iOS) and Google (Android) release new operating system versions, legacy apps often encounter "breaking changes." 
  
    - **Unsupported**: Crashes, UI glitches, or failure to launch on new mobile OS versions released after 2025. 
  
    - **Resolution**: Continued compatibility is only guaranteed on the V4 application, which is built on the latest SDKs. 

 
