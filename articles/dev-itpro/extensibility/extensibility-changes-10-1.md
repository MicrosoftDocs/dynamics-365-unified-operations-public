---
# required metadata

title: Extensibility changes in Dynamics 365 for Finance and Operations version 10.0.1
description: This topic lists the extensibility features that were released in Dynamics 365 for Finance and Operations version 10.0.1.
author: FrankDahl
manager: AnnBe
ms.date: 05/10/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 


# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2019-05-10
ms.dyn365.ops.version: App 10.0

---

# Extensibility changes in Dynamics 365 for Finance and Operations version 10.0.1

[!include [banner](../includes/banner.md)]

This is a list of extensibility features that were implemented in Dynamics 365 for Finance and Operations version 10.0.1. For more information about the schedule of changes that support extensibility, see [Application extensibility plans](extensibility-roadmap.md).

## Enumerations made extensible

These enumerations have been made extensible in this update.

| Enumeration |
|---|
| ACOCostStatus_BR |
| ACOCostType_BR |
| ACOJournalType_BR|
| BankModuloCheck_NO |
| InventTransferOrderType_BR
| ProdJourType |
| ProjTransStatus |
| RetailLabelTypeBase |
| RetailLedgerBank |
| RetailTenderFunction |
| SalesPurchTrntype_BR |
| SMAGetPriceFrom |
| SMASubscriptionIndexChange |

## SQL operations made extensible

These SQL operations have been made extensible in this update.

| Operations |
|---|
| InventSumDelta.findInventSumDeltaInventSumFieldsAll |
| LedgerFiscalJournal changed to use QueryObject |
| TaxTransDP |

## Metadata changes

These metadata changes have been made in this update.

| Operations |
|---|
| Data Entities/WMSItemArrivalJournalLineEntity.IsPublic, PublicCollectionName, PublicEntityName |
| DataEntities/LedgerJournalNameEntity/Fields/voucherSeriesCode.Allow Edit; Allow Edit on Create |
| DataEntities/LedgerJournalNameEntity/Fields/VoucherSeriesCompanyId.AllowEdit |
| Enums\SalesStatus::Backorder, Delivered.Label |
| Extended Data Types/WeightBase.Scale |
| InventTransferOrders added form control group in grid |

## Refactored methods

These methods have been refactored to support extensibility.

