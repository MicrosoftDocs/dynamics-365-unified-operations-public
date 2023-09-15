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


# Price change tracking troubleshooting guide

[!include [banner](../../includes/banner.md)]

This article describes common issues for price change tracking in Microsoft Dynamics 365 Commerce, and provides guidance and troubleshooting steps to help system users and partners mitigate the issues.

## Guidance for feature adoption

### Specify batch group for price change tracking batch jobs

The price change tracking feature triggers batch jobs to run in the background. To prevent the batch jobs blocking other critical jobs from processing, it is recommended to specify a batch group following the steps below:
1. Reuse an existing batch group or [create a batch group](/dynamicsax-2012/appuser-itpro/create-a-batch-group)
2. Go to **Retail and Commerce > Headquarters setup > Parameters > Commerce shared parameters > Prices and discounts**
3. Under **Backend tasks**, specify the batch group which will be used to run pricing batch jobs. It is recommended to dedicate a few AOS instances to that batch group, separate from other instances dedicated to processing of backbone operations.

*Please refer to [LCS Issue 830636](https://fix.lcs.dynamics.com/Issue/Details/?bugId=830636&dbType=3)* for the availability of batch group support.

### Usage patterns not suitable for feature enablement

The price change tracking feature is enabled by default for Azure Search configured legal entities. It is efficient when tracking occasional changes based on stable settings, so the following usage patterns are not recommended for feature enablement:
1. Large-scale changes (for example, bulk data migration)
2. Hightly frequent update of pricing or product data (for example, more than one line per second)

For such cases, it is recommended to temporarily disable the feature by removing **ALL** legal entities from **Price change tracking** grid in **Retail and Commerce > Headquarters setup > Parameters > Commerce shared parameters > Prices and discounts** and **restart AOS**. After the data changes are done, to re-enabled the feature for desired legal entities, add them back to the grid and **restart AOS**. If AOS restart is not practical, please make sure the aforementioned batch group for pricing processing is properly setup, so the pricing jobs generated would not impact processing of other system batch tasks.

### Cross-company entity change tracking

The following tables are cross-company entities, and modifying them will trigger change tracking, even if the legal entity where changes are made is not set up for change tracking:

- RetailGroupMemberLine
- RetailChannelTable
- RetailCatalogPriceGroup
- RetailChannelPriceGroup
- EcoResProductCategory

## Troubleshooting

### Symptoms

Common symptoms of price change tracking issues are:
1. The price change tracking batch job takes too long
2. Too many price change tracking batch jobs are triggered and waiting in queue

### Mitigations

The mitigation usually contains 2 parts: stop creating more batch jobs and clear existing batch jobs.

#### Mitigation step 1. Stop creating more batch jobs

1. Go to **Retail and Commerce > Headquarters setup > Parameters > Commerce shared parameters > Prices and discounts**
2. Under **Price change tracking**, remove **ALL** legal entities from the grid and save the change
3. Restart AOS

In general, [Specify batch group for price change tracking batch jobs](price-change-tracking.md#specify-batch-group-for-price-change-tracking-batch-jobs) is always a recommended preparation prior to enabling the price change tracking feature, so that the impact of the price change tracking batch jobs is limited within given AOS instances, instead of blocking the default batch job pool.

#### Mitigation step 2. Stop and clear existing batch jobs 

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