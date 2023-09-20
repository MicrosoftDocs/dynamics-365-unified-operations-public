---
title: Price change tracking troubleshooting guide 
description: This article describes common issues for price change tracking in Microsoft Dynamics 365 Commerce, and provides guidance and troubleshooting steps to help system users and partners mitigate the issues.
author: leshe
ms.date: 09/19/2023
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

- The price change tracking batch job takes too long.
- Too many price change tracking batch jobs are triggered and waiting in queue.

## Mitigations

The mitigation for price change tracking issues usually contains two parts: stop creating more batch jobs and clear existing batch jobs.

### Stop creating more batch jobs

To stop creating more batch jobs, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters \> Prices and discounts**
1. Under **Price change tracking**, remove all legal entities from the grid, and then select **Save**.
1. Restart Application Object Server (AOS).

In general, Microsoft recommends that you [specify a batch group for price change tracking batch jobs](/dynamics365/commerce/troubleshoot/price-change-tracking#specify-batch-group-for-price-change-tracking-batch-jobs) prior to enabling the price change tracking feature so that the impact of the price change tracking batch jobs is limited within given AOS instances, instead of blocking the default batch job pool.

### Stop and clear existing batch jobs 

To stop and clear existing batch jobs, run the following script in the Commerce headquarters database.

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

<!--[Price change tracking](../price-change-tracking.md)-->
