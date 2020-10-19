---
# required metadata

title: Troubleshoot upgrade and migration to advanced warehouse management
description: This topic describes how to fix common issues that you might encounter while upgrading and migrating to advanced warehouse management.
author: perlynne
manager: tfehr
ms.date: 10/19/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2020-10-19
ms.dyn365.ops.version: 10.0.15
---

# Troubleshoot upgrade and migration to advanced warehouse management

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while upgrading and migrating to advanced warehouse management.

## java.security.cert.certPathValidatorException: Trust anchor for certification path is not found.
<!-- KFM: some context is needed for this heading-->
**Issue:** On OnPrem environments, self-signed certificates are not trusted on Android 8+ causing this error to occur on the warehouse mobile app.

**Fix:** Use external (public) CA. A fix for this issue has been made available in 1.9.0.0. <!-- KFM: is this the same as the issue already described in [Troubleshoot warehouse app connection issues](troubleshoot-warehouse-app-connection.md)? -->

## Moving from Basic to Advanced Warehousing.

**Issue:** We are currently running under stock/inventory management and using basic stock functionality. We want to move to advanced warehousing to take advantage of mobile devices, waves, and work. We cannot change our products to use storage dimensions (site, warehouse, and location) as they have transactions against them. What is the approved process to move from basic to advanced warehousing?

**Fix:** See the following blog posts for more information about the process:

- [Enable warehouse management process for existing items and warehouses](https://cleverax.wordpress.com/2017/12/06/d365fo-enable-warehouse-management-process-for-existing-items-and-warehouses/)
- [Migration of Microsoft Dynamics AX WMS to new R3 warehouse and transportation functionality](https://cloudblogs.microsoft.com/dynamics365/no-audience/2015/08/17/migration-of-microsoft-dynamics-ax-wms-to-new-r3-warehouse-and-transportation-functionality/)
- [WMSI/WMS2 item migration](https://cloudblogs.microsoft.com/dynamics365/no-audience/2018/05/03/wmsiwms2-item-migration/)
