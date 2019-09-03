---
# required metadata

title: Telemetry logger
description: This topics covers the telemetry logger in Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Telemetry Logger

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topics covers the telemetry logger in Dynamics 365 Commerce.

## Overview

The Commerce online software develpoment kit (SDK) comes with a custom telemetry logger which provides the ability to log to multiple resources at various levels while maintaining a unified context on both the server and the client.

## Access the telemetry Logger

The SDK logger is available by default to all react components by accessing it as the **this.prop.telemetry** prop:

```typescript
this.props.telemetry
```

There are instances where you will want to access the logger in a shared component, rather than having to pass down the logger through the props of every component within your module. The SDK provides a `WithContext()` utility within the SDK repository which allows you to inject the logger directly into your component.

By default, the SDK logger will log all events to an "application insights" instance. When running on a development environment, all logs will also be displayed on the console.

## Trace logging

Logging of messages, ranging in importance from debug statements to critical errors, can be accomplished with the trace logging feature of the SDK logger. The trace logger uses the following logging methods and levels.

``` ts
enum LogLevel {
    Trace = 'trace',
    Debug = 'debug',
    Information = 'information',
    Warning = 'warning',
    Error = 'error',
    Critical = 'critical',
    None = 'none'
}
```

### Trace logging APIs

The primary API used to log a trace message is as follows.

``` ts
telemetry.log(
    logLevel: LogLevel,                 // One of the log levels listed in the enum above
    messageTemplate: string,            // A string that follows a message template format (see below for more info)
    logOptions?: TelemetryLogOptions    // Object wrapping up the optional parameters for the log statement
)
```

The trace logging system uses message templates to enforce a structured logging system of telemetry. This means that the logs will be capturable and renderable in both human- and machine-friendly formats. The `messageTemplate` argument to the `.log` call will use what are called 'named holes' for any event data. When writing trace log messages, you can write human-readable messages and include event data. To include event data, mark the place in the message template with `{<name>}`, where `<name>` is what you want to call the data that will go there. The actual value that will fill that named hole will be provided in the `logOptions.values` parameter. The `logOptions` parameter contains any of the optional parameters that should be included for a trace log, as follows.

``` ts
type TelemetryLogOptions = {
    values?: unknown[];       // Holds any arguments that are meant for placeholders in the message template
    customTags?: string[];    // Array of custom tags to add to log. Custom tags can be used to group message in the telemetry back-end
    exception?: Error;        // Exception that can be attached to the log. Will contain details like stack trace info
};
```

The benefits of this structured logging system is that when rendering the log messages for a human to read, the system can replace the named holes with the values provided. But when sending and storing the message, or when processing the telemetry by a machine, the event data can be kept separate. Event data can be used for things like aggregation or filtering specific messages, without requiring any string parsing. More information on structured logging and message templates can be found at https://messagetemplates.org/.

The following examples show some trace log calls.

``` ts
telemetry.log(LogLevel.Debug, "{user} says {word}", {values: ["Bill", "Hi!"]});
// Output: "Bill says Hi!"

telemetry.log(LogLevel.Debug, "Customer {customer} purchased item {productID}", {values: [12345, 321]});
// Output: "Customer 12345 purchased item 321

telemetry.log(LogLevel.Debug, "Module {id} threw error {code} while rendering", {values: [123, 404], customTags: ["Module Error"], exception: error});
// Output: "Module 123 threw error 404 while rendering
// The customTags and exception will be attached to the log call, and can be viewed in the telemetry back-end
```

There are also wrapper methods that simplify the logging calls, but they are only able to log strings. There is one for each log level, as follows.

``` ts
this.props.telemetry.trace("This will log at log level 'trace'");
this.props.telemetry.debug("This will log at log level 'debug'");
this.props.telemetry.information("This will log at log level 'information'");
this.props.telemetry.warning("This will log at log level 'warning'");
this.props.telemetry.error("This will log at log level 'error");
this.props.telemetry.critical("This will log at log level 'critical");
```

If you want to include additional strings or other objects in the wrapper methods, you can add them to the message by passing them as arguments at the end of the call. All additional arguments will be converted to strings, joined with the first string message, and separated by a comma.

```ts
this.props.telemetry.trace("This is the first message", "This is the second message", {some object})

// Output will be: "This is the first message,This is the second message,{.toString result of {some object}}"
```

The console logs are controlled by a query string called **?debug=true**.

## Exception Logging

Logging of `Error` objects (and classes inheriting from them) can be done through the `.exception(Error)` API.

```ts
this.props.telemetry.exception(new Error("Something is broken!"));
```

### .error vs .exception

There may be some confusion as to when you should use `.error()` or `.exception()` to log an error in your application, due to similar naming and the fact that it is possible to log `Error` objects using `.error()` by passing them as additional arguments.

The best guidance is to use `.exception()` to log an actual `Error` object, and to use `.error()` to log a string message stating that an error has occurred in the business logic. The reason for this is that in the AppInsights backend, `.exception()` logs are more easily correlated with issues, and allow for faster debugging when a real issue arises. The messages from `.error()` are treated as another trace log and may require more detailed analysis to find the issue than if you used `.exception()`, and therefore can increase the time it takes to recognize that an issue has occurred. In addition, `.exception()` allows for better tracking across different requests, and so supports things like automatic alerting when an issue begins to affect a large number of requests.
