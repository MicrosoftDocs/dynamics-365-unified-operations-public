---
title: Track sales order and free text invoice history 
description: Learn how to set up and use the Customer invoice logging framework to track sales order and free text invoice history Microsoft Dynamics 365 Finance. 
author: JodiChristiansen
ms.author: reetuchopra
ms.topic: article
ms.date: 04/21/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-02-09
ms.search.form: CustPosting, CustVendExternalItem
ms.dyn365.ops.version: 10.0.25
ms.assetid: cb82245e-8c02-429c-b36e-8db0e3e6f7e5
---

# Customer invoice logging framework for tracking sales order and free text invoice history 

[!include [banner](../includes/banner.md)]

This article explains how to set up and use the customer invoice logging framework to track sales order and free text invoice history Microsoft Dynamics 365 Finance. 

## Prerequisites
Before you enable the Customer Invoice Logging Framework for Sales Order and FTI History Tracking, the following prerequisites must be met:

In Feature management, enable the **Customer invoice logging framework for sales order and FTI history tracking** feature. This feature introduces a structured logging framework to track the lifecycle of customer 
invoice documents, including sales orders and free text invoices. The logged data supports a detailed posting history in the **Customer invoice workspace**, improving traceability and diagnostics. 

### Parameters
To set up parameters, follow these steps: 
1.	Go to **Accounts receivable** > **Parameters** > **Updates** > **Data maintenance**.
2.	In **Number of days to retain customer logging data** parameter, enter a number of days. The default value is 30 days. Organizations can use this field to set their own data retention policies. 
4.	The organization can set this value for a maximum period of up to 45 days.

### Data maintenance jobs 
Starting in Microsoft Dynamics 365 Finance version 10.0.45, data maintenance jobs are automatically scheduled to run daily. 
These jobs automatically clean up customer data from the following logging tables: 
 - CustomerInvoiceDocumentLifecycleStageTransition
 - CustomerInvoiceDocumentLifecycleStageTransitionLog

By default, customer logging data from the past 30 days is retained. Older entries are deleted in small batches.

To schedule the data maintenance job, follow these steps:
1.	Go to **System administration** > **Periodic tasks** > **Data maintenance**.
The automatic data maintenance job helps prevent excessive growth of the logging tables. 

### Customer invoicing workspace
Previously, the **Customer invoicing workspace** provided a high-level overview showing the count of posted, open, and errored invoices. However, users were unable to drill down into the specifics of posted or 
errored invoices for further analysis.

With the introduction of the Customer invoice logging framework, the following enhancements are introduced:
 - The workspace displays only two columns: **Posted** and **Error**.
 - Users can click **Posted** or **Error** counts to access detailed information. For invoices with errors, an additional **Error details** tab is available, which shows specific error messages related to sales order or free text invoice posting failures.
 - The **Sales order posting history** and **Free text invoice posting history** tabs displays data for the past 14 days by default.



