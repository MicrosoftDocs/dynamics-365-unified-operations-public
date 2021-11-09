---
title: User-configurable queries
description: This topic describes how to create configurable queries and use them with the process automation framework.
author: RyanCCarlson2
ms.date: 09/10/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2020-09-10
ms.dyn365.ops.version: AX 7.0.0
---

# User-configurable queries

[!include [banner](../includes/banner.md)]

This topic describes how to create configurable queries and use them with the process automation framework. If a process won't support user-configurable queries via the **SysQueryForm** form, you can skip this task.

The process automation framework provides limited support for custom queries via the **SysQueryForm** form. A custom query lets a user add custom criteria to limit how a process runs. The framework has logic to extract user-provided custom criteria and tables to store those criteria. The custom query criteria are stored for each occurrence of a given series and can be modified individually. The framework also provides an API to apply the custom criteria to the query that is used to run the process for each occurrence.

> [!NOTE]
> When a user applies query criteria, the whole query object isn't saved. Instead the query criteria are saved individually, to allow for better support of query extensions. Therefore, extensions that are made to existing queries for existing query criteria should not cause breaking changes when this approach is used. In this case, a new extension should not require modification or re-creation of the query criteria for a saved series or occurrences. However, modification or re-creation of the query criteria is allowed.

## ProcessScheduleIQueryable interface

The **ProcessScheduleIQueryable** interface retrieves the original query (that is, the query as it was before the user modified it) and the user-modified query. These queries are used either to apply criteria when the process runs or to extract criteria when the user makes changes. These criteria are stored by the process automation framework.

This interface is accessed in the criteria form for a given implementation of process automation. For an example of access to this interface, see the **VendPaymProposalAutomationCriteria** form. That form also has a sample implementation of the **SysQueryForm** form.

| Method | Description |
|---|---|
| `public Query getOriginalQuery()` | This method gets the original, unmodified query to use as a basis for comparison. |
| `public Query getQueryForApplicationOrExtractionOfQueryCriteria()` | This method gets the query that has been or will be modified, and that is used to apply or extract query criteria. |

> [!NOTE]
> The query that is used on the implementation of **ProcessScheduleIQueryable** must have the same structure as the query that is used during the run of the underlying process that is being automated. Any structural deviation that isn't additive in nature will cause runtime errors when the saved query criteria are applied at runtime. To ensure that the query structure remains the same, you should either use a designed query or use shared logic that builds up the query.

## ProcessScheduleQueryCriteriaApplicator class

The **ProcessScheduleQueryCriteriaApplicator** class is used to apply the saved query criteria for a given occurrence to the runtime instance of the query that is used when a process is run. This API must be called by an uptaking process at a point in the run where the query is ready to accept the saved criteria. If a designed query or shared logic that builds up the query is used, this call can typically occur after the query has been correctly initialized. For an example that shows how this API is used, see the **CustVendCreatePaymJournal.constructFromAutomationExecutionContract** method.

| Method | Description |
|---|---|
| `public static void applyCriteriaForOccurrenceExecution(Query _queryToApplyCriteria, RefRecId _scheduleOccurrenceRecId)` | |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]