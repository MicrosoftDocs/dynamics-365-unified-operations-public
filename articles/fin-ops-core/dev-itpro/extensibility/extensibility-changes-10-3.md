---
title: Extensibility changes in Dynamics 365 for Finance and Operations version 10.0.3
description: Learn about the extensibility features that were released in Microsoft Dynamics 365 for Finance and Operations version 10.0.3.
author: FrankDahl
ms.author: fdahl
ms.topic: article
ms.date: 06/14/2019
ms.custom:
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-05-10
ms.dyn365.ops.version: App 10.0
---

# Extensibility changes in Dynamics 365 for Finance and Operations version 10.0.3

[!include [banner](../includes/banner.md)]

This article lists the extensibility features that were implemented in Microsoft Dynamics 365 for Finance and Operations version 10.0.3. For more information about the schedule of changes that support extensibility, see [Application extensibility plans](extensibility-roadmap.md).

## Enumerations made extensible

The following enumerations have been made extensible in this update:

- LedgerJournalWFApprovalModule
- RetailReceiptTransaction

## SQL operations made extensible

The following SQL operations have been made extensible in this update:

- CustVendTrans support for an extensible map pattern

## Metadata changes

The following metadata changes have been made in this update:

- CostSheetAmount.NoOfDecimalsIsExtensible
- SalesLinePercent.NoOfDecimalsIsExtensible

## Refactored methods

The following methods have been refactored to support extensibility:

- BankReconciliationDataInitializer.initDocumentOpenTmp
- BankReconciliationDataInitializer.initStatementOpenTmp
- Class\\BomCalcJob\_All.processSingleTask
- Class\\KanbanEventQuantityMap.newStandard
- Class\\MCRFullTextSearchRefresh.run
- Class\\PdsRebateAgreementValidate.validate
- Class\\PurchRFQFormLetter.main
- Class\\ReqTransPoMarkFirm.getPurchIdSingleThread
- Class\\TAMVendRebateCorrectClaims.correctClaims
- Class\\TAMVendRebateCorrectClaims.createClaimCorrection
- Class\\TAMVendRebateCorrectClaims.rebateAmountPerUnit
- Class\\WhsReleaseToWarehouseForm.buttonRelease\_clicked
- Classes\\LedgerAllocationRules.ValidateDimension
- Classes\\ProjJournalCheckPost.checkFeeJournalDimensions
- Commission\_Sales.run
- CreditcardPaymentCardTokenize.getFromDialog
- CustInPaymDialog.openDialog
- CustVendDisputeHelper.canDeleteDispute
- EcoResCategoryTreeDatasource.new
- EcoResProductRelationtable.validateWrite
- Form\\EcoResProductCreate.updateCallers
- Form\\InventOnhandReserve\\DataSource\\InventSum.reserveNow
- Form\\PdsRebateAgreement\\DataSource\\PdsRebateAgreement.executeQuery
- Form\\ProcCategoryHierarchyManagement\\FormDesign\\CategoryTreeGroup\\CategoryTreeCtrl.selection
- Form\\ReqSupplyDemandSchedule.updateDesign
- Form\\SalesTable\\DataSource\\MCRSalesLineDropShipment\\field\\DropShipment.modified
- Form\\SalesTable\\DataSource\\SalesTable.create
- FormletterService.removeProforma
- InventJournalTrans.validateWrite
- InventJournalTrans\_Tag.validateWrite
- InventMovement.addLedgerPhysicalAmount
- InventMovement.canAutoReserveQuantity
- InventTransSerialNumberCreate.checkFormat
- InventUpd\_Reservation.updateReserveLess
- LedgerJournalEngine.onSegmentChangedForPrimaryAccount
- LedgerJournalTransCustPaym.enableDisableMandate
- LedgerTransStatementDP.processOffsetAccountInStaging
- PdsBatchAttribReserveForm.checkReserveLine
- PriceDisc.findDiscAgreement
- PriceDiscAdmCheckPost.postJournal
- PriceDiscHeading.updateDiscQty
- PriceDiscHeading.updateMultiLineDiscTmp
- PriceDiscPolicyFindOrCreate.run
- ProjInvoiceControl.projInvoiceControl
- ProjPostCostJournal.new
- PurchLineType.validateWrite
- ReqTransFormExplosion.tmpReqExplosionOnhandBuildServer
- ReqTransPoMarkFirm.createPurchTable
- ReqTransPoMarkFirm.updatePurchBuyerGroup
- RequisitionPurchaseOrderGeneration.createPurchaseOrder
- RetailBarCodeManagement.CreateBarCodeNoDim
- RetailTransactionServiceOrders.createCustomerOrder
- RetailTransactionTransformer.readTransactionSalesTrans
- SalesLine.createLine
- SalesLine.initFromPriceDisc
- SalesLine.insert
- SalesLine.update
- SalesLine.validateDelete
- SalesLine.writeRetailSalesLine
- SalesTable.updateMultiLineDisc
- SmaServiceFunctionLine\_transfer.Run
- SmmOpportunityStatusUpdate.updateFromQuote
- Table\\MCRCustpaymTable.salesTableByPassCreditLimit, displayOrderID, getCurrency, and mcrCustPaym\\getCustomerPostingProfile
- Table\\ReqPO.findAnySalesLineForReqPO
- TaxUncommitted.createTaxUncommitted, added local method createTaxUncommittedFromTmpTaxWorkTrans
- TmpTaxReport\_IT.create
- TrvExpTrans.defaultTaxGroupFromWorker
- WHSBillOfLadingDP.insertWHSBillOfLadingTmp
- WHSControlItemId.populate
- WhsWarehouseRelease.creditLimitCheck
- WhsWorkCreate.addRangesToWorkTemplateQuery
- WHSWorkExecute.CreateTransferJournalLine
- WhsWorkTypePrintHandler.buildLabelAndConfirm

## Other extensibility enhancements

- The PriceDiscHeading map was made extensible.
- **Retail channel:** Pre-triggers were added for Shipped, PackingSlip, and MarkAsPacked.
- **Retail channel:** The Cancellation charge dialog box can be overridden.
- **Retail channel:** Recall order default parameter value extension for the search order dialog box.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
