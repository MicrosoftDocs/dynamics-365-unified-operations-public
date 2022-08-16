---
title: Commerce component events for diagnostics and troubleshooting
description: This article explains where to find events from Commerce-specific components.
author: ShalabhjainMSFT
ms.date: 08/15/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.custom: 85493
ms.assetid: a22c9493-c000-4514-bb0d-b3cc674439d9
ms.search.industry: Retail
---

# Commerce component events for diagnostics and troubleshooting

[!include [banner](../includes/banner.md)]

This article explains where to find events from Commerce-specific components. To enable diagnostics and troubleshooting, Commerce components, which include self-hosted components such as the Retail Modern POS and cloud-hosted components, such as Commerce Scale Unit and E-Commerce modules, log their events locally to Event Viewer (or to the browser developer tools console such as F12). Events are also logged in the Microsoft Dynamics Lifecycle Services (LCS) log search experience.

## Viewing events in Event Viewer

You can use Event Viewer to view events for components that are installed on computers that run Microsoft Windows, if you have physical access to the computer where the events are logged. For more information about Event Viewer, see [Event Viewer](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766042(v=ws.11)) on TechNet. You can also use Event Viewer to view events remotely from computers that you have access to. For more information about how to use Event Viewer to view events remotely, see [Work with Event Logs on a Remote Computer](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766438(v=ws.11)) on TechNet. Typically, Event Viewer is used for troubleshooting in the following use cases:

- Development on a developer topology or on a downloadable virtual hard disk (VHD) that provides access to Event Viewer.
- Client components, when you're running a conference room pilot and have access to Event Viewer for that computer.

However, for most other cases, and especially when you don't have access to Event Viewer for the computer, you can use Log Search on LCS. For E-Commerce modules, events are currently available only in browser developer tools (such as F12). Log Search is discussed later in this article. This section applies to the following components:

- Commerce Scale Unit
- Retail Modern POS
- Retail Hardware Station

### Find Commerce-specific events in Event Viewer

To start Event Viewer on a computer, right-click the **Start** button, and then click **Event Viewer**.

[![Event Viewer command on the shortcut menu for the Start button.](./media/launch-event-viewer.png)](./media/launch-event-viewer.png)

All Commerce-specific event logs can be found under the following path in Event Viewer: Application and Services Logs\\Microsoft\\Dynamics We provide the following Commerce-specific event logs:

- **Commerce-RetailServer** – This log contains events that are logged by the Commerce Scale Unit components.
- **Commerce-ModernPos** – This log contains events that are logged by Retail Modern POS. These events include events from the TypeScript and C\# (CRT) layer.
- **Commerce-LoggingProvider** – This log contains events that are logged by all other Commerce components that aren't included in the list earlier in this article.

### Enable debug event logs

Currently, some of the events that are logged by various components are sent to debug event logs. These events are verbose events that are logged at very high rates and are useful only for detailed debugging scenarios. Follow this step to enable the debug event logs in Event Viewer.

- Right-click a debug log, and then click **Enable Log**.

![Enable Log command on the shortcut menu for a debug log.](./media/enable-debugging-log.png)

## Viewing events by using the (F12) browser developer tools console

Because Retail Cloud POS and E-Commerce modules are browser-based components, you can use the browser developer tools console to view events for it. For information about the Microsoft browser developer tools console, see [Using the Console to view errors and debug](/microsoft-edge/devtools-guide/console). To use the browser developer tools for Retail Cloud POS or E-Commerce modules, you must use a supported browser version.

### View events in the browser developer tools console

1. Start your browser, and navigate to Retail Cloud POS or your E-Commerce website.
2. Press F12, and then click the **Console** tab.
3. As you perform operations on Retail Cloud POS or on your E-Commerce website, events are logged in the console. You can filter by event severity to view events that have different severity levels.

[![Console tab in the browser developer tools.](./media/browser-console-1024x522.png)](./media/browser-console.png)

## Correlating events

This section explains how to correlate events from various Commerce components.

### Data flow between a POS client and Commerce Scale Unit

The diagram that follows shows the data flow between a point of sale (POS) client and the Commerce Scale Unit.

#### POS client startup

When a user starts a POS client, a new AppSessionID is generated. The AppSessionID is used to log every event that is instrumented in the POS client. All events that are logged to Event Viewer and App Insights have this ID.

#### User sign-in

