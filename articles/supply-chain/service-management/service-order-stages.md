---
title: Service order stages  
description: Learn how you can control the flow of a service order through the tasks that various people perform in the service organization.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMAServiceOrderTable, SMAStageTable
ms.topic: conceptual
ms.date: 01/30/2025
ms.custom: 
  - bap-template
---

# Service order stages

[!include [banner](../includes/banner.md)]

You can set up stages for a service order to define the tasks that must be completed, the order in which they are completed, and the workers who are responsible for completing them. By defining the stages for a service order and assigning them to workers, you can control the flow of a service order through the tasks that various people perform in the service organization. The sequence of stages must include an initial stage.

You can also define the actions that are permitted at each stage. For example, if you clear the **Post** check box for all stages except the final stage, you prevent any service orders from being posted before the service orders are processed through the complete sequence of stages.

## Branching in service order stages

When you set up a service stage, you can create multiple options, or branches, to select from for the next service stage. All the branches that you create are available to select from when the initial stage is completed. For example, you set up *Planning* as an initial stage. You create two stages named *In process* and *Cancel*, and then select *Planning* as the parent for them. You assign the *Planning* stage to sales order. When the planning stage for the sales order is completed, you can select the *In process* stage if the sales order is ready to work on, or you can select the *Cancel* stage if the sales order is canceled.

## Related information

- [Set up service order stages](set-up-service-order-stages.md)
- [Change the service order stage](change-service-order-stage.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