| Refactored methods |
|---|
| AssetProposalDepreciation.run |
| BankStatementValidate.validateDate |
| Class\BankDocumentBankAccountTrans.loadSourceBuffer |
| Class\BankReconMatchingRuleAutoProcessor.doProcessMatchRule |
| Class\ProjJournalTransMapForm.initFromProjTable |
| Class\RetailEodStatementPaymentJournal.createPaymentJournalLine |
| Class\RetailKitAssemblyOrder.CreateOrUpdateBOMJournal |
| Class\RetailTransactionServiceOrders.createOrUpdateRetailOrderLines |
| Class\SalesInvoiceController.initReportName_IN |
| Class\SalesInvoiceJournalPost.endUpdate |
| Class\WrkCtrScheduler.loadRoute |
| CreditCard.mcrInitFromCustPaymTable |
| CreditcardProcess.mcrDoCapture |
| CreditCardProcess.mcrDoRefund |
| CreditCardProviderProcess.Submit |
| CustCollectionLetterCreate.skipCustomer |
| CustVendCheque.output |
| CustVendSumForPaym.run |
| EFDOCDanfe_BR.additionalInformationPageBreak |
| EfDocDANFEDP_BR.additionalInformationBox |
| ERDocuManagement.insertFile |
| ERFileDestinationAttachment.saveFile |
| ERFileDestinationBrowser.saveFile |
| Form\BankReconciliationWorksheet.Init |
| FreeTextInvoiceController.initReportName_IN |
| HcmWorkerTransition.createHcmWorker |
| InventCostClosingCancel_Init.createTasks |
| InventDimCtrl_Frm_OnHand.initFromCaller |
| InventMov_Jour_BOM.journalPostTrans |
| InventProcessGuideDisplayLicensePlateDetailsPageBuilder.generateItemInfoForLicensePlate |
| InventProcessGuideDisplayLocationDetailsPageBuilder.generateItemInfoForLocation |
| InventStockCardDP.createInventStockCardTmpLineDetail |
| InventTable.checkProjCategoryId |
| InventUpd_WHSReservation.updateReserveMore |
| JmgCalcApproveWeekView.initializeData |
| LedgerConsolidate.Run and getSelectedDimensionAttributes |
| LedgerFiscalJournalDP_IT.addStarsToTmpTable |
| LedgerFiscalJournalDP_IT.insertLedgerFiscalJournalTmp_IT |
| LedgerFiscalJournalDP_IT.insertLedgerFiscalJournalTmp_IT |
| LedgerFiscalJournalDP_IT.processReport |
| LedgerJournalTrans.checkAllowEditWhenCheckPrinted |
| LedgerJournalTransUpdateVend.pdateNow |
| LedgerVoucherTransList.First |
| LedgerVoucherTransList.next |
| MCRFullTextIndexField.tableIdFromEnum |
| MCRFullTextIndexField.viewFromTable |
| MCRInventSearch.searchProduct |
| McrPriceHistoryLine_Purch.initAndInsertRebate |
| PartyProvider.operatingUnitTypeToName |
| PdsRebateAgreementValidate.construct |
| POS_IssueLoyaltyCardView.NA |
| PriceDiscAdmCheckPostPriceDiscTableUpdater.formattedQueryValue |
| PriceDiscAdmTrans.checkItemRelation |
| ProjBudgetManager.deleteProjBudgetLinesWhenZeroAmount |
| ProjBudgetManager.updateProjBudgetLinesWithAmt |
| ProjHourCostPrice.psaFindCostPrice |
| ProjInvoiceProposalListPageInteraction.initializeQuery |
| ProjPostEmplProposalSale.new |
| ProjPostRevenueProposalSale.new |
| ProjTable.initProjectFromCustomerAndInvoice |
| ProjTransferPrice.findByContractResourceCategory, findTransferPrice, find |
| ProjValElementServer.addProjToResource |
| ProjValElementServer.deleteProjFromResource |
| PurchPackingSlipJournalPost.postMarkupOnTrans |
| PurchReqLine.setProjSalesPrice |
| PurchRFQSendJournalCreate.createOrUpdateRFQLine |
| ReqCalc.covCalcDim |
| ReqCalc.covCalcDim |
| ReqCalc.covCalcDim |
| RequisitionPurchaseOrderGeneration.create |
| RequisitionPurchaseOrderGeneration.create |
| Retail extension point in CRT to override the ValidateCartLineQuantityAndPriceSymbol method. |
| RetailCatalogProductAttributeFormHelper.addProductAttributeControls |
| RetailCreateSpecificLabel.makeLabel |
| RetailEodStatementCustomerOrderInvoiceController.run |
| RetailEodStatementPaymentJournal.ledgerBank2LedgerJournalACType |
| RetailEodStatementPaymentJournal.postPaymentJournalForOthers, postPaymentJournalForSales, | | createTenderedPaymentLines, createPaymentJournalLine |
| RetailEodTransactionTransformer.ReadTransactionHeader |
| RetailEodTransactionTransformer.setExtensionProperty |
| RetailEventNotificationAction.packingSlipCompletion |
| RetailMediaAssociationHelper.associateProduct |
| RetailProductPropertyManager.validateWriteOnInventModelGroupItem |
| RetailSMBSeedGenerator.AccountReceivable |
| RetailStatementPost.createPaymentLedgerTrans |
| RetailTransactionSalesTransMark.MarkTransactions |
| RetailTransactionServiceOrder.settleCustomerOrder |
| RetailTransactionServiceOrders.cancelCustomerOrder |
| RetailTransactionServiceOrders.createCustomerOrder |
| RetailTransactionServiceOrders.createLedgerJournalForStore |
| RetailTransactionServiceOrders.createOrUpdateRetailOrderHeader |
| RetailTransactionServiceOrders.createOrUpdateRetailOrderLines |
| RetailTransactionServiceTransactions.fillPaymentTransDetails |
| RetailTransactionServiceTransactions.fillRetailTransactionDetails |
| RetailTransactionServiceTransactions.fillSalesTransDetails |
| RetailTransactionServiceTransactions.getJournalListQuery |
| SalesCreateOrder.updateDeliveryAddress |
| SubledgerJournalizer.loadAccountingdistributionTmp |
| SubledgerJournalizer.recordSubledgerJourAccEntriesForRounding |
| SubledgerJournalizer.recordSubledgerJournalAccountEntries |
| Table\MCRContinuityScheduleLine.UpdateOtherLines |
| Tax1099SummaryHelper.populateTaxSummaryFromVendSettlementTax |
| TrvCreditCardTransactionEntity.validateWrite |
| TrvExpenses.initializePersonalAmount |
| TrvExpenses.updateFormVisibilityOnCategoryChange |
| TrvExpenses.updateItemizationControls |
| TrvExpTrans.copyValueToChildLines |
| TrvExpTrans.defaultTaxGroupFromWorker |
| TrvExpTrans.modifiedField |
| TsTimesheetSignOffDP.insertTmpTSTimesheetSignOff |
| WHSBillOfLadingDataUtil.populateCarrierInformation |
| WHSBillOfLadingDataUtil.populateCustomerOrderInfo |
| WHSLoadPlanningWorkbenchServerForm.addLoadLinesToLoad |
| WHSLocationDirective.getValidSellableDaysQty |
| WHSMobileAppAttachedImageDetails.getImageTypeFromSymbol |
| WhsPostPackingSlip.updatePurchaseLoadLines |
| WhsPostPackingSlip.updatePurchParmLineQuantityData |
| WhsWarehouseRelease.main |
| WhsWorkManualComplete.executeWorkLines |
| WhsWorkManualComplete.performValidation |
| WorkTimeCheckClassWorkCalendarDateLineTableWorkTimeLineTable.whole class, validateWrite(), | | validateWrite() |
| WorkTimeLine.createWorkTimeCheck |

## Other extensibility enhancements
| Operations |
|---|
| Retail channel: Allow extensions to support Select all and Clear all in order fulfillment view. |
| Retail channel: Expose Add Return line to cart from transaction API by line id. |
| Retail channel: OrderFulfillmentView ability to view line item locations |
| Retail channel: OrderFulfillmentView adding ICustomListColumn to allow for more information |
| Retail statement posting method adds another aggregation by new table RetailTransactionAggregationFieldList for adding additional fields |

