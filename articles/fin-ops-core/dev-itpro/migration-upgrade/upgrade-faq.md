---
# required metadata

title: Upgrade from AX 2012 - Data upgrade FAQ
description: This topics answers some common questions about data upgrade when upgrading from AX 2012.
author: ttreen
ms.date: 06/30/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 2021-06-30

---

# Upgrade from AX 2012 - Data upgrade FAQ

[!include[banner](../includes/banner.md)]

This topic answers some common questions about the data upgrade when upgrading from AX 2012.

## Is the Tier 2 Azure SQL database sized enough for large databases upgrades? 
If the database size grows, Tier 2 sandbox deployed on “Elastic pool” should auto-resize as needed.

## Does this toolkit support Microsoft's Government Community Cloud (GCC)?
It’s currently not supported.

## What kind of validations are being done as part of this toolkit?
There are few validations in place e.g., validate whether you have installed required KBs (pre-requisites) in AX 2012 or not. If you haven’t installed required KBs in AX 2012, you will not be able to start the replication process. There is also the option to run a record count check on the replicated data.

## If source AX 2012 database is in different region than the target database, what's the recommendation in such scenario?
Recommendation is to have both source and target in the same region for optimal replication performance. Customers can deploy the sandbox environment in the same region as the  source and complete data upgrade. After the upgrade, move the sandbox environemnt to the needed region. 

## Are the SQL BACPAC and DACPAC processes still supported for AX 2012 data upgrade in sandbox?
No, both BACPAC and DACPAC processes are no longer supported for AX 2012 data upgrade in sandbox environments. This toolkit is the only way for customers to perform data upgrade in sandbox environments. 

## I’ve upgraded an AX 2012 database in a DEV (Tier 1) environment and uploaded the upgraded BACPAC file into Lifecycle Services (LCS). I am getting the error below when importing this BACPAC file from LCS into a sandbox environment. How do I resolve this error? 

**Error: "Importing AX 2012 bacpac file into Dynamics 365 environment is not supported as it would result in a loss of the imported data and would put the environment in a failed state."**

We have validation not to allow BACPAC import into a sandbox environment if your project implementation type is **AX2012 data upgrade**. You must use the AX 2012 Database Upgrade Toolkit for Dynamics 365 for data upgrade and perform data upgrade in a sandbox environment. 

## Can I filter on the table data that will be replicated e.g., to limit specific records only for replication to the target database?
No, this is not supported within AX 2012 Database Upgrade Toolkit. 
