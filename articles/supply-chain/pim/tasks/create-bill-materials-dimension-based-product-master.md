--- 
# required metadata 
 
title: Create a bill of materials for a dimension-based product master
description: For this procedure you should have completed the previous 4 guides in this sequence of eight recordings. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductMaintainWorkspace, EcoResProductOpenCasesFormPart, EcoResProductDetailsExtended, BOMConsistOf, BOMTable, InventItemIdLookupSimple, HcmWorkerLookUp   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a bill of materials for a dimension-based product master

[!include [banner](../../includes/banner.md)]

For this procedure you should have completed the previous 4 guides in this sequence of eight recordings. The first 4 recordings set up data that is required to complete this procedure. The demo data company used to create this procedure is USMF. This task is typically handled by the product designer.

## Select the product

1. Go to **Product information management \> Products \> Released products**.
1. In the list, mark the selected row.
    * Find the released product master with dimension-based configuration technology that you created in the first task guide in this sequence.  
1. On the Action Pane, select **Engineer**.
1. Select **BOM versions**.

## Create new BOM and BOM version

1. Select **New**.
1. Select **BOM and BOM version**.
1. In the **Name** field, type a value.
    * Setting a site  
    * In this procedure we don't set a specific site for the BOM.  
1. Select **OK**.
1. Select **New**.
    * In this procedure we will add four lines to the BOM. Two lines represent cable options and two lines represent cabinet options.  
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.
    * Select item number A0001, HDMI 6' Cables.  
1. In the **Configuration group** field, enter or select a value.
    * Select the cable configuration group created in guide 4 in this sequence.  
1. Select **New**.
    * Select item number A0002, HDMI 12' Cables.  
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.
1. In the **Configuration group** field, enter or select a value.
    * Select the cable configuration group again.  
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.
    * Select item number D0002 Cabinet.  
1. In the **Configuration group** field, enter or select a value.
    * Select the cabinet configuration group for this BOM line.  
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.
    * Select Item number M0007 StandardCabinet as the last BOM line.  
1. In the **Configuration group** field, enter or select a value.
    * Select the Cabinet configuration group for the last BOM line.  

## Approve and activate

1. Close the page.
1. Select **Approve**.
1. In the **Approved by** field, enter or select a value.
1. Select *Yes* in the **Do you also want to approve the bill of materials?** field.
1. Select **OK**.
1. Select **Activate**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]