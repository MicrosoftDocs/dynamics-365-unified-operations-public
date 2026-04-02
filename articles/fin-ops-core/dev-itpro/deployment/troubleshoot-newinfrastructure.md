---
title: Troubleshoot environments deployed through self-service deployment
description: Learn how to troubleshoot and diagnose issues in an environment that was deployed using the self-service deployment experience.
author: laneswenka
ms.author: laswenka
ms.topic: troubleshooting-general
ms.date: 04/02/2026
ms.reviewer: johnmichalak
ms.custom:
  - bap-template
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-12-31
ms.search.form: 
ms.dyn365.ops.version: 8.1.1
ms.custom:
  - sfi-image-nochange
---

# Troubleshoot environments deployed through self-service deployment

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This article explains how to troubleshoot problems in an environment that you deployed by using the [self-service deployment](infrastructure-stack.md) experience. When a user reports a problem, use various tools in Microsoft Dynamics Lifecycle Services to troubleshoot. The rich set of telemetry data helps you build a storyboard view that shows what that user and other users were doing when the problem was reported.

To open the **Environment Monitoring** dashboard, follow these steps:

1. Open Lifecycle Services and go to the appropriate project.
1. In the **Environments** section, select the environment that you want to view, and then select **Full details**.
1. On the **Environment details** page, select **Environment monitoring** to open the Monitoring and diagnostics portal.

On the Environment Monitoring dashboard, you see two tabs: **Overview** and **Activity**.

:::image type="content" source="./media/DiagnoseIssues.jpg" alt-text="Screenshot of the Diagnose Issues environment monitoring dashboard.":::

## Overview tab

The **Overview** tab provides a storyboard view that shows how the environment was used during a specific period. Use the filters on this page to narrow the information logs. Here are some of the available filters:

- **Time duration**: Go back 60 minutes from the selected date and time.
- **User**: View a specific user's activities.
- **Search terms**: Create a search that's based on the issue that you're investigating.

You also see two sections:

- The **User interaction** chart shows a user's activities on various machines in the environment and the SQL utilization trend.
- The **User activity** grid shows the various activities that users performed, based on their session timestamp. The active sessions display on the left side of the grid. For each session, the Form:Control:Command and the corresponding timestamp show when the action was taken. You can trace the exact steps that the user took in the information presented in this grid.
  
 > [!IMPORTANT]
 > The Overview tab will also include the CPU and memory health metrics to help with diagnostics.  This feature isn't currently available but will be added soon.

## Activity tab

The **Activity** tab shows a predefined set of queries for advanced troubleshooting. This set gives you access to the raw information logs. You can export the logs to do more advanced analysis. The following types of queries are available:

- User-related errors
- Slow queries
- Deadlocks
- Crashes

> [!NOTE]
> The data shown on the **Overview** and **Activity** tabs is only retained for 30 days.

> [!IMPORTANT]
> The Environment monitoring experience will also include advanced SQL troubleshooting tools to diagnose and mitigate performance problems. This feature isn't currently available but will be added soon.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
