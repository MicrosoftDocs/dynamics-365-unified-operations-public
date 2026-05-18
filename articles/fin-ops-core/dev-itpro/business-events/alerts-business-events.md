---
title: Alerts as business events
description: Learn about alerts as business events through understanding the two kinds of alerts that can be configured by users.
author: Sunil-Garg
ms.author: sunilg
ms.topic: article
ms.date: 04/08/2026
ms.custom: 
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: Platform update 25
# ms.search.form:  [Operations AOT form name to tie this article to]
ms.dyn365.ops.version: 2019-02-28
---

# Alerts as business events

[!include[banner](../includes/banner.md)]

You can configure two kinds of alerts: change-based alerts and due date alerts. For more information about the alerts functionality, see [Alerts](../../fin-ops/get-started/alerts-overview.md).

You can configure change-based alerts and due date alerts to send a business event as a mechanism to notify or trigger external applications or systems. By using this feature, alerts can participate in advanced user notification scenarios and also in business process integration across systems.

To generate a business event from an alert, in the **Create alert rule** dialog box, set **Alert me with** > **Send externally** to **Yes**. 

To process alerts, set the batch processes for change-based alerts and due-date alerts for batch processing. For more information, see [Batch processing for due-date events](../../fin-ops/get-started/alerts-managing.md#set-up-processing-for-change-based-alerts).

The business event for the change-based alert and the due date alert must also be active for the alert to be sent as a business event. To learn more about the activation process, see [Activating business events](home-page.md#activating-business-events).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
