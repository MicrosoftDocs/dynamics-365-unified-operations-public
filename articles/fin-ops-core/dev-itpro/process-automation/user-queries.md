---
# required metadata

title: User-configurable queries
description: This topic describes how to create and use configurable queries with the process automation framework.
author: RyanCCarlson2
manager: AnnBe
ms.date: 09/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2020-09-10
ms.dyn365.ops.version: AX 7.0.0
---

# User-configurable queries

If the process isn’t going to support user configurable queries via SysQueryForm, then you can skip this task.

The process automation framework provides limited support for custom queries via the **SysQueryForm** form. This allows users to add custom criteria to limit how a process runs. The framework has logic to extract user provider custom criteria and tables to store the criteria. The custom query criteria are stored for each occurrence of a given series and can be modified individually if desired. The framework also provides an API to apply the custom criteria to the query used for process execution when the occurrence executes.

> [!NOTE]
> The query criteria that are applied by the user are saved individually, as opposed to the entire query object, to allow for better support of query extensions. As a result, extensions made to existing queries for already existing query criteria shouldn't cause breaking changes with this approach. A new extension, in this case, shouldn't
require a modification or recreation of the query criteria for a saved series or occurrences, unless desired.

## ProcessScheduleIQueryable interface

This interface retrieves the original query, before the end user modifies it, and the user-modified query. These queries are used to apply criteria when the process executes or extract criteria when the user makes changes. These criteria are stored by the framework. This interface is accessed on the criteria form for a given process automation implementation. An example access of this interface can be found on the **VendPaymProposalAutomationCriteria** form. A sample implementation of the **SysQueryForm** form can also be found on the same form.

Method | Description
---|---
`public Query getOriginalQuery()` | Get the original unmodified query to use as a basis for comparison.
`public Query getQueryForApplicationOrExtractionOfQueryCriteria()` | Gets the modified or, to be modified, query used for application or extraction of query criteria.

> [!NOTE]
> The query that is used on the implementation of the **ProcessScheduleIQueryable** must have the same structure as the query that is used during the execution of the underlying process that is being automated. Any structural deviation that is not additive in nature results in runtime errors when applying the saved query criteria at runtime. To ensure that the query structure remains the same, you should use either a designed query, or you should utilize shared logic that builds up the query.

## ProcessScheduleQueryCriteriaApplicator class

This class is used to apply saved query criteria for a given occurrence to the runtime instance of the query that is being used for execution during a process automation occurrence execution. This API must be called by an up taking process at a point in the execution that the query is ready to accept the saved criteria. If a designed query or
shared logic that builds up the query is used, then this call can typically occur after the query has been properly initialized. An example uptake of this API can be found in the **CustVendCreatePaymJournal.constructFromAutomationExecutionContract** method.

Method | Description
---|---
`public static void applyCriteriaForOccurrenceExecution(Query _queryToApplyCriteria, RefRecId _scheduleOccurrenceRecId)` | 
