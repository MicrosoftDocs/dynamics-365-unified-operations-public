---
# required metadata

title: Comparison of ETW and EventLog logger functionality
description: This article compares the functionality of the legacy Event Tracing for Windows (ETW) logger with the EventLog logger in Microsoft Dynamics 365 Commerce.
author: stuharg
ms.date: 12/22/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.search.region: global
ms.author: stuharg
ms.reviewer: v-chgriffin
ms.search.validFrom: 2022-12-30

---

# Comparison of ETW and EventLog logger functionality

[!include [banner](../includes/banner.md)]

This article compares the functionality of the legacy Event Tracing for Windows (ETW) logger with the EventLog logger in Microsoft Dynamics 365 Commerce.

As of Dynamics 365 Commerce version 10.0.32, the new, decentralized nature of event definitions required Commerce to switch from using the ETW logger to using the EventLog logger to log events. The EventLog logger is based on the Microsoft.Extensions.Logging framework and uses structured logging patterns, which simplify log generation and maintenance.

The EventLog logger logs structured XML event data and includes additional information, such as the original log level. Structured XML event data can be filtered and queried, for example by using XPath in Event Viewer (**Filter \> XML \> Edit query manually**). During the transition period from Commerce version 10.0.21 to version 10.0.32, both the ETW and EventLog loggers were enabled. The ETW logger was removed from Commerce starting in version 10.0.32.

For the comparison between loggers, Retail Server logs are used in the following examples.

## Log location

### ETW

With the ETW logger, Event Viewer events are placed under **Applications and Services Logs \> Microsoft \> Dynamics** in a provider-specific directory, as shown in the following example image.

![ETW logs location](media\ETWLogsLocation.png)

### Event Log

With the EventLog logger, Event Viewer events are placed in the **Windows Logs  \> Application** log, as shown in the following example image.

![EventLog logs location](media\EventLogLogsLocation.png)

In the **Application** log, logs from providers are grouped by the source property, shown in the following example image as **Microsoft Dynamics - Retail Server**.

![EventLog Logs Source](media\EventLogLogsSource.png)

## Log structure

### ETW

#### Legacy events

With ETW logger, legacy Event Viewer events are logged and presented according to the manifest, as shown in the following example image.

![ETW Logs Structure](media\ETWLogsStructure.png)

#### New events

Because the ETW logger has limited support for structured logging, all new events are logged as "GenericStructuredLogging" events, as listed in the following table.

| Structured logging method name | Translated method name              | Event ID |
| ------------------------------ | ----------------------------------- | -------- |
| LogCritical                    | GenericStructuredLoggingCritical    | 65000    |
| LogError                       | GenericStructuredLoggingError       | 65001    |
| LogWarning                     | GenericStructuredLoggingWarning     | 65002    |
| LogInformation                 | GenericStructuredLoggingInformation | 65003    |
| LogDebug                       | GenericStructuredLoggingDebug       | 65004    |

Due to manifest limitations, only generic and the most commonly used properties are logged as separate event data entries. The rest of the properties are logged as aggregated JSON objects, as shown in the following example image.

![ETW New Logs Structure](media\ETWNewLogsStructure.png)

### EventLog

#### Legacy events

With EventLog logger, legacy Event Viewer events are logged in legacy format for backward compatibility. For example, only a formatted message is logged, as shown in the following image.

![EventLog Legacy Logs Structure](media\EventLogLegacyLogsStructure.png)

#### New events

With EventLog logger, new Event Viewer events are logged in structured format to provide more information and allow precise filtering and querying. For example, both the formatted message and all properties from state and scope are logged as separate event data entries, as shown in the following image.

![EventLog New Logs Structure](media\EventLogNewLogsStructure.png)

## Query and filter structured events

For basic filtering, it's possible to use the Event Viewer UI to filter by criteria such as specific provider and log level. 

### ETW

