---
# required metadata

title: Troubleshooting performance issues in ER configurations
description: This topic explains how to find and fix performance issues in Electronic reporting (ER) configurations.
author: NickSelin
ms.date: 05/14/2021
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

This topic explains how to find and solve performance issues in [Electronic Reporting](general-electronic-reporting.md) (ER)[configurations](general-electronic-reporting.md#Configuration).

## Overview

Usually, performance investigation consists of several steps:

1.  [Collect](#collecting-data) data.
2.  Analyze the collected data.
3.  Using ER configurations, make [modifications](#making-changes) based on the analysis, or decide to collect more data.

## Troubleshooting 

### Analyze execution time

Execution time can depend on random factors such as other tasks running in the same environment or caching using data when they are accessed the first time, so repeat the execution and measurement several times.

Sometimes performance issues are caused by the X++ code used to launch an ER format configuration that is used for reporting, not the ER format configuration itself.

1. Look at the execution time of report in the [Infolog](#infolog-time) or the [Event log](#event-log-time). 
2. Compare the execution time of the report with the total execution time in the scenario.
3. If the report time is much less then the total execution time, there are two possible situations:

  - If the reports work with a small amount of data, the issue could be with loading time of configuration.
  - If the report processes a large amount of data, the issue could be with preprocessing X++. Use [TraceParser](#analyze-trace-parser-trace) to analyze this case.
  - In other cases, please, see the next sections.

4. Run multiple tests with different data amounts to determine how execution time depending on the amount of data.

### <a name="analyze-trace-parser-trace"></a>Analyze trace parser trace

Prepare a small example or collect several traces in random parts of the report generation.

Perform a standard bottom-to-up analysis in [Trace Parser](#trace-parser) and note:
- What are the top methods for time consumption? What part of overall time do they use? 
- Answer the same questions for queries.

If you see that methods are prefixed with ER, continue to the next section. 

If you see that methods or queries originated in application suite, consider generic optimizations (creation of indexes, etc.)

Analyze the number of calls. If the number is significantly higher than expected, consider caching the corresponding nodes of configuration. 

### <a name="analyze-database-calls"></a>Analyze database calls

Prepare an example with small amount of data to collect [ER trace](#electronic-reporting-traces). 

Open trace in the ER model mapping designer and look at the bottom of the page:

  - Is there any query duplication? If so, consider one of the following fixes:
    - [Use caching](#use-caching): If you think there are several accesses inside one parent record.
    - [Use cached parametrized calculated field](#cached-parametrized): If you think there are accesses inside different records but to the same record.
    - [Use join](#use-join-datasource): If you have access to the substantial number of different records.
  - Does the number of queries and fetched records correspond with the overall amount of data? For example, if you have 10 lines in a document do the stats show that the report extracts 10 lines or 1000 lines? If you have a substantial number of fetched records, consider one of the following:
     - [Use the FILTER](#filter) function instead of WHERE to process data on the SQL side.
     - Use caching to avoid fetching the same data.
     - [Use collected data functions](#collected-data) to avoid fetching the same data for summarization.

### Analyze PerfView trace

[Perfview](#perfview) is a tool for experienced developers. For more detailed information of the following steps, see [Wall Clock Time Investigation Basics](https://channel9.msdn.com/Series/PerfView-Tutorial/Tutorial-12-Wall-Clock-Time-Investigation-Basics) .

  1. Collect a trace with thread time.
  2. Include only stacks with **runUnattended** to filter only thread that has configuration execution (add **runUnattended to IncPats** input box).
  3. Fold all CPU, Network, and Blocked time.
  4. Load [ER presets for perfview](ER_PerfViewPresets.xml).
  5. Select **ER** > **Other preset**.
  6. Look at the names:
     - You probably see the platform code that consumes most time.
     - You can double-click, and go up through **callees**:
        - If you find some classes with the **ERExpression** prefix and they are functions related to formulas, you can guess the function name by class name and look at the ER repo to see the attributes.

### Fixes

- If you see that most CPU are consumed by queries, try to reduce number of queries:
  - [Look at GER trace](#analyze-database-calls) for duplicated queries.
  - Look how many records are fetched and evaluate how much data should be fetched theoretically.
- By used functions, try to find the place in the configuration that consumes the most resources.
- If you see that most of the CPU is consumed by data collection functions, consider replacing them with *SQL group by* on the model mapping side.

### <a name="collecting-data"></a>Collecting data

Depending on your environment, there are several ways to collect available data.
  - Get the total running time:
    - From the Infolog
    - From the Event log
  - Profile the execution:
    - Using ER tools
    - Using TraceParser
    - Using PerfView

#### Collecting data on production environment

Sometimes issues can be reproduced only on a production environment. Data can be collected by:
- Using [Trace parser](../perf-test/trace-trace-tutorial.md) traces.
- Using [ER execution](trace-execution-er-troubleshoot-perf.md) traces.
- Using the total execution time.

#### Collecting data on a development environment

In addition to tools that can be used in the production environment, there are several tools you can use in a development environment:
  - Event log (Microsoft-Dynamics-ElectronicReporting). This can give you the total execution time.
  - Common .NET tools such as PerfView.

Also, on a development environment there is more flexibility to experiment. For example, you can turn off parts of reports to see how how the execution time is affected.

### <a name="tools"></a>Tools

#### <a name="infolog-time"></a> Execution time in Infolog

Electronic reporting can show the execution time of the configuration in the Infolog. This option works only for a specific user and specific company, and only for interactive sessions. To enable this feature, complete the following steps.

1.  Go to **Organization administration** > **Electronic reporting** > **Configurations** page.
2.  On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
3.  In the **User parameters** dialog box, set the **Show file generation time** parameter to **Yes**.

#### <a name="event-log-time"></a>Execution time in event log

1. Open Windows Event Viewer.
2. Under **Applications and Services logs**, open **Microsoft-Dynamics-ElectronicReporting/Operational**.
3. Look for **FormatMapingRun** events with **EventID=2** as they contain the elapsed time information.

#### <a name="trace-parser"></a>Trace parser traces 

Because Electronic reporting is implemented in X++, you can use common X++ tools for analyze performance. For more information, see [Take traces by using Trace parser](../perf-test/trace-trace-tutorial.md).

There are a couple of limitations. Because part of ER is implemented in C#, not all of the details will be available. However, you can see the data access details. Additionally, the long report runs can exceed trace storage limitations.

#### <a name="electronic-reporting-traces"></a>Electronic reporting traces

Electronic reporting can collect its own traces and have tools for visualization and analysis of them see 
 [Trace the execution of ER formats to troubleshoot performance issues](trace-execution-er-troubleshoot-perf.md) for details.

#### <a name="perfview"></a>PerfView

Since both X++ and ER are implemented on top of the .NET platform, you can use common .NET tools. For example, you can use [PerfView](https://github.com/Microsoft/perfview) which is a free tool.

You can also collect data from command line. For example, this powershell script collects the execution time until any format execution is stopped on the machine.

```powershell
c:\programs\PerfView collect "e:\traces\$(date -format "ddMMyyyy_hhmm").etl" `
     -CircularMB:20000 -ThreadTime `
     -NoNGenRundown `
     -StopOnEtwEvent:Microsoft-Dynamics-ElectronicReporting/FormatMappingRun/Stop
```

There are a couple of limitations. You must have administrative access to machine and you must be an experienced developer as there is a steep learning curve.


### <a name="making-changes"></a>Making changes

#### <a name="use-caching"></a>Use caching

Caching reduces the time required to fetch data again, but is does cost memory. Use caching for cases when the amount of fetched data isn't very big. For more information, see this [example](trace-execution-er-troubleshoot-perf.md#improve-the-model-mapping-based-on-information-from-the-execution-trace) about using caching.

#### <a name="cached-parametrized"></a>Use a cached parametrized calculated field

Sometimes there are several values, like account name or account number, that must be looked up repeatedly. You save time by creating a calculated field with parameters on the top level and then adding the field to the cache.

We recommend that you use this only when cached data size is small. For more information, see [Improve the performance of ER solutions by adding parameterized CALCULATED FIELD data sources](er-calculated-field-ds-performance.md).

#### <a name="use-join-datasource"></a>Use join datasource

The Join data source allows several connected records to be fetched using one query instead of fetching each connected record with a separate query. For example, if you have 1000 lines and fetch item data for each line by relation, you will have 1000 + 1 query. The same data fetched using join will cost only 1 query. For more information, see [Use JOIN data sources in ER model mappings to get data from multiple application tables](er-join-data-sources.md). 

#### <a name="filter"></a>Use FILTER instead of WHERE

The [FILTER](er-functions-list-filter.md) function executes conditions on SQL server, while the WHERE function fetches all data from the list one-by-one and applies the condition for each. If you select one record from 1000 using WHERE, all records will be fetched. If you select using FILTER, exactly one will be fetched. Also, FILTER can use indexes on the database side.

#### <a name="collected-data"></a>Using collected data functions/accumulated data datasource

If your configuration has a group by component that summarizes data already fetched by report, the component will fetch all the data again. Using collected data functions can let ER accumulate data during the first fetch. For more information, see [ER Configure format to do counting and summing](tasks/er-format-counting-summing-2.md).

#### Rewrite portions of the configuration in X++

ER supports calling methods of tables and classes, including extensions. Consider rewriting parts of the model mapping in X++ to get better performance.

Electronic Reporting can consume data from:
  - Classes (**object** and **class** data sources)
  - Tables (**table** and **table records**) datasource

[ER API](er-apis-app73.md#how-to-access-internal-x-objects-by-using-erobjectsfactory) also provides a way to send precalculated data from the calling code. The application suite contains numerous examples of this approach.
