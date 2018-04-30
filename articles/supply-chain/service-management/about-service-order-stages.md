---
title: About service order stages
TOCTitle: About service order stages
ms:assetid: 78a8cb66-5faa-4c17-86a0-62836e9c953c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Aa550052(v=AX.60)
ms:contentKeyID: 62629947
ms.date: 07/28/2014
mtps_version: v=AX.60
_tocRel: gg243285(v=ax.60)/toc.json
---

# About service order stages 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

You can set up stages for a service order to define the tasks that must be completed, the order in which they are completed, and the workers who are responsible for completing them. By defining the stages for a service order and assigning them to workers, you can control the flow of a service order through the tasks that various people perform in the service organization. The sequence of stages must include an initial stage.

You can also define the actions that are permitted at each stage. For example, if you clear the **Post** check box for all stages except the final stage, you prevent any service orders from being posted before the service orders are processed through the complete sequence of stages.

## Branching in service order stages

When you set up a service stage, you can create multiple options, or branches, to select from for the next service stage. All the branches that you create are available to select from when the initial stage is completed. For example, you set up **Planning** as an initial stage. You create two stages named **In process** and **Cancel**, and then select **Planning** as the parent for them. You assign the **Planning** stage to sales order. When the planning stage for the sales order is completed, you can select the **In process** stage if the sales order is ready to work on, or you can select the **Cancel** stage if the sales order is canceled.

## See also

[Set up service order stages](set-up-service-order-stages.md)

[Change the service order stage](change-the-service-order-stage.md)

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

