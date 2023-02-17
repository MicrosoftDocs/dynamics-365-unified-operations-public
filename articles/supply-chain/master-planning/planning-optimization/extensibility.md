---
# required metadata

title: Planning Optimization extensibility
description: This article describes the extensibility scenarios that are supported in Planning Optimization. 
author: t-benebo
ms.date: 08/05/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2020-07-07
ms.dyn365.ops.version: 10.0.13

---
# Planning Optimization extensibility

[!include [banner](../../includes/banner.md)]

This article describes the extensibility scenarios that are related to master planning and supported in Planning Optimization. 

## Custom processing when master planning is completed

In the most common extensibility scenario in Planning Optimization, custom processing is done after the plan has been updated. For example, you might add a column to the planned orders table (`ReqPO`), or you might want to derive some statistical information from the generated plan. The main extensibility point that enables this scenario is the method `jobCompletedSuccessfully` in the `MpsMasterPlanningEvents` class. If the job fails you can also leverage the method `jobFailed` in the same class. 

It is important to note that the post-processing actions using the current extensibility point will only apply to the items directly specified as in the planning filter run (if used) and not to the subcomponents. This means that additional items included as part of the **Include all BOM levels** or **BOM levels to include** when selecting these options as part of the Planning Optimization run dialog. For more information on the filters see [Run planning for a subset of items](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/plan-filters).
 

## Job completed successfully

For `jobCompletedSuccessfully`:

```X++
public static void jobCompletedSuccessfully(MpsMasterPlanningJobCompletedSuccessfullyEventArgs _args)
```

Here is an example of an extension that sets a custom `CstmOrderPriority` field on the planned order.

```X++
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

When you add custom logic, consider the following constraints and best practices:

- The `jobCompletedSuccessfully` method is called outside the transaction scope. Therefore, the plan is already visible to the user when the custom logic starts to run. If your customization sets additional fields on planned orders, it's important that you let users know that the values of those fields will eventually be consistent (in other words, they might be out of date immediately after a planning job is completed).
- Another master planning job can start when the `jobCompletedSuccessfully` method is called. The new job might affect the full plan or part of the plan. The new job might update or delete the same planned orders or requirement transactions that were created or updated as part of the planning job that was handled in `jobCompletedSuccessfully`. Update conflict exceptions must be handled when this event is extended.
- Avoid using single transaction scope when you extend this method. A single master planning run can produce millions of requirement transactions and hundreds of thousands of planned orders. If all these transactions and planned orders are processed in the scope of a single transaction, many SQL locks will occur and block other planning processes. Additionally, if the transaction is held for a long time, "ghost records" will be created in the SQL database. Ghost records will negatively affect every process in the system.
- The query included in MpsMasterPlanningJobCompletedSuccessfullyEventArgs includes all items that were part of original filter - even if they had errors. 
- The query included for `jobCompletedSuccessfully` will not include additional items included as part of the **Include all BOM levels** or **BOM levels to include** when selecting these options as part of the Planning Optimization run dialog. 
 

## Job failed

For when Planning Optimization job failed, it may be needed to start another process like a retry. For this, the method`jobFailed` can be used and is available from release 10.0.31. 

When adding custom logic, consider the following:
- The query included for `jobFailed` will not include additional items included as part of the **Include all BOM levels** or **BOM levels to include** when selecting these options as part of the Planning Optimization run dialog. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
