--- 
# required metadata 
 
title: Quality management item sampling
description: This article describes how to set up item sampling.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: how-to 
ms.prod: 
ms.technology: 
 
# optional metadata 
 
ms.search.form: InventItemSampling
audience: Application User 
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---

# Quality management item sampling

[!include [banner](../includes/banner.md)]

Item sampling is used as part of a quality association. It defines the amount of current physical inventory that must be inspected. Sampling can be based on fixed quantities, a percentage, or a full license plate.

## Set up item sampling

Follow these steps to set up item sampling.

1. Go to **Inventory management \> Setup \> Quality control \> Item sampling**.
1. Select **New**.
1. In the **Item sampling** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Value** field, enter a number. This value is related to the quantity specification value that is selected in the adjacent field.
1. In the **Process** section, select the **Full blocking** check box if the whole lot or order line quantity should be blocked if a test is failed. If this check box is cleared, only the items in the quality order will be blocked if a test is failed.
1. Select **Save**.
1. Close the page.

> [!NOTE]
> The *Quality management for warehouse processes* feature provides additional item sampling capabilities. It adds the concept of *item sampling scope* and lets you define a full license plate as the quantity specification. If you've turned on this feature, see [Quality management for warehouse processes](quality-management-for-warehouses-processes.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
