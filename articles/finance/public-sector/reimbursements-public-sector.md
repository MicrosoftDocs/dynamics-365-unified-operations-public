---
title: Reimbursements in the public sector
description: This article answers common questions related to reimbursements in the public sector.
author: JodiChristiansen
ms.date: 11/02/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: jchrist
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9d61d1d8-1672-4bd0-ae0d-605b09240890
ms.search.industry: Public sector
ms.search.form: CustBillingClassification
---

# Reimbursements in the public sector

[!include [banner](../includes/banner.md)]

This article answers common questions related to reimbursements in the public sector. 

## How do billing classifications affect reimbursements for overpayments?
They don’t. Billing classifications are never applied to customer payments, so they aren’t used when processing reimbursements for overpayments.

## Can I process a reimbursement for a customer who has outstanding debit transactions?
Yes. If you need to process a reimbursement for a customer with outstanding debit transactions, use the filters on the reimbursement page to select the customer, and select the option to include customers with outstanding debit transactions. When you do this, reimbursement transactions are created for the full amount of all of the customer’s credit transactions. The outstanding debit amounts are not deducted from the credit amounts.

## Can I process reimbursements for customers who have pending settlements?
No. Reimbursements are not processed for any customer who has pending settlements that have not been posted to the journal.

## Can I reverse reimbursement settlements?
No, not directly. However, you could use general journal entries to create transactions that would have the effect of reversing the general ledger entries.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
