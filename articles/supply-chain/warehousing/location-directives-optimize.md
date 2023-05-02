---
title: Optimize location directive queries
description: This topic describes how to use the Optimize location directive queries tool, which identifies location directive queries that are using a sub-optimal query pattern and transforms them to use the optimal querying approach made possible by the new data model.
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

As a result of recent improvements made to the on-hand inventory data model, location directive queries can now run much faster than before. However, if you've been running Supply Chain Management for a while, you may have many older location directives that are still using queries that were designed for the old data model. The *Optimize location directive queries* tool identifies location directive queries that are using a sub-optimal query pattern and transforms them to use the optimal querying approach made possible by the new data model.

The [optimization advisor](../../fin-ops-core/dev-itpro/sysadmin/optimization-advisor-overview.md) now includes a rule that periodically checks whether your queries can be optimized. If it identifies a potential for improvement, it generates an optimization advisor opportunity that highlights the changes and suggests that you to run the tool as described in this article.

> [!IMPORTANT]
>
> - We recommend that you run the tool on a user acceptance testing (UAT) environment before you run it on a production environment. Make sure that all location directives are still behaving as expected on the UAT environment, and that all [location directive acceptance tests](location-directive-acceptance-tests.md) are still passing. Only if all tests are successful should you then run the tool on your production environment.
> - Avoid running the tool during during peak hours. It will lock your location directives and flush them from all application object servers, which will cause waving and work creation to run slower for the duration of the job.

## Prerequisites

To use the *Optimize location directive queries* tool, you must be running Supply Chain Management 10.0.35 or higher. <!-- KFM: Any other requirements? Feature management? -->

## Run the tool

Follow these steps to run the *Optimize location directive queries* tool:

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Optimize location directive queries**.
1. The **Optimize location directive queries** dialog opens.
1. If you'd like to limit the scope of the optimization, then expand the **Records to include** FastTab and select **Filter** to open a standard query editor dialog, where you can define selection criteria. The fields work just as they do for other types of queries in Supply Chain Management.
1. On the **Run in the background** FastTab, specify how, when, and how often to run the tool. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management. <!-- KFM: Any recommendations here? Use Batch or no? Schedule or no? Anything else? -->
1. Select **OK** to run the tool using the options you selected.

## How it works

<!-- KFM: Please review my edit to the following text. -->

Location directives for picks typically rely on on-hand inventory information available in the `InventSum` table to determine where to pick from. Because location directive queries normally include inventory dimensions to make sure product variants are considered when deciding where an item should be stored, these queries previously required a join between the `InventSum` and `InventDim` tables. However, the data model has now been denormalized to optimize this very common query pattern, so now, all the required information is available directly in the `InventSum` table. This saves a join operation, which typically boosts location directive queries by 30-50%.

The *Optimize location directive queries* tool transfers all ranges from `InventDim` to `InventSum`, and removes the join to `InventDim`.
