---
title: Offline reliability toast notifications in the Store Commerce app
description: Learn about the various toast notifications that are available in the Microsoft Dynamics 365 Commerce Store Commerce app.
author: anush6121
ms.author: anvenkat 
ms.topic: conceptual 
ms.date: 01/21/2025
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
---

# Offline reliability toast notifications in the Store Commerce app

This article describes the various toast notifications that are available as of the 10.0.43 release of the Microsoft Dynamics 365 Commerce Store Commerce app to support offline reliability scenarios.

Revisit this article as more notifications are added in future releases.

## Enable the toast notifications feature

To enable toast notifications in the Store Commerce app, you must turn on the following feature management flags:

- Enable proactive notifications for offline functionalities
- Enable proactive notifications for network connectivity insights

## Toast notification for offline sign-in authentication failures

Store employees receive a notification if the offline mode is unavailable because of an offline sign-in authentication failure. The notification includes a link to more detailed error information. That information can be copied and sent to an administrator for corrective action.

:::image type="content" source="../../media/toastnotificationofflinelogon.jpg" alt-text="Screenshot that shows an example of a toast notification about an offline sign-in authentication failure.":::

## Toast notification for seamless switches to offline mode

Store employees receive a notification when the point of sale (POS) switches to offline mode through the seamless switch mechanism. They also receive a notification when POS switches back to online mode.

:::image type="content" source="../../media/seamlessoffline.jpg" alt-text="Screenshot that shows an example of a toast notification about a seamless switch to offline mode.":::

## Toast notification for missing or weak network connections

Store employees receive a notification when network connectivity is missing or weak. The notification prompts employees to switch to offline mode. The notification also includes a direct link to network connectivity insights, so that employees can learn more about the issue. Learn more about network connectivity insights in [Network health checks](../../pos-healthcheck.md#network-health-checks).

:::image type="content" source="../../media/network-connectivity-notification.jpg" alt-text="Screenshot that shows an example of a notification about a missing network connection.":::
