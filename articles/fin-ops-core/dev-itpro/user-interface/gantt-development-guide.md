---
title: Gantt control development guide
description: This article describes how to create new forms by using the Gantt control.
author: josaw1
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: e5cd372c-6ac2-4995-bb3c-ff863b40fedb
---

# Gantt control development guide

[!include [banner](../includes/banner.md)]

This article describes how to create new forms by using the Gantt control. We highly recommend that you look at the code in the Tutorial_Gantt form. This code demonstrates the full capabilities of the Gantt control, and shows how to load data and work with the application programming interface (API).

## What’s new for Gantt

In Microsoft Dynamics AX 2012, the client was a Win32 application, and extensions used Microsoft ActiveX, WinForm, or Microsoft Windows Presentation Foundation (WPF) controls. ActiveX and ManagedHost controls can no longer be used to add custom controls, because they are incompatible with the HTML-based platform. Instead, a new extensible control framework lets you add controls by using HTML and JavaScript. The new Gantt control is implemented by using this framework. Note that, unlike in earlier versions, you don't have to pay an additional license fee to use the control in your own forms or to extend the control.

## High-level overview of the control
The following illustration shows the visual elements of the Gantt control.

[![Elements of the Gantt.](./media/ganttchartelements.png)](./media/ganttchartelements.png)

To add the control to a new form, just right-click the top node in the form design, and then select **Add new** &gt; **Gantt**. After you set the **Height** and **Width** properties to **SizeToAvailable**, there are no other properties that must be set in the designer. Unlike many other controls, Gantt controls can't be bound to data sources. Instead, you must add all data to the control from code.

## Adding activities, links, and milestone markers
The most basic element of a Gantt chart is the task activity. Each activity is allocated its own row in the chart. Activities can form a hierarchy, like a tree, by referencing a parent activity. Additionally, any two activities can be connected to each other through links (across hierarchies). To add data to the control, you build up a list that contains the instances of the element that you want to add. You then assign the list to the control by using a **parm** method. Note that, when you modify data, you can't just modify the content of the list. To notify the client that data has changed, and to trigger a refresh, you must reassign the list to the control by using the **parm** method.

[![API for activities and links.](./media/ganttchartactivitiesapi.png)](./media/ganttchartactivitiesapi.png)

Each activity must have a unique ID across all activity types. This ID is required in order to build the hierarchy and the links. The ID is also used to identify the activity when the server is notified after a user interaction. There are two types of milestones: the milestone activity is a stand-alone activity that receives its own row in the chart and can be referenced from the links, whereas the milestone markers appear on the same row as the related activity. Both types of markers are represented by using symbols from the Dynamics Symbol font.

## Column headers and content
In the “grid” on the left side of the control, you can arrange the data into columns. The column definitions are provided through the **GanttControl.parmColumns** property, which is a list of **GanttControlColumn** objects. The content of the columns is given as a simple **List** object that contains the text strings for an activity through the **GanttControlActivity.parmColumnTexts** property. Note that the values in the column list must be strings. Therefore, any formatting of numbers, enumerations, dates, and so on, must occur on the server side. The formatting of **utcdatetime** must take into account the user's preferred time zone, because that time zone will be used when the Gantt chart is rendered.

[![API for configuring the control.](./media/ganttchartconfigurationapi.png)](./media/ganttchartconfigurationapi.png)

## Working times
An activity can reference a calendar. A calendar is basically a list of working time intervals. A calendar is used to visually separate working time from non-working time by giving the “cells” (intersections of a row and a time scale interval) a different background color. Note that these working time intervals don't have to come from the standard calendar tables. The intervals are just data that you can load from anywhere. Although calendars are a nice feature that can give you a good overview, there are some performance issues that you must consider. When you turn calendars on (by setting **GanttControlConfiguration.parmUseCalendars** to **true**), each “cell” is rendered in HTML by using a DIV element. If a calendar shows lots of activities for a long period at a very granular minor timescale, there will be many DIV elements. Depending on the browser and hardware, the large number of DIV elements can cause performance issues for the user. In this case, you might have to turn calendars off. In this way, you significantly reduce the number of DIV elements that must be rendered. The control can't turn off calendars by itself to improve performance. Based on the specific scenario, you must determine what will be best for the user.

## Color use
Elements such as the activities and milestone markers have a color property. Typically, either the int value for a specific color is calculated by using the **WinAPI::RGB2int** method, or the user sets the value by using the color picker (which is opened by calling **ColorSelection::selectColor**). Instead of controlling the colors yourself, you can specify that the colors should adhere to the current theme. When you set the **GanttControlConfiguration.parmUseThemeColors** option to **true**, if any color values have been set that aren't part of the current theme, they are overridden (no colors have to be specified manually). When theme colors are used, the **parmIsActive** flag on an activity is used to determine whether the activity should appear in a dark color or a light color.

## Interactions
Whenever the user interacts with the Gantt, an event is raised to notify the server-side code. The following events are currently available:

-   onActivitySelected(str \_activityId, GanttControlActivityIdCollection \_allSelectedActivityIds)
-   onActivityDblClick(str \_activityId)
-   onSummaryActivityExpand(str \_activityId)
-   onSummaryActivityCollapse(str \_activityId)
-   onActivityChanged(GanttControlActivityModification \_modification, GanttControlActivityModificationResponse \_response)

All these events are one-way notifications from the client. However, the **onActivityChanged** event is somewhat special, because you can set a response. Typically, when a user makes a modification (for example, dragging an activity to a new time), either other activities must also be updated or some adjustments must be made to the activity itself (for example, the column texts must be changed). In the **GanttControlActivityModificationResponse** response, you can provide a list of activities that must be updated. If the change that the user makes is just accepted as is, no response must be set. However, at the very least, the column texts of the current activity must be updated in most cases, to guarantee that the new from and to dates appear. On an activity, the **parmAllowMove** flag determines whether the activity can be moved. However, higher-level flags on **GanttControlConfiguration** determine whether any activity can be moved (**parmAllowMoveActivities**) or resized (**parmAllowResizeActivities**), or whether the completion percentage for the activity can be changed (**parmAllowCompletionChange**).





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
