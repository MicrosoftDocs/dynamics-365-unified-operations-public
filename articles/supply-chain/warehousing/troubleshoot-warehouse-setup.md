---
# required metadata

title: Troubleshoot warehouse setup
description: This topic describes how to fix common issues that you might encounter while setting up warehouses in Dynamics 365 Supply Chain Management.
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

# Troubleshoot warehouse setup

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while setting up warehouses in Dynamics 365 Supply Chain Management.

## Security roles and permission for the warehouse mobile device portal.
<!-- KFM: Is the device portal the same as the device emulator? I think maybe we should instead call this the "warehouse app emulator", but I'm not sure. -->
**Issue:** Unable to use roles different than administrator on the mobile device emulator.

**Fix:** The mobile emulator is set to work only with the administrator account. For all testing and live process purposes, we recommend using the warehouse app itself.
