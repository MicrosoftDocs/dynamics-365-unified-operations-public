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

The most common extensibility scenario for Planning Optimization is to apply custom processing after the plan has been updated. For example, you might add a column to the planned orders table (`ReqPO`), or you might want to derive some statistical information from the generated plan. The main extensibility point that enables this scenario is the `jobCompletedSuccessfully` method in the `MpsMasterPlanningEvents` class. To apply processing after a job fails, use the `jobFailed` method in the same class.

> [!IMPORTANT]
> Post-processing actions that use the current extensibility point will only apply to items directly specified in the filters (if used) and not to their subcomponents. Therefore, additional items included as a result of enabling the **Include all BOM levels** and/or **BOM levels to include** options in the **Planning Optimization** run dialog won't be affected by these post-processing actions. For more information about how to use the filters, see [Run planning for a subset of items](plan-filters.md)

## The job completed successfully method

This section shows how to use the `jobCompletedSuccessfully` method.

```X++
public static void jobCompletedSuccessfully(MpsMasterPlanningJobCompletedSuccessfullyEventArgs _args)
```

Here's an example of an extension that sets a custom `CstmOrderPriority` field on the planned order.

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

- The `jobCompletedSuccessfully` method is called outside the transaction scope. Therefore, the plan is already visible to the user when the custom logic starts to run. If your customization sets other fields on planned orders, it's important that you let users know that the values of those fields will eventually be consistent (in other words, they might be out of date immediately after a planning job is completed).
- Another master planning job can start when the `jobCompletedSuccessfully` method is called. The new job might affect the full plan or part of the plan. The new job might update or delete the same planned orders or requirement transactions that were created or updated as part of the planning job that was handled in `jobCompletedSuccessfully`. Update conflict exceptions must be handled when this event is extended.
- Avoid using single transaction scope when you extend this method. A single master planning run can produce millions of requirement transactions and hundreds of thousands of planned orders. If all these transactions and planned orders are processed in the scope of a single transaction, many SQL locks will occur and block other planning processes. Additionally, if the transaction is held for a long time, "ghost records" will be created in the SQL database. Ghost records will negatively affect every process in the system.
- The query included in `MpsMasterPlanningJobCompletedSuccessfullyEventArgs` includes all the items that were included in the original filters, including those that had errors.
- The query included for `jobCompletedSuccessfully` won't include items added as a result of enabling the **Include all BOM levels** and/or **BOM levels to include** options in the **Planning Optimization** run dialog.

## The job failed method

When a Planning Optimization job fails, it may be necessary to start another process (such as a retry operation). For this, you can use the `jobFailed` method, which is supported in Supply Chain Management version 10.0.31 and higher.

When adding custom logic, keep in mind that the query included for the `jobFailed` method won't include items added as a result of enabling the **Include all BOM levels** and/or **BOM levels to include** options in the **Planning Optimization** run dialog.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
