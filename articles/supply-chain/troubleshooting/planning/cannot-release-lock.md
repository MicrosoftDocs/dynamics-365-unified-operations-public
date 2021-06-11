---
title: Not able to release lock in due time
description: "When you are calculating GTE tax, you get the error: 'Posting results for journal batch number %1 Not able to release lock in due time.'"
author: ankubik
ms.date: 06/10/2021
ms.topic: troubleshooting
ms.search.form: Dialog_ReqCalcScheduleItemTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: ankubik
ms.search.validFrom: 2021-06-10
ms.dyn365.ops.version: 10.0.20
---

# Not able to release lock in due time

Error code: SCM:AppLockLockNotReleasedBeforeTimeout

## Symptoms

<!-- KFM: Spell out "GTE". Please confirm the error text (looks wrong--doesn't seem to match the intro sentence, and maybe a period missing?) -->

When you are calculating GTE tax, the system displays the following error message:

> Posting results for journal batch number %1 Not able to release lock in due time.

## Resolution

<!-- We do not normally document flighted features. Are we sure we want to mention this issue at all? What is "Mooncake"--is that a customer-facing term? What do I do if I am not on "mooncake" or if I am on Service Fabric? -->

You need to enable the flight called `ReaderWriterUserConnection`. To enable the flight on Mooncake and on an Infrastructure as a service (IaaS) installation (not on Service Fabric installations), use following SQL query:

```sql
BEGIN TRANSACTION;  

-- Insert or update an enabled flight:
DECLARE @flightName NVARCHAR(100) = 'ReaderWriterUserConnection';
IF NOT EXISTS (SELECT TOP 1 1 FROM SysFlighting WHERE flightName = @flightName)
INSERT INTO SYSFLIGHTING(FLIGHTNAME,ENABLED, FLIGHTSERVICEID,PARTITION)
SELECT @flightName, 1, 12719367,RECID FROM DBO.[PARTITIONS];
ELSE
UPDATE SysFlighting SET enabled = 1, flightServiceId = 12719367 WHERE flightName = @flightName;


COMMIT TRANSACTION;
```
