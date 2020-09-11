---
# required metadata

title: Process automation framework development
description: This topic provides an overview of development with the process automation framework.
author: RyanCCarlson2
manager: AnnBe
ms.date: 09/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2020-09-10
ms.dyn365.ops.version: AX 7.0.0
---

# Process automation framework development

Process automation allows simple scheduling of processes that will be run by the batch server. The process automation framework is a set of APIs that lets you implement process automation.

You should use only the public APIs to implement process automation.

- Don't select from, insert into, or directly reference the process automation tables.
- Don't extend the framework or integrate your code with the classes.
- Don't subscribe to table events such as insert, update, and delete. Finance and Operations apps skip most of those events.
- If functionality is missing that you need, then submit feature requests.

We plan to add features in the future and integrating too deeply with this framework could cause your integration to break.

Some of the examples for the framework aren't representative of shipping quality code. As always, it's expected that processes built using the framework will follow all the best practices and quality standards.

For more information about process automation, see [Process automation](../sysadmin/process-automation.md).

## Definitions

| Term | Definition                                                                             |
|------------------|--------------------------------------------------------------------------------- |
| Poller             | The poller is a system-critical batch process that runs every minute, invoking various subsystems of the process automation framework. It consults with the schedule to see what processes are ready to run and then it invokes the runtime side of the framework to ensure that processes are run. |
| Scheduled process  | A process that is scheduled by users in the UI. Occurrences for these processes can be seen on a calendar view. |
| Background process | A background process that runs frequently that doesn’t require user input and performs some background processing. Subledger transfer to general ledger is an example of a polled process. The term **polled** is synonymous with the term **background**.  |
| Type               | In these docs, the term **type** refers to **ProcessScheduleType**, as discussed in [Type registration](type-registration.md). |
| Series             | Every process that has a registered type must have a series. Series for scheduled processes are created in the UI by end users. Series for background processes are created via series registration. For more information, see [Series registration](series-registration.md). |
| Date and time         | All framework dates are stored in UTC and displayed in the user-preferred timezone. |

## Tasks

Implementing a process automation solution consists of a set of tasks, some required and some optional.

Most of the user interface customizations aren't supported for background processes. The series list page and logging results and messages is supported.

| Section                                             | Required For Scheduled Process | Required For Background Process |
|-----------------------------------------------------|---------------|-----------------------|
| [Type registration](type-registration.md)           | Yes           | Yes                   |
| [Series registration](series-registration.md)       | Not supported | Yes                   |
| [Process parameters](process-parameters.md)         | No            | Not supported         |
| [User-configurable queries](user-queries.md)        | No            | Not supported         |
| [Run the process](run-process.md)                   | Yes           | Yes                   |
| [Log results and messages](log-results.md)          | Yes           | Yes                   |
| [Customize the user interface](ui-customization.md) | No            | See Below             |
