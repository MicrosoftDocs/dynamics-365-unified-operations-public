---
title: Finance and operations storage account security updates
description: This article describes the latest security enhancements in finance and operations storage account. 
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

This article describes the latest security enhancements in finance and operations storage account. 

## Frequently asked questions (FAQs)

### I'm receiving  "Fetching a valid storage connection string is disabled" error in dev machine/CHE. How can I resolve this?
The public method, Microsoft.Dynamics.Clx.ServicesWrapper.CloudInfrastructure::GetCsuStorageConnectionString() is getting deprecated. For more information, see [End of support for sharing storage account](/fin-ops/get-started/removed-deprecated-features-platform-updates.md#end-of-support-for-sharing-storage-account-connection-strings-via-public-api-getcsustorageconnectionstring). An issue has been identified while deploying changes in developer environments or customer hosted environments (CHE) as the flight is set to false by default. If you're receiving the following error in your developer machine: <br> “EnableSharingOfValidStorageConnectionString is false. Fetching a valid storage connection string has been disabled”, follow these steps: <br><br>
a) Execute the below query in SSMS: <br>
declare @flightName NVARCHAR(100) = 'EnableSharingOfValidStorageConnectionString'; <br>
IF NOT EXISTS (SELECT TOP 1 1 FROM SysFlighting WHERE flightName = @flightName) <br>
INSERT INTO SYSFLIGHTING(FLIGHTNAME,ENABLED, FLIGHTSERVICEID,PARTITION) <br>
SELECT @flightName, 1, 12719367,RECID FROM DBO.[PARTITIONS]; <br>
ELSE <br>
UPDATE SysFlighting SET enabled = 1, flightServiceId = 12719367 WHERE flightName = @flightName; <br>
select * from SysFlighting where flightName = 'EnableSharingOfValidStorageConnectionString';<br><br>
b) Restart AOS and Batch service in CHE Environment.
