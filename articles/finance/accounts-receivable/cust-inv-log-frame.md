---
title: Customer invoice logging framework for tracking sales order and free text invoice history 
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

In Feature management, enable the Customer Invoice Logging Framework for Sales Order and FTI History Tracking feature. This feature introduces a structured logging framework to track the lifecycle of customer 
invoice documents, including sales orders and free text invoices (FTI). The logged data supports a detailed posting history in the Customer Invoice workspace, improving traceability and diagnostics. 

### Parameters
Set up parameters under Accounts receivable
1.	Go to Accounts Receivable > Parameters > Updates > Data Maintenance.
2.	Update the "Number of days to retain customer logging data" parameter. The default value is 30 days. Organizations can use this field to set their own data retention policies, based on their requirements. 
3.	The organization can set this value for a maximum period of up to 45 days.

### Data maintenance jobs 
As of Microsoft Dynamics 365 Finance version 10.0.45, data maintenance jobs are automatically scheduled to run daily. These jobs automatically clean up customer data from the logging tables 
 - CustomerInvoiceDocumentLifecycleStageTransition
 - CustomerInvoiceDocumentLifecycleStageTransitionLog

By default, customer logging data from the past 30 days is retained, with older entries deleted in small batches.

To schedule the data maintenance job, follow these steps:
1.	Go to System administration > Periodic tasks > Data maintenance.
The automatic data maintenance job helps prevent excessive growth of the logging tables. 

### Customer invoicing workspace
Previously, the Customer Invoicing workspace provided a high-level overview showing the count of posted, open, and errored invoices. However, users were unable to drill down into the specifics of posted or 
errored invoices for further analysis.

With the introduction of the Customer Invoice Logging Framework, the following enhancements have been introduced:
 - The workspace now displays only two columns – Posted and Error – providing a simplified yet more informative view.
 - Users can now click on the Posted or Error counts to access detailed information. For errored invoices, an additional Error Details tab is available, which shows specific error messages related to sales order or
 free text invoice posting failures.
 - The Sales Order Posting History and Free Text Invoice (FTI) Posting History tabs continue to retain and display data for the past 14 days by default.
 - The tab layout within the workspace remains unchanged, ensuring a familiar and seamless experience for users even after the feature is enabled.


