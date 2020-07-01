---
# required metadata

title: Planning Optimization extensibility
description: This topic covers the supported extensibility scenarios in Planning Optimization. 
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
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.5

---
# Supported Extensibility Scenarios in Planning Optimization

[!include [banner](../../includes/banner.md)]

This topic covers the supported extensibility scenarios related to master planning with Planning Optimization, that is available from version 10.0.13.


## Custom Processing when Master Planning Completes
The most common extensibility scenario in planning optimization is to perform custom processing after the plan has been updated. For example you have added an additional column to the planned orders table (ReqPO) or you want to derive some statistical information from the generated plan. The main extensibility point to enable such scenarios is the jobCompletedSuccessfully method in the MpsMasterPlanningEvents class.

```C#
public static void jobCompletedSuccessfully(MpsMasterPlanningJobCompletedSuccessfullyEventArgs _args)
```

**MpsMasterPlanningJobCompletedSuccessfullyEventArgs** class contains parameters of the planning run. It also exposes the **MpsMasterPlanningPostProcessingQueryBuilder** object which can be used to get the list of planned orders and net requirements which were created or updated during the planning run.

Below is an example of an extension which populates a custom CstmOrderPriority field on the planned order.

```C#
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
When adding custom logic the following constraints and best practices must be taken into consideration:
- The <c>jobCompletedSuccessfully</c> method is called outside of the transaction scope. It means that plan is already visible to the user when the custom logic starts executing. If the customization populates additional fields on planned orders then it's important to set expectations with the users that values of these fields will be eventually consistent (i.e. may be out of date right after completion of a planning job).
- Another master planning job can start when the <c>jobCompletedSuccessfully</c> method is called. The new job may affect the full plan or part of the plan. The new job may update or delete the same planned orders or requirement transactions that were created or updated as part of the planning job handled in <c>jobCompletedSuccessfully</c>. Update conflict exceptions must be handled when extending this event.
- Avoid using single transaction scope when extending this method. A single master planning run can produce millions of requirement transactions and hundreds of thousands of planned orders. Processing them all in the scope of a single transaction will result in large numbers of SQL locks, blocking other planning processes, and, if the transaction is held for a long period of time, creation of "ghost records" in SQL. "Ghost records" will negatively affect every process in the system.
