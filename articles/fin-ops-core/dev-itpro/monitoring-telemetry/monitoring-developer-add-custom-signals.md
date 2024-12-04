---
title: Adding custom telemetry signals
description: Learn how to add custom telemetry signals in Dynamics 365 Finance & Supply Chain Management.  
author: kesaelen
ms.topic: how-to-guide
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 08/11/2024
ms.author: kesaelen
ms.reviewer: kesaelen
ms.custom: bap-template
---
# Adding custom telemetry signals

When the Monitoring and Telemetry feature is activated, telemetry is emitted to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)]. On top of what is already emitted out of the box, you can provide extensions to add your own custom telemetry signals. These signals can provide additional insights into your custom processes.

## Telemetry logger

The main entry point for logging custom telemetry is through the **SysApplicationInsightsTelemetryLogger** class. It encupsulates the [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] telemetry client and provides access to the necessary operations to track an event, pageview, trace, exception or metric. 

The logger uses the [static constructor pattern](https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/dev-ref/xpp-static-classes#static-constructors) ensuring a singleton instance per user session. The encapsulated [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] telemetry client is further cached to ensure only one telemetry client is created per AOS instance.

## Telemetry data contract types

[!INCLUDE[d365foscm](./includes/finops-product-name-long.md)] currently supports the following types of data contracts to be used:

| Type             | X++ class                                     | Application Insights Data Type |
|------------------|-----------------------------------------------|--------------------------------|
| Event            | SysApplicationInsightsEventTelemetry          | [Microsoft.ApplicationInsights.DataContracts.EventTelemetry](https://learn.microsoft.com/dotnet/api/microsoft.applicationinsights.datacontracts.eventtelemetry?view=azure-dotnet) |
| PageView         | SysApplicationInsightsPageViewTelemetry       | [Microsoft.ApplicationInsights.DataContracts.PageViewTelemetry](https://learn.microsoft.com/dotnet/api/microsoft.applicationinsights.datacontracts.pageviewtelemetry?view=azure-dotnet) |
| Exception        | SysApplicationInsightsExceptionTelemetry      |  [Microsoft.ApplicationInsights.DataContracts.ExceptionTelemetry](https://learn.microsoft.com/dotnet/api/microsoft.applicationinsights.datacontracts.exceptiontelemetry?view=azure-dotnet) |
| Trace            | SysApplicationInsightsTraceTelemetry          |  [Microsoft.ApplicationInsights.DataContracts.TraceTelemetry](https://learn.microsoft.com/dotnet/api/microsoft.applicationinsights.datacontracts.tracetelemetry?view=azure-dotnet) |

### Event

To log a custom event to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)], we can create an instance of **SysApplicationInsightsEventTelemetry** and pass in the necessary payload. Next, use the **trackEvent** method on the **SysApplicationInsightsTelemetryLogger** to emit the event.

The following example shows how to emit an event when a record is created in the SysUserLog table. 

```xpp
[PostHandlerFor(tableStr(SysUserLog), tableMethodStr(SysUserLog, insert))]
internal static void logUserLogOn(XppPrePostArgs _args)
{
    if(     SysIntParameters::Find().CaptureUserSessions
        &&  SysApplicationInsightsTelemetryHelper::useSysApplicationInsightsTelemetryLogger())
    {
        SysUserLog  sysUserLog = _args.getThis();
        UserInfo    userInfo;

        select firstonly RecId, ObjectId 
            from    userInfo 
            where   userInfo.id == sysUserLog.UserId;

        SysApplicationInsightsEventTelemetry eventTelemetry = SysApplicationInsightsEventTelemetry::newFromEventIdName('Admin001', 'UserLogOn');
        eventTelemetry.addProperty(SysApplicationInsightsUserIdProperty::newFromValue(sysUserLog.UserId));
        eventTelemetry.addProperty(SysApplicationInsightsUserObjectIdProperty::newFromValue(guid2Str(userInfo.ObjectId)));
        eventTelemetry.addProperty(SysApplicationInsightsUserLogBuildNumberProperty::newFromValue(sysUserLog.BuildNum));
        eventTelemetry.addProperty(SysApplicationInsightsUserLogSessionIdProperty::newFromValue(int2Str(sysUserLog.SessionId)));
        eventTelemetry.addProperty(SysApplicationInsightsUserLogBuildNumberProperty::newFromValue(sysUserLog.BuildNum));
        eventTelemetry.addProperty(SysApplicationInsightsComputerNameProperty::newFromValue(sysUserLog.Computername));

        SysApplicationInsightsTelemetryLogger::instance().trackEvent(eventTelemetry);
    }
}
```

### PageViews

Using PageView entries, [!INCLUDE[d365foscm](./includes/finops-product-name-long.md)] is out of the box already logging every form that is opened in the application.

```xpp
[SubscribesTo(classStr(FormRun), staticDelegateStr(FormRun, onFormRunCompleted))]
public static void FormRun_onFormRunCompleted(FormRun _formInstance)
{
    if(     SysIntParameters::Find().CaptureFormRun
        &&  _formInstance.args()
        &&  _formInstance.args().menuItemName()
        &&  SysApplicationInsightsTelemetryHelper::useSysApplicationInsightsTelemetryLogger())
    {
        SysApplicationInsightsPageViewTelemetry pageTelemetry = SysApplicationInsightsPageViewTelemetry::newFromPageIdName(_formInstance.instanceId(), _formInstance.args().menuItemName(), _formInstance.lifecycleHelper().GetFormLoadingDuration());
        SysApplicationInsightsTelemetryLogger::instance().trackPageView(pageTelemetry);
    }
}
```

### Exceptions

The following example shows how to track exceptions to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] by using the **SysApplicationInsightsExceptionTelemetry** contract and calling the **trackException** method on the **SysApplicationInsightsTelemetryLogger**.

```xpp
SysApplicationInsightsExceptionTelemetry exceptionTelemetry = SysApplicationInsightsExceptionTelemetry::newFromExceptionMessage(Args.getArg('txt'));
exceptionTelemetry.addProperty(SysApplicationInsightsClassNameProperty::newFromValue(classStr(Global)));
exceptionTelemetry.addProperty(SysApplicationInsightsMethodNameProperty::newFromValue(staticmethodStr(Global, Error)));
exceptionTelemetry.addProperty(SysApplicationInsightsCallStackProperty::newFromCurrentCallStack());

SysApplicationInsightsTelemetryLogger::instance().trackException(exceptionTelemetry);
```

> [!NOTE]
> The above example is taken from the SysApplicationInsightsGlobalTelemetry class where all errors that are presented in the infolog are automatically emitted to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)]. 

### Traces

The following example shows how to track exceptions to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] by using the **SysApplicationInsightsTraceTelemetry** contract and calling the **trackTrace** method on the **SysApplicationInsightsTelemetryLogger**

```xpp
SysApplicationInsightsTraceTelemetry traceTelemetry = SysApplicationInsightsTraceTelemetry::newFromMessageAndSeverity('My custom trace message', Microsoft.ApplicationInsights.DataContracts.SeverityLevel::Information);

SysApplicationInsightsTelemetryLogger::instance().trackTrace(traceTelemetry);
```

### Metrics

Interacting with metrics is different than the previous examples. Instead of using a specific data contract, we can interact with the **SysApplicationInsightsTelemetryLogger** directly using **trackMetric**. This is because the logger will first get the existing Metric instance from [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] and update the value. Using **trackMetricWithDimensions**, you can add properties to be used as dimensions to slice values based on those dimensions. 

Metrics use local pre-aggregation for performance reasons. This ensures that updates to a certain metric are only sent to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] after a one minute period. This is benificial in batch processing scenarios where a lot of updates could happen to a specific metric.

For a complete overview of Metrics, see [Azure Monitor Metrics overview](https://learn.microsoft.com/azure/azure-monitor/essentials/data-platform-metrics)