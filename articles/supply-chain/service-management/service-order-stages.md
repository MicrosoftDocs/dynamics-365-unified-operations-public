---
# required metadata

title: Service order stages  
description: By defining the stages for a service order and assigning them to workers, you control the flow of a service order through the tasks that various people perform in the service organization.
author: sorenva
ms.date: 04/30/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMAServiceOrderTable, SMAStageTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sorenand
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Service order stages   

[!include [banner](../includes/banner.md)]


You can set up stages for a service order to define the tasks that must be completed, the order in which they are completed, and the workers who are responsible for completing them. By defining the stages for a service order and assigning them to workers, you can control the flow of a service order through the tasks that various people perform in the service organization. The sequence of stages must include an initial stage.

You can also define the actions that are permitted at each stage. For example, if you clear the **Post** check box for all stages except the final stage, you prevent any service orders from being posted before the service orders are processed through the complete sequence of stages.

## Branching in service order stages

When you set up a service stage, you can create multiple options, or branches, to select from for the next service stage. All the branches that you create are available to select from when the initial stage is completed. For example, you set up **Planning** as an initial stage. You create two stages named **In process** and **Cancel**, and then select **Planning** as the parent for them. You assign the **Planning** stage to sales order. When the planning stage for the sales order is completed, you can select the **In process** stage if the sales order is ready to work on, or you can select the **Cancel** stage if the sales order is canceled.

## See also

[Set up service order stages](set-up-service-order-stages.md)

[Change the service order stage](change-service-order-stage.md)

  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]