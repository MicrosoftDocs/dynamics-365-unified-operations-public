---
title: Purge Commerce transactions
description: Learn how to use the Purge Commerce sales transactions capability to delete old transactional data that's no longer needed in Microsoft Dynamics 365 Commerce.
author: shajain
ms.date: 10/24/2025
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2024-09-30
---

# Purge Commerce transactions

[!include [banner](../includes/banner.md)]

This article describes how to use the Purge Commerce sales transactions capability to delete old transactional data that is no longer needed in Microsoft Dynamics 365 Commerce.

Because the retention of large amounts of data in Commerce back end systems can increase data costs and affect system performance, organizations often want to remove outdated data. The Commerce version 10.0.42 release gives organizations the capability to delete old transactional data themselves. The **Purge commerce sales transactions** dialog is available in Commerce headquarters at **Retail and Commerce IT** \> **Clean up** \> **Purge commerce sales transactions**. However, it's hidden behind a flighting flag and organizations must contact the Microsoft Support team to enable the capability in their environments. In future Commerce releases, this capability is enabled by default in all environments.

Users who have the appropriate role can select a date range for the deletion of transactions regardless of their posting status. Currently, the date range is limited to a maximum of six months at a time, and both the start and end dates must be before the previous calendar year. For example, if the current year is 2024, both the start and end dates of the date range must be in 2022 or earlier.

> [!NOTE]
> As of Commerce version 10.0.42, this capability is only available to users who are assigned to the **Retail operations manager** role. However, because of the risks that are associated with irreversible transaction deletion, in later releases this capability is restricted to users who are assigned to the **Information technology officer** role.

The purge job runs as a batch job. There can be only one active job per legal entity. After the purge batch job is completed, the information log for the job shows details of the tables and record counts that were deleted. The purge job doesn't lock the tables that it deletes transactions from. Therefore, the system can continue to use those tables for other business processes.

The following image shows an example of the **Purge commerce sales transactions** dialog box, the navigation that is used to open it, and the details of the purge batch job that runs.

![Screenshot that shows the Purge commerce transactions dialog box, the navigation to it, and the details of the purge batch job.](media/Purge_commerce_transactions_1.png)

## Purge only log and error files

With Commerce version 10.0.46, Microsoft has enabled an additional configuration named **Only delete logs and error files** on the **Purge commerce sales transaction** dialog. If this configuration is enabled, then the system only deletes the log and error files that include the following files: 

- RetailEodStatementControllerLog
- RetailEodStatementEventLog
- RetailEodTransactionError

## Tables purged by the Purge commerce sales transactions job

If the **Only delete logs and error files** configuration isn't selected, then the **Purge Commerce sales transactions** job deletes the content from the following tables:

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

> [!NOTE]
> Two more tables (**RetailTransactionPriceTrans** and **RetailReceiptsContent**) will be added to the list in upcoming releases.


