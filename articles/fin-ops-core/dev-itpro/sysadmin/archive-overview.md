---
title: Archive solution overview
description: This article provides an overview of how to use the archive solution to archive various types of records in finance and operations apps.
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

Finance and operations applications generate business data at a regular cadence over time.  On average, medium to upper-mid market businesses accumulate over a terabyte of data in less than five years. The data growth is directly proportional to the age of the business and the number of transactions made year over year.

## How the solution works

The *archive solution* lets you archive transactional data to *history tables* within the transactional SQL database. These history tables have *limited indexing*, which results in a significant reduction in the storage space used. From a user perspective, data moves from the live tables to the history tables as a single process, but the system actually moves the data using several smaller database transactions to avoid processing delays in other areas of the app. The following steps happen as a single process from the user perspective:

1. The system copies the data range specified from the live tables to the history tables.
1. The system removes the data range specified from the live tables.

> [!NOTE]
> Data in the history tables can't be edited.

## The Archive workspace

Use the **Archive** workspace to create and work with your archives. It lets you do the following actions:

- Set up and schedule move to history jobs
- Monitor the progress of running jobs
- Review the move to history and logs
- Reverse move to history (for example, if you need to edit the data of a history record)

## Next steps

- Install the required add-in and enable the features you need as described in [Set up the archive solution](archive-setup.md)
- [Extend the archive solution to support custom tables and fields](archive-customizations.md)
- [Archive general ledger data](archive-general-ledger.md)
- [Archive sales orders](archive-sales-orders.md)
