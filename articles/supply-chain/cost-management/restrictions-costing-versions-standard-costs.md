---
# required metadata

title: Restrictions on costing versions for standard costs | Microsoft Docs
description: This topic describes the restrictions that apply to a costing version for standard costs. 
author: AndersGirke
manager: AnnBe
ms.date: 2015-04-29 03:30:00
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: CostingVersion
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 121
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 3371
ms.assetid: fdb32dd4-b6dd-4b99-ac4e-34be45b00579
ms.search.region: global
ms.industry: Retail
ms.author: yuyus
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Restrictions on costing versions for standard costs

This topic describes the restrictions that apply to a costing version for standard costs. 

The following restrictions help guarantee adherence to standard costing principles:

-   Charges must be included in an item's cost. The charges for a manufactured item represent the amortized constant costs in the bill of materials (BOM) and route information. Therefore, the charges must be included in the unit cost. The charges for a purchased item are also included in the item's unit cost.
-   Calculation of standard costs for manufactured items must be based on the cost records in a costing version for standard costs. Alternative sources of cost data can be used only with a costing version for planned costs, such as purchase price trade agreements for purchased items. Alternative sources of cost data are defined by the BOM calculation group.
-   BOM calculations must be performed in a single-level explosion mode.

The item cost data for standard costs can be copied to another costing version that contains standard costs or planned costs. However, the item cost data for planned costs can't be copied to a cost version that contains standard costs, because the restrictions that are listed earlier in this topic don't apply to planned costs.

See also
--------

[Costing versions](http://authoring.help.dynamics.com/en/wiki/costing-versions/)

[Update standard costs in a non-manufacturing environment](http://authoring.help.dynamics.com/en/wiki/update-standard-costs-in-a-nonmanufacturing-environment/)

[Prepare to maintain standard costs for manufactured items](http://authoring.help.dynamics.com/en/?post_type=incsub_wiki&p=81691)

