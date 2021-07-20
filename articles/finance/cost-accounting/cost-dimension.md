---
# required metadata

title: Create dimensions and import dimension members
description: Cost accounting is an independent module that requires master data from other modules.
author: ShylaThompson
ms.date: 09/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CAMDimension
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 256254
ms.assetid: e1b0a6e3-0c72-4a7d-90e1-20f870c6dbad
ms.search.region: Global
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Create dimensions and import dimension members

[!include [banner](../includes/banner.md)]

Cost accounting is an independent module that requires data from other modules. This data is categorized into the following:

-  Cost elements
-  Cost objects
-  Statistical dimensions

A **Cost element** corresponds to a cost-relevant item in the chart of accounts. A **Cost object** corresponds to any type of financial dimension, such as products, cost centers, and projects that you want to estimate, allocate costs to, or measure directly. A **Statistical dimension** and its members are used to register non-monetary entries. Statistical dimension members can be used as an allocation base in cost distribution and allocation 

The following diagram illustrates the dimensions that are used in Cost accounting.

[![Cost accounting dimensions.](./media/cost-eos-dimensions.png)](./media/cost-eos-dimensions.png)

After the data is imported into Cost accounting, you can use it to build various perspectives that provide insights to managers at all levels of the organization. The following topics provide information about creating dimensions and importing dimension members. 

-  [Cost element dimensions](cost-elements.md)
-  [Create cost elements](./tasks/create-cost-elements.md)
-  [Cost object dimensions](cost-objects.md)
-  [Map cost element dimension members to a common set of dimension members](map-cost-elements-dimension-members.md)
-  [Map a cost element dimension](./tasks/map-cost-element-dimension.md)
-  [Statistical dimension members and statistical measure provider templates](statistical-measure-provider-template.md)








[!INCLUDE[footer-include](../../includes/footer-banner.md)]