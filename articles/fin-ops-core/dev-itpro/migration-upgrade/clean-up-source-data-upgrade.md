---
# required metadata

title: Clean up source data for upgrade from Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations
description: This topic describes how to clean up source data as part of an upgrade from Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations.
author: ttreen 
ms.date: 04/22/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Clean up source data for upgrade from Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations

[!include [banner](../includes/banner.md)]

This topic describes how to clean up source data as part of an upgrade from Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations. 

## Background

Over time the Microsoft Dynamics AX 2012 database can grow to a large size. Reducing the size of the database by purging or archiving data prior to the upgrade can reduce the time that it takes to complete the data upgrade.

## Clean-up operations

The following clean-up operations should be run before upgrading to Dynamics 365 Finance + Operations.

### Run the Dynamics AX Intelligent Data Management Framework (IDMF) tool

Although no longer being updated, the Dynamics AX Intelligent Data Management Framework (IDMF) tool can be used as a way to archive or purge data in the Dynamics AX 2012 database. For more information, see [Dynamics AX Intelligent Data Management Framework](/dynamicsax-2012/appuser-itpro/microsoft-dynamics-ax-intelligent-data-management-framework-idmf).

### Clean up batch job history tables

The following tables can be fully or partially cleaned directly in SQL or via a custom X++ job. There are no out-of-the-box clean-up scripts, so you'll need to develop something yourself.
 - BatchJobHistory
 - BatchHistory
 - BatchConstraintsHistory

