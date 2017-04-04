---
# required metadata

title: Generate the Singapore GST-05 report
description: This article explains the functionality for generating Singapore GST-05 reports in Microsoft Dynamics AX. The GST-05 report is used to file a goods and services tax (GST) return. 
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: TaxAuthority
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: ShylaThompson
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 12831
ms.assetid: 90ea6084-920a-4174-8b3e-9b7b96aed0b4
ms.search.region: Singapore
# ms.search.industry: 
ms.author: leguo
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

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

