---
# required metadata

title: Subscription billing workspace and Power BI analytical reports
description: This topic explains how to setup the Power BI reports on the Subscription billing workspace
author: JodiChristiansen
ms.date: 11/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Subscription billing Power BI content

This topic describes what is included in the Subscription billing Microsoft Power BI content. It explains how to access the Power BI reports and provides information about the data model and entities that were used to build the content. 

## Overview

The Subscription billing Power BI content was created for subscription billing clerks and managers. It provides key subscription billing metrics such as Monthly recurring revenue (MRR) for billing schedules and the declining balance and waterfall information for deferral schedules. It uses the data from the billing schedules and deferral schedules to provide an overview on recurring income and revenue.

The Power BI content has three tabs with a total of 4 reports. 
Analytics - MRR has the Monthly recurring billing report and Billing schedule details report
Analytics - Waterfall that has the Revenue waterfall report
Analytics - Declining balance that has the Declining balance report

## Setup needed to view Power BI content

To view the data on the analytical reports a periodic process needs to run first. This periodic process generates the reporting data for each report. The data needed for the reports needs to be generated because it is not stored directy in the the database. 
1. Go to **Subscription billing > Recurring contract billing > Periodic tasks > MRR analytical report batch processing**.
   a. Enter a date range of no more than three years.
   b. Optional: Setup a recurring batch process job to refresh the data on a periodic basis.  
   c. Select Ok.
   d. Once the batch job is finished go to Go to **System administration > Setup > Entity Store** to refresh the  **MRR report** aggregate measurement.  
2. Go to **Subscription billing > Revenue and expense deferrals > Periodic tasks > Waterfall analytical report batch processing**. 
   a. Enter a start date and end date that spans no more than 26 periods. 
   b. Change **Forecast past amounts in current period** to Yes if you want to view the forecasted amount of past periods in the current period.
   c. Optional: Setup a recurring batch process job to refresh the data on a periodic basis.  
   d. Select OK. 
   e  Once the batch job is finished go to Go to **System administration > Setup > Entity Store** to refresh the  **Waterfall report** aggregate measurement
3. Go to **Subscription billing > Revenue and expense deferrals > Periodic tasks > **Declining balance analytical report batch processing**.
   a. Enter a start date and end date that spans no more than 26 periods. 
   b. Change **Forecast past amounts in current period** to Yes if you want to view the forecasted amount of past periods in the current period.
   c. Optional: Setup a recurring batch process job to refresh the data on a periodic basis.  
   d. Select OK. 
   e. Once the batch job is finished go to Go to **System administration > Setup > Entity Store** to refresh the  **Declining balance report** aggregate measurement

## Accessing the Power BI content
The Subscription billing Power BI content is shown on the Subscription billing workspace. 
