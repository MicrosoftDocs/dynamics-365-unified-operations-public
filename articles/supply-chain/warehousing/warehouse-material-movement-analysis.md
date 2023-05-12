---
title: Analyze warehouse material movement through process mining
description: This article provides information about the Warehouse material movement analysis template for the Power Automate process advisor, which helps warehouse and operations managers gain insights into the material flow in the warehouse.
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

The Power Automate process advisor feature allows you to gain a better understanding of your business processes so you can optimize them. Process advisor offers *task mining* and *process mining* capabilities to do this. Supply Chain Management offers a *Warehouse material movement analysis* template for the process advisor, which can be used to create processes that help warehouse and operations managers gain insights into the material flow in the warehouse. It can help find inefficiencies that could be removed to improve the performance of the warehouse. It uses warehousing, product, and transactional data stored in your system and lets you visualize and analyze material movements on the warehouse floor based on closed warehouse work records. In process advisor terminology, each warehouse work record corresponds to a *case*, while each pick or put work line corresponds to an *event*. Depending on your configuration, an *activity* can be any one of the following:

- Warehouse location
- Warehouse location profile
- Warehouse zone

For more information about the process advisor, see [Overview of process advisor](/power-automate/process-advisor-overview).

This article describes what's included in the *Warehouse material movement analysis* template and explains how to deploy and access the process advisor processes.

## Prerequisites

The *Warehouse material movement analysis* process advisor template requires the following prerequisites:

- You must be running Supply Chain Management version 10.0.35 or later.
- Your Supply Chain Management environment must be linked to a Dataverse environment.
- The user who deploys the process in the process advisor must have the *Warehouse manager*, *Warehouse planner*, and/or *System administrator* roles.
- The Supply Chain Manager user who performs the deployment of the process in the process advisor must also be a configured as a user in the linked Dataverse environment. To deploy the process, a user must have the *Environment maker* and/or *System administrator* roles. Once the process is deployed, it can be shared with other users who will automatically get the necessary permissions to use the process.

## Deploy a new process advisor process based on the template

You can set up as many processes as you need, each with a different name and different settings. Follow these steps to deploy a *Warehouse material movement analysis* process:

1. Go to **Warehouse management \> Setup \> Process mining \> Warehouse material movement process configuration**.
1. On the Action Pane, select **Deploy process** to launch the deployment wizard.
1. Follow the instructions on your screen. You will be asked to specify the following information:

    - **Process name** – Identifies the process. We recommend that you include the legal entity and other filter information into the name so you can easily identify the process later.
    - **Company** – Acts as a filter. Only warehouse work records in the selected company will be included in the process advisor process.
    - **Number of months to load** – Acts as a filter. Use this to avoid loading excessive or irrelevant data into the process advisor. Only warehouse work records that were closed after the specified time threshold will be included into the process advisor process.
    - **Activity** – Specifies which column the process advisor will treat as an *activity*. To learn more about process advisor terminology, see the [process advisor documentation](/power-automate/process-advisor-overview).

    > [!NOTE]
    > Try to limit the data by optimizing the **Number of months to load** filter value. Power Query Online includes several threshold checks, so if you try to load too much data, the system may fail with timeout or quota-violation exceptions. We recommend that you load less than 25 months of data into the *Warehouse material movement analysis* process and ensure that the total number of events in the process is less than 4 millions.

When you're done filling out the deployment wizard, the the following actions will occur:

- **Load initial data** – The system loads 200 *cases* into the staging table. In context of the *Warehouse material movement analysis* process template, each *case* corresponds to a single closed warehouse work record. Most likely, many more than 200 records will meet the filtering criteria set in the deployment wizard, but loading only 200 cases enhances the performance and user experience, so you can access the visualization more quickly.
- **Prompt you to complete the deployment process** – The process advisor user interface opens in new tab in your browser. You may be asked to sign in. Your credentials will be used by the process advisor to read data from Supply Chain Management. Be sure not to close the page right away because that will interrupt the deployment. You don't have to do anything else here. The process advisor will let you know when deployment is complete.

## Refresh data in the staging table and process advisor

As mentioned, after you deploy a new process, the system loads an initial set of 200 cases into the staging table and loads that data into the process advisor. This lets you get started quickly. However, to start working with your full data set, you'll need to refresh the staging table and process advisor. This section describes how to trigger this process manually.

> [!TIP]
> Though it can be handy to refresh the data on demand from time to time, you'll probably want to set up each process to refresh its data automatically on a regular basis. For instructions, see [Configure the warehouse material movement process](#config).

Follow these steps to manually refresh data in the staging table and process advisor:

