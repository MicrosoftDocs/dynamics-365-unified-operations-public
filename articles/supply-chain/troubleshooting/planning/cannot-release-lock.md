---
# required metadata

title: Posting results for journal with specific batch number. Not able to release lock in due time.
description: Posting results for journal with specific batch number. Not able to release lock in due time.
author: ankubik@microsoft.com
manager: tfehr
ms.date: 4/25/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: Dialog_ReqCalcScheduleItemTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: ankubik@microsoft.com
ms.assetid: 
ms.search.region: Global
ms.author: ankubik@microsoft.com

---

# Posting results for journal with specific batch number. Not able to release lock in due time.

Error code: SCM:AppLockLockNotReleasedBeforeTimeout

The system displays the followign error message:
	SCM:AppLockLockNotReleasedBeforeTimeout



## Symptoms
When GTE tax calculating, there are error message: Posting results for journal batch number XXX Not able to release lock in due time.




## Resolution
The "ReaderWriterUserConnection" flight should be enabled. For Mooncake and on an IaaS (not Service Fabric) sandbox environments you can use following sql query:

BEGIN TRANSACTION;  

-- Insert or update an enabled flight:
DECLARE @flightName NVARCHAR(100) = 'ReaderWriterUserConnection';
IF NOT EXISTS (SELECT TOP 1 1 FROM SysFlighting WHERE flightName = @flightName)
INSERT INTO SYSFLIGHTING(FLIGHTNAME,ENABLED, FLIGHTSERVICEID,PARTITION)
SELECT @flightName, 1, 12719367,RECID FROM DBO.[PARTITIONS];
ELSE
UPDATE SysFlighting SET enabled = 1, flightServiceId = 12719367 WHERE flightName = @flightName;


COMMIT TRANSACTION;



