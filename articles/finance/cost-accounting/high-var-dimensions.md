---
title: Highly variable dimensions
description: Learn about highly variable dimensions. These financial dimensions are characterized by values that aren't reused, either individually or in combination with other values.
author: twheeloc
ms.author: moaamer
ms.topic: how-to
ms.date: 01/03/2025
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0
---

# Highly variable dimensions

[!include [banner](../../includes/banner.md)]

A *highly variable dimension* is a financial dimension that is characterized by values that aren't reused, either individually or in combination with other values. Financial dimensions are designed for values that persist for years. Therefore, issues with highly variable dimensions typically occur when values are used for only days or weeks. The generation of combinations is a resource-intensive process.

Two types of highly variable dimensions produce numerous combinations:

- **Individual highly variable dimensions** – These dimensions typically appear in only one transaction or a few specific transactions.
- **Combination highly variable dimensions** – These dimensions have limited reusability when they are combined with others. The results are excessive permutations.

## Background

The financial dimension framework enables dimensions values to flow from master data through posted transactions. The financial dimension model is designed for data patterns that have low variability and a high rate of reuse. Therefore, it's unsuitable for high-volume, unique values that don't aggregate well. Because of the loss of aggregation for highly variable dimensions, additional tracking is required for account balances. Therefore, highly variable dimensions slow transaction processing. 

### Examples of highly variable dimensions

The following dimensions lack financial significance and must not be used as financial dimensions:

- **Document numbers:** Sales/purchase order IDs, receipt/sales transaction IDs, and check numbers
- **Serial numbers:** Item serial numbers and batch numbers

These dimensions aren't useful for financial analysis, such as profit and loss statements or trial balances. They must be considered financial tags and not included as financial dimensions.

Examples that lead to highly variable dimensions become problematic if the dimensions are used in combination with others:

- Customer ID
- Vendor ID
- Project ID
- Item ID
- Asset ID
- Employee ID

### Explanation

Even though a highly variable dimension is included in a ledger account, it's ineffective for grouping or reporting because of its highly unique values. Dimensions of this type inflate the number of unique combinations in a dimension set and therefore make it computationally demanding. For example, a highly variable dimension that is based on a unique identifier such as a sales order number doesn't allow for aggregation. Therefore, it leads to slowdowns and high memory usage that affects the size and cost of data storage. If a business uses customers as financial dimensions, regularly adds thousands of new customers, and processes hundreds of thousands of transactions, the results are millions of variable dimensions. Inclusion of a highly variable dimension, such as a unique identifier that has no value reuse, greatly increases combinations and strains system performance.

### Impact on financial processes

Highly variable dimensions significantly affect several financial processes:

- **Year-end close** – During year-end close, all unique dimension values are processed to create new beginning balances. As part of this process, **Rebuild balances** is run to update each dimension. If highly variable dimensions are present, this process creates a high number of combinations and therefore drastically slows down the system.
- **Consolidation** – Like year-end close, consolidation involves the creation of unique combinations of dimension values. This process is delayed if there are numerous highly variable dimensions.
- **General ledger currency revaluation** – The General ledger currency revaluation process creates unique combinations of dimension values. If there are numerous high-volatility dimensions, the process is slowed down.
- **Trial balance** – On a trial balance report, every unique dimension is aggregated onto a single line. Highly variable dimensions reduce aggregation efficiency and slow down balance updates and report generation.
- **Entity import** – The import of records that have highly variable dimensions leads to dimension combinations that aren't reused. The results are many unique entries, which strain system performance and increase the data storage size.

### Recommendations

To optimize financial dimensions, follow these recommendations:

- Align financial dimensions with external reporting and analytics that require aggregation and consistency.
- Use financial tags for detailed internal tracking instead of overloading the financial dimension framework.
- Reserve financial dimensions for high-reuse, low-variability data that is relevant to external reporting.
- Avoid highly variable dimensions such as customer accounts or document numbers, because they create excessive combinations, strain performance, and inflate data storage costs.
- Before implementation, test potentially volatile dimensions, such as customer ID or vendor ID, to evaluate their impact on performance.
