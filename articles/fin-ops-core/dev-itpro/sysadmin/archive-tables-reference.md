---
title: Archive table naming reference
description: Reference documentation showing how Microsoft-provided tables are named across live, history, finance and operations data entity, and Dataverse layers for each archive scenario.
author: kehoej99 
ms.author: Weijiesa 
ms.topic: reference
ms.date: 01/27/2026
ms.custom:
ms.reviewer: twheeloc

---
# Archive table naming reference

This reference shows how Microsoft-provided tables are named across the archive framework layers. Each row maps the same logical entity as it moves through the archive pipeline: from the live transaction table in Dynamics 365 finance and operations, to the history table, to the finance and operations data entity, and finally to the Dataverse-managed data lake table.

**Use this reference to:**
- Understand naming conventions across archive layers
- Look up corresponding table names when implementing customizations
- Verify entity names for your archive job contracts
- Map data between different storage layers

## Table naming conventions

| Layer | Naming Pattern | Example |
|-------|---------------|---------|
| Live table | Original F&O table name | `SALESTABLE` |
| History table | Live table + "History" suffix | `SALESTABLEHISTORY` |
| Finance and operations data entity | Live table + "BiEntity" suffix | `SalestableBiEntity` |
| Dataverse table | "mserp_" prefix + data entity name | `mserp_SalestableBiEntity` |

> [!NOTE]
> These finance and operations data entities use the "BiEntity" suffix in their technical names (for example, `SalestableBiEntity`). This naming convention identifies them as data entities specifically designed for archive and Dataverse integration.

## Supported scenarios

The following table lists all Microsoft-provided archive scenarios and their corresponding table names across each layer.

