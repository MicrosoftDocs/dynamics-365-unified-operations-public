---
# required metadata

title: Financial reporting best practices
description: This article describes the financial reporting in Microsoft Dynamics 365 Finance and best practices.
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

This article describes the financial reporting in Microsoft Dynamics 365 Finance and provides tips and best practices for optimizing financial reports based on customer
feedback and common issues encountered. 

## Introduction: This documentation provides tips and best practices for optimizing financial reports based on customer feedback and common issues encountered. The goal 
is to help users enhance report design, performance, and maintainability. The FR report engine, like any other processing engine, is optimized for certain patterns of 
design. Adjusting the report design based on the general design guidelines will allow the report engine to yield its best performance.
Optimize Report Design for better report generation performance. Based on existing report engine optimization rules, consider the following suggestions to improve your 
report design:
1.	Avoid using row modifiers in row definition if the same criteria can be specified in other ways or if the criteria can be converted to criteria in column definition.
2.	 General tip: consider using generic row definitions.
3.	Avoid using dimension or attribute filters in column definition if the same criteria can be specified in other ways or if the criteria can be converted to criteria 
4.	in row definition.
5.	Avoid cross ledger/company consolidation for the ledger/company with different accounting currencies if that level of consolidation is not required.
6.	Reduce the number of tree units and columns in the design file by breaking a single large design into several smaller designs that can be generated in parallel.
7.	 Alternatively, utilize different report details levels (account and transaction level detail) in report design to spread out, pivot, and drill into various aspects
8.	  of the data.
9.	Consider scheduling reports to run reports during off peak times when allowable or after scheduled posting runs.
