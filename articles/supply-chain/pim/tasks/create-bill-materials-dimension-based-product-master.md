---
title: Create a bill of materials for a dimension-based product master
description: This article shows how to create a bill of materials for a dimension-based product master.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: DefaultDashboard, EcoResProductMaintainWorkspace, EcoResProductOpenCasesFormPart, EcoResProductDetailsExtended, BOMConsistOf, BOMTable, InventItemIdLookupSimple, HcmWorkerLookUp   
ms.topic: how-to
ms.date: 11/10/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Create a bill of materials for a dimension-based product master

[!include [banner](../../includes/banner.md)]

This article shows how to create a bill of materials for a dimension-based product master.

This is the fifth procedure [of an eight-procedure sequence](../dimension-based-product-configuration.md#sequence) that explains how to build combinations for dimension-based configuration. You should do all eight procedures, in order, because each new procedure builds on data created by the previous procedures. To work through this sequence by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed, and you must select the *USMF* legal entity before you begin.

This task is typically handled by the product designer.

## Select the product

1. Go to **Product information management \> Products \> Released products**.
1. Select the product you want to work with in the grid.
    - Find the released product master with dimension-based configuration technology that you created in the [first procedure](create-dimension-based-product-master.md) in this sequence of eight.  

1. On the Action Pane, open the **Engineer** tab and select **BOM versions**.

## Create new BOM and BOM version

1. On the Action Pane, select **New \> BOM and BOM version**.
1. In the **Name** field, type a value.
1. Select **OK**.
1. Select **New** from the **Bill of materials lines** FastTab toolbar.
    - In this procedure we will add four lines to the BOM. Two lines represent cable options and two lines represent cabinet options.  
1. Make the following settings for the new line:
    - **Item number** – Select item number A0001, HDMI 6' Cables.  
    - **Configuration group** – Select the cable configuration group created in the [fourth procedure](define-configuration-groups.md) in this sequence.  
1. Select **New** from the **Bill of materials lines** FastTab toolbar and then make the following settings for the new line:
    - **Item number** – Select item A0002, HDMI 12' Cables.  
    - **Configuration group** – Select the cable configuration group created in the [fourth procedure](define-configuration-groups.md) in this sequence.  
1. Select **New** from the **Bill of materials lines** FastTab toolbar and then make the following settings for the new line:
    - **Item number** – Select item number D0002, Cabinet.  
    - **Configuration group** – Select the cabinet configuration group for this BOM line.  
1. Select **New** from the **Bill of materials lines** FastTab toolbar and then make the following settings for the new line:
    - **Item number** – Select item number M0007, StandardCabinet.  
    - **Configuration group** – Select the cabinet configuration group for this BOM line.  

## Approve and activate

1. Close the page.
1. On The Action Pane, open the BOM version tab and select **Approval**.
1. In the **Approved by** field, enter or select a value.
1. Set **Do you also want to approve the bill of materials?** to *Yes*.
1. Select **OK**.
1. Select **Activate**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]