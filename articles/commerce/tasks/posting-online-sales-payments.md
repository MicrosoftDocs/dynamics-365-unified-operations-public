---
title: Posting of online sales and payments
description: This procedure walks through configuring and running a recurrent batch job to create sales orders and payments for online store transactions.
author: jashanno
ms.date: 08/06/2019
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: jashanno
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.industry: Retail
ms.search.form: RetailChannelOperationsWorkspace, RetailOperatingUnitPicker, SysRecurrence
---
# Posting of online sales and payments

[!include [banner](../includes/banner.md)]

This procedure walks through configuring and running a recurrent batch job to create sales orders and payments for online store transactions.

Posting online sales and payments is a two-stage process.

- Pulling the online commerce transaction data in HQ.
- Synchronizing orders to create sales orders in HQ.

Pulling the online transaction data can be done either by manually running the P-job or by creating a recurrent batch job.

### Manually running the P-job

1. Go to All workspaces > Retail and Commerce IT.
2. Click Distribution schedule.
3. Select P-0001.
4. Adjust channel database groups, if required.
5. Click Run now.
6. Click Yes.

### Scheduling a recurring P-job

1. Go to All workspaces > Retail and Commerce IT.
2. Click Distribution schedule.
3. Select P-0001.
4. Click Create batch job.
5. Click Run in the background.
5. Enable Batch processing.
6. Click Recurrence..
7. Select the No end date option.
8. In the Count field, enter interval between the runs in minutes. Typically this would be 5-10.
9. Click OK.
10. Click OK.

Orders can be synchronized either by manually running the "Synchronize orders"-job or by creating a recurring batch job.

### Manually running order synchronization 

Follow these steps to manually run "Synchronize orders" job once.

1. Go to All workspaces > Store financials.
2. Click Synchronize orders.
3. In the Organization hierarchy field, select 'Stores by Region'.
    * Select either a specific online store, or select a node if you want to create the batch job for a group of stores.  
    * Click the arrow to add your selection.  
4. Click the Run in the background tab.
5. Disable Batch processing
6. Click Recurrence.
7. Select End After option
8. In the End After field, enter 1.
9. Click OK.
10. Click OK.

### Scheduling recurring order synchronization

This procedure walks through configuring and running a recurrent batch job to create sales orders and payments for online store transactions. This procedure uses the USRT company in demo data.

1. Go to All workspaces > Store financials.
2. Click Synchronize orders.
3. In the Organization hierarchy field, select 'Stores by Region'.
    * Select either a specific online store, or select a node if you want to create the batch job for a group of stores.  
    * Click the arrow to add your selection.  
4. Click the Run in the background tab.
5. Enable Batch processing
6. Click Recurrence.
7. Select the No end date option.
8. In the Count field, enter interval between the runs in minutes. Typically this would be 2-20
9. Click OK.
10. Click OK.

## Data entities involved in the process

- RetailTransactionTable
- RetailTransactionAddressTrans
- RetailTransactionInfocodeTrans
- RetailTransactionTaxTrans
- RetailTransactionSalesTrans
- RetailTransactionTaxMeasure
- RetailTransactionDiscountTrans
- RetailTransactionTaxTransGTE
- RetailTransactionMarkupTrans
- RetailTransactionPaymentTrans
- RetailTransactionAttributeTrans


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
