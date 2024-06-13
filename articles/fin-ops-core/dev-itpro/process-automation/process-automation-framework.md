---
title: Process automation framework development
description: Learn about development that uses the process automation framework, including a table that defines various terms.
author: RyanCCarlson2
ms.author: rcarlson
ms.topic: article
ms.date: 06/10/2024
ms.custom:
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-09-10
ms.dyn365.ops.version: AX 7.0.0
---

# Process automation framework development

[!include [banner](../includes/banner.md)]

Process automation enables simple scheduling of processes that will be run by the batch framework. The process automation framework allows you to build and implement your own process automations.

As with any customization, you should use the documented approach to extend the process automation framework and follow the general guidelines to avoid [intrusive customizations](../extensibility/intrusive-customizations.md). You should also follow these specific guidelines:

- Don't integrate directly with the process automation framework tables.
- Don't extend the framework or integrate directly with the framework classes.
- Don't subscribe to table events on the framework tables. The process automation framework skips most of those events.
- If functionality that you require is missing, submit an extensibility request.

> [!NOTE]
> If you integrate with the process automation framework in an unsupported way, your integration might break because it did not follow the best practices.

For more information about process automation, see [Process automation](../sysadmin/process-automation.md).

## Definitions

| Term               | Definition |
|--------------------|------------|
| Poller             | The poller is a system-critical batch process that runs every minute and invokes various subsystems of the process automation framework. It consults the schedule to determine which processes are ready to run, and then it invokes the runtime side of the framework to ensure that processes are run. |
| Scheduled process  | A scheduled process is a process that is scheduled in the user interface (UI) by a user. Occurrences for these processes can be seen in a calendar view. |
| Background process | A background process is also known as a *polled process*. It's a process that runs frequently, without requiring user input, and performs some background processing. Subledger transfer to the general ledger is an example. |
| Type               | In this article and related topics, the term *type* refers to **ProcessScheduleType**, as discussed in [Type registration](type-registration.md). |
| Series             | Every process that has a registered type must have a series. Series for scheduled processes are created in the UI by users. Series for background processes are created through series registration. For more information, see [Series registration](series-registration.md). |
| Date and time      | All framework dates are stored in Coordinated Universal Time (UTC) but shown in the user's preferred time zone. |

## Tasks

Implementation of a process automation solution consists of a set of tasks, some of which are required and some of which are optional.

Most of the UI customizations aren't supported for background processes. The **Series** list page and logging of results and messages are supported.

| Task                                                | Required for a scheduled process | Required for a background process |
|-----------------------------------------------------|----------------------------------|-----------------------------------|
| [Type registration](type-registration.md)           | Yes | Yes |
| [Series registration](series-registration.md)       | Not supported | Yes |
| [Process parameters](process-parameters.md)         | No | Not supported |
| [User-configurable queries](user-queries.md)        | No | Not supported |
| [Run processes](run-process.md)                     | Yes | Yes |
| [Log results and messages](log-results.md)          | Yes | Yes |
| [Customize the user interface](ui-customization.md) | No | See [Customize the user interface](ui-customization.md). |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
