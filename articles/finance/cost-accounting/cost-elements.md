---
title: Cost element dimensions
description: As one of the core pillars in Cost accounting, cost element dimensions are used to categorize and track where costs flow to.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: article
ms.date: 05/27/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: global
ms.search.validFrom: 2016-11-30
ms.search.form: CAMDimension
ms.dyn365.ops.version: Version 1611
ms.assetid: 1eda0e62-760b-4737-9dfd-3c3c38d80c1a
---

# Cost element dimensions

[!include [banner](../includes/banner.md)]

As a core pillar in cost accounting, use cost element dimensions to categorize and track where costs flow.

A cost element corresponds to a cost-relevant item in the chart of accounts. It can be any type of element at the lowest level in a business where costs can flow. The concept of cost elements includes ledger accounts and all cost-relevant resources. Currently, Cost accounting supports ledger accounts.

## Two types of cost elements

There are two types of cost elements: primary cost elements and secondary cost elements. The following table describes the difference between the two types.

| **Primary cost elements** | **Secondary cost elements** |
|---|---|
| The primary cost elements represent the flow of costs from financial accounting to cost accounting. The cost element structure corresponds to the profit and loss account structure in the general ledger, where a cost element can correspond to a main account. Not all main accounts need to be represented as cost elements depending on the business needs. Examples of primary cost elements include:<ul><li>Costs of goods sold (COGs)</li><li>Indirect material costs</li><li>Personnel costs</li><li>Energy costs</li></ul> | The secondary cost elements represent the flow of costs internally because these costs are created and used only in Cost accounting. Use them to ensure that you can trace the source of costs. Use these cost elements in cost allocations and overhead calculations. Examples of secondary cost elements include:<ul><li>Production costs</li><li>Production, material, and marketing overheads</li></ul> |

## Cost element dimensions and cost element dimension members

Cost elements are *cost element dimensions*. The individual dimension values are *cost element dimension members*. For example, you have a US chart of accounts structure (COA) that serves as the base for your statutory reporting. Use this COA as the cost element dimension. The accounts, which are primary cost elements, appear as the cost element dimension members in Cost accounting. The following screenshot shows an example of Main Accounts as the cost element dimension with its actual main accounts as the cost element dimension members.

:::image type="content" source="./media/cost-element-dimensions.png" alt-text="Screenshot of Main Accounts as cost element dimension." lightbox="./media/cost-element-dimensions.png":::

## Import cost element dimension members through data connectors

To simplify the setup of cost element dimension members in Cost accounting, use data connectors that are either prebuilt or custom built to retrieve the primary cost elements from one or more source systems.

## Implementation considerations

Because cost elements represent the lowest level of cost details, make sure you include all the cost elements required for managerial reporting when you implement the cost elements structure. It can be a challenge to find an appropriate number of cost elements for cost control. Having thousands of cost elements can make it difficult to control each cost element. As an alternative, group cost elements and manage cost control at an aggregated level.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
