---
# required metadata

title: Troubleshoot upgrade and migration to advanced warehouse management
description: This topic describes how to fix common issues that you might encounter while you upgrade and migrate to advanced warehouse management.
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

This topic describes how to fix common issues that you might encounter while you upgrade and migrate to advanced warehouse management.

## I receive the following error message: "java.security.cert.certPathValidatorException: Trust anchor for certification path is not found."

### Issue description

You receive this error message in the warehouse app, because self-signed certificates aren't trusted on Android 8+ in on-premises environments.

### Issue resolution

Use an external (public) certifying authority (CA). A fix for this issue is available in version 1.9.0.0 of the warehouse app. For more information about this issue and how to fix it, see [Troubleshoot warehouse app connection issues](troubleshoot-warehouse-app-connection.md).

## What is the approved process for moving from basic warehousing to advanced warehousing?

### Issue description

You're currently running under stock/inventory management and using basic stock functionality, and you want to move to advanced warehousing to take advantage of mobile devices, waves, and work. However, you're experiencing issues when you try to make this move. For example, you can't change your products so that they use storage dimensions (site, warehouse, and location), because the products have transactions against them. Therefore, you must learn the approved process for moving from basic warehousing to advanced warehousing.

### Issue resolution

For more information about the process for moving from basic warehousing to advanced warehousing, see the following blog posts and documentation:

- [Enable warehouse management process for existing items and warehouses](https://cleverax.wordpress.com/2017/12/06/d365fo-enable-warehouse-management-process-for-existing-items-and-warehouses/)
- [Migration of Microsoft Dynamics AX WMS to new R3 warehouse and transportation functionality](https://cloudblogs.microsoft.com/dynamics365/no-audience/2015/08/17/migration-of-microsoft-dynamics-ax-wms-to-new-r3-warehouse-and-transportation-functionality/)
- [WMSI/WMS2 item migration](https://cloudblogs.microsoft.com/dynamics365/no-audience/2018/05/03/wmsiwms2-item-migration/)
- [Upgrade warehouse management from Microsoft Dynamics AX 2012 to Supply Chain Management](https://docs.microsoft.com/dynamics365/supply-chain/warehousing/upgrade-migration-warehouse-management-processes)
