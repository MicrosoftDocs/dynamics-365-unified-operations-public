---
title: Finance and operations storage account security updates
description: This article describes 
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

This article describes the latest security enhancements that we are doing in interaction with FnO storage account. A brief of all modifications and decprecations can be found at [Removed or deprecated platform features](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/removed-deprecated-features-platform-updates).

## Disabling public access to storage connection string via public API GetCsuStorageConnectionString
Public method: Microsoft.Dynamics.Clx.ServicesWrapper.CloudInfrastructure::GetCsuStorageConnectionString() is getting depcrecated. More details are [here](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/removed-deprecated-features-platform-updates.md#end-of-support-for-sharing-storage-account-connection-strings-via-public-api-getcsustorageconnectionstring).

###Note for dev machines and CHE environments
An issue has been identified while deploying changes in developer environments or customer hosted environments (CHE) as the flight is set to false by default. If you're receiving the following error in your developer machine: <br> “EnableSharingOfValidStorageConnectionString is false. Fetching a valid storage connection string has been disabled”, follow these steps to get unblocked: <br><br>
a) Execute the below query in SSMS: declare @flightName NVARCHAR(100) = 'EnableSharingOfValidStorageConnectionString';
IF NOT EXISTS (SELECT TOP 1 1 FROM SysFlighting WHERE flightName = @flightName)
INSERT INTO SYSFLIGHTING(FLIGHTNAME,ENABLED, FLIGHTSERVICEID,PARTITION)
SELECT @flightName, 1, 12719367,RECID FROM DBO.[PARTITIONS];
ELSE
UPDATE SysFlighting SET enabled = 1, flightServiceId = 12719367 WHERE flightName = @flightName;
select * from SysFlighting where flightName = 'EnableSharingOfValidStorageConnectionString';<br><br>
b) Restart AOS and Batch service in CHE Environment.
