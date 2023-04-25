---
title: Post Brazilian fiscal documents via retail statements in Commerce headquarters
description: This article describes how to post Brazilian fiscal documents via retail statements in Microsoft Dynamics 365 Commerce.
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

# Post Brazilian fiscal documents via retail statements in Commerce headquarters 

[!include[banner](../includes/banner.md)]

This article describes how to post Brazilian fiscal documents via retail statements in Microsoft Dynamics 365 Commerce.

After you run P-jobs and post a retail statement, NFC-e (Nota Fiscal do Consumidor eletrônica) fiscal documents that were issued through Commerce point of sale (POS) terminals can be viewed on the **View XML message** page in Commerce headquarters.

## Post retail statements

NFC-e documents that are issued in POS are posted in Commerce headquarters when open retail statements are posted in the **Retail and Commerce** module. Retail statements can contain both NFC-e and NF-e (Nota Fiscal eletrônica) transactions for returns.

To post an NFC-e document that was issued in POS, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Run the **P-job** for the channel database.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> POS posting**.
1. Run the **Validate store transactions** batch job.
1. Run the **Calculate transactional statements in batch** batch job.
1. Run the **Post transactional statements in batch** job.
1. Go to **Retail and Commerce \> Inquiries and reports \> Posted statements**, and verify that the statement has been posted.

> [!NOTE]
> This procedure does trickle feed–based posting, as described in [Trickle feed-based order creation for retail store transactions](../trickle-feed.md). 
For more information, see [Retail statements](../retail-statements.md).

## View fiscal document details in Commerce headquarters

To view fiscal document details in Commerce headquarters, follow these steps.

1. To view an NFC-e document in Commerce headquarters, go to **Retail and Commerce \> Inquiries and reports \> All fiscal documents**. The **All fiscal documents** page shows the same format that is shown when you view an NF-e model 55 fiscal document. It includes the header, lines, and all attributes. For more information, see [Fiscal documents and fiscal document framework for Brazil](../../finance/localizations/latam-bra-fiscal-documents-fiscal-document-framework.md).

    > [!NOTE]
    > By default, if you open the **All fiscal documents** page in Commerce headquarters, it lists only NFC-e model 65 fiscal documents. To view returns that have NFC-e model 55 fiscal documents, you must change the filter criteria. However, if you open the **All fiscal documents** page in the **General ledger** module, it lists all incoming and outgoing fiscal document models, including model 55 and model 65.

1. On the **All fiscal documents** page, review the **Status** field for the fiscal documents that you want to view. For sales that have been authorized by the state's tax authority, the **Status** field will be set to **Approved**.
1. Select the required fiscal documents, and then, on the **NF-e federal** tab, select **XML document**.
1. On the **View XML message** page, on the **NF-e** and **NF-e return** tabs, validate the XML requests and responses that are available.
1. On the **Cancel** tab, validate any canceled XML requests and responses that are available.

## Additional resources

[Set up and deploy Commerce localization for Brazil](latam-bra-deployment.md)

[Commerce localization for Brazil](latam-bra-commerce-localization.md)

[NFC-e fiscal document functionality in Commerce POS for Brazil](latam-bra-nfce.md)

[Manage customer information in POS for Brazil](latam-bra-customer-information.md)

[Cancellation and return of NFC-e documents in Commerce POS for Brazil](latam-bra-nfce-cancel-return.md)

[Postponed registration of NFC-e documents issued in offline contingency mode](latam-bra-nfce-contingency-mode.md)