When a user signs in to a POS client, a new UserSessionID is generated. The UserSessionID is used to log every event that is instrumented in the POS client. All user events that are logged to Event Viewer have this ID. This ID is maintained for as long as the user is signed in. When the current user signs out and a new user signs in, a new UserSessionID is generated.

#### POS client calls to Commerce Scale Unit

Whenever a POS client makes a call to the Commerce Scale Unit, the AppSessionID and UserSessionID are sent as headers. The Commerce Scale Unit then logs an event for the incoming request (Event ID 5000). This event includes those two IDs and also an ActivityID. The ActivityID is then also used for all related events. The AppSessionID, UserSessionID, and ActivityID are available in the event log where Commerce Scale Unit is hosted. They are also available in LCS Log Search.

#### Request activity on Commerce Scale Unit

Every event that is logged as part of a Commerce Scale Unit request has the same ActivityID as the initial event that was logged for the initial incoming request event (Event ID 5000). These events are available in both Event Viewer and LCS Log Search.

[![Data flow between a POS client and Commerce Scale Unit.](./media/event-log-data-flow1-1018x1024.png)](./media/event-log-data-flow1.png)

### Finding Retail Modern POS events in Event Viewer

Every event that is logged by Retail Modern POS includes the following data points:

- **AppSessionID** – A unique ID that is generated when the app is first started. It's included with every event that is logged.
- **UserSessionID** – A unique ID that is generated when a user signs in to Retail Modern POS. It's included with every event that is logged, for as long as the user remains signed in. When a new user signs in, a new UserSessionID is created.

You can find the AppSessionID and UserSessionID values on the **Details** tab in Event Viewer on the machine where Retail Modern POS is installed.

[![Details tab in Event Viewer.](./media/correlation-1024x672.png)](./media/correlation.png)

### Finding incoming Commerce Scale Unit request events in Event Viewer

To correlate data for incoming Commerce Scale Unit requests in Event Viewer, you must first enable the **Analytic** channel. To enable the Analytic channel, follow these steps.

1. In Event Viewer, in the left pane, select **Commerce-RetailServer**.
2. Click **View** &gt; **Enable Analytic and Debug log**. A new node for the Analytic channel appears under the **Commerce-RetailServer** logging provider.
3. Right-click the **Analytic** node, and then click **Enable log**.

In Event Viewer, all incoming Commerce Scale Unit requests are logged to the Analytic channel of the Commerce-RetailServer source as event 5000. These events also have the AppSessionID and UserSessionID that were described earlier. Every event also has a unique ActivityID that is instrumented for every logged event for the same request.

## Using LCS Log Search

LCS Log Search lets you view data from all the components from a single portal. You can access events from both cloud-hosted components (such as Commerce Scale Unit) and in-store components (such as Retail Modern POS and Retail Hardware Station). Event data from all cloud-hosted and in-store components flows to LCS Log Search, where it's indexed and made searchable. Data is typically available within 5 minutes after it's logged. For POS clients and Retail Hardware Station, all events are locally queued in persistent storage and then uploaded in batches after the queue is filled. This behavior enables network traffic to be optimized. It also enables events to be saved even when there is no Internet connectivity. After connectivity is restored, all pending events are uploaded.

LCS Log Search is available for the HA production topology. It can be used for the following Commerce components:

- Retail Modern POS
- Retail Cloud POS
- Commerce Scale Unit (running on Retail Cloud Scale Unit)

LCS Log Search does **not** include logs from the following Commerce components:

- Commerce layout designer
- Commerce receipt designer
- Self-service installer for Retail Modern POS
- Self-service installer for Retail Hardware Station
- Commerce Scale Unit (running on Retail Store Scale Unit)
- Retail Hardware Station

### Access LCS Log Search

To access LCS Log Search, follow these steps.

