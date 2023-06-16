---
title: Archive solution overview
description: This article provides an overview of the archive solution that you can use to archive different types of records in finance and operations apps.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: ArchiveWorkspace
ms.topic: overview
ms.date: 06/13/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Archive solution overview

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Finance and operations apps generate business data on a regular cadence over time. On average, medium to upper-mid-market businesses accumulate over a terabyte of data in under five years. The data growth is directly proportional to the age of the business and the number of transactions that are made year over year.

## How the solution works

The *archive solution* lets you archive transactional data to *history tables* in the transactional SQL database. Because these history tables have *limited indexing*, the amount of storage space that's used is significantly reduced. To help prevent processing delays in other areas of the app, the system moves data from the live tables to the history tables through several smaller database transactions:

1. Copy the specified data range from the live tables to the history tables.
1. Remove the specified data range from the live tables.

Nevertheless, from a user perspective, the movement of data occurs as a single process.

> [!NOTE]
> Data in the history tables can't be edited.

## The Archive workspace

Use the **Archive** workspace (**System administration \> Workspaces \> Archive**) to create and work with your archives. From the **Archive** workspace, you can perform the following actions:

- Set up and schedule move-to-history jobs.
- Monitor the progress of running jobs.
- Review the move to history and logs.
- Reverse the move to history (for example, if you must edit the data of a history record).

## Next steps

- [Set up the archive solution](archive-setup.md) – Install the required add-in, and enable the features that you need.
- [Extend the archive solution to support custom tables and fields](archive-customizations.md)
- [Archive general ledger data](archive-general-ledger.md)
- [Archive sales orders](archive-sales-orders.md)
