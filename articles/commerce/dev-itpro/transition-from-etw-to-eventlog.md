---
# required metadata

title: POS Transition from ETW to EventLog logger
description: This article describes how to view POS telemetry from the new EventLog logger.
author: stuharg
ms.date: 12/18/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.search.region: global
ms.author: stuharg
ms.search.validFrom: 2023-01-30

---

# POS Transition from ETW to EventLog logger

## Introduction 

Dynamics 365 Commerce is switching to a new logging approach based on the Microsoft.Extensions.Logging framework and structured logging patterns, which will simplify log generation and maintenance. Previously an ETW logger was used, but the new decentralized nature of event definitions requires that we switch to using an EventLog logger.

The EventLog logger will log structured XML event data and include additional information (such as original log level). Such events can be filtered and queried, for example by using XPath in Event Viewer (**filter \> XML \> Edit query manually**). During the transition period from Commerce version 10.0.21 to version 10.0.32, both the ETW and EventLog loggers were enabled. The ETW logger will be removed starting in 10.0.32.

Further in these transition guidelines we'll be using `Retail Server` logs as an example.

## Log location

### ETW

Previously, with ETW logger, in `Event Viewer` events were placed in `Applications and Services Logs` under `Microsoft/Dynamics` in provider-specific folder, as shown in the following example image.

![ETW Logs Location](media\ETWLogsLocation.png)

### Event Log

Now, with EventLog logger, in `Event Viewer` events are placed in `Windows Logs` in `Application` log, as shown in the following example image.

![EventLog Logs Location](media\EventLogLogsLocation.png)

Inside `Application`, logs from providers can be differentiated by `Source` property, as shown in the following example image.

![EventLog Logs Source](media\EventLogLogsSource.png)

## Log structure

### ETW

#### Legacy events

With ETW logger, Event Viewer legacy events were logged and presented according to manifest, as shown in the following example image.

![ETW Logs Structure](media\ETWLogsStructure.png)

### New events

The ETW logger has limited support for structured logging. 
All events will be logged as `GenericStructuredLogging*` events according to the table:
| Structured logging method name | Translated method name              | Event ID |
| ------------------------------ | ----------------------------------- | -------- |
| LogCritical                    | GenericStructuredLoggingCritical    | 65000    |
| LogError                       | GenericStructuredLoggingError       | 65001    |
| LogWarning                     | GenericStructuredLoggingWarning     | 65002    |
| LogInformation                 | GenericStructuredLoggingInformation | 65003    |
| LogDebug                       | GenericStructuredLoggingDebug       | 65004    |

Due to manifest limitations, only generic and most commonly used properties are logged as separate event data entries. The rest of the properties are logged as aggregated JSON objects.

![ETW New Logs Structure](media\ETWNewLogsStructure.png)

### Event log

#### Legacy events

With EventLog logger, Event Viewer legacy events are logged in legacy format (for example, only a formatted message is logged) for backward compatibility, as shown in the following example image.

![EventLog Legacy Logs Structure](media\EventLogLegacyLogsStructure.png)

#### New events

With EventLog logger, Event Viewer new events are logged in structured format (for example, both the formatted message and all properties from state and scope are logged as separate event data entries) to provide more information and allow precise filtering and querying, as shown in the following example image.

![EventLog New Logs Structure](media\EventLogNewLogsStructure.png)

## Querying and filtering structured events from ETW and EventLog loggers

### Basics

For basic filtering, it's possible to use the Event Viewer UI where you can filter by criteria such as specific provider and log level. Filter for structured information logs from Retail Server:

#### ETW

![ETW Basic Filters](media\ETWBasicFilters.png)

#### EventLog

![EventLog Basic Filters](media\EventLogBasicFilters.png)

### Advanced filters

Event Viewer allows a subset of XPath queries to be used for filtering. You can save such filters as custom views (for example, filtering by event name or filtering by original log level) that allow you to easily perform such tasks in future (for example, substituting event names in filters instead of writing a new XPath query).

#### Filter by event name

Design for new way of logging (i.e. structured logging via LogInformation, etc.) assumed that events will be uniquely identifiable only by EventName, so EventIds are just default enum values (since events are now distributed across repositories and classes there's no feasible way to enforce uniqueness of EventId, since it is just simple integer). To search for specific events, we can query them by event name via XPath:

##### ETW

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

This query will display all logs from `Microsoft-Dynamics-Commerce-RetailServer/Operational` log, with `eventName` equal to `Microsoft.Dynamics.Retail.RetailServerLibrary.Authentication.JsonWebKeySetResolver+Events.KeyFoundAfterJwksForceRefresh`.

#### Event Log

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

This query will display all logs from `Application` log, with provider `Microsoft Dynamics - Retail Server` and with event name `Microsoft.Dynamics.Retail.RetailServerLibrary.Authentication.JsonWebKeySetResolver+Events.KeyFoundAfterJwksForceRefresh`.

#### Filter by original log level

EventLog supports following entry types: `Error`, `Warning`, `Information`, `SuccessAudit`, `FailureAudit` ([see link for more details](/dotnet/api/system.diagnostics.eventlogentrytype?view=netframework-4.6.1&preserve-view=true)). So, logger maps log levels from different subsystems to match such limitations. Current mapping:
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

To allow more precise filtering, information about original log level (from Microsoft.Extensions.Logging) is stored as part of the event. So, we can query them by original log level via XPath:

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

This query will display all logs from `Application` log, with provider `Microsoft Dynamics - Retail Server` and with original log level being `Information` (i.e. it will allow us separate `Information` logs from `Debug` and `Trace`).
