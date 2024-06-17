---
title: Upgrade from AX 2012 - Data upgrade FAQ
description: Access answers to some frequently asked questions about data upgrade during an upgrade from Microsoft Dynamics AX 2012.
author: ttreen
ms.author: ttreen
ms.topic: article
ms.date: 08/02/2021
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-07-01
---

# Upgrade from AX 2012 – Data upgrade FAQ

[!include[banner](../includes/banner.md)]

This article answers some frequently asked questions about data upgrade during an upgrade from Microsoft Dynamics AX 2012.

## Is the Tier 2 Azure SQL database sized enough for upgrades of large databases?

If the database size grows, a Tier 2 sandbox that is deployed on an "elastic pool" should automatically be resized as required.

## Does the AX 2012 Database Upgrade Toolkit for Dynamics 365 support the Microsoft Government Community Cloud?

No, the AX 2012 Database Upgrade Toolkit for Dynamics 365 doesn't currently support the Government Community Cloud (GCC).

## What type of validation is done as part of the AX 2012 Database Upgrade Toolkit for Dynamics 365?

Few validations are done as part of the AX 2012 Database Upgrade Toolkit for Dynamics 365. For example, the toolkit validates that you've installed the required KBs (prerequisites) in AX 2012. If you haven't installed them, you can't start the replication process. There is also an option to run a record count check on the replicated data.

## What is the recommended approach if the source AX 2012 database is in a different region than the target database?

For optimal replication performance, we recommend that the source AX 2012 database and the target database be in the same region. Customers can deploy the sandbox environment in the same region as the source and do the data upgrade. Then, after the upgrade is completed, the sandbox environment can be moved to the required region.

## Are the SQL BACPAC and DACPAC processes still supported for AX 2012 data upgrades in sandbox environments?

No, the SQL BACPAC and DACPAC process are no longer supported for AX 2012 data upgrades in sandbox environments. Customers must use the AX 2012 Database Upgrade Toolkit for Dynamics 365 to do data upgrades in sandbox environments.

## I've upgraded an AX 2012 database in a cloud hosted environment (dev) and uploaded the upgraded BACPAC file into Lifecycle Services. However, I receive an error message when I then try to import the BACPAC file into a sandbox environment. How do I fix the error?

When you try to import an upgraded BACPAC file from Microsoft Dynamics Lifecycle Services (LCS) into a sandbox environment, you might receive the following error message:

> Importing AX 2012 bacpac file into Dynamics 365 environment isn't supported as it would result in a loss of the imported data and would put the environment in a failed state.

Validation is done to prevent a BACPAC file from being imported into a sandbox environment. For the AX 2012 database upload into a sandbox environment, you must use the AX 2012 Database Upgrade Toolkit for Dynamics 365, which utilizes SQL replication to transfer the data.

## Can I filter on the table data that will be replicated (for example, to limit specific records only for replication to the target database)?

No, the AX 2012 Database Upgrade Toolkit for Dynamics 365 doesn't support filtering on the table data that will be replicated.
