--- 
title: Certification path error when upgrading or migrating to WMS 
description: If the app shows the error “Trust anchor for certification path not found” when upgrading or migrating to WMS, this page gives info on how to fix the issue. 
author: perlynne 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form:  
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: perlynne 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 
 # Trust anchor for certification path not found when updating and migrating to WMS

## Symptoms

When upgrading and migrating to advanced warehouse management (WMS), the Warehouse Management app may show you the following error message:

> java.security.cert.certPathValidatorException: Trust anchor for certification path not found.

## Cause

This occurs because self-signed certificates aren't trusted on Android 8+ in on-premises environments.

## Resolution

Use an external (public) certifying authority (CA). A fix for this issue is available in version 1.9.0.0 of the Warehouse Management app. For more information on this issue and how to fix it, see [Trust anchor for certification path not found when setting up app connection](certification-path-app-connection-error.md).
