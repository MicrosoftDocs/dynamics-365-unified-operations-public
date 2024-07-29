---
title: Archive Dynamics 365 Commerce transactions
description: Learn about how to archive Dynamics 365 Commerce transactions.
author: shajain
ms.author: shajain
ms.topic: conceptual
ms.date: 7/26/2024
ms.custom:
ms.reviewer: v-chrgriffin
---

# Archive Dynamics 365 Commerce transactions

This article explains how to archive Dynamics 365 Commerce transactions.

## Prerequisites

The Archival framework should be enabled in the Dynamics 365 Commerce headquarters. To enable this framework, see [Set up and management](archive-setup-manage.md).

## Turn on the feature using Feature management workspace

The **Archive with Dataverse long term retention** feature should be enabled.

## Set up an archival job

To schedule the long-term retention job, follow these steps.

1. In Dynamics 365 Commerce, go to **System administration** \> **Archive with Dataverse long term retention workspace**.
1. Select **Retail transactions**.
1. Select **New long term retention job** to open a wizard that you can use to schedule a new retail transaction archival job with Dataverse long-term retention.
1. Enter a name for the job, and then select **Next**.
1. Select the date of the oldest retail transactions to archive ("From" date). Select the date of the newest retail transactions to archive ("To" date).
1. Select the legal entity (company) to archive the sales orders for.
1. Select **Next**.
1. Select the type of scheduling. Two types are supported:

    - **Single run** – Long-term retention and saving to history run continuously until both processes are completed. Data is always archived in Dataverse long-term retention first. Then the save to history tables occurs.
    - **Daily during allotted time** – The long-term retention runs continuously until it's completed. The **Save to history** process runs only during the specified start and stop archiving time.

1. On the last page of the wizard, confirm the details, and then select **Finish** to schedule the **Retail transactions archive ** job for the selected interval and company.

The archive jobs appear on the dashboard.
Refer the below image showing the Archive with Dataverse long term retention workspace with a completed archive job for retail
![Archive with Dataverse long term retention workspace for Retail](../media/Retail_LTR.png "Archive with Dataverse long term retention workspace for Retail")

## View the status of the long term retention job

Select **View progress** on the archival job dashboard to view job status details.

## View historical data

The **Archive with Dataverse long term retention** workspace shows the full archiving history. Each row in the grid shows information such as the date when the archive was created, the user who created it, and its status.

To view details about a selected archive, follow these steps.

1. Select the job, and then select **View history data** on the toolbar.
1. The **Archived retail transactions** page shows every retail transaction that's included in the archive job. 

## Tables that are archived with Retail long term retention job
- RetailTransactionTable
- RetailTransactionCashManagementTrans
- RetailTransactionFiscalCustomer
- RetailTransactionSupplementaryInvoice
- RetailTransactionTable_RU
- RetailTransactionBankedTenderTrans
- RetailTransactionValidationError
- RetailTransactionTenderDeclarationTrans
- RetailTransactionTaxMeasure
- RetailTransactionSalesTrans
- RetailTransactionPaymentTrans
- RetailTransactionPaymentTrans_BR
- RetailTransactionSafeTenderTrans
- RetailTransactionPaymentRefundableAmounts
- RetailTransactionAdditionalAddressTrans
- RetailTransactionAddressTrans
- RetailTransactionAffiliationTrans
- RetailTransactionAttributeTrans
- RetailTransactionChargeTaxMeasure
- RetailTransactionChargeTaxTrans
- RetailTransactionChargeTaxTransGTE
- RetailTransactionCustomerAccountDepositTrans
- RetailTransactionDiscountTrans
- RetailTransactionFiscalTrans
- RetailTransactionFiscalTransExtendedData
- RetailTransactionIncomeExpenseTrans
- RetailTransactionInfocodeTrans
- RetailTransactionKitsDisassemblyTrans
- RetailTransactionLoyaltyRewardPointTrans                          
- RetailTransactionMarkupTrans
- RetailTransactionNoteTrans
- RetailTransactionOrderInvoiceTrans
- RetailTransactionTaxTrans_IN
- RetailTransactionTaxTrans
- RetailTransactionTaxTransGTE
- RetailEodStatementControllerLog
- RetailEodStatementEventLog
- RetailEodTransactionAggregationHeader
- RetailEodTransactionAggregationTrans
- RetailEodTransactionError
- RetailEodTransactionBankedTenderTrans
- RetailEodTransactionIncomeExpenseTrans
- RetailEodTransactionInfocodeTrans
- RetailEodTransactionOrderInvoiceTrans
- RetailEodTransactionPaymentTrans
- RetailEodTransactionSafeTenderTrans
- RetailEodTransactionSalesTrans
- RetailEodTransactionTable
- RetailEodTransactionTenderDeclarationTrans
- RetailStatementJour
- RetailStatementTrans
- RetailStatementVoucher  

