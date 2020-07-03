---
# required metadata

title: Planning Optimization extensibility
description: This topic describes the extensibility scenarios supported in Planning Optimization. 
author: ChristianRytt
manager: tfehr
ms.date: 07/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2020-07-07
ms.dyn365.ops.version: 10.0.13

---
# Planning Optimization extensibility

[!include [banner](../../includes/banner.md)]

This topic describes the extensibility scenarios related to master planning supported in Planning Optimization. These capabilities are available starting in Dynamics 365 Supply Chain Management version 10.0.13.

## Custom processing when master planning completes

The most common extensibility scenario in Planning Optimization is to perform custom processing after the plan has been updated. For example, if you have added an additional column to the planned orders table (`ReqPO`) or if you want to derive some statistical information from the generated plan. The main extensibility point to enable such scenarios is the `jobCompletedSuccessfully` method in the `MpsMasterPlanningEvents` class.

```csharp
public static void jobCompletedSuccessfully(MpsMasterPlanningJobCompletedSuccessfullyEventArgs _args)
```

Here is an example of an extension that populates a custom `CstmOrderPriority` field on the planned order:

```csharp
[ExtensionOf(classStr(MpsMasterPlanningEvents))]
public static final class MpsMasterPlanningEvents_Cstm_Extension
{
    public static void jobCompletedSuccessfully(MpsMasterPlanningJobCompletedSuccessfullyEventArgs _args)
    {
        ttsbegin;

        var affectedPlannedOrdersQuery = _args.parmPostProcessingQueryBuilder().buildAffectedPlannedOrdersQuery();
        var affectedPlannedOrdersQueryRun = new QueryRun(affectedPlannedOrdersQuery);

        while (affectedPlannedOrdersQueryRun.next())
        {
            ReqPO reqPO = affectedPlannedOrdersQueryRun.get(tableNum(ReqPO));
            reqPO.selectForUpdate(true);
            reqPO.CstmOrderPriority = reqPO.ReqDate - systemDateGet() < 7 ? CstmPlannedOrderPriority::Urgent : CstmPlannedOrderPriority::Regular;
            reqPO.doUpdate();
        }

        ttscommit;

        next jobCompletedSuccessfully(_args);
    }

}
```

When adding custom logic, take the following constraints and best practices into consideration:

- The `jobCompletedSuccessfully` method is called outside of the transaction scope. This means that plan is already visible to the user when the custom logic starts executing. If your customization populates additional fields on planned orders, then it's important to let users know that the values of these fields will eventually be consistent (in other words, they may be out of date right after a planning job completes).
- Another master planning job can start when the `jobCompletedSuccessfully` method is called. The new job may affect the full plan or part of the plan. The new job may update or delete the same planned orders or requirement transactions that were created or updated as part of the planning job handled in `jobCompletedSuccessfully`. Update conflict exceptions must be handled when extending this event.
- Avoid using single transaction scope when extending this method. A single master planning run can produce millions of requirement transactions and hundreds of thousands of planned orders. Processing them all in the scope of a single transaction will result in a large number of SQL locks, which will block other planning processes, and (if the transaction is held for a long period of time) will create "ghost records" in SQL. Ghost records will negatively affect every process in the system.
