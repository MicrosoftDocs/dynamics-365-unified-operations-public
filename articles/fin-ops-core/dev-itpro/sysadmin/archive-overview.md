---
title: Archive overview
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

# Archiving overview

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Dynamics 365 Finance and Operations applications customers naturally
generate business data at a regular cadence over time.  On average,
medium to upper-mid market businesses accumulate \>1TB of data in less
than 5 years. The data growth is directly proportional to the age of the
business and the number of transactions made YoY.

## Solution
The **Archive** solution will provide the ability to **archive
transactional data to a [historical table]{.underline}** within the
transactional SQL database. These historical tables will have *limited
indexing* which results in a **significant reduction in storage space
used**.  The movement of data from the live tables to the 'history
tables' happens as one process from a user perspective but will occur in
small database transactions on the server to avoid processing delays in
other areas of the application. 

The following steps happen as a single process from the user
perspective:

-   F&O copies the data range specified from the Live tables to the
    History tables.

-   F&O removes the data range specified from the Live tables.

**Note**: Data cannot be changed once it is moved to the historical
table set. 

The solution will also provide the ability to 'reverse' data from the
historical table back to the live table in case you need the data to be
moved back for any unexpected requirement, or if you need to rectify the
archive data selection. 

## Next steps

- Install the required add-in and enable the features you need as described in [Set up record Archive](archive-setup.md)
- [Archive sales orders](archive-sales-orders.md)
