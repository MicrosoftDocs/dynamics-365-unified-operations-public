---
title: Restrictions on costing versions for standard costs
description: Learn about the restrictions that apply to a costing version for standard costs, including an outline on restrictions that help guarantee adherence to principles.
author: JennySong-SH
ms.author: yanansong
ms.topic: article
ms.date: 01/17/2018
ms.custom:
ms.reviewer: kamaybac
ms.industry: Manufacturing 
ms.search.form: CostingVersion
---


#  Restrictions on costing versions for standard costs

[!include [banner](../includes/banner.md)]

This article describes the restrictions that apply to a costing version for standard costs. 

The following restrictions help guarantee adherence to standard costing principles:

-  Charges must be included in an item's cost. The charges for a manufactured item represent the amortized constant costs in the bill of materials (BOM) and route information. Therefore, the charges must be included in the unit cost. The charges for a purchased item are also included in the item's unit cost.

-  Calculation of standard costs for manufactured items must be based on the cost records in a costing version for standard costs. Alternative sources of cost data can be used only with a costing version for planned costs, such as purchase price trade agreements for purchased items. Alternative sources of cost data are defined by the BOM calculation group.

-  BOM calculations must be performed in a single-level explosion mode.

The item cost data for standard costs can be copied to another costing version that contains standard costs or planned costs. However, the item cost data for planned costs can't be copied to a cost version that contains standard costs, because the restrictions that are listed earlier in this article don't apply to planned costs.

## Related articles

[Costing versions overview](costing-versions.md)

[Update standard costs in a non-manufacturing environment](update-standard-costs-non-manufacturing-environment.md)

[Prepare to maintain standard costs for manufactured items](update-standard-costs-manufacturing-environment.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]