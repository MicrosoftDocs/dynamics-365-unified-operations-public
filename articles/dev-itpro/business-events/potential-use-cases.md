---
# required metadata

title: Application business events
description: This topic lists application business events.
author: Sunil-Garg
manager: AnnBe
ms.date: 01/23/2019
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

# Application business events

[!include[banner](../includes/banner.md)]
[!include[preview-banner](../includes/preview-banner.md)]

Following are potential uses cases where business events can be used to realize the scenario. This is by no means an exhaustive list of the potential use cases for business events. It should also be noted that, some of these use cases may not have been implemented yet. These are meant to provide ideas and help with the thought process.

| **Use case**                                                                                                                                                                                                                                                                                                                                                                                   | **Value addition**                                                                                                                                                                                                                                                                   |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Procurement process is frequently relying on manual intervention. Automating this process should increase procurement manager productivity.                                                                                                                                                                                                                                                    | Should make procurement process more efficient by alerting procurement managers when quotation requests are sent, allowing for prompt follow-up and faster engagement. Aim to have procurement managers follow-up within three days and may create a Flow automating this follow-up. |
| Managers are not informed about newly created financial reports. As a result, managers are making analysis and decisions based on outdated data.                                                                                                                                                                                                                                               | Should make reporting process more efficient by alerting managers when financial reports are sent, allowing for prompt follow-up and faster engagement. Aim to have managers follow-up within three days and may create a Flow automating this follow-up.                            |
| When a new customer is created a credit limit check is needed. We need something that automatically triggers an API that subscribes to a credit limit checking website and that imports specific credit limit check fields such as limit amount, rating, etc. At the same time, an approval Flow needs to be started and allows using the customer account after approval from the management. | Required by many companies especially in the retail area. Big benefit to be expected because all partners develop customizations for this purpose.                                                                                                                                   |
| The month end closing schedule is a simple list that does not allow automatic actions. We need a functionality / trigger / signal that informs a group of people about tasks that have been completed and checked as complete so that a different group can start working.                                                                                                                     | Put ‘life’ to the currently static and difficult to use month end closing workspace.                                                                                                                                                                                                 |
| We need a functionality that triggers a flow when the status of a period is changed – either opened or closed.                                                                                                                                                                                                                                                                                 | Users are not automatically informed when new periods are opened after the month end close is completed and they are allowed to start recording transactions in the new period.                                                                                                      |
