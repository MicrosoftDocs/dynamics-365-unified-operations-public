---
# required metadata

title: Subscription billing Power BI content
description: This topic describes what is included in the Subscription billing Microsoft Power BI content.
author: JodiChristiansen
ms.date: 04/13/2022
ms.topic: article
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: jchrist
ms.search.validFrom: 2021-04-13

---

# Subscription billing Power BI content

[!include[banner](../includes/banner.md)]

This topic describes what is included in the Subscription billing Microsoft Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that were used to build the content. 

## Overview

The Subscription billing Power BI content was created for subscription billing clerks and managers. It provides key subscription billing metrics, such as the monthly recurring revenue (MRR) for billing schedules, and the declining balance and waterfall information for deferral schedules. It uses the data from the billing schedules and deferral schedules to provide an overview of recurring income and revenue.

The Power BI content has the following three tabs that provide a total of four analytical reports: 

- **Analytics - MRR** – This tab provides the **Monthly recurring billing** report and the **Billing schedule details** report.
- **Analytics - Waterfall** – This tab provides the **Revenue waterfall** report.
- **Analytics - Declining balance** – This tab provides the **Declining balance** report.

## View data on the analytical reports

Before you can view data on the analytical reports, you must run a periodic process that generates the reporting data for each report. This data that the reports require must be generated because it isn't stored directly in the database. 

1. Go to **Subscription billing \> Recurring contract billing \> Periodic tasks \> MRR analytical report batch processing**, and follow these steps:

    1. Enter a date range of no more than three years.
    2. Optional: Set up a recurring batch process job to periodically refresh the data.
    3. Select **OK**.

2. After the batch job has finished running, go to **System administration \> Setup \> Entity Store**, and refresh the **MRR report** aggregate measurement. 
3. Go to **Subscription billing \> Revenue and expense deferrals \> Periodic tasks \> Waterfall analytical report batch processing**, and follow these steps:

    1. Enter a start date and an end date that span no more than 26 periods. 
    2. If you want to view the forecasted amount of past periods in the current period, set the **Forecast past amounts in current period** option to **Yes**.
    3. Optional: Set up a recurring batch process job to periodically refresh the data.
    4. Select **OK**. 

4. After the batch job has finished running, go to **System administration \> Setup \> Entity Store**, and refresh the **Waterfall report** aggregate measurement.
5. Go to **Subscription billing \> Revenue and expense deferrals \> Periodic tasks \> Declining balance analytical report batch processing**, and follow these steps:

    1. Enter a start date and an end date that span no more than 26 periods. 
    2. If you want to view the forecasted amount of past periods in the current period, set the **Forecast past amounts in current period** option to **Yes**.
    3. Optional: Set up a recurring batch process job to periodically refresh the data.
    4. Select **OK**.

6. After the batch job has finished running, go to **System administration \> Setup \> Entity Store**, and refresh the **Declining balance report** aggregate measurement.

## Accessing the Power BI content

The Subscription billing Power BI content is shown in the **Subscription billing** workspace.
