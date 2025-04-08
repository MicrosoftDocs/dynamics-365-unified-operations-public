---
title: Troubleshooting performance issues in ER configurations
description: Learn how to find and fix performance issues in Electronic reporting (ER) configurations, including fixes and tools.
author: kfend
ms.author: kfend
ms.topic: article
ms.date: 05/12/2022
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-04-01
ms.search.form: ERModelMappingDesigner, EROperationDesigner, ERFormatMappingRunJobTable, ERParameters, ERSolutionTable
ms.dyn365.ops.version: 10.0.1
ms.assetid: 
---

# Troubleshooting performance issues in ER configurations

This article explains how to find and solve performance issues in [Electronic reporting](general-electronic-reporting.md) (ER) [configurations](general-electronic-reporting.md#Configuration).

Typically, performance investigation consists of several steps.

1. [Collect](#collecting-data) data.
2. Analyze the collected data.
3. Based on the results of the analysis, use ER configurations to [make changes](#making-changes), or decide to collect more data.

## Troubleshooting

### Analyze execution time

Execution time can depend on unpredictable factors, such as other tasks that are running in the same environment and caching that uses data when it's called for the first time. Therefore, you should repeat the execution and measurement several times.

Sometimes, performance issues aren't caused by an ER format configuration that is used for reporting. Instead, they are caused by the X++ code that is used to open that ER format configuration.

1. In either the [Action center](#infolog-time) or the [event log](#event-log-time), look at the execution time of the report.
2. Compare the execution time of the report with the total execution time in the scenario.
3. If the execution time of the report is much less than the total execution time, consider the amount of data that the report processes:

    - If the report processes a small amount of data, the issue might involve the loading time of the configuration.
    - If the report processes a large amount of data, the issue might involve preprocessing X++. Use [Trace parser](#analyze-trace-parser-trace) to analyze this case.

    For other cases, see the next sections.

4. Run multiple tests that involve different amounts of data to determine how the execution time depends on the amount of data.

### <a name="analyze-trace-parser-trace"></a>Analyze Trace parser traces

Prepare a small example, or collect several traces during random parts of the report generation.

Then, in [Trace parser](#trace-parser), do a standard bottom-up analysis, and answer the following questions:

- What are the top methods in terms of time consumption?
- What part of the overall time do those methods use?

Answer the same questions for queries.

If you see that methods are prefixed with "ER," move on to the next section.

If you see that methods or queries originated in the application suite, consider generic optimizations (for example, create indexes).

Analyze the number of calls. If the number is significantly higher than expected, consider caching the corresponding nodes of the configuration.

### <a name="analyze-database-calls"></a>Analyze database calls

Prepare an example that has a small amount of data, so that you can collect an [ER trace](#electronic-reporting-traces).

Then open the trace in the ER model mapping designer, and look at the bottom of the page. Answer the following questions:

- Is there any query duplication? If there is, consider one of the following fixes:

    - [Use caching](#use-caching) if you think that there are several calls inside one parent record.
    - [Use a cached, parameterized calculated field](#cached-parameterized) if you think that there are calls to the same record inside different records.
    - [Use a **JOIN** data source](#use-join-datasource) if you have to read to a substantial number of different records from a database.

- Does the number of queries and fetched records correspond to the overall amount of data? For example, if a document has 10 lines, do the statistics show that the report extracts 10 lines or 1,000 lines? If you have a substantial number of fetched records, consider one of the following fixes:

    - [Use the **FILTER** function instead of the **WHERE** function](#filter) to process data on the Microsoft SQL Server side.
    - Use caching to avoid fetching the same data.
    - [Use collected data functions](#collected-data) to avoid fetching the same data for summarization.

### Analyze PerfView traces

[PerfView](#perfview) is a tool for experienced developers. For more detailed information about the following steps, see [Wall Clock Time Investigation Basics](https://channel9.msdn.com/Series/PerfView-Tutorial/Tutorial-12-Wall-Clock-Time-Investigation-Basics).

1. Collect a trace by using thread time.
2. Include only stacks that use **runUnattended**, to filter only the thread that has configuration execution. (Add **runUnattended** to the **IncPats** input box.)
3. Fold all CPU, network, and blocked time.
4. Load [ER presets for PerfView](https://download.microsoft.com/download/2/d/0/2d037b0f-ffd1-4d65-b64f-fcdf51f2c81f/ER_PerfViewPresets.xml).
5. Select **ER** \> **Other preset**.
6. Look at the names:

    - You will probably see the platform code that consumes the most time.
    - You can double-tap (or double-click) and go up through **callees**.

        If you find classes that have the prefix "ERExpression," and if they are functions that are related to formulas, you can guess the function name based on the class name, and you can look at the ER repo to view the attributes.

### Fixes

- If you see that most of the CPU time is consumed by queries, try to reduce the number of queries:

    - [Review the ER trace](#analyze-database-calls) for duplicated queries.
    - See how many records are fetched, and evaluate how much data should theoretically be fetched.

- If you see that most of the CPU time is consumed by the functions that are used, try to find the place in the configuration that consumes the most resources.
- If you see that most of the CPU time is consumed by data collection functions, consider replacing them with *SQL group by* on the model mapping side.

### <a name="collecting-data"></a>Collecting data

Depending on your environment, there are several ways to collect available data:

- Get the total running time:

    - From the Action center
    - From the event log

- Profile the execution:

    - By using ER tools
    - By using Trace parser
    - By using PerfView

#### Collecting data in a production environment

Sometimes, issues can be reproduced only in a production environment. Data can be collected in the following ways:

- By using [Trace parser](../perf-test/trace-trace-tutorial.md) traces
- By using [ER execution](trace-execution-er-troubleshoot-perf.md) traces
- By using the total execution time

#### Collecting data in a development environment

In addition to the tools that can be used in a production environment, there are several tools that you can use in a development environment:

- Event log (Microsoft-Dynamics-ElectronicReporting). This log can give you the total execution time.
- Common .NET tools, such as PerfView.

Additionally, a development environment gives you more flexibility to experiment. For example, you can turn off parts of reports to see how the execution time is affected.

### <a name="tools"></a>Tools

#### <a name="infolog-time"></a>Execution time in the Action center

ER can show the execution time of the configuration in the Action center. This option works only for a specific user and a specific company, and only for interactive sessions. To make this feature available, follow these steps.

1. Go to **Organization administration** \> **Electronic reporting** \> **Configurations**.
2. On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
3. In the **User parameters** dialog box, set the **Show file generation time** option to **Yes**.

#### <a name="event-log-time"></a>Execution time in the event log

1. Open Windows Event Viewer.
2. Under **Applications and Services logs**, open **Microsoft-Dynamics-ElectronicReporting/Operational**.
3. Look for **FormatMapingRun** events where **EventID=2**, because these events contain the information about elapsed time.

#### <a name="trace-parser"></a>Trace parser traces 

Because ER is implemented in X++, you can use common X++ tools to analyze performance. For more information, see [Take traces by using Trace parser](../perf-test/trace-trace-tutorial.md).

There are a few limitations to this approach. Because part of ER is implemented in C#, not all the details will be available. However, you can view the data usage details. Additionally, long report runs can exceed trace storage limitations.

#### <a name="electronic-reporting-traces"></a>ER traces

ER can collect its own traces, and it has visualization and analysis tools for those traces. For more information, see [Trace the execution of ER formats to troubleshoot performance issues](trace-execution-er-troubleshoot-perf.md).

#### <a name="perfview"></a>PerfView

Because both X++ and ER are implemented on top of the .NET platform, you can use common .NET tools. For example, you can use the free [PerfView](https://github.com/Microsoft/perfview) tool.

You can also collect data from the command line. For example, the following Windows PowerShell script collects the execution time until any format execution is stopped on the machine.

```powershell
c:\programs\PerfView collect "e:\traces\$(date -format "ddMMyyyy_hhmm").etl" `
    -CircularMB:20000 -ThreadTime `
    -NoNGenRundown `
    -StopOnEtwEvent:Microsoft-Dynamics-ElectronicReporting/FormatMappingRun/Stop
```

There are a few limitations to this approach. You must have administrative access to the machine. Additionally, you must be an experienced developer, because there is a steep learning curve.

### <a name="making-changes"></a>Making changes

#### <a name="use-caching"></a>Use caching

Although caching reduces the amount of time that is required to fetch data again, it costs memory. Use caching in cases where the amount of fetched data isn't very large. For more information and an example that shows how to use caching, see [Improve the model mapping based on information from the execution trace](trace-execution-er-troubleshoot-perf.md#improve-the-model-mapping-based-on-information-from-the-execution-trace).

#### <a name="reduce-fetched-data"></a>Reduce volume of data fetched

You can reduce memory consumption for caching by limiting the number of fields in the records of an application table that you fetch at runtime. In this case, you will fetch only those field values of an application table that you need in your ER model mapping. Other fields in that table won't be fetched. Therefore, the volume of memory that is required to cache fetched records is reduced. For more information, see [Improve performance of ER solutions by reducing the number of table fields that are fetched at runtime](er-reduce-fetched-fields-number.md).

#### <a name="cached-parameterized"></a>Use a cached, parameterized calculated field

Sometimes, values must be looked up repeatedly. Examples include account names and account numbers. To help save time, you can create a calculated field that has parameters on the top level, and then add the field to the cache.

We recommend that you use this approach only when the size of the cached data is small. For more information, see [Improve the performance of ER solutions by adding parameterized CALCULATED FIELD data sources](er-calculated-field-ds-performance.md).

#### <a name="use-join-datasource"></a>Use a JOIN data source

A **JOIN** data source enables several connected records to be fetched by one query. A separate query doesn't have to be used to fetch each connected record. For example, if you have 1,000 lines, and you fetch item data for each line by relation, you will have 1,001 queries (= 1,000 + 1). If you use a **JOIN** data source, you will use only one query to fetch the same data. For more information, see [Use JOIN data sources in ER model mappings to get data from multiple application tables](er-join-data-sources.md).

#### <a name="filter"></a>Use the FILTER function instead of the WHERE function

The **[FILTER](er-functions-list-filter.md)** function runs conditions on SQL Server, whereas the **WHERE** function fetches all data from the list, one record at a time, and applies the condition for each record. For example, you want to select one record out of 1,000 records. If you use **WHERE**, all 1,000 records will be fetched. However, if you use **FILTER**, exactly one record will be fetched. **FILTER** can also use indexes on the database side.

#### <a name="collected-data"></a>Using collected data functions or an accumulated data data source

If your configuration has a *group by* component that summarizes previously fetched data by report, the component will fetch all the data again. By using collected data functions, you enable ER to accumulate data during the first fetch. For more information, see [ER Configure format to do counting and summing](tasks/er-format-counting-summing-2.md).

#### Rewrite parts of the configuration in X++

ER supports calling methods of tables and classes, including extensions. Consider rewriting parts of the model mapping in X++ to help improve performance.

ER can consume data from the following sources:

- Classes (**object** and **class** data sources)
- Tables (**table** and **table records** data sources)

The [ER application programming interface (API)](er-apis-app73.md#how-to-access-internal-x-objects-by-using-erobjectsfactory) also provides a way to send precalculated data from the calling code. The application suite contains numerous examples of this approach.
