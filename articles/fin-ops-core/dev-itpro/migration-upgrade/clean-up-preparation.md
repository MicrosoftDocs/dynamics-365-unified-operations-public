---
# required metadata

title: Clean-up preparation
description: An overview sentence that describes what this article is all about.
author: ttreen 
ms.date: 04/08/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Clean-up Preparation
[!include[banner](../includes/banner.md)]

This topic provides information on cleaning up source data as part of an upgrade from Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations 

## Background
Over time the Microsoft Dynamics AX 2012 database can grow to a large size. Reducing the size of the database by purging or archiving data prior to the upgrade can reduce the time it will take to complete the data upgrade.

## Clean-up Operations

### Dynamics AX Intelligent Data Management Framework (IDMF)
Although no longer being updated, the IDMF tool can be used as a way to archive or purge data in the AX 2012 database. See:
[Dynamics AX Intelligent Data Management Framework](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/microsoft-dynamics-ax-intelligent-data-management-framework-idmf)

### Batch Job History
The following tables can be fully or partially cleaned directly in SQL or via a custom x++ job. There are no out of the box clean-up scripts, so you'll need to develop something youself.
 - BatchJobHistory
 - BatchHistory
 - BatchConstraintsHistory