1. Go to **Warehouse management \> Setup \> Process mining \> Warehouse material movement process configuration**.
1. From the list pane, select the process for which you want to refresh the data.
1. On the Action Pane, select **Refresh staging table**. The batch job responsible for refreshing the staging table runs every five minutes. The next time it runs, it will pick up the request to refresh the table and then load all the data that matches the filters specified during deployment.
1. The **Last staging table refresh** field (on the **General** FastTab) will update to indicate that the table has been refreshed, but the new data won't be available in the process advisor until you refresh it there. To do so, select **Open in process advisor** on the Action Pane. Then select the **Refresh data** button in the process advisor.

A staging table cleanup batch job runs daily and removes any records from the staging table that no longer satisfy the filter criteria (for example, to remove records that are now too old).

## <a name="config"></a>Configure warehouse material movement processes

After you have deployed a process, you can configure it at any time as needed. Follow these steps:

1. Go to **Warehouse management \> Setup \> Process mining \> Warehouse material movement process configuration**.
1. From the list pane, select the process for which you want to refresh the data.
1. Make the following settings on the **General** FastTab:
    - **Automatic refresh recurrence** – Select how often the system should update the data table (*None*, *Once per day*, or *Once per week*). This will refresh data in the staging table, but won't automatically load that data into the process advisor. To set the process advisor to load this data periodically from the staging table, select **Open in process advisor** on the Action Pane. Then, in the process advisor, select the **Schedule refresh** button and choose the desired refresh schedule. You can also manually refresh the data in the process advisor by selecting the **Refresh data** button here.
    - **Last staging table refresh** – This read-only field shows the date and time when the staging table was last refreshed.
    - **Enforce offline hours** – Set this option to *yes* to prevent the system from refreshing the staging table during the specified hours. This can be useful if you want to avoid refreshing the table during peak hours.
1. Read the following information on the **Process parameters** FastTab:
    - **Legal entity** – This read-only field shows the legal entity that was specified during deployment.
    - **Number of months to load** – This read-only field shows the number of months to load, as specified during deployment.
    - **Activity** – This read-only field shows the activity that was specified during deployment.
1. The **Processing log** FastTab shows a history of data refresh and cleanup operations. This can be useful during troubleshooting.

## Access the warehouse material movement analysis process

You can access the warehouse material movement analysis process both from within Supply Chain Management and from the process advisor user interface.

To open the process from Supply Chain Management, follow these steps:

1. Go to **Warehouse management \> Enquiries and reports \> Warehouse performance analysis \> Warehouse material movement analysis**.
1. In the **Process name** field, select the name of the process that you want to view. This drop-down list only shows the processes that are both ready for analysis (deployed and analyzed in process advisor) and accessible to the current user (created by or shared with the current user).
1. The Power BI report for your selected process opens. You can interact with the report to view the process and analyze it in various ways.
1. To view the selected process in the process advisor, select **Open in process advisor** on the Action Pane, which opens the process advisor in a new browser tab.

    > [!TIP]
    > From this page in the process advisor, you can select **Download minit** to download the **Minit** desktop application, which gives much richer process mining capabilities than the Power BI report. You can read more about its capabilities in [Minit overview](/power-automate/minit/minit-desktop-application-overview).

## FAQs

### Why don't I see all the events (work lines) and cases (work headers) that I expect in the process advisor process?

There are several reasons why you might not see all of the events and cases that you expect. Here are some things to check:

- Check that the staging table has been refreshed recently. Go to **Warehouse management \> Setup \> Process mining \> Warehouse material movement process configuration** and review the **Last staging table refresh** and **Processing log**.
- Make sure that the warehouse work you expect to see in the process is closed. The warehouse work closed date and company should fall into the process filtering criteria specified during process deployment. You can check that on the **Warehouse material movement process configuration** page.
- Verify that the process advisor process has been refreshed recently. See [Configure the warehouse material movement process](#config) for details about how to view refresh information and set up schedules to refresh the staging table and process advisor process automatically.

### Why don't I see the process I'm looking for on the Warehouse material movement analysis page?

There are several reasons why you might not see a particular process on the **Warehouse material movement analysis** page. Here are some things to check:

- You might not have access to the process. To view a process, you usually must either have created it yourself, or the creator must share it with you. You can check this by signing in to the process advisor (in Power Automate) using the same user account and seeing whether you can access it there.
- The **Warehouse material movement analysis** page only shows processes that are ready for analysis. If the process is still being deployed, it might not yet appear on the **Warehouse material movement analysis** page. You can check this by trying to open the Power BI report for the process in the process advisor user interface.

### Why do I get an error during process deployment?

The system performs several checks while provisioning the process. Most failures occur because the Supply Chain Management user account being used isn't registered in Dataverse or the account doesn't have the required privileges. If deployment is taking a long time (around 4 hours), then you are probably exceeding the threshold limits for the process advisor integration. Consider changing the filters to reduce the number of events to be loaded into the process advisor. This is normally achieved by reducing the **Number of months to load** filter.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
