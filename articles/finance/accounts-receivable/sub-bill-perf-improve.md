---
title: Performance improvements for subscription billing consumption entry
description: Learn about the Performance improvements for subscription billing consumption entry.
author: JodiChristiansen
ms.author: reetuchopra
ms.topic: article
ms.date: 04/21/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-02-09
ms.search.form: CustPosting, CustVendExternalItem
ms.dyn365.ops.version: 10.0.25
ms.assetid: cb82245e-8c02-429c-b36e-8db0e3e6f7e5
---

# Performance improvements for subscription billing consumption entry

[!include [banner](../includes/banner.md)]

With the 10.0.44 release of Dynamics 365 Finance, Microsoft has introduced key performance improvements and functional enhancements aimed at resolving bottlenecks in Subscription billing consumption entry. These 
changes address critical business challenges faced during consumption registration and introduce better pricing control for various pricing methods.

## Performance improvements 
Prior to this release, performance issues have been encountered when importing numerous records or processing billing details with many lines. This issue was particularly impactful for businesses managing large 
volumes of contracts and usage lines every month. The performance issues in subscription billing led to several operational challenges as well. 
To address these challenges, Microsoft introduced the following technical changes in version 10.0.44: 
 - Set-based processing has replaced line-based logic, resulting in improved performance during consumption updates. If users continue to experience delays, use **Update estimated consumption quantity via batch** to process updates in the background, improving usability and efficiency.
 - Pricing control logic has been updated to ensure consistency and prevent pricing discrepancies:
     - If the **Pricing method** is **Standard** - the **Unit price** field on the **Detail line** page is locked and can't be changed by users.
     - If the **Pricing method** is **Flat** - the **Unit price** field is editable.

