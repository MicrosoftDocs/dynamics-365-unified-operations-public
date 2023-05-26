---
title: Record archiving overview
description: This article provides an overview of how to archive various types of records in finance and operations apps.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: overview
ms.date: 05/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Record archiving overview

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Finance and operations applications generate business data at a regular cadence over time.  On average, medium to upper-mid market businesses accumulate over a terabyte of data in less
than five years. The data growth is directly proportional to the age of the business and the number of transactions made year over year.

## How the solution works

The archive solution lets you archive transactional data to *historical tables* within the transactional SQL database. These historical tables have *limited indexing*, which results in a significant reduction in the storage space used. From a user perspective, data moves from the live tables to the history tables as a single process, but the system actually moves the data using several smaller database transactions to avoid processing delays in other areas of the app. The following steps happen as a single process from the user perspective:

1. The system copies the data range specified from the live tables to the history tables.
1. The system removes the data range specified from the live tables.

> [!NOTE]
> Data can't be changed once it is moved to a historical table.

The solution also provides the ability to reverse data from the historical table back to the live table if needed, such as if you need to rectify the archived data.

## Next steps

- Install the required add-in and enable the features you need as described in [Set up record archiving](archive-setup.md)
- [Extend the archive solution to support custom tables and fields](archive-customizations.md)
- [Work with the Archive workspace](archive-using.md)
