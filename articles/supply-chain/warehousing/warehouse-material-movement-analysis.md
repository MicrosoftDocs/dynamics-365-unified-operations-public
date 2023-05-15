---
title: Analyze warehouse material movement through process mining
description: This article provides information about the Warehouse material movement analysis template for the Microsoft Power Automate process advisor. This template helps warehouse and operations managers gain insights into the material flow in the warehouse.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 05/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Analyze warehouse material movement through process mining

[!include [banner](../includes/banner.md)]

The Microsoft Power Automate process advisor feature offers *task mining* and *process mining* capabilities to help you better understand your business processes, so that you can optimize them. Dynamics 365 Supply Chain Management offers a *Warehouse material movement analysis* template for the process advisor. This template can be used to create processes that help warehouse and operations managers gain insights into the material flow in the warehouse. It helps find inefficiencies that can be removed to improve the performance of the warehouse.

The *Warehouse material movement analysis* template uses warehousing, product, and transactional data that's stored in your system, and lets you visualize and analyze material movements on the warehouse floor, based on closed warehouse work records. In process advisor terminology, each warehouse work record corresponds to a *case*, and each pick or put work line corresponds to an *event*. Depending on your configuration, an *activity* can be any one of the following items:

- Warehouse location
- Warehouse location profile
- Warehouse zone

For more information about the process advisor, see [Overview of process advisor](/power-automate/process-advisor-overview).

This article describes what's included in the *Warehouse material movement analysis* template, and explains how to deploy and access the process advisor processes.

## Prerequisites

The *Warehouse material movement analysis* template for the process advisor has the following prerequisites:

- You must be running Supply Chain Management version 10.0.35 or later.
- Your Supply Chain Management environment must be linked to a Dataverse environment.
- The user who deploys the process in the process advisor must have the *Warehouse manager*, *Warehouse planner*, and/or *System administrator* role.
- The Supply Chain Manager user who deploys the process in the process advisor must also be configured as a user in the linked Dataverse environment. To deploy the process, a user must have the *Environment maker* and/or *System administrator* role. After the process is deployed, it can be shared with other users. Those users will automatically get the permissions that are required to use the process.

## Deploy a new process advisor process based on the template

You can set up as many processes as you need, each of which has a different name and filters. Follow these steps to deploy a *Warehouse material movement analysis* process.

1. Go to **Warehouse management \> Setup \> Process mining \> Warehouse material movement process configuration**.
1. On the Action Pane, select **Deploy process** to open the deployment wizard.
1. Follow the on-screen instructions. You'll be asked to provide the following information:

    - **Process name** – Enter a name for the process. We recommend that you include the legal entity (company) and other filter information in the name, so that you can easily identify the process later.
    - **Company** – Select the legal entity that you want to use this process to analyze. Only warehouse work records in the selected legal entity will be included in the process advisor process.
    - **Number of months to load** – Specify the number of months to load at a time. This filter helps prevent excessive or irrelevant data from being loaded into the process advisor. Only warehouse work records that were closed after the specified time threshold will be included in the process advisor process.
    - **Activity** – Specify which column the process advisor should treat as an *activity*. To learn more about process advisor terminology, see [Overview of process advisor](/power-automate/process-advisor-overview).

    > [!NOTE]
    > Try to limit the data by optimizing the **Number of months to load** filter value. Power Query Online includes several threshold checks. Therefore, if you try to load too much data, time-out or quota violation exceptions might occur, and the system might fail. We recommend that you load less than 25 months of data into the *Warehouse material movement analysis* process and ensure that the total number of events in the process is less than 4 million.

When you've completed the deployment wizard, the following actions occur:

- **Initial data is loaded.** The system loads 200 *cases* into the staging table. In context of the *Warehouse material movement analysis* process template, each case corresponds to a single closed warehouse work record. Most likely, many more than 200 records will meet the filtering criteria that were set in the deployment wizard. By loading only 200 cases, the system enhances performance and the user experience, so that you can access the visualization more quickly.
- **You're prompted to complete the deployment process.** The process advisor user interface (UI) is opened on a new tab in your browser. You might be asked to sign in. The process advisor will use your credentials to read data from Supply Chain Management. Don't close the page right away. Otherwise, you'll interrupt the deployment. You don't have to do anything else on the page. The process advisor will let you know when deployment is completed.

## Refresh data in the staging table and the process advisor

As was mentioned, after you deploy a new process, the system loads an initial set of 200 cases into the staging table and loads that data into the process advisor. This behavior lets you get started quickly. However, to work with your full data set, you must refresh the staging table and the process advisor. This section describes how to manually trigger this process.

> [!TIP]
> Although it can be useful to refresh the data on demand from time to time, you'll probably want to set up each process so that it automatically refreshes its data on a regular basis. For instructions, see the [Configure the warehouse material movement process](#config) section of this article.

Follow these steps to manually refresh data in the staging table and the process advisor.