| Scenario | Live table | History table | Finance and operations data entity | Dataverse-managed data lake table |
|---|---|---|---|---|
| Finance General ledger | GENERALJOURNALACCOUNTENTRY | GENERALJOURNALACCOUNTENTRYHISTORY | GeneraljournalaccountentryBiEntity | mserp\_GeneraljournalaccountentryBiEntity |
| | GENERALJOURNALACCOUNTENTRY\_W | GENERALJOURNALACCOUNTENTRYHISTORY\_W | GeneraljournalaccountentrywBiEntity | mserp\_GeneraljournalaccountentrywBiEntity |
| | GENERALJOURNALENTRY | GENERALJOURNALENTRYHISTORY | GeneraljournalentryBiEntity | mserp\_GeneraljournalentryBiEntity |
| | GENERALJOURNALENTRY\_W | GENERALJOURNALENTRYHISTORY\_W | GeneraljournalentrywBiEntity | mserp\_GeneraljournalentrywBiEntity |
| | LEDGERCONSOLIDATEHISTREF | LEDGERCONSOLIDATEHISTREFHISTORY | LedgerconsolidatehistrefBiEntity | mserp\_LedgerconsolidatehistrefBiEntity |
| | LEDGERENTRY | LEDGERENTRYHISTORY | LedgerentryBiEntity | mserp\_LedgerentryBiEntity |
| | LEDGERENTRYJOURNAL | LEDGERENTRYJOURNALHISTORY | LedgerentryjournalBiEntity | mserp\_LedgerentryjournalBiEntity |
| | LEDGERENTRYJOURNALIZING | LEDGERENTRYJOURNALIZINGHISTORY | LedgerentryjournalizingBiEntity | mserp\_LedgerentryjournalizingBiEntity |
| | LEDGERTRANSSETTLEMENT | LEDGERTRANSSETTLEMENTHISTORY | LedgertranssettlementBiEntity | mserp\_LedgertranssettlementBiEntity |
| | SUBLEDGERVOUCHERGENERALJOURNALENTRY | SUBLEDGERVOUCHERGENERALJOURNALENTRYHISTORY | SubledgervouchergeneraljournalentryBiEntity |mserp\_SubledgervouchergeneraljournalentryBiEntity |
| Supply Chain Management Sales order | MCRRETURNSALESTABLE | MCRRETURNSALESTABLEHISTORY | McrreturnsalestableBiEntity | mserp\_McrreturnsalestableBiEntity |
| | MCRSALESLINE | MCRSALESLINEHISTORY | McrsaleslineBiEntity | mserp\_McrsaleslineBiEntity |
| | MCRSALESTABLE | MCRSALESTABLEHISTORY | McrsalestableBiEntity | mserp\_McrsalestableBiEntity |
| | RETAILSALESLINE | RETAILSALESLINEHISTORY | RetailsaleslineBiEntity | mserp\_RetailsaleslineBiEntity |
| | RETAILSALESTABLE | RETAILSALESTABLEHISTORY | RetailsalestableBiEntity | mserp\_RetailsalestableBiEntity |
| | SALESLINE | SALESLINEHISTORY | SaleslineBiEntity | mserp\_SaleslineBiEntity |
| | SALESLINE\_BR | SALESLINEHISTORY\_BR | SaleslinebrBiEntity | mserp\_SaleslinebrBiEntity |
| | SALESLINE\_IN | SALESLINEHISTORY\_IN | SaleslineinBiEntity | mserp\_SaleslineinBiEntity |
| | SALESLINE\_W | SALESLINEHISTORY\_W | SaleslinewBiEntity | mserp\_SaleslinewBiEntity |
| | SALESTABLE | SALESTABLEHISTORY | SalestableBiEntity | mserp\_SalestableBiEntity |
| | SALESTABLE\_BR | SALESTABLEHISTORY\_BR | SalestablebrBiEntity | mserp\_SalestablebrBiEntity |
| | SALESTABLE\_RU | SALESTABLEHISTORY\_RU | SalestableruBiEntity | mserp\_SalestableruBiEntity |
| | SALESTABLE\_W | SALESTABLEHISTORY\_W | SalestablewBiEntity | mserp\_SalestablewBiEntity |
| Supply Chain Management Inventory transaction | INVENTTRANSARCHIVE | INVENTTRANSARCHIVEHISTORY | InventtransarchiveBiEntity | mserp\_InventTransArchiveBiEntity |
| Supply Chain Management Inventory Journal | INVENTJOURNALTABLE | INVENTJOURNALTABLEHISTORY | InventjournaltableBiEntity | mserp\_InventjournaltableBiEntity |
| | INVENTJOURNALTABLE_IN | INVENTJOURNALTABLE_INHISTORY | InventjournaltableinBiEntity | mserp\_InventjournaltableinBiEntity |
| | INVENTJOURNALTRANS | INVENTJOURNALTRANSHISTORY | InventjournaltransBiEntity | mserp\_InventjournaltransBiEntity |
| | INVENTJOURNALTRANS_IN | INVENTJOURNALTRANS_INHISTORY | InventjournaltransinBiEntity | mserp\_InventjournaltransinBiEntity |
| Finance Tax Trans | TAXTRANS | TAXTRANSHISTORY | TaxtransBiEntity | mserp\_TaxtransBiEntity |
| | TAXTRANS\_BR | TAXTRANSHISTORY\_BR | TaxtransbrBiEntity | mserp\_TaxtransbrBiEntity |
| | TAXTRANSGENERALJOURNALACCOUNTENTRY | TAXTRANSGENERALJOURNALACCOUNTENTRYHISTORY | TaxtransgeneraljournalaccountentryBiEntity | mserp\_TaxtransgeneraljournalaccountentryBiEntity |
| | TAXTRANS\_IN | TAXTRANSHISTORY\_IN | TaxtransinBiEntity | mserp\_TaxtransinBiEntity |
| | TAXTRANS_IT | TAXTRANSHISTORY\_IT | TaxtransitBiEntity | mserp\_TaxtransitBiEntity |
| | TAXTRANS_REPORTING | TAXTRANSHISTORY_REPORTING | TaxtransreportingBiEntity | mserp\_TaxtransreportingBiEntity |
| | TAXTRANS\_RU | TAXTRANSHISTORY\_RU | TaxtransruBiEntity | mserp\_TaxtransruBiEntity |
| | TAXTRANSSUBLEDGERJOURNALACCOUNTENTRY | TAXTRANSSUBLEDGERJOURNALACCOUNTENTRYHISTORY | TaxtranssubledgerjournalaccountentryBiEntity | mserp\_TaxtranssubledgerjournalaccountentryBiEntity |
| | TAXTRANS\_TH | TAXTRANSHISTORY\_TH | TaxtransthBiEntity | mserp\_TaxtransthBiEntity |
| | TAXTRANS\_W | TAXTRANSHISTORY\_W | TaxtranswBiEntity | mserp\_TaxtranswBiEntity | 
| Commerce transaction | RetailTransactionTable | RetailTransactionTableHistory | RetailTransactionTableBIEntity | mserp\_RetailTransactionTableBIEntity |
| | RetailTransactionCashManagementTrans | RetailTransactionCashManagementTransHistory | RetailTransactionCashManagementTransBIEntity | mserp\_RetailTransactionCashManagementTransBIEntity |
| | RetailTransactionFiscalCustomer | RetailTransactionFiscalCustomerHistory | RetailTransactionFiscalCustomerBIEntity | mserp\_RetailTransactionFiscalCustomerBIEntity |
| | RetailTransactionSupplementaryInvoice | RetailTransactionSupplementaryInvoiceHistory | RetailTransactionSupplementaryInvoiceBIEntity | mserp\_RetailTransactionSupplementaryInvoiceBIEntity |
| | RetailTransactionTable\_RU | RetailTransactionTable\_RUHistory | RetailTransactionTable\_RUBIEntity | mserp\_RetailTransactionTable\_RUBIEntity |
| | RetailTransactionBankedTenderTrans | RetailTransactionBankedTenderTransHistory | RetailTransactionBankedTenderTransBIEntity | mserp\_RetailTransactionBankedTenderTransBIEntity |
| | RetailTransactionValidationError | RetailTransactionValidationErrorHistory | RetailTransactionValidationErrorBIEntity | mserp\_RetailTransactionValidationErrorBIEntity |
| | RetailTransactionTenderDeclarationTrans | RetailTransactionTenderDeclarationTransHistory | RetailTransactionTenderDeclarationTransBIEntity | mserp\_RetailTransactionTenderDeclarationTransBIEntity |
| | RetailTransactionTaxMeasure | RetailTransactionTaxMeasureHistory | RetailTransactionTaxMeasureBIEntity | mserp\_RetailTransactionTaxMeasureBIEntity |
| | RetailTransactionSalesTrans | RetailTransactionSalesTransHistory | RetailTransactionSalesTransBIEntity | mserp\_RetailTransactionSalesTransBIEntity |
| | RetailTransactionPaymentTrans | RetailTransactionPaymentTransHistory | RetailTransactionPaymentTransBIEntity | mserp\_RetailTransactionPaymentTransBIEntity |
| | RetailTransactionPaymentTrans\_BR | RetailTransactionPaymentTrans\_BRHistory | RetailTransactionPaymentTrans\_BRBIEntity | mserp\_RetailTransactionPaymentTrans\_BRBIEntity |
| | RetailTransactionSafeTenderTrans | RetailTransactionSafeTenderTransHistory | RetailTransactionSafeTenderTransBIEntity | mserp\_RetailTransactionSafeTenderTransBIEntity |
| | RetailTransactionPaymentRefundableAmounts | RetailTransactionPaymentRefundableAmountsHistory | RetailTransactionPaymentRefundableAmountsBIEntity | mserp\_RetailTransactionPaymentRefundableAmountsBIEntity |
| | RetailTransactionAdditionalAddressTrans | RetailTransactionAdditionalAddressTransHistory | RetailTransactionAdditionalAddressTransBIEntity | mserp\_RetailTransactionAdditionalAddressTransBIEntity |
| | RetailTransactionAddressTrans | RetailTransactionAddressTransHistory | RetailTransactionAddressTransBIEntity | mserp\_RetailTransactionAddressTransBIEntity |
| | RetailTransactionAffiliationTrans | RetailTransactionAffiliationTransHistory | RetailTransactionAffiliationTransBIEntity | mserp\_RetailTransactionAffiliationTransBIEntity |
| | RetailTransactionAttributeTrans | RetailTransactionAttributeTransHistory | RetailTransactionAttributeTransBIEntity | mserp\_RetailTransactionAttributeTransBIEntity |
| | RetailTransactionChargeTaxMeasure | RetailTransactionChargeTaxMeasureHistory | RetailTransactionChargeTaxMeasureBIEntity | mserp\_RetailTransactionChargeTaxMeasureBIEntity |
| | RetailTransactionChargeTaxTrans | RetailTransactionChargeTaxTransHistory | RetailTransactionChargeTaxTransBIEntity | mserp\_RetailTransactionChargeTaxTransBIEntity |
| | RetailTransactionChargeTaxTransGTE | RetailTransactionChargeTaxTransGTEHistory | RetailTransactionChargeTaxTransGTEBIEntity | mserp\_RetailTransactionChargeTaxTransGTEBIEntity |
| | RetailTransactionCustomerAccountDepositTrans | RetailTransactionCustomerAccountDepositTransHistory | RetailTransactionCustomerAccountDepositTransBIEntity | mserp\_RetailTransactionCustomerAccountDepositTransBIEntity |
| | RetailTransactionDiscountTrans | RetailTransactionDiscountTransHistory | RetailTransactionDiscountTransBIEntity | mserp\_RetailTransactionDiscountTransBIEntity |
| | RetailTransactionFiscalTrans | RetailTransactionFiscalTransHistory | RetailTransactionFiscalTransBIEntity | mserp\_RetailTransactionFiscalTransBIEntity |
| | RetailTransactionFiscalTransExtendedData | RetailTransactionFiscalTransExtendedDataHistory | RetailTransactionFiscalTransExtendedDataBIEntity | mserp\_RetailTransactionFiscalTransExtendedDataBIEntity |
| | RetailTransactionIncomeExpenseTrans | RetailTransactionIncomeExpenseTransHistory | RetailTransactionIncomeExpenseTransBIEntity | mserp\_RetailTransactionIncomeExpenseTransBIEntity |
| | RetailTransactionInfocodeTrans | RetailTransactionInfocodeTransHistory | RetailTransactionInfocodeTransBIEntity | mserp\_RetailTransactionInfocodeTransBIEntity |
| | RetailTransactionKitsDisassemblyTrans | RetailTransactionKitsDisassemblyTransHistory | RetailTransactionKitsDisassemblyTransBIEntity | mserp\_RetailTransactionKitsDisassemblyTransBIEntity |
| | RetailTransactionLoyaltyRewardPointTrans | RetailTransactionLoyaltyRewardPointTransHistory | RetailTransactionLoyaltyRewardPointTransBIEntity | mserp\_RetailTransactionLoyaltyRewardPointTransBIEntity |
| | RetailTransactionMarkupTrans | RetailTransactionMarkupTransHistory | RetailTransactionMarkupTransBIEntity | mserp\_RetailTransactionMarkupTransBIEntity |
| | RetailTransactionNoteTrans | RetailTransactionNoteTransHistory | RetailTransactionNoteTransBIEntity | mserp\_RetailTransactionNoteTransBIEntity |
| | RetailTransactionOrderInvoiceTrans | RetailTransactionOrderInvoiceTransHistory | RetailTransactionOrderInvoiceTransBIEntity | mserp\_RetailTransactionOrderInvoiceTransBIEntity |
| | RetailTransactionTaxTrans\_IN | RetailTransactionTaxTrans\_INHistory | RetailTransactionTaxTrans\_INBIEntity | mserp\_RetailTransactionTaxTrans\_INBIEntity |
| | RetailTransactionTaxTrans | RetailTransactionTaxTransHistory | RetailTransactionTaxTransBIEntity | mserp\_RetailTransactionTaxTransBIEntity |
| | RetailTransactionTaxTransGTE | RetailTransactionTaxTransGTEHistory | RetailTransactionTaxTransGTEBIEntity | mserp\_RetailTransactionTaxTransGTEBIEntity |
| | RetailEodStatementControllerLog | RetailEodStatementControllerLogHistory | RetailEodStatementControllerLogBIEntity | mserp\_RetailEodStatementControllerLogBIEntity |
| | RetailEodStatementEventLog | RetailEodStatementEventLogHistory | RetailEodStatementEventLogBIEntity | mserp\_RetailEodStatementEventLogBIEntity |
| | RetailEodTransactionAggregationHeader | RetailEodTransactionAggregationHeaderHistory | RetailEodTransactionAggregationHeaderBIEntity | mserp\_RetailEodTransactionAggregationHeaderBIEntity |
| | RetailEodTransactionAggregationTrans | RetailEodTransactionAggregationTransHistory | RetailEodTransactionAggregationTransBIEntity | mserp\_RetailEodTransactionAggregationTransBIEntity |
| | RetailEodTransactionError | RetailEodTransactionErrorHistory | RetailEodTransactionErrorBIEntity | mserp\_RetailEodTransactionErrorBIEntity |
| | RetailEodTransactionBankedTenderTrans | RetailEodTransactionBankedTenderTransHistory | RetailEodTransactionBankedTenderTransBIEntity | mserp\_RetailEodTransactionBankedTenderTransBIEntity |
| | RetailEodTransactionIncomeExpenseTrans | RetailEodTransactionIncomeExpenseTransHistory | RetailEodTransactionIncomeExpenseTransBIEntity | mserp\_RetailEodTransactionIncomeExpenseTransBIEntity |
| | RetailEodTransactionInfocodeTrans | RetailEodTransactionInfocodeTransHistory | RetailEodTransactionInfocodeTransBIEntity | mserp\_RetailEodTransactionInfocodeTransBIEntity |
| | RetailEodTransactionOrderInvoiceTrans | RetailEodTransactionOrderInvoiceTransHistory | RetailEodTransactionOrderInvoiceTransBIEntity | mserp\_RetailEodTransactionOrderInvoiceTransBIEntity |
| | RetailEodTransactionPaymentTrans | RetailEodTransactionPaymentTransHistory | RetailEodTransactionPaymentTransBIEntity | mserp\_RetailEodTransactionPaymentTransBIEntity |
| | RetailEodTransactionSafeTenderTrans | RetailEodTransactionSafeTenderTransHistory | RetailEodTransactionSafeTenderTransBIEntity | mserp\_RetailEodTransactionSafeTenderTransBIEntity |
| | RetailEodTransactionSalesTrans | RetailEodTransactionSalesTransHistory | RetailEodTransactionSalesTransBIEntity | mserp\_RetailEodTransactionSalesTransBIEntity |
| | RetailEodTransactionTable | RetailEodTransactionTableHistory | RetailEodTransactionTableBIEntity | mserp\_RetailEodTransactionTableBIEntity |
| | RetailEodTransactionTenderDeclarationTrans | RetailEodTransactionTenderDeclarationTransHistory | RetailEodTransactionTenderDeclarationTransBIEntity | mserp\_RetailEodTransactionTenderDeclarationTransBIEntity |
| | RetailStatementJour | RetailStatementJourHistory | RetailStatementJourBIEntity | mserp\_RetailStatementJourBIEntity |
| | RetailStatementTrans | RetailStatementTransHistory | RetailStatementTransBIEntity | mserp\_RetailStatementTransBIEntity |
| | RetailStatementVoucher | RetailStatementVoucherHistory | RetailStatementVoucherBIEntity | mserp\_RetailStatementVoucherBIEntity |

## Related content

- [Archive customization](archive-custom.md)
- [Add custom fields to Microsoft-managed tables](archive-custom-add-fields.md)
- [Add custom tables to standard scenarios](archive-custom-add-tables.md)
- [Build your own custom archive scenario](archive-custom-build-scenario.md)