1. Go to [Lifecycle Services](https://lcs.dynamics.com/).
2. Sign in by using the credentials that are associated with your project.
3. On the project page, select the correct project.
4. On the **Project details** page, select the correct environment.
5. On the **Environment details** page, click **Environment Monitoring**.
6. On the **Environment monitoring** page, click **View raw logs**.
7. On the **Log Search** page, select one of the following queries:

    - **Commerce client events** query, which includes events from Retail Modern POS, Retail Cloud POS, and Commerce Scale Unit (running on Retail Cloud Scale Unit)
    - **All logs** query, which includes data from Commerce Scale Unit, Commerce Data Exchange, and Commerce Data Exchange: Real-time Service

You can filter by the following criteria to refine your query:

- Start and end dates and times (in Coordinated Universal Time \[UTC\])
- Device ID
- POS user
- POS application session ID
- POS user session ID
- Severity level


![Search results on the Environment monitoring page.](./media/log-search-results.png)

### Access logs in Application Insights

Diagnostic events for Commerce components can also be accessed in Application Insights.

#### Commerce Scale Unit minimum version requirements

Commerce Scale Unit has the following minimum version requirements:

- 10.0.23 (Retail Server version 9.33.22062.15 and later)
- 10.0.24 (Retail Server version 9.34.22062.14 and later)
- 10.0.25 (Retail Server version 9.35.22062.13 and later)
- 10.0.26 and later (all versions)

#### Enable diagnostic events in Application Insights

> [!IMPORTANT]
> If you used System Operational Insights Preview, you must complete the following procedure to enable System Operational Insights. That way, you ensure that reliable and secure access to events can continue.

To enable Commerce component diagnostic events, you must have an Application Insights account. You can use an existing account or [create a new account](/azure/azure-monitor/app/create-workspace-resource#create-workspace-based-resource). For data privacy reasons, we recommend that you use separate Application Insights accounts for production, sandbox, and development environments. After you have an account, you must enable the **Operational Insights** feature in Commerce headquarters.

To enable diagnostic events in Application Insights in Commerce headquarters, follow these steps.

1. In the **Feature Management** workspace, enable the **Operational Insights** feature.
1. Go to **System administration \> Operational Insights**.
1. On the **Configure** tab, set the **Commerce channel events** option to **Yes**.
1. On the **Environments** tab, enter **LCS Environment ID** and **Environment mode** values for every environment where you plan to use Application Insights. You can find each environment's LCS environment ID on the **Environment details** page for that environment in LCS. This step is required to prevent diagnostic events from being inadvertently sent to an incorrect environment when database copy operations are performed.
1. On the **Application Insights registry** tab, specify the Application Insights instrumentation key and corresponding environment mode of the environments where you plan to use each Application Insights account.
1. After you've completed the preceding configuration, the **CDX Job 1110** job must be run. You can wait for this job to run on its own schedule, or you can manually run it.
1. Restart each Commerce Scale Unit. In LCS, go to **Environment details \> Commerce \> Manage**, select a Commerce Scale Unit instance, and then select **Restart**.
1. Repeat the preceding steps for each environment where you plan to use Application Insights.

> [!NOTE]
> In Commerce version 10.0.29 and later, the procedures in this section also enable the streaming of point of sale (POS) operational insights events to your Application Insights account.
>
> To use the config file to control the POS operational insights events, complete the following steps.
>
>1.	Using a text editor, open the "DLLHost.exe.config" file that is located at “C:\Program Files (x86)\Microsoft Dynamics 365\70\Retail Modern POS\ClientBroker”.
>
>1.	Remove the sink XML element with the class name “Microsoft.Dynamics.Retail.Diagnostics.OperationalInsights.OperationalInsightsLogger” from the “diagnosticsSection”. 

#### Disable diagnostic events in Application Insights

If you no longer want to send diagnostic events to Application Insights, you must disable the feature.

> [!IMPORTANT]
> If you want to disable diagnostic events, it isn't enough that you turn off the feature in **Feature management**.

To disable diagnostic events in Application Insights in Commerce headquarters, follow these steps.

1. Go to **System administration \> Operational Insights**.
1. On the **Configure** tab, set the **Commerce channel events** option to **No**.
1. After you've completed the preceding configuration, the **CDX Job 1110** job must be run. You can wait for this job to run on its own schedule, or you can manually run it.
1. Restart each Commerce Scale Unit. In LCS, go to **Environment details \> Commerce \> Manage**, select a Commerce Scale Unit instance, and then select **Restart**.
1. Repeat the preceding steps for each environment where you plan to turn off Application Insights.

To disable diagnostic events for a single environment, delete the instrumentation key on the **Application Insights registry** tab of the **Operational Insights** page. Then complete steps 3 and 4 of the preceding procedure.

> [!NOTE]
> In Commerce version 10.0.29 and later, the steps in this section also disable streaming of POS operational insights events to your Application Insights account. 

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
