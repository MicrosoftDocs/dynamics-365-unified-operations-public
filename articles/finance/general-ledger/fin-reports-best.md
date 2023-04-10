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

This article provides tips and best practices for optimizing financial reports in Microsoft Dynamics 365 Finance, based on customer feedback and commonly encountered issues. 

The goal is to help users enhance report design, performance, and maintainability. The financial reporting report engine, like any other processing engine, is optimized for specific patterns of design. By adjusting the report design, based on the general design guidelines, you help the report engine achieve its best performance.

## Optimize report design 

Based on existing report engine optimization rules, consider the following suggestions to help improve report design:

- Avoid using dimension or attribute filters in column definitions if the same criteria can be specified in other ways, or if the criteria can be converted to criteria in a row definition.
- Avoid cross-ledger/cross-company consolidation for ledgers/companies that use different accounting currencies if that level of consolidation isn't required.
- Reduce the number of tree units and columns in the design file by breaking a single large design into several smaller designs that can be generated in parallel.
- Alternatively, use different report-level details (account-level and transaction-level details) in the report design to spread out, pivot, and drill into different aspects of the data.
- Consider scheduling reports to run either during off-peak times (if allowable) or after scheduled posting runs.
- Avoid using row modifiers in a row definition if the same criteria can be specified in other ways, or if the criteria can be converted to criteria in a column definition. Instead, consider using generic row definitions.
- If you want to include an image (for example, a company logo) on the report, use an image that has the lowest possible resolution.
