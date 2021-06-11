---
# required metadata
title: Postponed registration of NFC-e documents issued in offline contingency mode
description: This topic gives an overview of the functionality for postponed registration of NFC-e documents issued in contingency mode in Microsoft Dynamics 365 Commerce POS.
author: v-ankvik
manager: annbe
ms.date: 06/10/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 


# optional metadata
# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
ms.search.industry: Retail
ms.author: v-ankvik
ms.search.validFrom: 2021-01-01
ms.dyn365.ops.version: 10.0.18

---

# Postponed registration of NFC-e documents issued in offline contingency mode 

[!include[banner](../includes/banner.md)]

This topic gives an overview of the functionality for postponed registration of NFC-e (Nota Fiscal do Consumidor eletrônica) documents issued in contingency mode in Microsoft Dynamics 365 Commerce POS.

The NFC-e offline contingency mode must be used when a store internet connection is not available or if the SEFAZ (Secretaria de Estado de Fazenda) authorization service is down. When in offline contingency mode, the POS generates NFC-e documents locally and these documents are then transmitted to SEFAZ at a later time.

All NFC-e documents issued through POS terminals can be viewed in Commerce headquarters on the View XML message form after running P-jobs and posting the retail statement. The NFC-es that was issued on POS in offline contingency mode can then be submitted for authorization through Commerce headquarters. 

## View fiscal document details

To view an NFC-e document in Commerce headquarters, go to **Retail and Commerce \> Inquires and reports \> All fiscal documents**. The **All fiscal documents** form displays the same format seen when viewing a NF-e fiscal document model 55, showing the header, lines, and all attributes. For more information, see [Fiscal documents and fiscal document framework for Brazil](../../finance/localizations/latam-bra-fiscal-documents-fiscal-document-framework.md). 

> [!NOTE]
> - When viewed in Commerce headquarters, by default the **All fiscal documents** form only lists NFC-e model 65 fiscal documents. To view returns having NFC-e model 55 fiscal documents, the filter criteria must be changed. However, when viewed from **General ledger** module, the **All fiscal documents** form lists all incoming and outgoing fiscal document models, including model 55 and model 65. 
> - If the NFC-e document was issued and authorized in POS, the NFC-e status is shown as **Approved**. If the NFC-e document was issued in offline contingency mode, its status is shown as **Created**, **Rejected**, or **RejectedNoFix**. 
## Authorize NFC-e documents issued in offline contingency mode

To authorize an NFC-e document issued in offline contingency mode, follow these steps in Commerce headquarters. 

1. Go to **Accounts receivable \> Fiscal documents \> Electronic fiscal documents \> Export/import NF-e process**. If using the [Electronic invoicing add-on for Brazil](../../finance/localizations/e-invoicing-bra-get-started.md), go to **Retail and Commerce \> Retail and Commerce IT \> POS posting \> Export NFC-e documents**.  
1. Once the export process is completed, check the **NFC-e authorization** status by going to **Retail and Commerce > Inquires and reports > All fiscal documents**. The **Status** column will display **Approved** for sales authorized by the tax authority of the state.

## Additional resources

[Set up and deploy Commerce localization for Brazil](latam-bra-deployment.md) 

[Commerce localization for Brazil](latam-bra-commerce-localization.md) 

[NFC-e fiscal document functionality in Commerce POS for Brazil](latam-bra-nfce.md)

[Manage customer information in POS for Brazil](latam-bra-customer-information.md)

[Cancellation and return of NFC-e documents in Commerce POS for Brazil](latam-bra-nfce-cancel-return.md)

[Post Brazilian fiscal documents via retail statements in Commerce headquarters](latam-bra-retail-statements.md)
