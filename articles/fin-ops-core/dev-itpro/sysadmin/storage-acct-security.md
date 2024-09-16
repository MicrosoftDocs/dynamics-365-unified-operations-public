---
title: Finance and operations storage account security updates
description: This article describes the latest security enhancements in the finance and operations storage account.
author: mansijainms
ms.author: mansijain 
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 09/12/2024
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2024-09-12
ms.dyn365.ops.version: 
---

# Finance and operations storage account security updates

[!include [banner](../../../finance/includes/banner.md)]

This article describes the latest security enhancements in the finance and operations storage account.

## Frequently asked questions

### I receive the following error on my developer machine/customer-hosted environment: "Fetching a valid storage connection string is disabled." How can I fix this error?

The `Microsoft.Dynamics.Clx.ServicesWrapper.CloudInfrastructure::GetCsuStorageConnectionString()` public method is being deprecated. Learn more in [End of support for sharing storage account connection strings via public API GetCsuStorageConnectionString](/fin-ops/get-started/removed-deprecated-features-platform-updates#end-of-support-for-sharing-storage-account-connection-strings-via-public-api-getcsustorageconnectionstring).

If the flight is set to *false* by default, an issue occurs when changes are deployed in developer environments or customer-hosted environments (CHEs). In this case, you receive the following error on your developer machine:

> EnableSharingOfValidStorageConnectionString is false. Fetching a valid storage connection string has been disabled.

If you receive the error, follow these steps.

1. In Microsoft SQL Server Management Studio (SSMS), run the following query.

    ```sql
    declare @flightName NVARCHAR(100) = 'EnableSharingOfValidStorageConnectionString';
    IF NOT EXISTS (SELECT TOP 1 1 FROM SysFlighting WHERE flightName = @flightName)
    INSERT INTO SYSFLIGHTING(FLIGHTNAME,ENABLED, FLIGHTSERVICEID,PARTITION)
    SELECT @flightName, 1, 12719367,RECID FROM DBO.[PARTITIONS];
    ELSE
    UPDATE SysFlighting SET enabled = 1, flightServiceId = 12719367 WHERE flightName = @flightName;
    select * from SysFlighting where flightName = 'EnableSharingOfValidStorageConnectionString';
    ```

2. In the CHE, restart Application Object Server (AOS) and the Batch service.
