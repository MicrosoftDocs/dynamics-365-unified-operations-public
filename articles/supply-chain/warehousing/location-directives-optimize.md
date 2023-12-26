---
title: Optimize location directive queries
description: This article describes how to use the Optimize location directive queries tool to identify location directive queries that use a suboptimal query pattern and transform them so that they use the optimal querying approach that the new data model enables.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 05/26/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Optimize location directive queries

Because of recent improvements to the on-hand inventory data model, location directive queries can now run much faster than before. However, if you've been running Microsoft Dynamics 365 Supply Chain Management for a while, you might have many older location directives that still use queries that were designed for the old data model. The *Optimize location directive queries* tool identifies location directive queries that use a suboptimal query pattern and transforms them so that they use the optimal querying approach that the new data model enables.

The [optimization advisor](../../fin-ops-core/dev-itpro/sysadmin/optimization-advisor-overview.md) now includes a rule that periodically checks whether your queries can be optimized. If it identifies the potential for improvement, it generates an optimization advisor opportunity that highlights the changes and suggests that you to run the tool as described in this article.

> [!IMPORTANT]
> - We recommend that you first run the tool on a user acceptance testing (UAT) environment. You should run it on your production environment only after you're sure that all location directives still behave as expected in the UAT environment, and that all [location directive acceptance tests](location-directive-acceptance-tests.md) still pass.
> - Avoid running the tool during peak hours. It will lock your location directives and flush them from all application object servers. Therefore, waving and work creation will run slower for the duration of the job.

## Prerequisites

To use the *Optimize location directive queries* tool, you must be running Supply Chain Management 10.0.35 or later.

## Run the tool

Follow these steps to run the *Optimize location directive queries* tool.

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Optimize location directive queries**.
1. The **Optimize location directive queries** dialog box appears. If you want to limit the scope of the optimization, on the **Records to include** FastTab, select **Filter** to open a standard query editor dialog box, where you can define selection criteria. The fields work just as they do for other types of queries in Supply Chain Management.
1. On the **Run in the background** FastTab, specify how, when, and how often the tool should run. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.

    - We recommend that you run the tool only as it's needed instead of setting up a recurring schedule.
    - As was mentioned, we also recommend that you run the tool only during off-peak hours. Therefore, instead of running it immediately, consider setting it up as a batch job that's scheduled to run just once at an appropriate time (such as Sunday at 8 PM).

1. Select **OK** to run the tool by using the options that you selected.

## How it works

Location directives for picks typically rely on on-hand inventory information that's available in the `InventSum` table to determine where items should be picked from. Because location directive queries usually include inventory dimensions to ensure that product variants are considered when this determination is made, these queries previously required a join between the `InventSum` and `InventDim` tables. However, the data model has now been denormalized to optimize this common query pattern. All the required information is now available directly in the `InventSum` table. The elimination of a join operation typically boosts the performance of location directive queries by 30 to 50 percent.

The *Optimize location directive queries* tool transfers all ranges from `InventDim` to `InventSum` and removes the join to `InventDim`.
