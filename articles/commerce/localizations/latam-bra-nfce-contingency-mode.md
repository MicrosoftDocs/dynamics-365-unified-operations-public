---
title: Postponed registration of NFC-e documents issued in offline contingency mode
description: This article gives an overview of the functionality for postponed registration of NFC-e documents that are issued in Microsoft Dynamics 365 Commerce point of sale (POS) in contingency mode.
author: EvgenyPopovMBS
ms.date: 06/10/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Brazil
ms.author: josaw
ms.search.validFrom: 2021-01-01
ms.dyn365.ops.version: 10.0.18
ms.search.industry: Retail
---

# Postponed registration of NFC-e documents issued in offline contingency mode

[!include[banner](../includes/banner.md)]

This article gives an overview of the functionality for postponed registration of NFC-e (Nota Fiscal do Consumidor eletrônica) documents that are issued in Microsoft Dynamics 365 Commerce point of sale (POS) in contingency mode.

The NFC-e offline contingency mode must be used when a store's internet connection isn't available, or when the SEFAZ (Secretaria de Estado de Fazenda) authorization service is down. In offline contingency mode, POS locally generates NFC-e documents. Those documents are then transmitted to SEFAZ later.

All NFC-e documents that are issued through POS terminals can be viewed on the **View XML message** page in Commerce headquarters after P-jobs are run and the retail statement is posted. The NFC-e documents that were issued in POS in offline contingency mode can then be submitted for authorization through Commerce headquarters.

## View fiscal document details

To view an NFC-e document in Commerce headquarters, go to **Retail and Commerce \> Inquiries and reports \> All fiscal documents**. The **All fiscal documents** page shows the same format that is shown when you view an NF-e model 55 fiscal document. It includes the header, lines, and all attributes. For more information, see [Fiscal documents and fiscal document framework for Brazil](../../finance/localizations/latam-bra-fiscal-documents-fiscal-document-framework.md).

> [!NOTE]
> - By default, if you open the **All fiscal documents** page in Commerce headquarters, it lists only NFC-e model 65 fiscal documents. To view returns that have NFC-e model 55 fiscal documents, you must change the filter criteria. However, if you open the **All fiscal documents** page in the **General ledger** module, it lists all incoming and outgoing fiscal document models, including model 55 and model 65.
> - If the NFC-e document was issued and authorized in POS, its status is shown as **Approved**. If the NFC-e document was issued in offline contingency mode, its status is shown as **Created**, **Rejected**, or **RejectedNoFix**.

## Authorize NFC-e documents that were issued in offline contingency mode

To authorize an NFC-e document that was issued in offline contingency mode, follow these steps in Commerce headquarters.

1. Follow one of these steps:

    - Go to **Accounts receivable \> Fiscal documents \> Electronic fiscal documents \> Export/import NF-e process**.
    - If you're using the [Electronic invoicing add-on for Brazil](../../finance/localizations/e-invoicing-bra-get-started.md), go to **Retail and Commerce \> Retail and Commerce IT \> POS posting \> Export NFC-e documents**.

1. After the export process is completed, review the NFC-e authorization status by going to **Retail and Commerce \> Inquiries and reports \> All fiscal documents**. For sales that have been authorized by the state's tax authority, the **Status** field will be set to **Approved**.

## Additional resources

[Set up and deploy Commerce localization for Brazil](latam-bra-deployment.md)

[Commerce localization for Brazil](latam-bra-commerce-localization.md)

[NFC-e fiscal document functionality in Commerce POS for Brazil](latam-bra-nfce.md)

[Manage customer information in POS for Brazil](latam-bra-customer-information.md)

[Cancellation and return of NFC-e documents in Commerce POS for Brazil](latam-bra-nfce-cancel-return.md)

[Post Brazilian fiscal documents via retail statements in Commerce headquarters](latam-bra-retail-statements.md)
