---
# required metadata

title: Troubleshooting performance issues in ER configurations
description: This topic explains how to find and fix performance issues in Electronic reporting (ER) configurations
author: NickSelin
ms.date: 04/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERModelMappingDesigner, EROperationDesigner, ERFormatMappingRunJobTable, ERParameters, ERSolutionTable
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 220314
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: maximbel
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.1

---

# Troubleshooting performance issues in ER configurations

This topic explains how to find and solve performance issues in the [Electronic Reporting](general-electronic-reporting.md)  (ER) [configurations](general-electronic-reporting.md#Configuration).

## Overview

Usually, performance investigation consists in several steps:

1.  First we [collect](#collecting-data) some data.
2.  Then, we need to analyze the collected data.
3.  Finally, we [modify](#making-changes) using ER configurations based on the analysis or decide to collect some more data.

## Troubleshooting steps

### Analyze execution time

Take into account that execution time can depend on random factors such as other tasks running in the same environment, caching using data when they are accessed the first time, etc. So, repeat execution and measurement several times.

Sometimes performance issues are caused by the X++ code using to launch an ER format configuration that is used for reporting, not an ER format configuration itself.

1. Look at execution time of report in [Infolog](#infolog-time) or [Event log](#event-log-time) (see [Tools](#tools)).
2. Compare execution time of report with total execution time in scenario.
3. If report time is much less then total execution time, then it can be two situations:

  - If reports work with small amount of data issue can be with loading time of configuration.
  - If report process large amount of data it can be issue with preprocessing X++. Use [TraceParser](#analyze-trace-parser-trace) to analyze this case.
  - In other cases, please, see the next topics.

4. Try to run several tests with different amount data to determine how execution time depend on amount data.

### <a name="analyze-trace-parser-trace"></a>Analyze trace parser trace

Prepare a small example or collect several traces in random parts of report generation.

Perform standard bottom-to-up analysis in [Trace Parser](#trace-parser):
- What are the top methods for time consumption? What part of overall time do they use? 
- Answer the same questions for queries

If you see that methods are prefixed with ER please go to the next section. 

If you see that methods or queries originated in application suite, please, consider generic optimizations (creation of indexes, etc.)

Analyze number of calls. If number is significantly higher than expected consider caching corresponding nodes of configuration. 

### <a name="analyze-database-calls"></a>Analyze database calls

Prepare an example with small amount of data. Collect [ER trace](#electronic-reporting-traces). 

Open trace in the ER model mapping designer, look at the bottom of the page:

  - Do you have any query duplication? If so, consider one of the following fixes:
    - [Use caching](#use-caching) (in case you think there are several accesses inside one parent record)
    - [Use cached parametrized calculated field](#cached-parametrized) (in case you think there are accesses inside different records but to the same record)
    - [Use join](#use-join-datasource) (in case you have accesses to the substantial number of different records)
  - Does the number of queries and fetched record correspond with overall amount of data? For example, if you have 10 lines in a document do the stats show that report extracts 10 lines or 1000 lines? If you have the substantial number of fetched records consider one of the following:
     - [Use FILTER](#filter) function instead of WHERE for processing data on SQL side.
     - Use caching to avoid fetching the same data.
     - [Use collected data functions](#collected-data) to avoid fetching the same data for summarization.

### Analyze PerfView trace

[Perfview](#perfview) is a tool for experienced developers. See also [Wall Clock Time Investigation Basics](https://channel9.msdn.com/Series/PerfView-Tutorial/Tutorial-12-Wall-Clock-Time-Investigation-Basics) if you want to understand explanation of these steps.

  1. Collect a trace with thread time.
  2. Include only stacks with **runUnattended** to filter only thread with configuration execution (add **runUnattended to IncPats** input box).
  3. Fold all CPU, Network and Blocked time.
  4. Load [ER presets for perfview](ER_PerfViewPresets.xml).
  5. Select ER \> Other preset.
  6. Look at names:
     1. You, probably, see platform code that consumes most time.
     2. You can double click and go up through "callees":
        1. If you find some classes with the **ERExpression** prefix - that are functions related to formulas, you can guess function name by class name and look at the ER repo and see attributes.

### Fixes

- If you see that most CPU consumed by queries, try to reduce number of queries:
  - [Look at GER trace](#analyze-database-calls) for duplicated queries.
  - Look how many records are fetched and think how much data should be fetched theoretically.
- By used functions try to find place in configuration that consumes most resources.
- If you see that most CPU is consumed by data collection functions, consider replacing them with SQL group by on the model mapping side.

### <a name="collecting-data"></a>Collecting data

Depending on environment there are several ways to collect data available:
  - Get total running time
    - From Infolog
    - From Event log
  - Profile execution
    - Using ER tools
    - Using TraceParser
    - Using PerfView

#### Collecting data on production environment

Sometimes issues can be reproduced only on production environment. Possible ways of collecting data are:
- Use [Trace parser](../perf-test/trace-trace-tutorial.md) traces
- Use [ER execution](trace-execution-er-troubleshoot-perf.md) traces
- Use total execution time

#### Collecting data on development environment

In addition to tools that can be used in production environment, in dev environment there are several tools that can be used:
  - Event log (Microsoft-Dynamics-ElectronicReporting) - there we can get total execution time
  - Common .NET tools such as PerfView

Also, on development environment we have more flexibility to make experiments (for example, disable parts of reports to see how it affects execution time).

### <a name="tools"></a>Tools

#### <a name="infolog-time"></a> Execution time in Infolog

Electronic reporting can show execution time of configuration in the Infolog. This option works only for specific user and specific company and only for interactive sessions. To enable this feature, do the following:

1.  Go to **Organization administration \> Electronic reporting \> Configurations** page.
2.  On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
3.  In the **User parameters** dialog box, set the **Show file generation time** parameter to **Yes**.

#### <a name="event-log-time"></a>Execution time in event log

- Open Windows Event Viewer
- Open Microsoft-Dynamics-ElectronicReporting/Operational under "Applications and Services logs"
- Look for FormatMapingRun events with EventID=2 - they contain elapsed time

#### <a name="trace-parser"></a>Trace parser traces 

Electronic reporting is implemented in X++, so one can use common X++ tools for analyze performance. [See documentation](../perf-test/trace-trace-tutorial.md) for details.

Limitations: 
- Since part of ER is implemented in C# not all details will be available, but one can see data access details at least.
- Long report runs can exceed trace storage limitations.

#### <a name="electronic-reporting-traces"></a>Electronic reporting traces

Electronic reporting can collect its own traces and have tools for visualization and analysis of them see 
 [Trace the execution of ER formats to troubleshoot performance issues](trace-execution-er-troubleshoot-perf.md) for details.

#### <a name="perfview"></a>PerfView

Since both X++ and ER are implemented on top of .NET platform one can use common .NET tools.

[PerfView](https://github.com/Microsoft/perfview) is a free tool.

One can collect data from command line, for example this powershell script collects execution time until any format execution stopped on machine:

```powershell
c:\programs\PerfView collect "e:\traces\$(date -format "ddMMyyyy_hhmm").etl" `
     -CircularMB:20000 -ThreadTime `
     -NoNGenRundown `
     -StopOnEtwEvent:Microsoft-Dynamics-ElectronicReporting/FormatMappingRun/Stop
```

Limitations:
  - Need administrative access to machine
  - Steep learning curve (need to be an experienced developer)


### <a name="making-changes"></a>Making changes

#### <a name="use-caching"></a>Use caching

Caching reduce time required to fetch data again, but at cost of memory. So, use caching for cases when amount of fetched data is not very big. See also [example](trace-execution-er-troubleshoot-perf.md#improve-the-model-mapping-based-on-information-from-the-execution-trace) of using caching.

#### <a name="cached-parametrized"></a>Use cached parametrized calculated field

Sometimes we have several values (like account name for account number) looked up repeatedly. We can save time by:
  1. Creating a calculated field with parameters on the top level
  2. Adding it to cache

Please, use it only when cached data size is small. See also [Improve the performance of ER solutions by adding parameterized CALCULATED FIELD data sources](er-calculated-field-ds-performance.md)

#### <a name="use-join-datasource"></a>Use join datasource

See also [documentation on Join datasource](er-join-data-sources.md). Join data source allows to fetch several connected records using one query instead of fetching each connected record with a separate query. For example, if you have 1000 lines and fetch item data for each line by relation, you will have 1000 + 1 query. The same data fetched using join will cost only 1 query.

#### <a name="filter"></a>Use FILTER instead of WHERE

The [FILTER](er-functions-list-filter.md) function executes condition on SQL server, while WHERE functions fetches all data from list one-by-one and apply condition for each. If you select 1 record from 1000 using WHERE - all records will be fetched. If you select using FILTER - exactly this one will be fetched. Also, FILTER can use indexes on database side.

#### <a name="collected-data"></a>Using collected data functions / accumulated data datasource

If your configuration has a group by component that summarizes data already fetched by report, it will fetch all the data once again. Using collected data functions can let ER accumulate data during the first fetch. See also [documentation](tasks/er-format-counting-summing-2.md) for details and examples.

#### Rewrite portions of configuration in X++

ER supports calling methods of tables, classes including extensions. You can consider rewriting parts of model mapping in X++ to get better performance.

Electronic Reporting can consume data from:
  - Classes ("object" and "class" data sources)
  - Tables ("table" and "table records") datasource

[ER API](er-apis-app73.md#how-to-access-internal-x-objects-by-using-erobjectsfactory) also provides a way to send a precalculated data from the calling code. Application suite contains numerous examples of this approach.
