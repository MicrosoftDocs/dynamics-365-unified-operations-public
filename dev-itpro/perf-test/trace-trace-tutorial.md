---
# required metadata

title: Take a trace using Trace parser
description: This tutorial provides guidelines on how to take traces.
author: RobinARH
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 25471
ms.assetid: 607c1810-f872-4b23-a2c7-ee01522d90e3
ms.search.region: Global
# ms.search.industry: 
ms.author: chwolf
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Take a trace using Trace parser

This tutorial provides guidelines on how to take traces.

In this tutorial, you'll take a tour of how to collect and download traces. The trace analysis tool works largely similar to the Dynamics AX 2012 version yet it is not backward compatible and you can't use it to analyze Dynamics AX 2012 traces. The trace parser tool can be found in the PerfSDK folder on your development deployments.

## Prerequisites
This tutorial requires that you access the environment as an administrator on the instance. The administrator can also grant rights to other users to take a trace. In this way you can trace scenarios which can't be reproduced with administrative rights.

## Capture the trace
1.  Before you trace make sure your scenario is in a "Warm" state meaning you executed the scenario you want to trace once before you take the trace. That will prevent things like metadata loading and other possible warm up tasks from being in the trace.
2.  In the navigation bar, select **Settings**, and then click **Trace**. 

    [![Trace1](./media/trace1-300x176.jpg)](./media/trace1.jpg)
    
3.  Name the trace that you are about to capture, and then click **Start trace**.
4.  Perform actions that need to be analyzed like for example opening "Accounts payable &gt; Vendors &gt; All vendors".
5.  When you are finished, click **Stop trace**. Then, you can select one of the following options (for this tutorial, select the second option):
    -   **Download trace** – Store the captured trace on a local machine. You can analyze a downloaded trace with the desktop version of Trace Parser. **Note**: If you download a trace it will not be available for later uploading.
    -   **Upload trace **– Store the trace in the cloud for later downloading by for example the admin, it will be automatically deleted after 7 days and can also be deleted manually from the captured traces form.

**Please note:** If your scenario takes more than 1-2 minutes it is better to try to take multiple smaller traces of 30 seconds each as the trace will likely get too big to be easily analyzed and there is a risk for losing data if the trace gets too big.

## Assign trace rights to user
1.  To give a user rights to capture a trace, go to "System administration &gt; Users &gt; Users".
2.  Select the user and assign the "System tracing user" role. 

    [![trace2](./media/trace2-284x300.jpg)](./media/trace2.jpg)
    
    Remove the user role again once the user is done with tracing to avoid unwanted tracing.

## Open captured trace
1.  In the navigation bar, select **Settings**, and then click **Trace**.
2.  Click on Captured traces. **Note:** The captured traces button can only be seen by users with administrative rights.
3.  Click on the trace name to download to open and analyze it with the desktop version of trace parser or
4.  Click on the user name to get to the user options.
5.  Delete the trace if you want. You might do this if you have downloaded it.

**Note: **The trace will be deleted after 7 days. For more information about the desktop version of trace parser, see [Trace parser: Using the desktop version to diagnose problems and analyze performance issues](trace-parser.md).

