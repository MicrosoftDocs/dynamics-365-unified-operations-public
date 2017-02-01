---
# required metadata

title: Performance timer | Microsoft Docs
description: This topic provides an overview of the Performance timer, which is a tool that helps you to determine why your system's performance might be slow. 
author: RobinARH
manager: AnnBe
ms.date: 2015-12-13 05:01:02
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 27191
ms.assetid: 54b2ea09-8d67-41b4-aaa7-f97e1be6f144
ms.region: Global
# ms.industry: 
ms.author: chwolf

---

# Performance timer

This topic provides an overview of the Performance timer, which is a tool that helps you to determine why your system's performance might be slow. 

To open the Performance timer, open your webpage with the added parameter debug=develop: <https://testax21aos.cloud.test.dynamics.com/en/?cmp=USMF&debug=develop> **Note: **When you run in debug mode you will notice slower performance. You can quickly get an overview of most performance issues by pressing F12 and working with the debugging tools that are available in your browser. The timer will show up here. [![1\_Timer](./media/1_timer.png)](./media/1_timer.png)To open a list page, for example, such as the purchase order list page, click the Performance timer. The following screenshot shows the separation between client time and server time, and the total time. Additionally, you can see a set of performance counters and expensive server calls. [![2\_Timer](./media/2_timer.png)](./media/2_timer.png) For more information about the server performance counters, click on any of the links.

-   **Forms** - Forms will show how many forms are currently open, plus the rate at which they opened and closed (per second), and a set of counters, such as the total amount of created or closed forms.
-   **GC** - This is information about the garbage collection processes on the server.
-   **Web client session** - This shows how many web client sessions you currently have and how many are in use.
-   **Services Session provider** - This is the total number of sessions created.

For more information, click a link. In the next screen, you can see how many SQL queries were triggered by this individual call and which SQL query was the most expensive. [![3\_Timer](./media/3_timer.png)](./media/3_timer.png) This information can help you to understand what to trace and where to start troubleshooting. In addition to this topic, you can watch this video for more information: [PERF The Performance Timer and Other Tools](https://mix.office.com/watch/ij5cqidra5q3)

