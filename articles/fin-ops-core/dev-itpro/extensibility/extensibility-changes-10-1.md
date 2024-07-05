---
title: Extensibility changes in Dynamics 365 for Finance and Operations version 10.0.1
description: Learn about the extensibility features that were released in Microsoft Dynamics 365 for Finance and Operations version 10.0.1.
author: FrankDahl
ms.author: fdahl
ms.topic: article
ms.date: 05/10/2019
ms.custom:
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-05-10
ms.dyn365.ops.version: App 10.0
---

# Extensibility changes in Dynamics 365 for Finance and Operations version 10.0.1

[!include [banner](../includes/banner.md)]

This article lists the extensibility features that were implemented in Microsoft Dynamics 365 for Finance and Operations version 10.0.1. For more information about the schedule of changes that support extensibility, see [Application extensibility plans](extensibility-roadmap.md).

## Enumerations made extensible

The following enumerations have been made extensible in this update:

- ACOCostStatus\_BR
- ACOCostType\_BR
- ACOJournalType\_BR
- BankModuloCheck\_NO
- InventTransferOrderType\_BR
- ProdJourType
- ProjTransStatus
- RetailLabelTypeBase
- RetailLedgerBank
- RetailTenderFunction
- SalesPurchTrntype\_BR
- SMAGetPriceFrom
- SMASubscriptionIndexChange

## SQL operations made extensible

The following SQL operations have been made extensible in this update:

- InventSumDelta.findInventSumDeltaInventSumFieldsAll.
- LedgerFiscalJournal was changed so that it uses QueryObject.
- TaxTransDP.

## Metadata changes

The following metadata changes have been made in this update:

- Data Entities/WMSItemArrivalJournalLineEntity.IsPublic, PublicCollectionName, PublicEntityName.
- DataEntities/LedgerJournalNameEntity/Fields/voucherSeriesCode.Allow Edit, Allow Edit on Create.
- DataEntities/LedgerJournalNameEntity/Fields/VoucherSeriesCompanyId.AllowEdit.
- Enums\\SalesStatus::Backorder, Delivered.Label.
- Extended Data Types/WeightBase.Scale.
- InventTransferOrders added a form control group in the grid.

## Refactored methods

The following methods have been refactored to support extensibility:

