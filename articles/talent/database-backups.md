---
# required metadata

title: How database backups are handled
description: The customer wants to understand SQL backups.
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


**Environment details:** 

Production environments provisioned through Lifecycle Services (LCS).

**Problem:** 

-   The customer wants to understand the SQL backup plan for Dynamics 365 for Talent.

-   Customer wants to restore a SQL backup for a production environment.

-   Customer wants to move a database from a production to a test environment.

**Solution:** 

-   Talent uses a Standard Azure SQL SKU. You can learn more about the
    backup story by reading [Learn about automatic SQL Database backups](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-automated-backups).

-   Restoring an in-place production environment backup is a Development
    Operations (DevOps) procedure that is something that should be considered
    expensive. In fact, we have limits how far back we can restore since the
    code packages are being upgraded nearly every week, and we wouldn’t want to
    restore a backup that isn’t compatible with the current version of the code
    package. So, we would have to consider the best approach on a case-by-case
    basis.

-   Moving a database from a production to a test environment is presently a
    DevOps operation. Microsoft does not currently provide a way to move or copy
    DBs in the LCS experience today. This is a feature
    that has been requested but has not been completed yet. The recommended
    option is making use of data entity packages for export/import between
    environments.

**Long-term solution:**

Longer term future plans to add an option to copy a production database to a test environment.
