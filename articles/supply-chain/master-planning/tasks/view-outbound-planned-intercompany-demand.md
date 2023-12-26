--- 
# required metadata 
 
title: View outbound planned intercompany demand
description: This article provides a procedure that shows how to view outbound planned intercompany demand. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, ReqCreatePlanWorkspace, ReqTransPlanCard, ReqOutboundIntercompanyDemand   
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
# View outbound planned intercompany demand

[!include [banner](../../includes/banner.md)]

This procedure shows how to view all the planned orders that will be fulfilled by an intercompany vendor. The demo data company used to create this procedure is DEMF.

1. Select **Master planning**.
2. In the **Plan** field, enter or select a value.
    * In the **Plan** field, select plan *10*.  
3. Select *Run*.
4. In the **Number of threads** field, enter a number.
    * This represents the number of parallel threads to be used for master planning.  
5. Select **OK**.
    * This may take a while.  
6. Select **Planned intercompany demand**.
7. Select **Outbound planned intercompany demand**.
    * This page provides an overview of all the planned demand that will be fulfilled by an internal supply chain vendor.  
8. Expand the **Upstream demand details** section.
    * In this section, you can see the details about how the demand will be fulfilled. You may need to wait for master planning to be run in the supply company before you can see additional information here.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
