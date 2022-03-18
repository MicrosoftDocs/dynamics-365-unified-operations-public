---
title: Extensibility changes in Dynamics 365 for Finance and Operations update 8.0.2
description: This topic lists the extensibility features that were released in Dynamics 365 for Finance and Operations update 8.0.2.
author: FrankDahl
ms.date: 06/21/2018
ms.topic: article
ms.prod: 
ms.technology: 


# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2018-06-30
ms.dyn365.ops.version: App 8.0.2

---

# Extensibility changes in Dynamics 365 for Finance and Operations update 8.0.2

[!include [banner](../includes/banner.md)]

This is a list of extensibility features that were implemented in Dynamics 365 for Finance and Operations update 8.0.2. For more information about the schedule of changes that support extensibility, see [Application extensibility plans](extensibility-roadmap.md).

## Refactored methods to support extensibility

These methods have been refactored to support extensibility through chain of command, delegates, or by providing access to members.

| Method|
| --------------- |
|AccDistProcessorProjectExtension.allocateExistingDistribution|
|AccDistProcessorProjectExtension.createDistributionLists|
|AccDistProcessorProjectExtension.ledgerDimensionAllocationList|
|AgreementConfirmationDP.processReport|
|Bank_FR.checkControlText|
|Bank_IT.checkCIN|
|Bank_IT.checkRegistrationNum|
|CustVendCheque.initTmpChequePrintout|
|FBSpedFileCreator_Contabil_BR.createRecordI052|
|HierarchyTemplateCopying_proj.createFromHierarchySource|
|HierarchyTreeLookup.datasource smmActivities.init|
|InventDim.validateFieldCombination|
|InventTransWMS_Register|
|InventUpd_Financial.updateFinancialIssue|
|InventUpd_Registered|
|JmgPostStandardSystem.PostProjTime|
|MarkupAllocation.run|
|MarkupTrans. MarkupTrans(datasource).active|
|PdsBatchAttribByItem.checkDuplicateAttributes|
|PdsBatchAttribByItem.validateFieldValue|
|PdsBatchAttribReserve.linkActive|
|PdsBatchAttributes.Datasource.PdsBatchAttributes.linkactive|
|ProjInvoiceProposalCreateLines.closeOK|
|ProjInvoiceProposalInsertLines.doCost|
|ProjInvoiceProposalInsertLines.doEmpl|
|ProjInvoiceProposalInsertLines.doItem|
|ProjInvoiceProposalInsertLines.doOnAccount|
|ProjPeriodPostingLedgerSales.enteItem|
|ProjPeriodPostingLedgerSales.enterCost|
|ProjPeriodPostingLedgerSales.enterEmpl|
|ProjPeriodPostingLedgerSales.enterRevenue|
|ProjPeriodPostingLedgerSales.run|
|ProjPlanVersionsManager.CopyHierarchy|
|ProjPlanVersionsManager::copyHierarchy|
|ProjPlanVersionsManager::createDraftVersion|
|ProjPlanVersionsManager::createTemplateHierarchy|
|PurchAutoCreate_PurchReq.initializeAndCreatePurchLine|
|PurchOrderLineSourceDocumentLineItem.calculateSourceDocumentAmountMap|
|PurchRFQPriceDiscAdmCreate.createPriceDiscAdmTrans|
|SalesFormLetter.validate|
|SalesTable2LineUpdatePrompt.salesTableFieldModifiedHandler|
|SalesUpdateRemain.cancelOpenOrderLinesDeliveryRemainder|
|WHSShipmentTable.createShipmentNotes|
|WHSUnShipLoadLineTmpDataCreator.createTmpLoadLineInventoryFromContainerLines|

## Additional extensibility enhancements

In addition to the refactored methods, the following extensibility enhancements have been made.

- Support for extensions to map: CustVendTrans
- Support for extensions to map: CustVendTransOpen
- Support extensibility for SQL statement:  PriceDiscAdmCheckPost.postJournal


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]