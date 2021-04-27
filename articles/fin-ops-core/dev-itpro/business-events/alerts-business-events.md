---
# required metadata

title: Alerts as business events
description: This topic describes alerts as business events.
author: Sunil-Garg
ms.date: 11/12/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: Platform update 25
ms.dyn365.ops.version: 2019-02-28
---

# Alerts as business events

[!include[banner](../includes/banner.md)]

There are two kinds of alerts that can be configured by users. These are change-based alerts and due date alerts. For more information about the alerts functionality, see [Alerts](../../fin-ops/get-started/alerts-overview.md).

The change-based alerts and due date alerts can be configured to send out a business event as a mechanism to notify or trigger external applications or systems. This allows alerts to participate in advanced user notification scenarios and also in business process integration across systems.

To generate a business event from an alert, in the **Create alert rule** dialog box, set **Alert me with** > **Send externally** to **Yes**. 

In order for alerts to be processed, the batch processes for change-based and/or due-date alerts should be set for batch processing for due-date events. For more information, see [Batch processing for due-date events](../../fin-ops/get-started/alerts-managing.md#set-up-processing-for-change-based-alerts).

The business event for the change-based alert and/or the due date alert must also be active for the alert to be sent out as a business event. To learn more about the activation process, see [Activating business events](home-page.md#activating-business-events).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
