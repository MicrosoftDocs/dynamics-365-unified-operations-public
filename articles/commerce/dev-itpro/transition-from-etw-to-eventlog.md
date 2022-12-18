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

The EventLog logger will log structured event data (XML) and include additional information (e.g. original log level). Such events can be filtered and queried, e.g. using XPath in Event Viewer (filter -> XML -> Edit query manually). During the transition period from 10.0.21 to 10.0.32, both the ETW and EventLog loggers were enabled. The ETW logger will be removed starting in 10.0.32.

Further in these transition guidelines we will be using `Retail Server` logs as an example.

## Log location
### ETW
Previously, with ETW logger, in `Event Viewer` events were placed in `Applications and Services Logs` under `Microsoft/Dynamics` in provider-specific folder. E.g.:

![ETW Logs Location](\TransitionFromEtwToEventLogAssets\ETWLogsLocation.png "ETW Logs Location")

### Event Log
Now, with EventLog logger, in `Event Viewer` events are placed in `Windows Logs` in `Application` log. E.g.:

![EventLog Logs Location](\TransitionFromEtwToEventLogAssets\EventLogLogsLocation.png "EventLog Logs Location")

Inside `Application`, logs from providers can be differentiated by `Source` property, e.g.:

![EventLog Logs Source](\TransitionFromEtwToEventLogAssets\EventLogLogsSource.png "EventLog Logs Source")

## Log structure
### ETW
#### Legacy events
Previously, with ETW logger, in `Event Viewer` legacy events were logged and presented according to manifest, e.g.

![ETW Logs Structure](\TransitionFromEtwToEventLogAssets\ETWLogsStructure.png "ETW Logs Structure")

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

![ETW New Logs Structure](\TransitionFromEtwToEventLogAssets\ETWNewLogsStructure.png "ETW New Logs Structure")

### Event log
#### Legacy events
With EventLog logger, in `Event Viewer` legacy events are logged in legacy format (e.g. only formatted message is logged) for backward compatibility. E.g.:

![EventLog Legacy Logs Structure](\TransitionFromEtwToEventLogAssets\EventLogLegacyLogsStructure.png "EventLog Legacy Logs Structure")

#### New events
With EventLog logger, in `Event Viewer` new events are logged in structured format (e.g. both formatted message and all properties from state and scope are logged as separate event data entires), to provide more information and allow precise filtering and querying. E.g.:

![EventLog New Logs Structure](\TransitionFromEtwToEventLogAssets\EventLogNewLogsStructure.png "EventLog New Logs Structure")

## Querying and filtering structured events from ETW and EventLog loggers
### Basics

For basic filtering, it is possible to use Event Viewer UI. Here we can filter by specific provider, log level, etc. E.g., filter for structured information logs from Retail Server:

#### ETW

![ETW Basic Filters](\TransitionFromEtwToEventLogAssets\ETWBasicFilters.png "ETW Basic Filters")

#### EventLog

![EventLog Basic Filters](\TransitionFromEtwToEventLogAssets\EventLogBasicFilters.png "EventLog Basic Filters")

### Advanced filters
Event Viewer allows a subset of XPath queries to be used for filtering. Such filters can be save as Custom Views (e.g. filter by event name, filter by original log level, etc.), which will allow easily perform such tasks in future (e.g. just substitute event name in filters, instead of writing new XPath query, etc.).

#### Filter by event name
Design for new way of logging (i.e. structured logging via LogInformation, etc.) assumed that events will be uniquely identifiable only by EventName, so EventIds are just default enum values (since events are now distributed across repositories and classes there is no feasible way to enforce uniqueness of EventId, since it is just simple integer). So,to search for specific events, we can query them by event name via XPath:

##### ETW

![ETW Filter By Event Name](\TransitionFromEtwToEventLogAssets\ETWFilterByEventName.png "ETW Filter By Event Name")

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

![EventLog Filter By Event Name](\TransitionFromEtwToEventLogAssets\EventLogFilterByEventName.png "EventLog Filter By Event Name")

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
EventLog supports following entry types: `Error`, `Warning`, `Information`, `SuccessAudit`, `FailureAudit` ([see link for more details](https://learn.microsoft.com/en-us/dotnet/api/system.diagnostics.eventlogentrytype?view=netframework-4.6.1&preserve-view=true)). So, logger maps log levels from different subsystems to match such limitations. Current mapping:
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
