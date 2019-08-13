---
# required metadata

title: Warranty agreement
description: This topic explains warranty agreements in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 07/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Warranty agreement

In **Asset Management**, you can set up warranty terms that can be connected to an asset or an asset type. Warranty terms are created for a specific period. Warranty can be set up to provide full coverage or partial coverage, and you can set up terms to relate to hours, expenses, and items.

First step is to create the vendor warranty agreements that you may have on your equipment. Next, you attach warranty agreements to assets or asset types. Vendor warranty agreements are only used for information purposes. If vendor warranty is set up on the asset, you can see the warranty coverage period on the asset.

## Create warranty agreement

A warranty agreement may include several agreement lines covering warranty for work hours, expenses, and items.

1. Click **Asset management** > **Setup** > **Assets** > **Warranty**.

2. Click **New** to create a new product.

3. Insert a warranty ID in the **Warranty** field and a description in the **Name** field.

4. In the **Assets** field, you see the number of active assets that use the warranty agreement.

5. On the **Hour warranty** and **Item warranty** FastTabs, you add the lines to be included in the agreement pertaining to hours or items. Steps 6-9 explain how to fill out the lines.

6. Click **Add line** to add a new condition to the warranty. A sequential line number is automatically inserted in the **Line** field.

7. Select a period type for the warranty period in the **Period** field.

8. Insert an interval in the **Interval** field. This number defines how many periods the warranty should be valid for.

9. In the **Percent** field, insert the coverage percentage for the warranty line. The percentage indicates how much is covered by your company.


The figure below shows an example of a 1-year warranty agreement with full coverage.

![Figure 1](media/01-warranty.png)

