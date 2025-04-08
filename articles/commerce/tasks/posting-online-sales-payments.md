---
title: Post online sales and payments
description: This article describes how to configure and run a recurrent batch job to create sales orders and payments for online store transactions in Microsoft Dynamics 365 Commerce headquarters.
author: jashanno
ms.date: 05/28/2024
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2016-06-30
ms.search.form: RetailChannelOperationsWorkspace, RetailOperatingUnitPicker, SysRecurrence
ms.custom: 
  - bap-template
  - evergreen
---

# Post online sales and payments

[!include [banner](../includes/banner.md)]

This article describes how to configure and run a recurrent batch job to create sales orders and payments for online store transactions in Microsoft Dynamics 365 Commerce headquarters.

Posting online sales and payments is a two-stage process.

- Pull the online commerce transaction data in headquarters.
- Synchronize orders to create sales orders in headquarters.

Pulling the online transaction data can be done either by manually running the P-job, or by creating a recurrent batch job.

### Manually run the P-job

To manually run the P-job, follow these steps.

1. In headquarters, go to **All workspaces \> Retail and Commerce IT**.
2. Select **Distribution schedule**.
3. Select **P-0001**.
4. Adjust channel database groups, if required.
5. Select **Run now**.
6. Select **Yes**.

### Schedule a recurring P-job

To schedule a recurring P-job, follow these steps.

1. In headquarters, go to **All workspaces \> Retail and Commerce IT**.
2. Select **Distribution schedule**.
3. Select **P-0001**.
4. Select **Create batch job**.
5. Select **Run in the background**.
5. Enable **Batch processing**.
6. Select **Recurrence**.
7. Select the **No end date** option.
8. In the **Count** field, enter the interval between the runs in minutes. Typically, this would be 5-10 minutes.
9. Select **OK**.
10. Select **OK**.

Orders can be synchronized either by manually running the **Synchronize orders** job, or by creating a recurring batch job.

### Manually run order synchronization

To manually run the **Synchronize orders** job once, follow these steps.

1. In headquarters, go to **All workspaces \> Store financials**.
2. Select **Synchronize orders**.
3. In the **Organization hierarchy** field, select **Stores by Region**.
    1. Select either a specific online store, or select a node if you want to create the batch job for a group of stores.  
    1. Select the arrow to add your selection.  
4. Select the **Run in the background** tab.
5. Disable **Batch processing**.
6. Select **Recurrence**.
7. Select the **End After** option.
8. In the **End After** field, enter "1".
9. Select **OK**.
10. Select **OK**.

### Schedule recurring order synchronization

The following procedure walks through configuring and running a recurrent batch job to create sales orders and payments for online store transactions, using the USRT company in demo data.

To schedule recurring order synchronization, follow these steps.

1. In headquarters, go to **All workspaces \> Store financials**.
2. Select **Synchronize orders**.
3. In the **Organization hierarchy** field, select **Stores by Region**.
    1. Select either a specific online store, or select a node if you want to create the batch job for a group of stores.  
    1. Select the arrow to add your selection.  
4. Select the **Run in the background** tab.
5. Enable **Batch processing**.
6. Select **Recurrence**.
7. Select the **No end date** option.
8. In the **Count** field, enter the interval between the runs in minutes. Typically, this would be 2-20 minutes.
9. Select **OK**.
10. Select **OK**.

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
