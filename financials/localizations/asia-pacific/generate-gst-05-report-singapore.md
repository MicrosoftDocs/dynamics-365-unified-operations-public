---
# required metadata

title: Generate the Singapore GST-05 report | Microsoft Docs
description: This article explains the functionality for generating Singapore GST-05 reports in Microsoft Dynamics AX. The GST-05 report is used to file a goods and services tax (GST) return. 
author: ShylaThompson
manager: AnnBe
ms.date: 2015-11-16 21:17:03
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: TaxAuthority
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: ShylaThompson
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 12831
ms.assetid: 4f7a0045-23a2-4c4d-8ec7-7eb7f9411078
ms.region: Singapore
# ms.industry: 
ms.author: leguo

---

# Generate the Singapore GST-05 report

This article explains the functionality for generating Singapore GST-05 reports in Microsoft Dynamics AX. The GST-05 report is used to file a goods and services tax (GST) return. 

Singapore companies must file a goods and services tax (GST) return (GST-05) on a regular basis. The GST-05 report includes breakdown details such as standard-rated, zero-rated, and exempt purchases and sales in a regulated format. To accommodate the requirements, you must complete the following two operations while you complete the tax settlement process:

-   Categorize your tax codes into three categories by selecting proper value for the **VAT type** field on the **Sales tax codes** page:
    -   Standard
    -   Zero
    -   Exempt
-   On the sales tax authority page, specify the dedicated **Singapore report layout** reporting format.

When you settle and post sales tax to process a tax settlement, the GST-05 report will be generated and printed.

