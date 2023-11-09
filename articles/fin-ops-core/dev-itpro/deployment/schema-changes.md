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

This articles describes some best practices and guidelines for having near zero downtime while applying table schema changes to AxDB that Dynamics 365 finance and operations customers can use while planning their 
custom package deployments.

## Deployment phases
During any custom package deployment, the environment first goes to 'Pre-Servicing' phase. This is when the system is still accessible to the users, and they can login and use the environment. Many additive 
online table schema changes are made here. After this the downtime starts and the environment stays in the 'Servicing' phase. This is where all the online unsupported schema changes are made. This article provides details on all the points to keep in mind to reduce the downtime. After servicing, the environment goes to 'Post-Servicing' phase. This is where the majority of the index related schema changes are applied with online options. The customer can start using their environment in this phase.

## Online supported changes
SQL provides online schema change that can be done without exclusive locks on the table, i.e. table stays available for read and write operations. Finance and operations deployments are being modified to use these online options to perform most of the schema changes that can be done online without causing downtime for the users. 

The following list identifies the changes that are supported online:
 - All new field addition to the table. [Pre-Servicing]
 - All string size increase field change. (string size decreases are ignored as it can result in data truncation) [Pre-Servicing]
 - All string to memo field changes that don't require dependent index drops. [Pre-Servicing]
 - All memo to string field changes given it doesn't cause data truncation. [Pre-Servicing]
 - All non-clustered index addition and modifications. [Post-Servicing]
 - Non-Primary clustered index changes that don't require CI drop (including adding/removing fields from non-primary CI, changing it from one index to another). [Post-Servicing]
 - Non-clustered primary key change from one index to another. [Post-Servicing]
 - Columnstore index changes that do not require index drop. [Post-Servicing]


>[!Note]
> Since these changes are happening in Pre and Post servicing with online options, the execution time of these phases can be high depending on numerous factors like type of schema change, number of such changes,
> size of the tables, any transient blockers etc.
> Altering fields such as memo to string and clustered index changes can take a lot of time if there's a large table size as these internally requires whole table to be rebuilt. We have seen cases where memo to string on 300 GB table took 16 hours when run online. Explore the option to add new field/ new table instead OR if it's a staging table, check if the data can be removed before the alter.
> String size decrease change is ignored during database synchronization as it results in data loss.



## Online Unsupported changes
All the remaining schema changes not covered in the above section are not supported online yet in finance and operations deployments and should be avoided wherever possible. These run in the 'Servicing' phase of the deployments where the environment is down. 

Below is a list of changes and suggestions for avoiding these and alternatives:

1. Clustered PK change: Changing a clustered primary key for a table can't be done online. In general, it's not recommended to change the primary key of the table as it is likely to be used in multiple
other indexes. We suggest adding a new table with corrected primary index.
2. Numeric field scale change: In finance and operations, changing scale of a numeric field is allowed. This isn't supported online in finance and operations deployments. It's recommended to add a new field instead of modifying the existing one if the table size is larger.
3. Index drops: No index drop is supported online. Non clustered index drops will soon be supported online. Avoid changes that can cause clustered and/or primary index drop.
4. String to memo field change when it is the single field in the index resulting in index drop: Sql restricts any memo field to be part of the index. If any index has this single field, then the index needs to be
dropped and it isn't a supported change. For such cases, the index can be altered to include more fields and later can be removed if not needed in the next deployments.
5. Fulltext index changes: This isn't supported online.

## How to effectively plan custom deployments for Prod environments?
The following points should be considered before applying a custom package to Production instance:
 - Apply the package to sandbox environment, on a prod copy, to determine the time required for each servicing phase. Prod deployment can be scheduled based on this. Customers can keep using their environment in
   Pre and Post servicing phases.
 - Avoid online unsupported changes wherever possible. If it's needed, avoid adding multiple such changes in a single package as it can increase the deployment downtime.
