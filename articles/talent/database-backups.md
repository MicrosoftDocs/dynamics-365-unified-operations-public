---
# required metadata

title: How are database backups handled?
description: Customer wants to understand SQL backups.
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
ms.author: rschloma
ms.search.validFrom: 2018-11-02
ms.dyn365.ops.version: Talent

---

# How are database backups handled?

[!include [banner](includes/banner.md)]


**Environment details:** 

>   Production environments provisioned through LCS

**Problem:** 

-   Customer wants to understand the SQL backup plan for Talent.

-   Customer wants to restore a SQL backup for a Production environment.

-   Customer wants to move a database from a Production to a Test environment.

**Solution:** 

-   We use a Standard Azure SQL SKU for Talent, and you can learn more about the
    backup story here:

>   <https://docs.microsoft.com/en-us/azure/sql-database/sql-database-automated-backups>.

-   Restoring an in-place Production environment backup is a Development
    Operations (DevOps) procedure that is something that should be considered
    expensive. In fact, we have limits how far back we can restore since the
    code packages are being upgraded nearly every week, and we wouldn’t want to
    restore a backup that isn’t compatible with the current version of the code
    package. So, we would have to consider the best approach on a case-by-case
    basis.

-   Moving a database from a Production to a Test environment is presently a
    DevOps motion. Microsoft does not currently provide a way to move or copy
    DBs in the LCS (Life Cycle Services) experience today. This is a feature
    that has been requested but has not been completed yet. The recommended
    option is making use of data entity packages for export / import between
    environments.

Long-term solution:

-   Longer term future plans to add an option to copy a Production database to a
    Test environment.
