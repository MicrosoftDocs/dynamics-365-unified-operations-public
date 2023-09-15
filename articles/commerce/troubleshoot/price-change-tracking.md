---
title: Price change tracking troubleshooting guide 
description: This article describes common issues for price change tracking in Microsoft Dynamics 365 Commerce, and provides guidance and troubleshooting steps to help system users and partners mitigate the issues.
author: leshe
ms.date: 09/13/2023
ms.topic: Troubleshooting
audience: Application User, Developer, IT Pro
ms.reviewer: 
ms.search.region: Global
ms.author: leshe
ms.search.validFrom: 2023-09-13

---


# Price change tracking troubleshooting

This article describes common issues for price change tracking in Microsoft Dynamics 365 Commerce, and provides guidance and troubleshooting steps to help system users and partners mitigate the issues.


## Symptoms

Common symptoms of price change tracking issues are:
1. The price change tracking batch job takes too long
2. Too many price change tracking batch jobs are triggered and waiting in queue

## Mitigations

The mitigation usually contains 2 parts: stop creating more batch jobs and clear existing batch jobs.

### Mitigation step 1. Stop creating more batch jobs

1. Go to **Retail and Commerce > Headquarters setup > Parameters > Commerce shared parameters > Prices and discounts**
2. Under **Price change tracking**, remove **ALL** legal entities from the grid and save the change
3. Restart AOS

In general, [Specify batch group for price change tracking batch jobs](price-change-tracking.md#specify-batch-group-for-price-change-tracking-batch-jobs) is always a recommended preparation prior to enabling the price change tracking feature, so that the impact of the price change tracking batch jobs is limited within given AOS instances, instead of blocking the default batch job pool.

### Mitigation step 2. Stop and clear existing batch jobs 

Run the following script in HQ database:
```sql
-- find the existing executing jobs
select count(*) from BATCH where CAPTION like '%Price change%' and status = 2 --executing
select count(*) from BATCHJOB where CAPTION like '%Price change%' and status = 2 --executing

-- update the job status (DO NOT update to 0-Hold status, when batch service restarts they will be picked up again) 
update BATCH set STATUS = 3 where CAPTION like '%Price change%' and STATUS = 2 --set to error
Update BATCHJOB set STATUS = 3 where CAPTION like '%Price change%' and STATUS = 2 --set to error

-- clear the jobs
delete from BATCH where CAPTION like '%Price change%' and status = 3 --error
delete from BATCHJOB where CAPTION like '%Price change%' and status = 3 --error
```

## Additional resources

[Price change tracking](../price-change-tracking.md)
