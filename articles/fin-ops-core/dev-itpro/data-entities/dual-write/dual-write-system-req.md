---
title: System requirements for dual-write
description: This topic describes the system requirements for the setup of a dual-write connection.
author: RamaKrishnamoorthy
ms.date: 01/14/2020
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2020-01-14
ms.dyn365.ops.version: AX 7.0.0
---

# System requirements for dual-write

[!include [banner](../../includes/banner.md)]

The setup of a dual-write connection has the following requirements:

+ Finance and Operations apps that have build version 10.0.9 (10.0.383.20013) (Quality update) and platform update 33 or later
+ Customer engagement apps that have platform version 9.1.0000.11732 or later

Dual-write has these limitations:

+ You can't run dual-write and the [Prospect to cash solution](../../../../supply-chain/sales-marketing/accounts-template-mapping-direct.md) for Data integrator side by side. If you're running the Prospect to cash solution for Data integrator, you must uninstall it.
+ Dual-write setup is not supported on trial instances of Finance and Operations apps.
+ Dual-write must be used to integrate a single Finance and Operations app instance and a single customer engagement app instance.
+ Dual-write currently has an initial synchronization limit of 40 legal entities.
+ Dual-write live synchronization has a limit of 250 legal entities.
+ Dual-write does not support [cross-company data sharing](../../sysadmin/cross-company-data-sharing.md).
+ Dual-write requires that the Finance and Operations app and the customer engagement app must be in the same Microsoft Azure Active Directory (Azure AD) tenant.
+ Dual-write requires that the Finance and Operations app and the customer engagement app must be deployed in the same Microsoft Azure datacenter.
+ Dual-write is not triggered by the **doInsert**, **doUpdate**, and **doDelete** events of Finance and Operations apps. Use the **Insert**, **Update**, and **Delete** events in Finance and Operations apps when you want to trigger dual-write. 
+ Dual-write doesn't support distributed transactions. For example, if the [product receipt posting process is cancelled](scm-field-service-procurement.md#cancelling-the-posting-process), dual-write might create the product receipt in Dataverse but not create it in Supply Chain Management. 



## One Version

Future updates of the dual-write solution will be available through One Version.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
