---
title: Advanced bank reconciliation overview
description: Learn about the flow for the advanced bank reconciliation process, which lets you import bank statements automatically reconciled from within bank transactions.
author: EricWangChen
ms.author: wangchen
ms.topic: overview
ms.date: 1/16/2024
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: BankReconciliationMatchRule
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: b0705653-1fa6-4d94-9728-bcf9fb387ad1
---

# Advanced bank reconciliation overview

[!include [banner](../includes/banner.md)]

This article describes the flow for the advanced bank reconciliation process. The advanced bank reconciliation feature lets you import bank statements that can be automatically reconciled from within bank transactions.

The advanced bank reconciliation feature lets you import bank statements. The imported bank statement can then be automatically reconciled from within bank transactions. Here are the steps in the advanced bank reconciliation flow.

1. Set up a bank statement import.

    - Import bank statements through the data entity framework.
    - Three typical bank statement formats are built in: ISO20022, BAI2, and MT940.
    - The functionality can be extended to any format.

1. Set up a number sequence to use for advanced bank reconciliation, and define the bank reconciliation matching rules.

    - A reconciliation matching rule is a set of criteria that are used to filter bank statement lines and Microsoft Dynamics 365 Finance bank transaction lines during the reconciliation process. Depending on your business practice, you can set up more than one matching rule to automate and optimize your reconciliation process.

1. Reconcile bank statements with Finance bank transactions.

    - Perform automatic matching and creation of reconciliation journals.
    - View bank statements and Finance bank transactions side by side.
    - Automatically post Finance bank transactions if they appear on a bank statement but don't appear in the Finance app.
    - Generate a reconciliation statement.

> [!NOTE]
> As of the 10.0.39 release, a new feature that's named **Modern bank reconciliation** enhances the capabilities in advanced bank reconciliation. Because modern bank reconciliation is in preview in Finance version 10.0.39, the objects and code that this feature introduces are subject to change before the feature goes to general availability (GA). Therefore, to help provide a better functional experience and address feedback from users, breaking changes might be introduced. The expectation is that the following classes, forms, and tables won't be customized.
> 
> **Classes:**
>
> - BankReconciliationHeaderReconcileDP
> - BankReconciliationHeaderUnreconDP
> - BankReconciliationLineReconcileDP
> - BankReconciliationLineUnreconDP
>
> **Forms:**
>
> - BankAutomationReconciliationWorksheet
> - BankAutomationStatementForm
> - BankAutomationStatementGenerateVoucherDialog
> - BankAutomationStatementMatchingRelationPreviewFormPart
> - BankAutomationStatementStatusStatisticsCardFormPart
> - BankAutomationStatementUnmatchedCardFormPart
> - BankStatementLineDetails
> - BankBridgingInquiryV2
>
> **Tables:**
>
> - BankReconciliationElectronicReportDocumentTmp
> - BankReconciliationElectronicReportStatementTmp

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