- AssetProposalDepreciation.run
- BankStatementValidate.validateDate
- Class\\BankDocumentBankAccountTrans.loadSourceBuffer
- Class\\BankReconMatchingRuleAutoProcessor.doProcessMatchRule
- Class\\ProjJournalTransMapForm.initFromProjTable
- Class\\RetailEodStatementPaymentJournal.createPaymentJournalLine
- Class\\RetailKitAssemblyOrder.CreateOrUpdateBOMJournal
- Class\\RetailTransactionServiceOrders.createOrUpdateRetailOrderLines
- Class\\SalesInvoiceController.initReportName\_IN
- Class\\SalesInvoiceJournalPost.endUpdate
- Class\\WrkCtrScheduler.loadRoute
- CreditCard.mcrInitFromCustPaymTable
- CreditcardProcess.mcrDoCapture
- CreditCardProcess.mcrDoRefund
- CreditCardProviderProcess.Submit
- CustCollectionLetterCreate.skipCustomer
- CustVendCheque.output
- CustVendSumForPaym.run
- EFDOCDanfe\_BR.additionalInformationPageBreak
- EfDocDANFEDP\_BR.additionalInformationBox
- ERDocuManagement.insertFile
- ERFileDestinationAttachment.saveFile
- ERFileDestinationBrowser.saveFile
- Form\\BankReconciliationWorksheet.Init
- FreeTextInvoiceController.initReportName\_IN
- HcmWorkerTransition.createHcmWorker
- InventCostClosingCancel\_Init.createTasks
- InventDimCtrl\_Frm\_OnHand.initFromCaller
- InventMov\_Jour\_BOM.journalPostTrans
- InventProcessGuideDisplayLicensePlateDetailsPageBuilder.generateItemInfoForLicensePlate
- InventProcessGuideDisplayLocationDetailsPageBuilder.generateItemInfoForLocation
- InventStockCardDP.createInventStockCardTmpLineDetail
- InventTable.checkProjCategoryId
- InventUpd\_WHSReservation.updateReserveMore
- JmgCalcApproveWeekView.initializeData
- LedgerConsolidate.Run and getSelectedDimensionAttributes
- LedgerFiscalJournalDP\_IT.addStarsToTmpTable
- LedgerFiscalJournalDP\_IT.insertLedgerFiscalJournalTmp\_IT
- LedgerFiscalJournalDP\_IT.insertLedgerFiscalJournalTmp\_IT
- LedgerFiscalJournalDP\_IT.processReport
- LedgerJournalTrans.checkAllowEditWhenCheckPrinted
- LedgerJournalTransUpdateVend.pdateNow
- LedgerVoucherTransList.First
- LedgerVoucherTransList.next
- MCRFullTextIndexField.tableIdFromEnum
- MCRFullTextIndexField.viewFromTable
- MCRInventSearch.searchProduct
- McrPriceHistoryLine\_Purch.initAndInsertRebate
- PartyProvider.operatingUnitTypeToName
- PdsRebateAgreementValidate.construct
- POS\_IssueLoyaltyCardView.NA
- PriceDiscAdmCheckPostPriceDiscTableUpdater.formattedQueryValue
- PriceDiscAdmTrans.checkItemRelation
- ProjBudgetManager.deleteProjBudgetLinesWhenZeroAmount
- ProjBudgetManager.updateProjBudgetLinesWithAmt
- ProjHourCostPrice.psaFindCostPrice
- ProjInvoiceProposalListPageInteraction.initializeQuery
- ProjPostEmplProposalSale.new
- ProjPostRevenueProposalSale.new
- ProjTable.initProjectFromCustomerAndInvoice
- ProjTransferPrice.findByContractResourceCategory, findTransferPrice, find
- ProjValElementServer.addProjToResource
- ProjValElementServer.deleteProjFromResource
- PurchPackingSlipJournalPost.postMarkupOnTrans
- PurchReqLine.setProjSalesPrice
- PurchRFQSendJournalCreate.createOrUpdateRFQLine
- ReqCalc.covCalcDim
- ReqCalc.covCalcDim
- ReqCalc.covCalcDim
- RequisitionPurchaseOrderGeneration.create
- RequisitionPurchaseOrderGeneration.create
- Retail extension point in the Commerce runtime (CRT) to override the ValidateCartLineQuantityAndPriceSymbol method
- RetailCatalogProductAttributeFormHelper.addProductAttributeControls
- RetailCreateSpecificLabel.makeLabel
- RetailEodStatementCustomerOrderInvoiceController.run
- RetailEodStatementPaymentJournal.ledgerBank2LedgerJournalACType
- RetailEodStatementPaymentJournal.postPaymentJournalForOthers, postPaymentJournalForSales, createTenderedPaymentLines, createPaymentJournalLine
- RetailEodTransactionTransformer.ReadTransactionHeader
- RetailEodTransactionTransformer.setExtensionProperty
- RetailEventNotificationAction.packingSlipCompletion
- RetailMediaAssociationHelper.associateProduct
- RetailProductPropertyManager.validateWriteOnInventModelGroupItem
- RetailSMBSeedGenerator.AccountReceivable
- RetailStatementPost.createPaymentLedgerTrans
- RetailTransactionSalesTransMark.MarkTransactions
- RetailTransactionServiceOrder.settleCustomerOrder
- RetailTransactionServiceOrders.cancelCustomerOrder
- RetailTransactionServiceOrders.createCustomerOrder
- RetailTransactionServiceOrders.createLedgerJournalForStore
- RetailTransactionServiceOrders.createOrUpdateRetailOrderHeader
- RetailTransactionServiceOrders.createOrUpdateRetailOrderLines
- RetailTransactionServiceTransactions.fillPaymentTransDetails
- RetailTransactionServiceTransactions.fillRetailTransactionDetails
- RetailTransactionServiceTransactions.fillSalesTransDetails
- RetailTransactionServiceTransactions.getJournalListQuery
- SalesCreateOrder.updateDeliveryAddress
- SubledgerJournalizer.loadAccountingdistributionTmp
- SubledgerJournalizer.recordSubledgerJourAccEntriesForRounding
- SubledgerJournalizer.recordSubledgerJournalAccountEntries
- Table\\MCRContinuityScheduleLine.UpdateOtherLines
- Tax1099SummaryHelper.populateTaxSummaryFromVendSettlementTax
- TrvCreditCardTransactionEntity.validateWrite
- TrvExpenses.initializePersonalAmount
- TrvExpenses.updateFormVisibilityOnCategoryChange
- TrvExpenses.updateItemizationControls
- TrvExpTrans.copyValueToChildLines
- TrvExpTrans.defaultTaxGroupFromWorker
- TrvExpTrans.modifiedField
- TsTimesheetSignOffDP.insertTmpTSTimesheetSignOff
- WHSBillOfLadingDataUtil.populateCarrierInformation
- WHSBillOfLadingDataUtil.populateCustomerOrderInfo
- WHSLoadPlanningWorkbenchServerForm.addLoadLinesToLoad
- WHSLocationDirective.getValidSellableDaysQty
- WHSMobileAppAttachedImageDetails.getImageTypeFromSymbol
- WhsPostPackingSlip.updatePurchaseLoadLines
- WhsPostPackingSlip.updatePurchParmLineQuantityData
- WhsWarehouseRelease.main
- WhsWorkManualComplete.executeWorkLines
- WhsWorkManualComplete.performValidation
- WorkTimeCheckClassWorkCalendarDateLineTableWorkTimeLineTable class, validateWrite()
- WorkTimeLine.createWorkTimeCheck

## Other extensibility enhancements

- **Retail channel:** Allow for extensions to support Select all and Clear all in OrderFulfillmentView.
- **Retail channel:** Expose Add return line to cart from the transaction application programming interface (API) by line ID.
- **Retail channel:** Line item locations can be viewed in OrderFulfillmentView.
- **Retail channel:** OrderFulfillmentView adds ICustomListColumn to allow for more information.
- Retail statement posting method adds another aggregation view by using the new RetailTransactionAggregationFieldList table that adds additional fields.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
