---
# required metadata

title: Commerce Data Exchange best practices
description: This topic is intended for people who implement functionality that is related to data synchronization (Commerce Data Exchange, or CDX) in a Microsoft Dynamics 365 Commerce environment. It gives best practices advice for implementations.
author: jashanno
manager: AnnBe
ms.date: 08/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailTerminalTable, RetailDevice
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2020-08-31
ms.dyn365.ops.version: 10.0.12
---

# Commerce Data Exchange best practices
[!include[banner](../includes/banner.md)]

This topic is intended for people who implement functionality that is related to data synchronization (Commerce Data Exchange \[CDX]) in a Microsoft Dynamics 365 Commerce environment. It gives best practices advice for implementations.

## Overview

Proper data configuration and data synchronization are crucial to correctly functioning implementation. Regardless of business requirements, IT infrastructure, and overall preparedness, if data isn't correctly synchronized, the whole environment is effectively useless. Therefore, a top priority is to understand what is required to configure, generate, synchronize, and verify data across the full implementation from Commerce headquarters through the Commerce Scale Unit to the brick-and-mortar stores that use Modern POS with an offline database.

Before you go through this topic, it's important that you understand the concepts of a channel (store), registers and devices, and the Modern POS offline database. Therefore, we recommend that you review some of the resources at the end of this topic, such as the Device management implementation guide and the overview of the Commerce architecture.

The main content of this topic is organized into tables, where the first column includes lists of tag-like "associated areas" to help you more quickly find best practices that are related to your areas of concern. For new implementations, you might find it useful to copy these tables to a location where you can check off the various best practices as they are completed. In this way, you can help ensure that the implementation is prepared as well as possible before you move forward to production.

## Valuable configurations

| Associated areas | Best practice |
|------------------|---------------|
| <ul><li>Parameters</li><li>Commerce scheduler</li><li>Retry</li></ul> | Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce scheduler parameters**, and set the **Try count** field to **3**. If the value of this field is too high, download sessions might fail during high-usage times. |
| <ul><li>Functionality profile</li><li>Data retention</li><li>Return policy</li> | Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profile**, and then, in the **Functions** section, set the **Days transactions exist** field to a value that is the same as, or close to, the value that is defined for the return policy. For example, if the return policy states an item can be returned within 30 days, set this field to **30**, **31**, or **60** if special exceptions are allowed beyond the normal policy (this would be twice the normal policy, allowing for faster returns even beyond the normal policy limits). |
| <ul><li>Channel database group</li><li>Distribution schedule</li><li>Offline profile</li><li>Pause</li><li>Data</li><li>Download</li></ul> | We highly recommend that you have either a "dummy" channel database group (that is, a group that isn't associated with any distribution schedule job) that you assign to the newly generated terminals, or a special offline profile where the **Pause offline synchronization** option is set to **Yes**. In this way, data generation can occur when it's required and when the system is most available to do it. (However, the system might pause multiple times as required.) |

## Practices that affect performance

| Associated areas | Best practice |
|------------------|---------------|
| <ul><li>Channel database group</li><li>Offline profile</li><li>Pause</li><li>Data</li><li>Download</li></ul> | <p>Don't generate data for offline databases until that data is required so that an offline database can be used. The following scenario shows why this best practice is important.</p><p>A new Modern POS offline database that has been added to the relevant channel database group inherits all existing download sessions since the last full database synchronization occurred. One hundred new Modern POS instances that have offline terminals are created, and a full synchronization hasn't occurred in two months. Only five scheduler jobs have actual changes every 20 minutes. (For example, these changes might involve prices and discounts, or customers, which can be updated often.) In this scenario, up to 2,000,000 download sessions are immediately generated and must be applied, regardless of whether the newly created terminals are activated and capable of applying this data.</p><p>Even at the best times, this type of exceptional data generation is large and affects performance. At the worst (that is, busiest) times, it severely impairs the environment's performance. Therefore, we highly recommend that you either have a "dummy" channel database group (that is, a group that isn't associated with any distribution schedule job) that you assign to the newly generated terminals, or set the **Pause offline synchronization** option for the offline profile to **Yes**. By setting the **Pause offline synchronization** option to **Yes**, you stop data generation for anything that uses the offline profile. Therefore, data generation can occur only when it's required, instead of constantly, and only when the system is most available to do it. (However, the system might pause multiple times as required.) |
| <ul><li>Distribution schedule</li><li>Scheduler jobs</li><li>Upload</li></ul> | No more than one P-job (upload batch job) should occur at any time. If multiple P-job upload batch jobs are created that might occur in parallel, table locking and delays (performance degradation) could occur while data of the uploaded transactions is being applied. The job doesn't have to occur multiple times at the same time. It can just occur frequently. |

## Resources

- [Commerce Data Exchange troubleshooting](CDX-Troubleshooting.md) 
- [Commerce Data Exchange implementation guidance](implementation-considerations-cdx.md) 
- [Dynamics 365 Commerce architecture overview](../commerce-architecture.md) 
- [Select an in-store topology](retail-in-store-topology.md) 
- [Device management implementation guidance](../implementation-considerations-devices.md) 
- [Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md) 
- [Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md) 
