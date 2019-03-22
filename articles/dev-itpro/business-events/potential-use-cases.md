---
# required metadata

title: Use cases for business events
description: This topic lists use cases for business events.
author: Sunil-Garg
manager: AnnBe
ms.date: 03/22/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: Platform update 24
ms.dyn365.ops.version: 2019-02-28
---

# Use cases for business events

[!include[banner](../includes/banner.md)]
[!include[preview-banner](../includes/preview-banner.md)]

The following are potential uses cases for business events. This is by no means an exhaustive list of the potential use cases. It should also be noted that some of these use cases may not have been implemented yet. These are meant to provide ideas and help with understanding certain business events.

| **Use case**                                                                                                                                                                                                                                                                                                                                                                                   | **Value**                                                                                                                                                                                                                                                                   |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The procurement process frequently relies on manual intervention, so automating this process should increase procurement manager productivity.                                                                                                                                                                                                                                                  | You can make the procurement process more efficient by alerting procurement managers when quotation requests are sent, allowing for prompt follow up and faster engagement. The goal is to have procurement managers follow up within three days and possibly create a Flow that automates this follow up. |
| Managers are not informed about newly created financial reports. As a result, managers might analyze and make decisions based on outdated data.                                                                                                                                                                                                                                               | You can make the reporting process more efficient by alerting managers when financial reports are sent, allowing for prompt follow up and faster engagement. The goal is to have managers follow up within three days and possibly create a Flow that automates this follow-up.                            |
| When a new customer is created, a credit limit check is needed. If something could automatically trigger an API that subscribes to a credit limit, and then check the website and import specific credit limit check fields, such as limit amount and rating. At the same time, an approval Flow needs to start so that the customer account can be used after approval from management. | This is required by many companies, especially in the retail area. This would be beneficial because partners develop customizations for this purpose.                                                                                                                                   |
| The month-end closing schedule is a simple list that does not allow automatic actions. If functionality could be created to inform a group of people about tasks that have been completed and verified as complete, then a different group of people could start working.                                                                                                                     | Use real-life scenarios to enhance the currently static and difficult to use month-end closing workspace.                                                                                                                                                                                                |
| If functionality could be created to trigger a flow when the status of a period is changed – either opened or closed.                                                                                                                                                                                                                                                                               | Users are not automatically informed when new periods are opened after the month-end close is completed and they are allowed to start recording transactions in the new period.                                                                                                      |
