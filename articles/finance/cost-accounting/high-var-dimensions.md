--- 
title: High variable dimensions
description: This article describes high variable dimensions.
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

#  High variable dimensions

[!include [banner](../../includes/banner.md)]

A highly variable dimension is a financial dimension characterized by values that aren't reused, either individually or in combination with others. Highly variable dimension issues typically arise when values are used for only days or weeks, while financial dimensions are designed for values that persist over the years. Generating combinations is resource-intensive. 
Two types of highly variable dimensions that produce numerous combinations: 
 - Individual highly variable dimensions - typically appear in only one or a few specific transactions.
 - Combination highly variable dimensions - limited reusability when combined with others, resulting in excessive permutations. 

## Background  

Highly variable dimensions slow transaction processing due to the additional tracking for account balances due to the loss of aggregation. The financial dimension framework allows dimensions values to flow from 
master data through posted transactions. The financial dimension model is designed for low variability and high reuse data patterns, making it unsuitable for high-volume unique values that don't aggregate well. 

### Examples of highly variable dimensions  

These dimensions lack financial significance and must not be used as financial dimensions: 

 - Document numbers: Sales/Purchase order ID, receipt/sales transaction ID, and check number.
 - Serial numbers: Item serial number and batch number. 

These dimensions aren't useful for financial analysis, such as profit and loss statements or trial balances. It must be considered as financial tags and not included as financial dimensions. 

Examples that result in highly variable dimensions become problematic if used in combination with others:  
 - Customer ID
 - Vendor ID
 - Project ID
 - Item ID
 - Asset ID
 - Employee ID 

### Explanation  

A highly variable dimension is included in a ledger account but is ineffective for grouping or reporting due to its highly unique values. Such dimensions inflate the number of unique combinations in a 
dimension set, making it computationally demanding. For instance, if a highly variable dimension is based on a unique identifier like a sales order. It doesn't permit aggregation, leading to slowdowns and high 
memory usage that impacts the data storage size and cost. When a business uses customers as financial dimensions, regularly adds thousands of new customers, and processes hundreds of thousands of transactions, it leads to millions of variable dimensions. Including a highly variable dimension, such as a unique identifier with no value reuse, greatly increases combinations and strains system performance. 

### Impact on financial processes  

Highly variable dimensions significantly impact several financial processes: 
 - Year-end close - During year-end closing, all unique dimension values are processed to create new beginning balances. This includes running **Rebuild balances** to update each dimension. If highly variable dimensions are present, this process creates a high number of combinations, drastically slowing down the system.
 - Consolidations - Similar to year-end close, consolidations involve creating unique combinations of dimension values. This delays the process if there are numerous highly variable dimensions.
 - General ledger currency revaluation - The General ledger currency revaluation process creates unique combinations of dimension values. If there are numerous high-volatility dimensions, this slows the process.
 - Trial balance - In a trial balance report, every unique dimension aggregates into a single line. Highly variable dimensions reduce aggregation efficiency and slows down balance updates and report generation.
 - Entity imports - Importing records with highly variable dimensions results in dimension combinations that aren't reused. This leads to a high number of unique entries, straining system performance and increasing the storage data size. 

### Recommendations 

To optimize financial dimensions: 
 - Align financial dimensions with external reporting and analytics that require aggregation and consistency.
 - Use financial tags for detailed internal tracking instead of overloading the financial dimension framework.
 - Reserve financial dimensions for high reuse, low variability data relevant to external reporting.
 - Avoid highly variable dimensions like customer accounts or document numbers, as they create excessive combinations, strain performance, and inflate data storage costs.
 - Test potentially volatile dimensions, such as customer ID or vendor ID, before implementation to evaluate their impact on performance. 


