--- 
# required metadata 
 
title: Maintain bar code types
description: This procedure shows you how to set up a new bar code definition which can then be used as part of the picking list report. 
author: yufeihuang
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: BarcodeSetup, InventParameters   
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
# Maintain bar code types

[!include [banner](../../includes/banner.md)]

This procedure shows you how to set up a new bar code definition which can then be used as part of the picking list report. You can walk through this procedure in demo data company USMF, or using your own data. If you are using USMF you can use the example values that are shown. These tasks would typically be carried out by a warehouse manager.

1. Go to **Bar codes**.
1. Select **New**.
1. In the **Bar code setup** field, type a value.
1. In the **Description** field, type a value.
1. In the **Bar code type** field, select an option.
    * If you're using USMF, you can select 'Code 39'.
1. In the **Mask ID** field, specify the bar code mask ID. Bar code masks are used to create bar codes and to quickly identify bar codes that are scanned into a point of sale (POS) system. For details, see [Set up bar code masks](../../../commerce/set-up-bar-code-masks.md).
1. In the **Size** field, enter a number.
1. In the **Maximum length** field, enter a number.
1. Select **Save**.
1. Close the page.
1. Go to **Inventory and warehouse management parameters**.
1. In the **Bar code setup** field, enter or select a value.
    * Select the bar code setup that you created before, but be aware that the bar code format must match the format of the unique identifier for the record type used in the process. For example, for picking routes, the bar code format should match the format of the picking route reference, which is typically a number sequence.  
1. Select **Save**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
