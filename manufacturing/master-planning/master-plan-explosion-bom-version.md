---
# required metadata

title: Explosion of a BOM version | Microsoft Docs
description: This article explains a master planning scenario that involves explosion of a bill of materials (BOM) version.
author: YuyuScheller
manager: AnnBe
ms.date: 2015-12-07 09:15:33
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: ReqTransExplosion
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 19211
ms.assetid: 6dd99875-7003-4b61-b63c-1c798c01c860
ms.region: Global
ms.industry: Manufacturing
ms.author: roxanad

---

# Explosion of a BOM version

This article explains a master planning scenario that involves explosion of a bill of materials (BOM) version.

A demand explosion of a bill of materials (BOM) version creates a demand for each BOM line item at a specific site and, possibly, at a specific warehouse. In a site-specific BOM, a specific warehouse can be defined for each BOM line. Additionally, for each BOM line, the item's dimension settings determine whether the warehouse is required. The resulting demand for each BOM line item then becomes the starting point for additional demand explosion. This master planning scenario involves the following conditions:

-   The site dimension is mandatory and must be entered on the demand transaction.
-   The site dimension is consistent. Therefore, the site for lower-level demand is the same as the site on the initial demand transaction.

The following illustration shows how the process for master planning demand explosion. ![Demand explosion using BOM version](./media/multisitedemandexplosionscenariousingbomversion.gif)

See also
--------

[Master planning - how the BOM version is determined](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-how-the-bom-version-is-determined)

[Master planning and multisite functionality](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-and-multisite-functionality)

