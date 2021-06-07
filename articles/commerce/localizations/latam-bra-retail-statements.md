---
# required metadata
title: Posting fiscal documents in retail statements
description: This topic gives an overview of the functionality for posting Brazilian fiscal documents in retail statements.
author: v-ankvik
manager: epopov
ms.date: 02/15/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 


# optional metadata
# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
ms.search.industry: Retail
ms.author: v-ankvik
ms.search.validFrom: 2021-01-01
ms.dyn365.ops.version: 10.0.18

---

# Posting fiscal documents in retail statements 

[!include[banner](../includes/banner.md)]

## Introduction

All the NFC-es issued through the POS terminals can be viewed in Commerce headquarters through the **View XML message** form after running P-jobs and posting the retail statement. 

## Posting retail statement

The NFC-e issued on POS are posted into Commerce headquarters throughout the posting of open statements in Retail and Commerce module. The statements can contain both NFC-e as well NF-e transactions for returns. In order to post the NFC-e issued on POS do as follows:  
1. Open **Retail and Commerce > Retail and Commerce IT > Distribution schedule** menu.
1. Run **P-job** for the channel database.
1. Expand **Retail and Commerce > Retail and Commerce IT > POS posting** menu, and post a statement as follows: 
    - run **Validate store transactions** batch job,
    - then run **Calculate transactional statements in batch** batch job,
    - next run **Post transactional statements in batch**.
1.	Open **Retail and Commerce > Inquiries and reports > Posted statements** menu.  
1.	Verify that the statement has been posted.

> [!NOTE]
> The above steps perform trickle feed-based posting described in the article [Trickle feed-based order creation for retail store transactions](../trickle-feed.md). 

For more information, go to [Retail statements](../retail-statements.md). 

## View fiscal document details
 
1. In order to view the NFC-e after posting of the statement, open **Retail and Commerce > Inquires and reports > All fiscal documents** form. This form keeps the same user experience when viewing a fiscal document model 55 (Federal NF-e), showing header and lines and all its attributes. For more information, see [Fiscal documents and fiscal document framework for Brazil](../../finance/localizations/latam-bra-fiscal-documents-fiscal-document-framework.md) page. 
    > [!NOTE]
    > When viewed from Retail and Commerce module, this form **filters only the fiscal documents model 65**. The filter criteria should be changed to view returns having fiscal documents model 55. However, when viewed from General ledger module, the form All fiscal document shows all fiscal document models, including 55, 65, and at both       directions (incoming and outgoing).    
1. Check the **Status** column: the authorized fiscal documents must be **Approved** by the tax authority of the State.
1. Select the needed fiscal document(s), and click on the **XML document** menu under the **NF-e federal** tab.
1. Validate XML request and response that are available on the **NF-e** and **NF-e return** tabs of the **View XML message** form.
1. Validate XML request and response that are available on the **Cancel** tab of the **View XML message** form in case of Cancellation.