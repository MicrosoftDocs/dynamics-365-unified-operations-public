---
# required metadata

title: How database backups are handled
description: This topic will help customers who want to understand SQL backups.
author: Darinkramer
manager: AnnBe
ms.date: 11/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2018-11-02
ms.dyn365.ops.version: Talent

---

# How database backups are handled

[!include [banner](includes/banner.md)]

**Environment details**

Production environments that are provisioned through Microsoft Dynamics Lifecycle Services (LCS)

**Issue**

- The customer wants to understand the SQL backup plan for Microsoft Dynamics 365 for Talent.
- The customer wants to restore a SQL backup for a production environment.
- The customer wants to move a database from a production environment to a test environment.

**Solution**

- Talent uses a standard Microsoft Azure SQL Database stock keeping unit (SKU). For more information about backups, see [Learn about automatic SQL Database backups](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-automated-backups).
- Restoration of an in-place production environment backup is a Development Operations (DevOps) operation that should be considered expensive. In fact, there are limits on how far back we can restore backups. Because the code packages are upgraded almost every week, we don't want to restore a backup that isn't compatible with the current version of the code package. Therefore, we must consider the best approach on a case-by-case basis.
- Currently, moving a database from a production environment to a test environment is a DevOps operation. Microsoft doesn't currently provide a way to move or copy databases in the LCS experience. This feature has been requested but hasn't yet been completed. We recommend that you use data entity packages to export/import between environments.

**Long-term solution**

As part of our longer-term future plans, we intend to add an option to copy a production database to a test environment.
