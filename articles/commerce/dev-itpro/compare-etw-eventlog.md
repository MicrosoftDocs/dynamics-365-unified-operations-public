---
# required metadata

title: Comparison of ETW and EventLog logger functionality
description: This article compares the functionality of the legacy Event Tracing for Windows (ETW) logger and the EventLog logger in Microsoft Dynamics 365 Commerce.
author: stuharg
ms.date: 01/30/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.search.region: global
ms.author: stuharg
ms.reviewer: v-chgriffin
ms.search.validFrom: 2022-12-30

---

# Comparison of ETW and EventLog logger functionality

[!include [banner](../includes/banner.md)]

This article compares the functionality of the legacy Event Tracing for Windows (ETW) logger and the EventLog logger in Microsoft Dynamics 365 Commerce.

Because of the new decentralized nature of event definitions, Dynamics 365 Commerce can no longer use the ETW logger to log events as of version 10.0.32. Instead, it must use the EventLog logger. The EventLog logger is based on the Microsoft.Extensions.Logging framework and uses structured logging patterns, which simplify log generation and maintenance.

The EventLog logger logs structured XML event data and includes additional information, such as the original log level. Structured XML event data can be filtered and queried by using, for example, XPath in Event Viewer (**Filter \> XML \> Edit query manually**). During the transition from Commerce version 10.0.21 to version 10.0.32, both the ETW logger and the EventLog logger were enabled. However, the ETW logger was removed from Commerce in version 10.0.32.

For the following comparison of the loggers, Retail Server logs are used in the examples.

## Log location

### ETW

For the ETW logger, Event Viewer events are put in a provider-specific directory under **Applications and Services Logs \> Microsoft \> Dynamics**, as shown in the following example illustration.

![ETW logs location.](media\ETWLogsLocation.png)

### EventLog

For the EventLog logger, Event Viewer events are put in the **Application** log under **Windows Logs**, as shown in the following example illustration.

![EventLog logs location.](media\EventLogLogsLocation.png)

In the **Application** log, logs from providers are grouped by the value of the **Source** property. In the following example illustration, the source is **Microsoft Dynamics - Retail Server**.

![EventLog logs source.](media\EventLogLogsSource.png)

## Log structure

### ETW

#### Legacy events

For the ETW logger, legacy Event Viewer events are logged and presented according to the manifest, as shown in the following example illustration.

![ETW logs structure.](media\ETWLogsStructure.png)

#### New events

Because the ETW logger has limited support for structured logging, all new events are logged as "GenericStructuredLogging" events, as listed in the following table.

| Structured logging method name | Translated method name              | Event ID |
| ------------------------------ | ----------------------------------- | -------- |
| LogCritical                    | GenericStructuredLoggingCritical    | 65000    |
| LogError                       | GenericStructuredLoggingError       | 65001    |
| LogWarning                     | GenericStructuredLoggingWarning     | 65002    |
| LogInformation                 | GenericStructuredLoggingInformation | 65003    |
| LogDebug                       | GenericStructuredLoggingDebug       | 65004    |

Because of manifest limitations, only generic properties and the most frequently used properties are logged as separate event data entries. The remaining properties are logged as aggregated JavaScript Object Notation (JSON) objects, as shown in the following example illustration.

![ETW new logs structure.](media\ETWNewLogsStructure.png)

### EventLog

#### Legacy events

For the EventLog logger, legacy Event Viewer events are logged in legacy format for backward compatibility. For example, only a formatted message is logged, as shown in the following example illustration.

![EventLog legacy logs structure.](media\EventLogLegacyLogsStructure.png)

#### New events

For the EventLog logger, new Event Viewer events are logged in structured format to provide more information, and to enable precise filtering and querying. For example, both the formatted message and all properties from state and scope are logged as separate event data entries, as shown in the following example illustration.

![EventLog new logs structure.](media\EventLogNewLogsStructure.png)

## Query and filter structured events

You can use the Event Viewer user interface (UI) to do basic filtering by criteria such as specific provider and log level.

### ETW

For the ETW logger, you can filter and query for structured information logs as shown in the following example illustration. In this example, the **Event logs** location is specified as being under **Microsoft-Dynamics-Retail-Server**, and the **Event sources** value is **Commerce-RetailServer**.

![ETW basic filters.](media\ETWBasicFilters.png)

### EventLog

