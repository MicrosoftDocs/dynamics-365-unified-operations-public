---
# required metadata

title: Telemetry logger
description: This topic covers the telemetry logger in Dynamics 365 Commerce.
author: samjarawan
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Telemetry logger

[!include [banner](../includes/banner.md)]

This topic covers the telemetry logger in Dynamics 365 Commerce.

The Dynamics 365 Commerce online software development kit (SDK) includes a custom telemetry logger that you can use to log to multiple resources at various levels but also maintain a unified context on both the server and the client.

## Access the telemetry logger

By default, the telemetry logger is available to all react components. It can be accessed with the **this.props.telemetry** property from the module view code file.

Sometimes you will want to access the telemetry logger in a shared component instead of having to pass it down through the properties of every component in your module. The SDK repository includes a **WithContext()** utility that lets you inject the telemetry logger directly into your component.

When the telemetry logger runs in a development environment, all logs are also shown in the console.

## Trace logging

The messages that are logged can range in importance from debug statements to critical errors. This logging is available through the trace logging feature of the telemetry logger. The trace logger uses the following logging methods and levels.

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

The following example shows the primary application programming interface (API) that is used to log a trace message.

``` ts
telemetry.log(
    logLevel: LogLevel,                 // One of the log levels listed in the enum above
    messageTemplate: string,            // A string that follows a message template format (see below for more info)
    logOptions?: TelemetryLogOptions    // Object wrapping up the optional parameters for the log statement
)
```

The trace logging system uses message templates to enforce a structured logging system for telemetry. Therefore, the logs can be captured and rendered in both human-friendly and machine-friendly formats. The **messageTemplate** argument of the **.log** call uses what are known as *named holes* for any event data. When you're writing trace log messages, you can write human-readable messages that include event data. To include event data, mark the place in the message template by using **{\<name\>}**, where **\<name\>** is the name that you want to use for the event data. The actual value that will fill that named hole is provided in the **logOptions.values** parameter. The **logOptions** parameter contains any optional parameters that should be included for a trace log. Here is an example.

``` ts
type TelemetryLogOptions = {
    values?: unknown[];       // Holds any arguments that are meant for placeholders in the message template
    customTags?: string[];    // Array of custom tags to add to log. Custom tags can be used to group message in the telemetry back-end
    exception?: Error;        // Exception that can be attached to the log. Will contain details like stack trace info
};
```

The benefit of this structured logging system is that when log messages are rendered so that a human can read them, the system can replace the named holes with the values that have been provided. However, when the messages are sent and stored, or when the telemetry is processed by a machine, the event data can be kept separate. Event data can be used, for example, to aggregate or filter specific messages without requiring any string parsing. For more information about structured logging and message templates, see [Message Templates](https://messagetemplates.org/).

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

There are also wrapper methods that simplify the logging calls. However, these wrapper methods can log only strings. There is one wrapper method for each log level, as the following example shows.

``` ts
this.props.telemetry.trace("This will log at log level 'trace'");
this.props.telemetry.debug("This will log at log level 'debug'");
this.props.telemetry.information("This will log at log level 'information'");
this.props.telemetry.warning("This will log at log level 'warning'");
this.props.telemetry.error("This will log at log level 'error");
this.props.telemetry.critical("This will log at log level 'critical");
```

If you want to include additional strings or other objects in the wrapper methods, you can add them to the message by passing them as arguments at the end of the call. All additional arguments will be converted to strings, joined to the first string message, and separated by a comma. Here is an example.

```ts
this.props.telemetry.trace("This is the first message", "This is the second message", {some object})

// Output will be: "This is the first message,This is the second message,{.toString result of {some object}}"
```

The console logs are controlled by the **?debug=true** query string.

## Exception logging

Logging of **Error** objects (and classes that inherit from them) can be done through the **.exception(Error)** API. Here is an example.

```ts
this.props.telemetry.exception(new Error("Something is broken!"));
```

### .error vs. .exception

You might be confused about when you should use **.error()** to log an error in your application, and when you should use **.exception()**. This confusion can arise because the names are similar, and because you can use **.error()** to log **Error** objects, by passing the **Error** objects as additional parameters.

The best guidance is to use **.exception()** to log actual **Error** objects and **.error()** to log string messages that state that an error has occurred in the business logic. Generally, **.exception()** logs are more easily correlated with issues and allow for faster debugging when real issues arise. The messages from **.error()** are treated as another trace log, and more detailed analysis might be required to find the issue than if you use **.exception()**. Therefore, it can take more time to recognize that an issue has occurred. In addition, **.exception()** allows for better tracking across different requests. Therefore, it supports features such as automatic alerting when an issue begins to affect many requests.

## Additional resources

[Online channel extensibility overview](overview.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
