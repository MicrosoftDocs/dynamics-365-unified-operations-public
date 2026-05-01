---
title: Diagnose issues and analyze performance by using Trace parser
description: Learn about how you can use the Trace parser to consume traces and analyze performance in your deployment, including overviews on capturing events.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 03/16/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.custom: sfi-image-nochange
---

# Diagnose problems and analyze performance by using Trace parser

[!include [banner](../includes/banner.md)]

This article explains how you can use the Trace parser to consume traces and analyze performance in your deployment. You can use the Trace Parser to find and diagnose various types of errors. You can also use the tool to visualize execution of X++ methods, as well as the execution call tree.

> [!NOTE]
> The Trace parser includes features that are similar to Microsoft Dynamics AX 2012. For more information, see the [Dynamics Ax Performance Team Blog](/archive/blogs/axperf/).

## Find the Trace parser

Trace parser should be preinstalled with your developer deployment or VHD. The install location is **C:\Program Files (x86)\Microsoft Dynamics Trace Parser**. If it's not installed, you can run the installer from **C:\PerfSDK\PerfTools\traceparser.msi**.

## Capture events

You can obtain the data that you analyze in the Trace parser by using one of the following methods:

- Capture events from the local installation.
  - If the **Select Trace** window isn't already open, go to the **File** menu and select **Open trace**. In the **Select Trace** window, select **Capture Events**. After selecting your providers, select **Start**. The Trace Parser tool starts listening to all the providers and capturing the events. Capturing stops when you select **Stop and Import**.
- Open an existing ETL (Windows Event) file that you captured by using tools such as Logman.

    :::image type="content" source="./media/1_desktop.png" alt-text="Screenshot of opened Windows Event file.":::

## Viewing traces

**Timeline view** The Timeline tab is the first tab that you see after you import a trace into the Trace Parser. The following illustration shows this tab.

:::image type="content" source="./media/2_desktop.png" alt-text="Screenshot of information in the Timeline tab.":::

The **Timeline** tab has the following major components:

- The **Select Grouping** drop-down menu allows you to group based on a variety of categories, such as Customer ID, Username, Session Name, and more. Groupings display the maximum and minimum timestamp of events, the total number of events, and the lowest event level within the grouping.
- A list of all events in a threaded or unthreaded view.
- A property grid displayed for the selected event.
- A timeline chart for all the selected events.
- Filtering of events.
- Session analysis notes.

**Call tree view** By selecting the **Call Tree** tab, you can see the call tree for all X++ methods. The following image shows the tab.

:::image type="content" source="./media/3_desktop.png" alt-text="Screenshot of information shown in the Call Tree tab.":::

Similarly, you can display the **X++** tab to view a list of all the X++ methods. They're sorted by fields such as inclusive or exclusive durations, RPC, or database calls. These tabs are similar to the corresponding tabs in Trace Parser and have the same behavior.

## Additional resources

[Develop and customize home page](../dev-tools/developer-home-page.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