For the EventLog logger, you can filter and query for structured information logs as shown in the following example illustration. In this example, the **Event logs** location is specified as being under **Application**, and the **Event sources** value is **Microsoft-Dynamics-Retail-Server**.

![EventLog basic filters.](media\EventLogBasicFilters.png)

## Advanced filters

Event Viewer enables a subset of XPath queries to be used for filtering. You can save such filters as custom views that are filtered by, for example, event name or original log level. By saving filters as custom views, you can easily perform the same or similar tasks later. For example, you can just substitute event names in filters instead of writing a new XPath query.

### Filtering by event name

#### ETW

To search for specific events by using the ETW logger, you can query by event name via XPath, as shown in the following example illustration and XML code block.

![ETW filtering by event name.](\media\ETWFilterByEventName.png)

````xml
<QueryList>
    <Query Id="0" Path="Microsoft-Dynamics-Commerce-RetailServer/Operational">
        <Select Path="Microsoft-Dynamics-Commerce-RetailServer/Operational">
        *[EventData[Data[@Name='eventName'] and (Data='Microsoft.Dynamics.Retail.RetailServerLibrary.Authentication.JsonWebKeySetResolver+Events.KeyFoundAfterJwksForceRefresh')]]
        </Select>
    </Query>
</QueryList>
````

This query shows all logs from the **Microsoft-Dynamics-Commerce-RetailServer/Operational** log that have the event name **Microsoft.Dynamics.Retail.RetailServerLibrary.Authentication.JsonWebKeySetResolver+Events.KeyFoundAfterJwksForceRefresh**.

#### EventLog

For the EventLog logger, structured logging assumes that events are uniquely identifiable by their **EventName** value. **EventId** values are default enumeration (enum) values. Because events are distributed across repositories and classes, there's no feasible way to enforce the uniqueness of **EventId** values that are simple integers.

To search for specific events by using the EventLog logger, you can query by event name via XPath, as shown in the following example illustration and XML code block.

![EventLog filtering by event name.](media\EventLogFilterByEventName.png)

````xml
<QueryList>
    <Query Id="0" Path="Application">
        <Select Path="Application">
        *[System[Provider[@Name=
        'Microsoft Dynamics - Retail Server']] and 
        EventData[Data and 
        (Data=
        'EventName: Microsoft.Dynamics.Retail.RetailServerLibrary.Authentication.JsonWebKeySetResolver+Events.KeyFoundAfterJwksForceRefresh')]]</Select>
    </Query>
</QueryList>
````

This query shows all logs from the **Application** log that have the **Microsoft Dynamics - Retail Server** provider and the event name **Microsoft.Dynamics.Retail.RetailServerLibrary.Authentication.JsonWebKeySetResolver+Events.KeyFoundAfterJwksForceRefresh**.

### Filtering by original log level

The EventLog logger supports following entry types:

- Error
- Warning
- Information
- SuccessAudit
- FailureAudit

The EventLog logger maps log levels from different subsystems to match entry type limitations. For more information, see [EventLogEntryType Enum](/dotnet/api/system.diagnostics.eventlogentrytype?view=netframework-4.6.1&preserve-view=true).

The following table shows the current log level mapping between subsystems.

| EventLevel (legacy events) | LogLevel (Microsoft.Extensions.Logging) | EventLogEntryType |
| -------------------------- | --------------------------------------- | ----------------- |
| Undefined                  | None                                    | Not logged        |
| LogAlways                  | Critical                                | Error             |
| Critical                   | Critical                                | Error             |
| Error                      | Error                                   | Error             |
| Warning                    | Warning                                 | Warning           |
| Informational              | Information                             | Information       |
| Verbose                    | Debug                                   | Information       |
| (No corresponding EventLevel) | Trace                                   | Information       |

To allow for more precise filtering, information about the original log level from Microsoft.Extensions.Logging is stored as part of the event. This approach lets you query by original log level via XPath, as shown in the following example query.

````xml
<QueryList>
    <Query Id="0" Path="Application">
        <Select Path="Application">
        *[System[Provider[@Name=
        'Microsoft Dynamics - Retail Server']] and 
        EventData[Data and 
        (Data=
        'LogLevel: Information')]]</Select>
    </Query>
</QueryList>
````

This query shows all logs from the **Application** log that have the **Microsoft Dynamics - Retail Server** provider and an original log level of **Information**. Therefore, you can separate **Information** logs from **Debug** and **Trace** logs.
