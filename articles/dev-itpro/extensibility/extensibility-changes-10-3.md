---
# required metadata

title: Extensibility changes in Dynamics 365 for Finance and Operations version 10.0.3
description: This topic lists the extensibility features that were released in Dynamics 365 for Finance and Operations version 10.0.3.
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

# Extensibility changes in Dynamics 365 for Finance and Operations version 10.0.3

[!include [banner](../includes/banner.md)]


This is a list of extensibility features that were implemented in Dynamics 365 for Finance and Operations version 10.0.3. For more information about the schedule of changes that support extensibility, see [Application extensibility plans](extensibility-roadmap.md).

## Enumerations made extensible

These enumerations have been made extensible in this update.

| Enumeration |
|---|
| LedgerJournalWFApprovalModule |
| RetailReceiptTransaction |


## SQL operations made extensible

These SQL operations have been made extensible in this update.

| Operations |
|---|
| CustVendTrans support for an extensible map pattern |

## Metadata changes

These metadata changes have been made in this update.

| Operations |
|---|
| CostSheetAmount.NoOfDecimalsIsExtensible |
| SalesLinePercent.NoOfDecimalsIsExtensible |

## Refactored methods

These methods have been refactored to support extensibility.

| Refactored methods |
|---|
| BankReconciliationDataInitializer.initDocumentOpenTmp |
| BankReconciliationDataInitializer.initStatementOpenTmp |
| Class\BomCalcJob_All.processSingleTask |
| Class\KanbanEventQuantityMap.newStandard |
| Class\MCRFullTextSearchRefresh.run |
| Class\PdsRebateAgreementValidate.validate |
| Class\PurchRFQFormLetter.main |
| Class\ReqTransPoMarkFirm.getPurchIdSingleThread |
| Class\TAMVendRebateCorrectClaims.correctClaims |
| Class\TAMVendRebateCorrectClaims.createClaimCorrection |
| Class\TAMVendRebateCorrectClaims.rebateAmountPerUnit |
| Class\WhsReleaseToWarehouseForm.buttonRelease_clicked |
| Classes\LedgerAllocationRules.ValidateDimension |
| Classes\ProjJournalCheckPost.checkFeeJournalDimensions |
| Commission_Sales.run |
| CreditcardPaymentCardTokenize.getFromDialog |
| CustInPaymDialog.openDialog |
| CustVendDisputeHelper.canDeleteDispute |
| EcoResCategoryTreeDatasource.new |
| EcoResProductRelationtable.validateWrite |
| Form\EcoResProductCreate.updateCallers |
| Form\InventOnhandReserve\DataSource\InventSum.reserveNow |
| Form\PdsRebateAgreement\DataSource\PdsRebateAgreement.executeQuery |
| Form\ProcCategoryHierarchyManagement\FormDesign\CategoryTreeGroup\CategoryTreeCtrl.selection |Changing
| Form\ReqSupplyDemandSchedule.updateDesign |
| Form\SalesTable\DataSource\MCRSalesLineDropShipment\field\DropShipment.modified |
| Form\SalesTable\DataSource\SalesTable.create |
| FormletterService.removeProforma |
| InventJournalTrans.validateWrite |
| InventJournalTrans_Tag.validateWrite |
| InventMovement.addLedgerPhysicalAmount |
| InventMovement.canAutoReserveQuantity |
| InventTransSerialNumberCreate.checkFormat |
| InventUpd_Reservation.updateReserveLess |
| LedgerJournalEngine.onSegmentChangedForPrimaryAccount |
| LedgerJournalTransCustPaym.enableDisableMandate |
| LedgerTransStatementDP.processOffsetAccountInStaging |
| PdsBatchAttribReserveForm.checkReserveLine |
| PriceDisc.findDiscAgreement |
| PriceDiscAdmCheckPost.postJournal |
| PriceDiscHeading.updateDiscQty |
| PriceDiscHeading.updateMultiLineDiscTmp |
| PriceDiscPolicyFindOrCreate.run |
| ProjInvoiceControl.projInvoiceControl |
| ProjPostCostJournal.new |
| PurchLineType.validateWrite |
| ReqTransFormExplosion.tmpReqExplosionOnhandBuildServer |
| ReqTransPoMarkFirm.createPurchTable |
| ReqTransPoMarkFirm.updatePurchBuyerGroup |
| RequisitionPurchaseOrderGeneration.createPurchaseOrder |
| RetailBarCodeManagement.CreateBarCodeNoDim |
| RetailTransactionServiceOrders.createCustomerOrder |
| RetailTransactionTransformer.readTransactionSalesTrans |
| SalesLine.createLine |
| SalesLine.initFromPriceDisc |
| SalesLine.insert |
| SalesLine.update |
| SalesLine.validateDelete |
| SalesLine.writeRetailSalesLine |
| SalesTable.updateMultiLineDisc |
| SmaServiceFunctionLine_transfer.Run |
| SmmOpportunityStatusUpdate.updateFromQuote |
| Table\MCRCustpaymTable.salesTableByPassCreditLimit, displayOrderID, getCurrency and  |mcrCustPaym\getCustomerPostingProfile
| Table\ReqPO.findAnySalesLineForReqPO |
| TaxUncommitted.createTaxUncommitted, local method  |createTaxUncommittedFromTmpTaxWorkTrans
| TmpTaxReport_IT.create |
| TrvExpTrans.defaultTaxGroupFromWorker |
| WHSBillOfLadingDP.insertWHSBillOfLadingTmp |
| WHSControlItemId.populate |
| WhsWarehouseRelease.creditLimitCheck |
| WhsWorkCreate.addRangesToWorkTemplateQuery |
| WHSWorkExecute.CreateTransferJournalLine |
| WhsWorkTypePrintHandler.buildLabelAndConfirm |

## Other extensibility enhancements

| Operations |
|---|
| Map PriceDiscHeading made extensible |
| Retail channel: Added pre-triggers for Shipped, PackingSlip and MarkAsPacked |
| Retail channel: Overridable Cancellation charge dialog. |
| Retail channel: Recall order default parameter value extension for search order dialogue |

