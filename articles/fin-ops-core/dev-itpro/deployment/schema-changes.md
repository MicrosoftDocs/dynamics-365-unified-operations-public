---

title: How to make schema changes for shorter downtime during custom package deployments
description: This article describes how to make schema changes for shorter downtime when deploying custom packages
author: gianugo
ms.date: 11/09/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# How to make schema changes for shorter downtime during custom package deployments

[!include [banner](../includes/banner.md)]

This article describes best practices and guidelines for having near zero downtime while applying table schema changes when planning custom package deployments.

## Deployment phases
During any custom package deployment, environments go through the following phases:
1. **Pre-servicing**: The system is accessible to the users and the environment can be used. Many online table schema changes can be made.
2. **Servicing**: The downtime starts and all the online unsupported schema changes are made.
3. **Post-servicing**: When index related schema changes are applied with online options. The customer can start using their environment in this phase.

## Online supported changes
SQL provides online schema change that can be done without exclusive locks on the table. Finance and operations deployments are modified to use these online options to perform most of the schema changes without causing downtime for the users. 

The following list identifies the changes that are supported online and the related phase:

|Supported changes | Phase |
|------------|-----------|
|All new field addition to the table.| **Pre-servicing**|
| All string size increase field change. String size decreases are ignored as it can result in data truncation.| **Pre-servicing**|
| All string to memo field changes that don't require dependent index drops.|**Pre-servicing**|
| All memo to string field changes if it doesn't cause data truncation. |**Pre-servicing**|
| All nonclustered index addition and modifications.| **Pre-servicing**|
| Nonprimary clustered index changes that don't require CI drop, including adding/removing fields from nonprimary CI, changing it from one index to another.| **Pre-servicing**|
| Nonclustered primary key change from one index to another.| **Pre-servicing**|
| Columnstore index changes that don't require index drop.|**Pre-servicing**|


>[!Note]
> These changes happen in the **Pre-servicing** and **Post-servicing** phases with online options, the execution time of these phases depend on numerous factors like type of schema change, number of such changes, size of the tables or any transient blockers.
> Altering fields such as memo to string and clustered index changes can be time consuming as the table has to be rebuilt. Explore options to add new field or new table or if it's a staging table, check if the data can be removed before the alter. String size decrease changes are ignored during database synchronization as it results in data loss.



## Unsupported online changes
Remaining schema changes not covered in the above section aren't supported online yet in finance and operations deployments and should be avoided. These run in the **Servicing** phase of deployments when the environment is down. 

Below is a list of changes and suggestions:

1. Clustered PK change: Changing a clustered primary key for a table can't be done online. It's not recommended to change the primary key of the table as it is likely to be used in multiple other indexes. We suggest adding a new table with corrected primary index.
2. Numeric field scale change: In finance and operations, changing scale of a numeric field is allowed and isn't supported online. It's recommended to add a new field instead of modifying the existing one if the table size is larger.
3. Index drops: No index drop is supported online. Avoid changes that can cause clustered and/or primary index drop.
4. String to memo field change when it's the single field in the index resulting in index drop: Sql restricts any memo field to be part of the index. If any index has this single field, the index needs to be
dropped and it isn't a supported change. For such cases, the index can be altered to include more fields and later can be removed if not needed in the next deployments.
5. Fulltext index changes: This isn't supported online.

## How to effectively plan custom deployments for production environments
Consider the following before applying a custom package to production environment:
 - Apply the package to sandbox environment, on a production copy, to determine the time required for each phase. Production deployments can be scheduled based on time required. Customers can keep using their environment in the **Pre-servicing** and **Post-servicing** phases.
 - Avoid online unsupported changes wherever possible. If it's needed, avoid adding multiple changes in a single package as it can increase the deployment downtime.
