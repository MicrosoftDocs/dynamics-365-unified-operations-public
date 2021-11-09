---
title: Process automation framework development
description: This topic provides an overview of development that uses the process automation framework.
author: RyanCCarlson2
ms.date: 09/10/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2020-09-10
ms.dyn365.ops.version: AX 7.0.0
---

# Process automation framework development

[!include [banner](../includes/banner.md)]

Process automation enables simple scheduling of processes that will be run by the batch server. The process automation framework is a set of APIs that lets you implement process automation.

You should use only the public APIs to implement process automation, and you should follow these guidelines:

- Don't select from, insert into, or directly reference the process automation tables.
- Don't extend the framework or integrate your code with the classes.
- Don't subscribe to table events such as insert, update, and delete. Finance and Operations apps skip most of those events.
- If functionality that you require is missing, submit feature requests.

Microsoft plans to add features in the future. If you integrate too deeply with the process automation framework, your integration might break when those features are added.

Some of the examples for the process automation framework aren't representative of release-quality code. As always, the expectation is that processes that are built by using the framework will follow all best practices and quality standards.

For more information about process automation, see [Process automation](../sysadmin/process-automation.md).

## Definitions

| Term               | Definition |
|--------------------|------------|
| Poller             | The poller is a system-critical batch process that runs every minute and invokes various subsystems of the process automation framework. It consults the schedule to determine which processes are ready to run, and then it invokes the runtime side of the framework to ensure that processes are run. |
| Scheduled process  | A scheduled process is a process that is scheduled in the user interface (UI) by a user. Occurrences for these processes can be seen in a calendar view. |
| Background process | A background process is also known as a *polled process*. It's a process that runs frequently, without requiring user input, and performs some background processing. Subledger transfer to the general ledger is an example. |
| Type               | In this topic and related topics, the term *type* refers to **ProcessScheduleType**, as discussed in [Type registration](type-registration.md). |
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