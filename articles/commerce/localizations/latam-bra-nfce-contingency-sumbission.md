---
# required metadata
title: Postponed registration of NFC-e issued in contingency mode
description: This topic gives an overview of the functionality for postponed registration of NFC-e issued in contingency mode.
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
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
ms.search.industry: Retail
ms.author: v-ankvik
ms.search.validFrom: 2021-01-01
ms.dyn365.ops.version: 10.0.18

---

# Postponed registration of NFC-e issued in contingency mode 

[!include[banner](../includes/banner.md)]

## Introduction

The NFC-e offline contingency mode must be used when the store internet connection is not available or if the SEFAZ authorization service is down. In this case POS generates NFC-e documents locally, and then these documents are transmitted to SEFAZ in some time.

All the NFC-es issued through the POS terminals can be viewed in Commerce headquarters through the **View XML message form** after running P-jobs and posting the retail statement. The NFC-es that was issued on POS in offline contingency mode can then be submitted for authorization through Commerce Headquarters. 

## View fiscal document details
 
In order to view the NFC-e in Commerce headquarters, open **Retail and Commerce > Inquires and reports > All fiscal documents** form. This form keeps the same user experience when viewing a fiscal document model 55 (Federal NF-e), showing header and lines and all its attributes. For more information, see [Fiscal documents and fiscal document framework for Brazil](../../finance/localizations/latam-bra-fiscal-documents-fiscal-document-framework.md) page. 

> [!NOTE]
> When viewed from Retail and Commerce module, this form **filters only the fiscal documents model 65**. The filter criteria should be changed to view returns having fiscal documents model 55. However, when viewed from General ledger module, the form All fiscal document shows all fiscal document models, including 55, 65, and at both directions (incoming and outgoing). 

> [!NOTE]
> When the NFC-e was issued and authorized in POS, the NFC-e status is shown as Approved. When the NFC-e was issued in offline contingency mode, its status is shown as Created, Rejected or RejectedNoFix. 

## Authorization of NFC-e issued in offline contingency mode

In order to authorize the NFC-e issued in offline contingency mode perform the following steps: 

1. Open **Accounts receivable > Fiscal documents > Electronic fiscal documents > Export/import NF-e process**  
   or **Retail and Commerce -> Retail and Commerce IT -> POS posting -> Export NFC-e documents** menu in case of using of the [Electronic invoicing add-on for Brazil](../../finance/localizations/e-invoicing-bra-get-started.md).
1. Once the export process is completed, check the **NFC-e authorization** status. Open **Retail and Commerce > Inquires and reports > All fiscal documents** menu. 
1. Check the **Status** column: the authorized sales must be **Approved** by the tax authority of the State.
