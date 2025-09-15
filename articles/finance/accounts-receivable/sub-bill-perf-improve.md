---
title: Performance improvements for subscription billing consumption entry
description: Learn about the performance improvements for subscription billing consumption entry.
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

In the 10.0.44 release of Microsoft Dynamics 365 Finance, Microsoft introduced key performance improvements and functional enhancements that are intended to fix bottlenecks in subscription billing consumption entry. These changes address critical business challenges that are faced during consumption registration and introduce better pricing control for various pricing methods.

## Performance improvements

Before this release, users encountered performance issues when they imported numerous records, or when they processed billing details that have many lines. These issues especially affected businesses that manage large volumes of contracts and usage lines every month. The performance issues in subscription billing also led to several operational challenges.

To address these challenges, Microsoft introduced the following technical changes in version 10.0.44:

- Set-based processing replaced line-based logic. The result is improved performance during consumption updates. If users continue to experience delays, use **Update estimated consumption quantity via batch** to process updates in the background. In this way, you help improve usability and efficiency.
- Pricing control logic was updated to ensure consistency and prevent pricing discrepancies:

    - If the pricing method is **Standard**, the **Unit price** field on the **Detail line** page is locked and can't be edited by users.
    - If the pricing method is **Flat**, the **Unit price** field is editable.
