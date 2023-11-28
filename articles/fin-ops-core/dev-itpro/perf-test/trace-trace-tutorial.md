---
title: Capturing a Trace
description: This tutorial provides guidelines on how to take traces.
author: ttreen
ms.date: 11/28/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 2023-11-23
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 607c1810-f872-4b23-a2c7-ee01522d90e3
---

# Capturing a Trace

[!include [banner](../includes/banner.md)]

This tutorial provides guidelines on how to take traces in Microsoft Dynamics 365 finance and operations.

In this tutorial, you'll take a tour of how to collect and download traces. The trace parser tool works largely similar to the Microsoft Dynamics AX 2012 version, but it is not backward compatible and can't be used to analyze AX 2012 traces. The tool can be found in your development environments. Go to the Windows Start menu > **Microsoft Dynamics Trace Parser**, or in **C:\Program Files (x86)\Microsoft Dynamics Trace Parser\Microsoft.Dynamics.AX.Tracing.TraceParser.exe**.

## Prerequisites

This tutorial requires that you access the environment as an administrator on the instance. The administrator can also grant rights to other users to take a trace. In this way, you can trace scenarios that can't be reproduced with administrative rights.

## Capture a trace - client

1. In the navigation bar, select **Help**, and then **Trace**. 
2. Enter in a **Trace name**, for the trace that you are about to capture.
3. If needed, set **Include SQL parameter value** to **Yes**.
4. Select **Start trace**.
5. Perform actions that need to be analyzed, for example, opening **Accounts payable > Vendors > All vendors**.
6. When you are finished, select **Stop trace**.
7. Once the trace has stopped, you can select one of the following options (for this tutorial, select the second option):
    - **Download trace** – Store the captured trace on a local machine. You can analyze a downloaded trace with the desktop version of **Trace parser**.
      
>[!NOTE]
>If you download a trace it will not be available for later uploading.

   - **Upload trace** – Store the trace in the cloud for later downloading by. For example, the admin, it will be automatically deleted after 7 days and can be deleted manually from the captured traces page.
   - **Return to main menu** – Returns to the main tracing menu to start another trace.

>[!NOTE]
>If your scenario takes more than 1-2 minutes, it is better to try to take multiple smaller traces of 30 seconds each. The trace will likely get too big to be easily analyzed and there's a risk for losing data if the trace gets too big.

### Assign trace rights to user

1. To give a user rights to capture a trace, go to **System administration > Users > Users**.
2. Select the user and assign the **System tracing user** role. 

    [![Example of assigning trace rights to a user.](./media/trace2-284x300.jpg)](./media/trace2.jpg)

Remove the user role after the user is done with tracing to avoid unwanted tracing.

### Open captured trace

1. In the navigation bar, select **Help**, and then **Trace**.
2. Select **Captured traces**.

>[!NOTE]
>The **Captured traces** button is only seen by users with administrative rights.

3. Select the trace name to download to open and analyze it with the desktop version of trace parser or select the user name to get to the user options.
4. After you download the trace, delete the trace.

> [!NOTE]
> The trace will be deleted after 7 days. For more information about the desktop version of the trace parser, see [Diagnose issues and analyze performance by using Trace parser](trace-parser.md).

### Capture a trace - performance monitor (Cloud hosted environments\VHDs\On-Premises LBD)

You can also capture a trace using Windows performance monitor. This option is only available on Cloud hosted environments (CHE), development VHDs and on-premises (LBD) servers.

To capture a trace using Windows performance monitor, follow these steps:

1. Remote desktop to the CHE, development VHD, or on-premises AOS Node (Batch\Interactive) you want to collect event traces from.
2. Start **Windows performance monitor (perfmon.msc)**. Add a new **User defined data collector set**.
3. Give the **Data collector set** a name, e.g. D365Trace, and select **Create manually**. You'll be able to use **Create from a template** after a template is created after going through the manual steps.
4. Click **Next**.
5. Go to **Create data logs**, check **Event trace data**, and click **Next**.
6. In **Which event trace provider would you like to enable?**, click **Add** and select the following from the **Event trace provider** list: 
   - Microsoft-Dynamics-AX-ExecutionTraces
   - Microsoft-Dynamics-AX-FormServer
   - Microsoft-Dynamics-AX-XppExecutionTraces
7. Click **OK**.
8. Click **Next** and specify a directory for storing trace files or keep the default directory.
9. Select **Save and close** and then click **Finish**.
10. The next step is to change settings for the newly created data collector. Select your new user defined trace, and in the righthand pane right click on the **DataCollector01**. Select **Properties**.
   - In the **Properties** window, switch to the **Trace buffers** tab and modify the default buffer settings. The default buffer values don't work well for collecting Dynamics 365 event trace data when there's a high volume of events in a short period of time. It is recommended to use the following values (leave all other settings as default):
       - Buffer size: 512 KB
       - Minimum buffers: 256
       - Maximum buffers: 256
11. Start or stop collecting Dynamics 365 finance event traces by clicking **Start/Stop** on the **Performance monitor** toolbar. 

### Save as template
 - You may want to save the data collector set as a template and reuse it on a different server.
 - To do save the data collector as a template, follow these steps: 
      1. Right click the **Data collector sets** and select **Save Template**.
      2. The template XML file can be copied and imported.

### Limit trace file size
 - Setting a maximum file size helps makes the traces more manageable when importing into the **Trace Parser** tool. You can set the data collector properties to restart after a set number of megabytes.
 - Follow these steps to set the file size to 1000MB (1GB):
      1. **Right click** on the user defined trace and select **Properties**.
      2. In the **Stop condition** tab, check **Restart the data collector set at limits.**
      3. In the **Maximum size** field, enter 1000.
 - After the trace reaches its maximum size, it'll start to write on top of the same file again. If you want the trace to create additional files, follow these steps: 
      1. Select your new user defined trace, and right click on the **DataCollector01**, and select **Properties**.
      2. In the **Properties** window, switch to the **File** tab and check **Circular (requires a non-zero maximum file size)**.

#### Additional notes
Before starting a trace, ensure your scenario is in a warm state. This means that you have run the scenario you want to trace once before you take the trace. Having the environment in a warm state prevents events like metadata loading, uncached queries and other warm-up tasks from being saved.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
