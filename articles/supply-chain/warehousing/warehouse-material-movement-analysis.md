---
title: Warehouse material movement analysis
description: This article provides information about the 'Warehouse material movement analysis' Process Advisor template.
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

# Warehouse material movement analysis through process mining

[!include [banner](../includes/banner.md)]

This article describes what's included in the **Warehouse material movement analysis** Process Advisor template. It explains how to deploy and access the Process Advisor processes.

## Overview

The Process Advisor feature allows you to gain a better understanding of your business processes so you can optimize them. Process Advisor offers task mining and process mining capabilities to do this. You can read more about the feature and terminology in [Overview of process advisor](/power-automate/process-advisor-overview).

The **Warehouse material movement analysis** Process Advisor template was created so that warehouse and operations managers can gain insights into the material flow in the warehouse. It can help find inefficiencies and thus improve the performance of the warehouse. It uses Warehouse management, product, and other transactional data from your system. This process allows to visualize and analyze the material movement in the warehouse floor based on the closed warehouse works. In Process Advisor terminology each warehouse work corresponds to the **Case**, each pick or put work line corresponds to an **Event**. Based on the configuration an **Activity** can be one of the following:

- Warehouse location.
- Warehouse location profile.
- Warehouse zone.

## Deploying the Process Advisor process template

### Prerequisites

- The **Warehouse material movement analysis** feature is available in 10.0.35 release.
- The user who performs the deployment of the process in Process Advisor must have **Warehouse manager** or **Warehouse planner** or **System administrator** roles. Alternatively the required privileges and/or duties must be assigned to the user.
- The user who performs the deployment of the process in Process Advisor must be a configured in the linked Dataverse environment. User must have **Environment maker** or **System administrator** roles. Note that those roles are required only for process deployment. Once process is deployment, it can be shared with other users who will automatically get the necessary permissions to use the process.

### Deployment instructions

The deployment of the **Warehouse material movement analysis** process is done from the **Warehouse material movement process configuration** page (**Warehouse management \> Setup \> Process mining \> Warehouse material movement process configuration**).

Click on the **Deploy process** button and follow the wizard. You need to specify:

- **Process name** - identifies the process. Recommendation is to include the legal entity and other filter information into the name so can easily distinguish processes afterwards.
- **Company** - acts as a filter. Only warehouse works in the given company will be included into the Process Advisor process.
- **Number of months to load** - acts as a filter. Allows to avoid loading excessive or irrelevant data into the Process Advisor. Only warehouse works closed after the given threshold will be included into the Process Advisor process.
- **Activity** - controls what column Process Advisor will treat as an **Activity** (please refer to [Process Advisor documentation](/power-automate/process-advisor-overview) to learn the terminology).

> [!NOTE]
> Try to limit the data by using the proper **number of months to load** filter value. There is a number of threshold checks in Power Query Online. If try to load too much data, the system may fail with timeout or quota violation exceptions. Microsoft recommends to load at most 24 months of data into **warehouse material movement analysis** process and the total number of events in the process should not exceed 4 millions.

Upon the completion of the deployment wizard, the system will:

- Perform initial data load - load 200 **cases** into the staging table. In context of **Warehouse material movement analysis** process template, each case corresponds to a single closed warehouse work. Most likely there are many more closed warehouse works satisfying the filtering criteria set in the deployment wizard. Loading only 200 cases enhances the performance and user experience. It allows user to quickly get to the visualization.
- Open a new tab in browser to complete the deployment of the process in Process Advisor. The Process Advisor template provision page will open inside power automate in the linked Dataverse environment. You may be asked for credentials. Those credentials will be used by Process Advisor to read data from Supply Chain Management. Please make sure not to close the page right away as the deployment will be interrupted in that case.

Once the deployment succeeds you can use the process - it will be available both from within Supply Chain Management and Process Advisor.

### Data refresh in staging table and Process Advisor

In order to load full set of data you have following options:

- One-time staging table refresh. Click the **Refresh staging table** button. Batch job responsible for staging table refresh runs every 5 minutes. It will pick up the request and load all the data satisfying the filters specified during deployment. Note, it does not have any immediate effect on the data loaded into Process Advisor as Process Advisor holds its own copy of data. You need to open process in Process Advisor (by clicking on **Open in Process Advisor** button) and click the **Refresh data** button there.
- Automatic refresh. You can set a Daily or Weekly schedule to refresh data in the staging table by changing the value of the **Automatic refresh recurrence** field. Similar to one-time staging table refresh this will just refresh data in the staging table and is not automatically loaded by Process Advisor process. You can configure the Process Advisor to automatically load data based on the schedule. You need to open process in Process Advisor (by clicking on **Open in Process Advisor** button), click the **Schedule refresh** button there and choose the desired refresh schedule.

There is a staging table cleanup batch job which runs daily and removes the records from the staging table which do not satisfy the filter criteria anymore (e.g. the records became too old).

## Accessing the Warehouse material movement analysis process

The process can be accessed both from within Supply Chain Management or in the Process Advisor user interface. To open the process in the Supply Chain Management, go to the **Warehouse material movement analysis** page (**Warehouse management \> Inquiries and reports \> Warehouse performance analysis \> Warehouse material movement analysis**). On this page you can choose the process to view via the **Process name** lookup. The lookup shows only the processes ready for analysis - it means the process must have been deployed and analyzed in Process Advisor. The lookup shows only processes current user has access to (normally it means the process has been created by or shared with the current user).

On the **Warehouse material movement analysis** page user can click on "Open in Process Advisor" button. The current process gets opened in a new browser tab in the Process Advisor user interface. User can click on **Download minit** button. This will download the **Minit** desktop application. It gives much richer process mining capabilities than the Power BI report. You can read more about its capabilities in [Minit overview](/power-automate/minit/minit-desktop-application-overview).

## Troubleshooting

### Why don't I see all the events (work lines) / cases (work headers) I expect in the Process Advisor process?

There could be many reasons for this:

- Check that the staging table has been refreshed recently. You can see that on the **Warehouse material movement process configuration** page in the **Last staging table refresh** field. You can gain more insights by looking into the **Processing log** tab on the same page.
- Make sure that the warehouse work you expect to see in the process is closed. The warehouse work closed date and company should fall into the process filtering criteria specified during the process deployment. You can check that on the **Warehouse material movement process configuration** page.
- Verify that the Process Advisor process is refreshed. You can refresh the Process Advisor process by clicking on **Refresh data** in Process Advisor user interface for the given process. Consider to setup the automatic refresh (deployment section describes how to achieve that).

### Why don't I see the process in the drop-down list in the **Warehouse material movement analysis** page?

There could be several reasons for that:

- Current user does not have access to the given process. Normally the process has been created by or shared with the current user. You can check if this is indeed a root cause of the problem by going to the Process Advisor user interface (inside Power Automate) using the same user account and check if you can access the process there.
- System shows only processes ready for analysis on the **Warehouse material movement analysis** page. It means if the deployment of the process is still in progress, it may not appear on the **Warehouse material movement analysis** page. You can check that by trying to open the Power BI report for the process in the Process Advisor user interface.

### Failure during the process deployment

There is a number of checks system performs during the process provisioning. Most of the failure reasons are due to current Supply Chain Management user is not registered in Dataverse or user does not have the required privileges. If that is not a root cause and the deployment took a long time (around 4 hours), the likely reason is that you are hitting the threshold limits for the Process Advisor integration. Consider to change the filters to reduce the number of events to be loaded into the Process Advisor. This is normally achieved by reducing the **number of months to load** filter.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