1. Go to **Warehouse management \> Setup \> Process mining \> Warehouse material movement process configuration**.
1. In the list pane, select the process to refresh the data for.
1. On the Action Pane, select **Refresh staging table**. The batch job that's responsible for refreshing the staging table runs every five minutes. The next time that it runs, it will pick up the request to refresh the table. It will then load all the data that matches the filters that were specified during deployment.
1. On the **General** FastTab, the **Last staging table refresh** field is updated to indicate that the table has been refreshed. However, the new data won't be available in the process advisor until you refresh it there. Select **Open in process advisor** on the Action Pane, and then select **Refresh data** in the process advisor.

A staging table cleanup batch job runs daily and removes any records from the staging table that no longer satisfy the filter criteria. (For example, it removes any records that are now too old.)

## <a name="config"></a>Configure warehouse material movement processes

After you've deployed a process, you can configure it at any time by following these steps.

1. Go to **Warehouse management \> Setup \> Process mining \> Warehouse material movement process configuration**.
1. In the list pane, select the process to refresh the data for.
1. On the **General** FastTab, set the following fields:

    - **Automatic refresh recurrence** – Select how often the system should update the data table (*None*, *Once per day*, or *Once per week*). Although this update refreshes data in the staging table, it won't automatically load that data into the process advisor. To set the process advisor to periodically load this data from the staging table, select **Open in process advisor** on the Action Pane. Then, in the process advisor, select **Schedule refresh**, and select a refresh schedule. You can also manually refresh the data in the process advisor by selecting **Refresh data** in the process advisor.
    - **Last staging table refresh** – This read-only field shows the date and time when the staging table was last refreshed.
    - **Enforce offline hours** – Set this option to *Yes* to prevent the system from refreshing the staging table during the specified hours. This option can be useful if you want to avoid refreshing the table during peak hours.

1. On the **Process parameters** FastTab, review the following fields:

    - **Legal entity** – This read-only field shows the legal entity that was specified during deployment.
    - **Number of months to load** – This read-only field shows the number of months to load, as specified during deployment.
    - **Activity** – This read-only field shows the activity that was specified during deployment.

    The **Processing log** FastTab shows a history of data refresh and cleanup operations. This information can be useful during troubleshooting.

## Access the warehouse material movement analysis process

You can access the warehouse material movement analysis process from both Supply Chain Management and the process advisor UI.

To access the process from Supply Chain Management, follow these steps.

1. Go to **Warehouse management \> Enquiries and reports \> Warehouse performance analysis \> Warehouse material movement analysis**.
1. In the **Process name** field, select the name of the process to view. The list includes only processes that meet both the following conditions:

    - The process is ready for analysis. (In other words, it has been deployed and analyzed in process advisor.)
    - The process is accessible to the current user. (In other words, it was created by or shared with the current user.)

1. The Power BI report for your selected process is opened. You can interact with the report to view the process and analyze it in various ways.
1. To view the selected process in the process advisor, select **Open in process advisor** on the Action Pane. The process advisor UI is opened on a new tab in your browser.

    > [!TIP]
    > From the process advisor page that appears, you can select **Download minit** to download the **Minit** desktop application. This application gives much richer process mining capabilities than the Power BI report. For more information about its capabilities, see [Minit overview](/power-automate/minit/minit-desktop-application-overview).

## FAQ

### Why don't I see all the events (work lines) and cases (work headers) that I expect in the process advisor process?

There are several reasons why you might not see all the events and cases that you expect. Here are some things to check:

- Confirm that the staging table has recently been refreshed. Go to **Warehouse management \> Setup \> Process mining \> Warehouse material movement process configuration**, and review the **Last staging table refresh** field on the **General** tab and the information on the **Processing log** FastTab.
- Confirm that the warehouse work that you expect to see in the process is closed. The warehouse work closed date and legal entity (company) should meet the process filtering criteria that were specified during process deployment. You can check these details on the **Warehouse material movement process configuration** page.
- Confirm that the process advisor process has recently been refreshed. For information about how to view refresh information, and how to set up schedules to automatically refresh the staging table and the process advisor process, see the [Configure the warehouse material movement process](#config) section of this article.

### Why don't I see the process that I'm looking for on the Warehouse material movement analysis page?

There are several reasons why you might not see a process on the **Warehouse material movement analysis** page. Here are some things to check:

- Confirm that you have access to the process. Usually, to view a process, you must have created it yourself, or the creator must share it with you. To confirm that you have access, sign in to the process advisor in Power Automate by using the same user account, and determine whether you can access the process there.
- Confirm that the process has been deployed and the process is ready for analysis. The **Warehouse material movement analysis** page shows only processes that are ready for analysis. If the process is still being deployed, it might not yet appear on the page. To confirm that the process is ready for analysis, try to open the Power BI report for the process in the process advisor UI.

### Why do I receive an error during process deployment?

The system performs several checks while it's provisioning a process. Most failures occur either because the Supply Chain Management user account that's used isn't registered in Dataverse or because the account doesn't have the required privileges. If deployment is taking a long time (about four hours), you're probably exceeding the threshold limits for the process advisor integration. Consider changing the filters to reduce the number of events that are loaded into the process advisor. You can typically lower the **Number of months to load** filter value.
