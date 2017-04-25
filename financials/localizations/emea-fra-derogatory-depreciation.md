---
# required metadata

title: Derogatory depreciation for France
description: This article provides information about derogatory depreciation and how to set it up. In derogatory depreciation, an extra amount of depreciation is calculated as the difference between the depreciation amount on the tax value model and the depreciation amount on the accounting value model during the life of a fixed asset.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 30321
ms.assetid: be90464e-2cce-445c-b95b-79ec559b411e
ms.search.region: France
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Derogatory depreciation for France

[!include[banner](../includes/banner.md)]


This article provides information about derogatory depreciation and how to set it up. In derogatory depreciation, an extra amount of depreciation is calculated as the difference between the depreciation amount on the tax value model and the depreciation amount on the accounting value model during the life of a fixed asset.

In derogatory depreciation, an extra amount of depreciation is calculated as the difference between the depreciation amount on the tax value model and the depreciation amount on the accounting value model during the life of a fixed asset. This extra amount of depreciation is posted as the **Derogatory increase** transaction type on the accounting value model if the depreciation amount on the tax value model is higher than depreciation amount on the accounting value model. Alternatively, this extra amount of depreciation is posted as the **Derogatory decrease** transaction type. For example, a fixed asset that has acquisition amount of EUR 1,000 is depreciated in the accounting value model for five years and in the tax value model for three years. In the first year, the accounting depreciation is EUR 200 (1,000 ÷ 5), and the tax depreciation is EUR 333.33 (1,000 ÷ 3). Therefore, the extra amount is EUR 133.33 (\[1,000 ÷ 3\] – \[1,000 ÷ 5\], or 333.33 – 200.00) and is posted as a derogatory increase. After the third year of the life cycle, the accounting depreciation will be EUR 200 (1,000 ÷ 5), and the tax depreciation will be 0 (zero). Therefore, the extra amount is EUR 200 (0.00 – \[1,000 ÷ 5\], or 0.00 – 200.00) and is posted as a derogatory decrease. To use derogatory depreciation, you first create and set up accounting and derogatory tax value models, and assign them to an asset. For the derogatory tax model, you enable the **Derogatory tax model** field on the **Value models** page. For the accounting model, you select the derogatory tax model in the **Derogatory calculation** field. The following conditions must be met:

-   Both value models must have the **Depreciation** field enabled.
-   **Allow negative net book value** is disabled in both value models.
-   Both value models have the same value in the **Calendar** field.
-   Both value models must have the same posting layer set to **Current**.
-   The depreciation profile that is selected on the derogatory tax model must have full depreciation activated if the depreciation method is of the **Reducing Balance** type.
-   The depreciation profiles that are selected on the both value models must have the same settings for **Depreciation Year** and **Period Frequency**.
-   Both value models must have the same setting in the **Depreciation convention** field on the **Fixed asset group/value model** page.
-   The **Placed in service** dates must be the same in both value models as soon as the models are assigned to a specific asset.

On the **Fixed asset posting profiles** page, you set up GL accounts for **Derogatory increase** and **Derogatory decrease** transactions in the accounting value model. On the **Disposal parameters** page, you can complete the setup to post derogatory increase amounts or derogatory decrease amounts to specific G/L accounts during disposal. You can review the derogatory depreciation amounts for the accounting value model on the **Fixed asset balances** page, the **Fixed asset note** report, or the **Fixed asset movement** report.



