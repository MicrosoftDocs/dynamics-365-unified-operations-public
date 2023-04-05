---
# required metadata

title: Financial reporting best practices
description: This article provides tips and best practices for optimizing financial reports in Microsoft Dynamics 365 Finance.
author: aprilolson
ms.date: 04/04/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: FinancialReports
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: ["10444", "intro-internal"]
ms.assetid: 3eae6dc3-ee06-4b6d-9e7d-1ee2c3b10339
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Financial reporting best practices

[!include [banner](../includes/banner.md)]

This article provides tips and best practices for optimizing financial reports in Microsoft Dynamics 365 Finance based on customer feedback and common issues encountered. 

## Introduction
The goal is to help users enhance report design, performance, and maintainability. The financial reporting report engine, like any other processing engine, is optimized for certain patterns of design. Adjusting the report design based on the general design guidelines allows the report engine to yield its best performance.

## Optimize report design 

Based on existing report engine optimization rules, consider the following suggestions to improve report design:
1.	Avoid using dimension or attribute filters in column definition if the same criteria can be specified in other ways or if the criteria can be converted to criteria 
in row definition.
2.  Avoid cross ledger/company consolidation for the ledger/company with different accounting currencies if that level of consolidation isn't required.
3.  Reduce the number of tree units and columns in the design file by breaking a single large design into several smaller designs that can be generated in parallel.
4.  Alternatively, utilize different report level details (account and transaction level detail) in report design to spread out, pivot, and drill into various aspects
of the data.
5.  Consider scheduling to run reports during off peak times when allowable or after scheduled posting runs.
6.  Avoid using row modifiers in row definition if the same criteria can be specified in other ways or if the criteria can be converted to criteria in column definition. Instead, consider using generic row definitions.
7.  When including an image on the report, such as a company logo, use an image with the lowest resolution possible.
