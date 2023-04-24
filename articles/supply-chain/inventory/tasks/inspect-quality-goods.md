--- 
# required metadata 
 
title: Inspect the quality of goods
description: This article describes how to process quality orders.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventQualityOrderTable, InventQualityOrderLineResults, HcmWorkerLookUp   
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

# Inspect the quality of goods

[!include [banner](../../includes/banner.md)]

This article describes how to process quality orders. Quality inspections are typically done by a quality clerk.

If the standard [demo data](../../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed, you can use it to complete the procedures in this article. To use the demo data, select the *USMF* legal entity before you begin. You must then confirm purchase order *000016* and post a product receipt. A quality order is automatically generated.

## Step 1: Select a quality order

To select a quality order, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Quality orders**.
1. Select the quality order that was generated before you started this procedure.

## Step 2: Record test results

To record test results, follow these steps.

1. Select **Results**.
1. Select **Edit**.
1. In the **Result quantity** field, enter a number.
1. In the **Outcome** field, select the desired record. In this example, the result is based on a predefined outcome. Usually, you will record a more specific test result, such as a size or other dimension.
1. Select **Save**.
1. Close the page.

## Step 3: Validate the quality order

To validate the quality order, follow these steps.

1. Select **Validate**.
1. In the **Validated by** field, select the user who is doing the inspection.
1. Select **Select**.
1. Select **OK**.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