With ETW logger, you can filter and query for structured information logs as shown in the following example image, where the **Event logs** location is specified as being under **Microsoft-Dynamics-Retail-Server**, and the **Event sources** value is **Commerce-RetailServer**.

![ETW Basic Filters](media\ETWBasicFilters.png)

### EventLog

With EventLog logger, you can filter and query for structured information logs as shown in the following example image, where the **Event logs** location is specified as being under **Application**, and the **Event sources** value is **Microsoft-Dynamics-Retail-Server**.

![EventLog Basic Filters](media\EventLogBasicFilters.png)

## Advanced filters

Event Viewer allows a subset of XPath queries to be used for filtering. You can save such filters as custom views, for example filtering by event name or filtering by original log level. Filters saved as custom views allow you to easily perform the same or similar tasks at a later time, for example substituting event names in filters instead of writing a new XPath query.

### Filter by event name

#### ETW

To search for specific events using the ETW logger, you can query them by event name via XPath, as shown in the following example image and XML code block.

![ETW Filter By Event Name](\media\ETWFilterByEventName.png)

````xml
<QueryList>
  <Query Id="0" Path="Microsoft-Dynamics-Commerce-RetailServer/Operational">
    <Select Path="Microsoft-Dynamics-Commerce-RetailServer/Operational">
    *[EventData[Data[@Name='eventName'] and (Data='Microsoft.Dynamics.Retail.RetailServerLibrary.Authentication.JsonWebKeySetResolver+Events.KeyFoundAfterJwksForceRefresh')]]
    </Select>
  </Query>
</QueryList>
````

This query displays all logs from the **Microsoft-Dynamics-Commerce-RetailServer/Operational** log, with **eventName** equal to **Microsoft.Dynamics.Retail.RetailServerLibrary.Authentication.JsonWebKeySetResolver+Events.KeyFoundAfterJwksForceRefresh**.

#### EventLog

With the EventLog logger, structured logging assumes that events are uniquely identifiable by **EventName**. **EventIds** are default enum values because events are distributed across repositories and classes and there's no feasible way to enforce the uniqueness of **EventId** values that are simple integers.

To search for specific events using the EventLog logger, you can query them by event name via XPath, as shown in the following example image and XML code block.

![EventLog Filter By Event Name](media\EventLogFilterByEventName.png)

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

The query above displays all logs from the **Application** log, with the provider **Microsoft Dynamics - Retail Server** and the event name **Microsoft.Dynamics.Retail.RetailServerLibrary.Authentication.JsonWebKeySetResolver+Events.KeyFoundAfterJwksForceRefresh**.

### Filter by original log level

The EventLog logger supports following entry types: 

- **Error**
- **Warning**
- **Information**
- **SuccessAudit**
- **FailureAudit** 

EventLog logger maps log levels from different subsystems to match entry type limitations. For more information, see [EventLogEntryType Enum](/dotnet/api/system.diagnostics.eventlogentrytype?view=netframework-4.6.1&preserve-view=true).

The following table shows current log level mapping between subsystems.

| EventLevel (legacy events) | LogLevel (Microsoft.Extensions.Logging) | EventLogEntryType |
| -------------------------- | --------------------------------------- | ----------------- |
| Undefined                  | None                                    | Not logged        |
| LogAlways                  | Critical                                | Error             |
| Critical                   | Critical                                | Error             |
| Error                      | Error                                   | Error             |
| Warning                    | Warning                                 | Warning           |
| Informational              | Information                             | Information       |
| Verbose                    | Debug                                   | Information       |
|                            | Trace                                   | Information       |

To allow for more precise filtering, information about the original log level from Microsoft.Extensions.Logging is stored as part of the event. This approach allows you to query by original log level via XPath, as shown in the following example query.

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

The query above displays all logs from the **Application** log with the provider **Microsoft Dynamics - Retail Server** and the original log level of **Information**, which allows you to separate **Information** logs from **Debug** and **Trace** logs.
