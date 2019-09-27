---
# required metadata

title: Alerts as business events
description: This topic describes alerts as business events.
author: Sunil-Garg
manager: AnnBe
ms.date: 09/13/2019
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
ms.search.validFrom: Platform update 25
ms.dyn365.ops.version: 2019-02-28
---

# Alerts as business events

[!include[banner](../includes/banner.md)]

There are two kinds of alerts that can be configured by users. These are change-based alerts and due date alerts. For more information about the alerts functionality, see [Alerts](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/alerts-overview).

The change-based alerts and due date alerts can be configured to send out a business event as a mechanism to notify or trigger external applications or systems. This allows alerts to participate in advanced user notification scenarios and also in business process integration across systems.

To configure an alert, the **Send externally** setting must be enabled. The business event for the change-based alert and/or the due date alert must also be active for the alert to be sent out as a business event. To learn more about the activation process, see [Activating business events](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/business-events/home-page#activating-business-events).
