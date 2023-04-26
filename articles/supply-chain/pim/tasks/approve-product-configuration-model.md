--- 
# required metadata 
 
title: Approve a product configuration model
description: Running this procedure requires that at least one product configuration model is available. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, PCProductConfigurationModelListPage, PCProductModelVersion, PCApproveProductModelVersion, HcmWorkerLookUp   
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
# Approve a product configuration model

[!include [banner](../../includes/banner.md)]

Running this procedure requires that at least one product configuration model is available. This procedure uses the High end speaker model in the demo data company USMF. Note that this model has already been approved, but the procedure walks you through the entire process.

1. Go to **Product information management \> Products \> Product configuration models**.
1. In the list, find and select the desired record.
    * Select the High end speaker model for this procedure.  
1. Select **Versions**.
1. Select **New**.
1. In the **Product number** field, enter or select a value.
    * The reference to a product represents a version of a product configuration model. Only product masters which have the constraint-based configuration technology will appear in this list.  
1. In the **From date** field, enter a date.
    * Select when the product model version will be available.  
1. In the **To date** field, enter a date.
    * Select an end date when this product model version will expire, or select Never.  
1. Select **Approve** to open the drop dialog.
1. In the **Approved by** field, enter or select a value.
    * Select the person who is responsible for approving product models for use in operations.  
1. Select **OK**.
1. In the **Pricing method** field, select an option.
    * Activate the product model version. It is only possible to have one product active for one product model at a time.  
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]