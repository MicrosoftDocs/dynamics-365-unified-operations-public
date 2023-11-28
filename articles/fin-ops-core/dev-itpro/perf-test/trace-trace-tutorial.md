---
title: Capturing a Trace
description: This tutorial provides guidelines on how to take traces.
author: ttreen
ms.date: 11/28/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: chwolf
ms.search.validFrom: 2023-11-23
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 607c1810-f872-4b23-a2c7-ee01522d90e3
---

# Capturing a Trace

[!include [banner](../includes/banner.md)]

This tutorial provides guidelines on how to take traces in Microsoft Dynamics 365 Finance and Operations.

In this tutorial, you'll take a tour of how to collect and download traces. The trace parser tool works largely similar to the Microsoft Dynamics AX 2012 version, but it is not backward compatible and can't be used to analyze AX 2012 traces. The tool can be found in your development environments, in the Windows Start menu under **Microsoft Dynamics Trace Parser**, or in **C:\Program Files (x86)\Microsoft Dynamics Trace Parser\Microsoft.Dynamics.AX.Tracing.TraceParser.exe**.

## Prerequisites

This tutorial requires that you access the environment as an administrator on the instance. The administrator can also grant rights to other users to take a trace. In this way, you can trace scenarios that can't be reproduced with administrative rights.

## Capture a Trace - Client

1. In the navigation bar, select **Help**, and then select **Trace**. 
2. Enter in a **Trace name**, for the trace that you are about to capture,
3. If needed set **Include SQL parameter value** to **Yes**
4. Select **Start trace**.
5. Perform actions that need to be analyzed, for example, opening **Accounts payable &gt; Vendors &gt; All vendors**.
6. When you are finished, select **Stop trace**.
7. Once the trace has stopped, you can select one of the following options (for this tutorial, select the second option):
    - **Download trace** – Store the captured trace on a local machine. You can analyze a downloaded trace with the desktop version of **Trace Parser**.
      
       > [!NOTE]
       > If you download a trace it will not be available for later uploading.
    - **Upload trace** – Store the trace in the cloud for later downloading by, for example, the admin, it will be automatically deleted after 7 days and can also be deleted manually from the captured traces form.
    - **Return to main menu** – Returns you to the main tracing menu to allow you to start another trace.

> [!NOTE]
> If your scenario takes more than 1-2 minutes it is better to try to take multiple smaller traces of 30 seconds each as the trace will likely get too big to be easily analyzed and there is a risk for losing data if the trace gets too big.

### Assign trace rights to user

1. To give a user rights to capture a trace, go to **System administration &gt; Users &gt; Users**.
2. Select the user and assign the **System tracing user** role. 

    [![Example of assigning trace rights to a user.](./media/trace2-284x300.jpg)](./media/trace2.jpg)

    Remove the user role again once the user is done with tracing to avoid unwanted tracing.

### Open captured trace

1. In the navigation bar, select **Help**, and then select **Trace**.
2. Select **Captured traces**.

    > [!NOTE]
    > The captured traces button can only be seen by users with administrative rights.

3. Select the trace name to download to open and analyze it with the desktop version of trace parser or
4. Select the user name to get to the user options.
5. Delete the trace if you want, for example once you have downloaded it.

> [!NOTE]
> The trace will be deleted after 7 days. For more information about the desktop version of trace parser, see [Diagnose issues and analyze performance by using Trace parser](trace-parser.md).

## Capture a Trace - Performance Monitor (Cloud Hosted Environments \ VHDs \ On-Premises LBD)

As well as capturing traces via the client, you can also capture a trace using Windows Performance Monitor. This option is only available on Cloud Hosted Environments (CHE), Development VHDs and On-Premises (LBD) servers.

### Steps

1. Remote desktop to the CHE, Development VHD, or On-Premises AOS Node (Batch\Interactive) you want to collect event traces from.
2. Start **Windows Performance Moniton (perfmon.msc)** and add a new **User Defined Data Collector Set**.
3. Give the **Data Collector Set** a name, e.g. D365Trace, and select **Create manually** (you will be able to use “Create from a template” once you have a template created after going through the manual steps); click **Next**.
4. Under **Create Data Logs** check **Event Trace Data**, and then click **Next**.
5. In the step **“Which Event Trace Provider would you like to enable?”**, click the **Add** button and select the following from the Event Trace Provider list, then click **OK**.
   - Microsoft-Dynamics-AX-ExecutionTraces
   - Microsoft-Dynamics-AX-FormServer
   - Microsoft-Dynamics-AX-XppExecutionTraces
6. Click **Next** and specify a directory for storing trace files or keep the default directory.
7. In the next step, select **Save and close** and then click **Finish**.
8. The next step is to change settings for the newly created data collector. Select your new user defined trace, and then in the righthand pane **right click** on the **DataCollector01**, and then select **Properties**.
   - In the Properties window, switch to the **Trace Buffers** tab and modify the default buffer settings. The default buffer values do not work well for collecting D365 event trace data when there is a high volume of events in a short period of time. Therefore, please use the following recommended values (leave all other setting as default):
       - Buffer Size: 512 KB
       - Minimum Buffers: 256
       - Maximum Buffers: 256
9. Now you can start or stop collecting D365 event traces by clicking the **Start/Stop** buttons on the **Performance Monitor Toolbar**. 

#### Additional Settings
##### Save as Template
 - You may want to save the data collector set as a template and reuse it on a different server. To do this follow these steps: 
      1. Right click the Data Collector Sets and select **Save Template** menu item.
      2. The template XML file can be copied and imported.
##### Limit Trace File Size
 - Setting a maximum file size helps makes the traces more manageable when importing into the **Trace Parser** tool. You can set the data collector properties to restart after a set number of megabytes. The following steps set the file size to 1000MB (1GB):
      1. **Right click** on the user defined trace and select **Properties**.
      2. In the **Stop Condition** tab, set the following:
         - Check **Restart the data collector set at limits.**
         - Check **Maximum Size**.
         - Enter 1000 in the **Maximum Size** field.
 - Once the trace reaches its maximum size, it'll start to write on top of the same file again. If you want the trace to write to additional files, then follow these extra steps. 
      1. Select your new user defined trace, and then in the righthand pane **right click** on the **DataCollector01**, and then select **Properties**.
      2. In the Properties window, switch to the **File** tab and modify the following setting:
         - Check **Circular (requires a non-zero maximum file size)**

# Additional Notes
Before starting a trace, ensure your scenario is in a warm state. This means that you have run the scenario you want to trace once before you take the trace. Have the environment in a warm state prevents events like metadata loading, un-cached queries and other **warm-up** tasks from being saved.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
