---
# required metadata

title: Upgrade from AX 2012 - Data Upgrade FAQ
description: This topics answers some common questions about data upgrade when upgrading from AX 2012.
author: ttreen
ms.date: 06/25/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 2021-06-25

---

# Upgrade from AX 2012 - Data Upgrade FAQ

[!include[banner](../includes/banner.md)]

This topic answers some common questions about the data upgrade when upgrading from AX 2012.

## Is the tier 2 Azure SQL database sized enough for large databases upgrades? 
If the database size grows, Tier 2 sandbox deployed on “Elastic pool” should auto-resize as needed.

## Does this toolkit support Microsoft's Government Community Cloud (GCC)?
It’s currently not supported.

## What kind of validations are being done as part of this toolkit?
There are few validations in place e.g., validate whether you have installed required KBs (pre-requisites) in AX2012 or not. If you haven’t installed required KBs in AX2012, you will not be able to start the replication process. There is also the option to run a record count check on the replicated data.

## If source AX2012 database is in different region than target, what's the recommendation in such scenario?
Recommendation is to have both source and target in the same region for optimal replication performance. Customers can deploy Sandbox in the same region as source and complete data upgrade. After the upgrade, move the Sandbox to the needed region. 

## Is SQL BACPAC and DACPAC processes are still supported for AX2012 data upgrade in Sandbox?
No, both BACPAC and DACPAC processes are no longer supported for AX2012 data upgrade in Sandbox. This toolkit is the only way for customers to perform data-upgrade in Sandbox environments. 

## I’ve upgraded an AX2012 database in a DEV (Tier-1) environment and uploaded the upgraded BACPAC file into LCS. I am getting the error below when importing this BACPAC file from LCS into Sandbox environment. How to resolve this error? 
#### Error: "Importing AX2012 bacpac file into Dynamics 365 environment is not supported as it would result in a loss of the imported data and would put the environment in a failed state."
We have validation not to allow BACPAC import into Sandbox environment if your project implementation type is ‘AX2012 data upgrade’. You must use AX2012 Database Upgrade Toolkit for Dynamics 365 for data upgrade and perform data upgrade in Sandbox environment. 


## Can I filter on the table data that will be replicated e.g., to limit specific records only for replication to the target database?
No, this is not supported within AX2012 Database Upgrade Toolkit. 
