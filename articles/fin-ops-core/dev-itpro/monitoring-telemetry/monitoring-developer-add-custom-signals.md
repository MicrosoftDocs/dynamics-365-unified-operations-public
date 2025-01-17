---
title: Add custom telemetry signals
description: Learn how to add custom telemetry signals in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: kennysaelen
ms.topic: how-to
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 01/20/2025
ms.author: kesaelen
ms.reviewer: johnmichalak
ms.custom: bap-template
---
# Add custom telemetry signals

[!include [banner](../includes/banner.md)]

When the Monitoring and telemetry feature is activated, telemetry is emitted to [!INCLUDE[appinsights](includes/azure-application-insights-name.md)]. Some telemetry is emitted out of the box. However, you can also provide extensions to add your own custom telemetry signals. These signals can provide more insights into your custom processes.

## Telemetry logger

The main entry point for logging custom telemetry is through the `SysApplicationInsightsTelemetryLogger` class. This class encapsulates the [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] telemetry client and provides access to the operations that are required to track an event, page view, trace, exception, or metric.

The logger uses the [static constructor pattern](/dynamics365/fin-ops-core/dev-itpro/dev-ref/xpp-static-classes#static-constructors) to ensure a singleton instance per user session. The encapsulated [!INCLUDE[appinsights](includes/azure-application-insights-name.md)] telemetry client is further cached to ensure that only one telemetry client is created per Application Object Server (AOS) instance.

## Telemetry data contract types

[!INCLUDE[d365foscm](./includes/finops-product-name-long.md)] currently support the following types of data contracts.

| Type      | X++ class                                | Application Insights data type |
| --------- | ---------------------------------------- | ------------------------------ |
| Event     | SysApplicationInsightsEventTelemetry     | [Microsoft.ApplicationInsights.DataContracts.EventTelemetry](/dotnet/api/microsoft.applicationinsights.datacontracts.eventtelemetry?view=azure-dotnet) |
| PageView  | SysApplicationInsightsPageViewTelemetry  | [Microsoft.ApplicationInsights.DataContracts.PageViewTelemetry](/dotnet/api/microsoft.applicationinsights.datacontracts.pageviewtelemetry?view=azure-dotnet) |
| Exception | SysApplicationInsightsExceptionTelemetry | [Microsoft.ApplicationInsights.DataContracts.ExceptionTelemetry](/dotnet/api/microsoft.applicationinsights.datacontracts.exceptiontelemetry?view=azure-dotnet) |
| Trace     | SysApplicationInsightsTraceTelemetry     | [Microsoft.ApplicationInsights.DataContracts.TraceTelemetry](/dotnet/api/microsoft.applicationinsights.datacontracts.tracetelemetry?view=azure-dotnet) |

### Events

To log a custom event to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)], you can create an instance of the `SysApplicationInsightsEventTelemetry` class and pass in the necessary payload. Then use the `trackEvent` method on the `SysApplicationInsightsTelemetryLogger` class to emit the event.

The following example shows how to emit an event when a record is created in the `SysUserLog` table.

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

### Page views

Out of the box, [!INCLUDE[d365foscm](./includes/finops-product-name-short.md)] already use `pageView` entries to log every form that is opened in the application.

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

The following example shows how to track exceptions to [!INCLUDE[appinsights](includes/azure-application-insights-name.md)] by using the `SysApplicationInsightsExceptionTelemetry` contract and calling the `trackException` method on the `SysApplicationInsightsTelemetryLogger` class.

```xpp
SysApplicationInsightsExceptionTelemetry exceptionTelemetry = SysApplicationInsightsExceptionTelemetry::newFromExceptionMessage(Args.getArg('txt'));
exceptionTelemetry.addProperty(SysApplicationInsightsClassNameProperty::newFromValue(classStr(Global)));
exceptionTelemetry.addProperty(SysApplicationInsightsMethodNameProperty::newFromValue(staticmethodStr(Global, Error)));
exceptionTelemetry.addProperty(SysApplicationInsightsCallStackProperty::newFromCurrentCallStack());

SysApplicationInsightsTelemetryLogger::instance().trackException(exceptionTelemetry);
```

> [!NOTE]
> The previous example is taken from the `SysApplicationInsightsGlobalTelemetry` class, where all errors that are presented in the Infolog are automatically emitted to [!INCLUDE[appinsights](includes/azure-application-insights-name.md)].

### Traces

The following example shows how to track exceptions to [!INCLUDE[appinsights](includes/azure-application-insights-name.md)] by using the `SysApplicationInsightsTraceTelemetry` contract and calling the `trackTrace` method on the `SysApplicationInsightsTelemetryLogger` class.

```xpp
SysApplicationInsightsTraceTelemetry traceTelemetry = SysApplicationInsightsTraceTelemetry::newFromMessageAndSeverity('My custom trace message', Microsoft.ApplicationInsights.DataContracts.SeverityLevel::Information);

SysApplicationInsightsTelemetryLogger::instance().trackTrace(traceTelemetry);
```

### Metrics

Interaction with metrics differs from the previous examples. For metrics, you don't have to use a specific data contract. Instead, you can interact directly with the `SysApplicationInsightsTelemetryLogger` class by using the `trackMetric` method. The logger first gets the existing metric instance from [!INCLUDE[appinsights](includes/azure-application-insights-name.md)] and updates the value. By using `trackMetricWithDimensions`, you can add properties that should be used as dimensions. Values can then be sliced based on those dimensions.

For performance reasons, metrics use local preaggregation. This approach ensures that updates to a specific metric are sent to [!INCLUDE[appinsights](includes/azure-application-insights-name.md)] only after a one-minute period. The use of local preaggregation is beneficial in batch processing scenarios, where many updates to a specific metric can occur.

You can get a complete overview of metrics in [Azure Monitor Metrics overview](/azure/azure-monitor/essentials/data-platform-metrics).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
