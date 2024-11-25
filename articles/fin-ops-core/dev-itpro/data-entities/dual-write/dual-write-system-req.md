---
title: System requirements for dual-write
description: Learn about the system requirements for the setup of a dual-write connection as is currently supported for various regions.
author: RamaKrishnamoorthy
ms.author: ramasri
ms.topic: conceptual
ms.date: 12/12/2023
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-01-14
ms.dyn365.ops.version: AX 7.0.0
---

# System requirements for dual-write

[!include [banner](../../includes/banner.md)]

## What regions are available?

Currently, we support dual-write in the following regions:

+ Asia
+ Australia
+ Brazil
+ Canada
+ Europe
+ France
+ Germany
+ India
+ Japan
+ South America
+ Switzerland
+ United Arab Emirates
+ United Kingdom
+ United States

> [!NOTE]
> There are currently no plans to support more regions.

The setup of a dual-write connection has the following requirements:

+ finance and operations apps that have build version 10.0.9 (10.0.383.20013) (Quality update) and platform update 33 or later
+ Customer engagement apps that have platform version 9.1.0000.11732 or later

Dual-write has these limitations:

+ You can't run dual-write and the [Prospect to cash solution](../../../../supply-chain/sales-marketing/accounts-template-mapping-direct.md) for Data integrator side by side. If you're running the Prospect to cash solution for Data integrator, you must uninstall it.
+ Dual-write setup is not supported on trial instances of finance and operations apps.
+ Dual-write must be used to integrate a single finance and operations app instance and a single customer engagement app instance.
+ Dual-write currently has an initial synchronization limit of 40 legal entities.
+ Dual-write live synchronization has a limit of 250 legal entities.
+ Dual-write does not support [cross-company data sharing](../../sysadmin/cross-company-data-sharing.md).
+ Dual-write requires that the finance and operations app and the customer engagement app must be in the same Microsoft Entra tenant.
+ Dual-write requires that the finance and operations app and the customer engagement app must be deployed in the same Microsoft Azure datacenter.
+ Dual-write is not triggered by the **doInsert**, **doUpdate**, and **doDelete** events of finance and operations apps. Use the **Insert**, **Update**, and **Delete** events in finance and operations apps when you want to trigger dual-write. 
+ Dual-write doesn't support distributed transactions. For example, if the [product receipt posting process is cancelled](../../../fin-ops/data-entities/scm-field-service-procurement.md#cancelling-the-posting-process), dual-write might create the product receipt in Dataverse but not create it in Supply Chain Management. 



## One Version

Future updates of the dual-write solution will be available through One Version.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
