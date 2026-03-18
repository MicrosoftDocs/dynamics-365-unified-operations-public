---
title: Upgrade from AX 2012 - Data upgrade FAQ
description: Access answers to some frequently asked questions about data upgrade during an upgrade from Microsoft Dynamics AX 2012.
author: ttreen
ms.author: ttreen
ms.topic: faq
ms.date: 03/17/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-07-01
---

# Upgrade from AX 2012 – Data upgrade FAQ

[!include[banner](../includes/banner.md)]

This article answers some frequently asked questions about data upgrade during an upgrade from Microsoft Dynamics AX 2012.

## Is the Tier 2 Azure SQL database sized enough for upgrades of large databases?

If the database size grows, a Tier 2 sandbox that you deploy on an elastic pool automatically resizes as required.

## Does the AX 2012 Database Upgrade Toolkit for Dynamics 365 support the Microsoft Government Community Cloud?

No, the AX 2012 Database Upgrade Toolkit for Dynamics 365 doesn't currently support the Government Community Cloud (GCC).

## What type of validation is done as part of the AX 2012 Database Upgrade Toolkit for Dynamics 365?

The AX 2012 Database Upgrade Toolkit for Dynamics 365 performs a few validations. For example, the toolkit validates that you installed the required KBs (prerequisites) in AX 2012. If you didn't install them, you can't start the replication process. There's also an option to run a record count check on the replicated data.

## What is the recommended approach if the source AX 2012 database is in a different region than the target database?

For optimal replication performance, the source AX 2012 database and the target database need to be in the same region. Deploy the sandbox environment in the same region as the source and perform the data upgrade. Then, after the upgrade finishes, move the sandbox environment to the required region.

## Are the SQL BACPAC and DACPAC processes still supported for AX 2012 data upgrades in sandbox environments?

No, the SQL BACPAC and DACPAC processes aren't supported for AX 2012 data upgrades in sandbox environments. Use the AX 2012 Database Upgrade Toolkit for Dynamics 365 to perform data upgrades in sandbox environments.

## I upgraded an AX 2012 database in a cloud-hosted environment (dev) and uploaded the upgraded BACPAC file into Lifecycle Services. However, I receive an error message when I try to import the BACPAC file into a sandbox environment. How do I fix the error?

When you try to import an upgraded BACPAC file from Microsoft Dynamics Lifecycle Services (LCS) into a sandbox environment, you might receive the following error message:

> Importing AX 2012 bacpac file into Dynamics 365 environment isn't supported as it would result in a loss of the imported data and would put the environment in a failed state.

Validation prevents importing this BACPAC file into a sandbox environment. For the AX 2012 database upload into a sandbox environment, you must use the AX 2012 Database Upgrade Toolkit for Dynamics 365, which uses SQL replication to transfer the data.

## Can I filter the table data for replication to limit specific records to the target database?

No, the AX 2012 Database Upgrade Toolkit for Dynamics 365 doesn't support filtering on the table data that it replicates.
