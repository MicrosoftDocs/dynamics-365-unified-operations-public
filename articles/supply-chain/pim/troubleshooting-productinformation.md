---
# required metadata

title: Troubleshoot Product Information
description: This topic describes how to fix issues that you might encounter while working with Product Information.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Product Information
This topic describes how to fix common issues that you might encounter while working with Product Information.

##  Unable to rename a released product 
		
**Resolution/Fix**
It is not possible to rename item numbers for released products as it would lead to corrupted data. We only allow it if and only if you need to repair data corruption caused by a previous rename of the primary key of a released product, as we indicate in https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/deprecated-features#finance-and-operations-1000-with-platform-update-24
