---
# required metadata

title: Clean up source data for upgrade from Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations
description: This topic describes how to clean up source data as part of an upgrade from Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises).
author: ttreen 
ms.date: 04/26/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Clean up source data for upgrade from Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations

[!include [banner](../includes/banner.md)]

This topic describes how to clean up source data as part of an upgrade from Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises).

## Background

Over time, the Dynamics AX 2012 database can grow to a large size. Before the upgrade, you can reduce the size of the database by purging or archiving data. In this way, you can help reduce the time that is required to complete the data upgrade.

## Clean-up operations

The following clean-up operations should be run before you upgrade to Dynamics 365 Finance + Operations.

### Run the Dynamics AX Intelligent Data Management Framework tool

Although the Dynamics AX Intelligent Data Management Framework (IDMF) tool is no longer being updated, you can use it to archive or purge data in the Dynamics AX 2012 database. For more information, see [Dynamics AX Intelligent Data Management Framework](/dynamicsax-2012/appuser-itpro/microsoft-dynamics-ax-intelligent-data-management-framework-idmf).

### Clean up batch job history tables

You can fully or partially clean the following tables either directly in SQL or via a custom X++ job. There are no out-of-box clean-up scripts. Therefore, you will have to develop something yourself.

- BatchJobHistory
- BatchHistory
- BatchConstraintsHistory
