---
# required metadata

title: Asset movements
description: This topic describes the Asset movement report, which serves as a rollforward report for the right-of-use asset balances for each lease.
author: moaamer
manager: Ann Beebe
ms.date: 08/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-08-18
ms.dyn365.ops.version: 10.0.14
---

# Asset movements

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the Asset movement report, which serves as a rollforward report for the right-of-use asset balances for each lease. This report lets you view the asset transactions of a lease during a specified period.

1.	To view this report, open the **Asset movements** report page (**Asset Leasing > Inquiries & reports > Asset movements**).
2.	A parameters page will open where you can set filters on the lease transactions. Enter filter criteria and click **OK**.
3.	The generated report will show the following fields within the specified date range.

|     Name                           |     Description                                                                |
|------------------------------------|--------------------------------------------------------------------|
|     Commencement Date              |     The commencement date of the lease’s earliest version.   |   
|     Lease Term                     |     The lease term of the lease’s earliest version.                               |
|     Short Term Lease               |     If lease is classified as a short-term lease will show as   “Yes”               |
|     Low Value Lease                |     If lease is classified as a low-value lease will show as   “Yes”                   |
|     Initial Right of Use Asset     |     The original value of the right of use asset from the   initial recognition journal entry      |
|     Beginning Balance              |     The net book value of the right of use asset as of the   From Date                             |
|     Period Depreciation Expense    |     The amount of depreciation expense taken between the To   and From Dates                       |
|     Accumulated Depreciation       |     The amount of accumulated depreciation as of the From Date                                     |
|     Impairment                    	|     The amount the asset was impaired between date parameters                                     |
|     Modifications                  |     The amount of adjustments to the right of use asset   between date parameters                  |
|     Net Book Value                 |     The ending net book value of the right of use asset, net   of accumulated depreciation as of the To Date    |

