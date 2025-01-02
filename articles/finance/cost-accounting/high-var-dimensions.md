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

Definition A highly variable dimension is a financial dimension characterized by values that are not reused, either individually or in combination with others. Highly variable dimension issues typically arise 
when values are used for only days or weeks, while financial dimensions are designed for values that persist over the years. Generating combinations is resource-intensive, and the following two types of highly
variable dimensions produce numerous combinations: 

Individually highly variable dimensions, These typically appear in only one or a few specific transactions. 

Combination- highly variable dimensions, These exhibit limited reusability when combined with others, resulting in excessive permutations. 

Background  

Highly variable dimensions slow transaction processing due to the additional tracking for account balances due to the loss of aggregation. The Financial dimension framework allows dimensions values to flow from 
master data through posted transactions. However, it is often misused as a quick way to add fields or data without modifying forms, tables, or processes. The financial dimension model is designed for 
low-variability and high-reuse data patterns, making it unsuitable for high-volume unique values that do not aggregate well. 

Examples of individually highly variable dimensions  

These dimensions lack financial significance and must not be used as financial dimensions: 

Document Numbers: Sales/Purchase Order ID, Receipt/Sales Transaction ID, Check # 

Serial Numbers: Item Serial #, Batch# 

These dimensions are not useful for financial analysis, such as profit and loss statements or trial balances, and must be considered as financial tags, and not included as financial dimensions. 

Examples that result in highly variable dimensions certain dimensions will become problematic if used in combination with others. These must be employed cautiously after performance testing: 

Customer ID, Vendor ID, Project ID, Item ID, Asset ID, Employee ID 

Explanation  

A highly variable dimension is included in a ledger account but is ineffective for grouping or reporting due to its highly unique values. Such dimensions will inflate the number of unique combinations in a 
dimension set, making it computationally demanding. For instance, if a highly variable dimension is based on a unique identifier like a Sales Order, it does not permit aggregation, leading to slowdowns and high 
memory usage that will impact the data storage size and cost as well. When a business uses customers as financial dimensions, regularly adds thousands of new customers, and processes hundreds of thousands of 
transactions, it will lead to millions of variable dimensions. Including a highly variable dimension, such as a unique identifier with no value reuse, greatly increases combinations and puts a strain on system 
performance. 

Impact on financial processes  

Highly variable dimensions are  significantly impact several financial processes: 

Year-End Close During year-end closing, all unique dimension values must be processed to create new beginning balances. This includes running a "Rebuild Balances" process to update each dimension. If highly 
variable dimensions are present, this process will lead to significantly high number of combinations, drastically slowing down the system. 

Consolidations Similar to year-end close, consolidations involve creating unique combinations of dimension values, which will delay the process if there are numerous highly variable dimensions. 

General ledger currency revaluation Like year-end close and consolidations, the GL currency revaluation process creates unique combinations of dimension values. If there are numerous high-volatility dimensions, 
this will slow down the process significantly. 

Trial Balance In a trial balance report, every unique dimension aggregates into a single line, so highly variable dimensions reduce aggregation efficiency and slow down balance updates and report generation. 

Entity Imports Importing records with highly variable dimensions results in no reuse of dimension combinations, which can lead to significantly high number of unique entries, straining system performance and 
increase the storage data size. 

 

Recommended alternative option To optimize financial dimensions: 

Align financial dimensions with external reporting and analytics that require aggregation and consistency. 

Use financial tags for detailed internal tracking instead of overloading the financial dimension framework. Financial tags - Finance | Dynamics 365 | Microsoft Learn 

Reserve financial dimensions for high-reuse, low- variability data relevant to external reporting. 

Avoid highly variable dimensions like customer accounts or document numbers, as they create excessive combinations, strain performance, and inflate data storage costs. 

Test potentially volatile dimensions, such as Customer ID or Vendor ID, before implementation to evaluate their impact on performance. 

By balancing aggregation needs with system efficiency, businesses can optimize financial reporting, analytics, transaction processing, and overall performance. 
