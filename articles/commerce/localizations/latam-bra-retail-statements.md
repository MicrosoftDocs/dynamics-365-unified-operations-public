---
# required metadata
title: Post Brazilian fiscal documents via retail statements in Commerce headquarters
description: This topic describes how to post Brazilian fiscal documents via retail statements in Microsoft Dynamics 365 Commerce.
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

# Post Brazilian fiscal documents via retail statements in Commerce headquarters 

[!include[banner](../includes/banner.md)]

This topic describes how to post Brazilian fiscal documents via retail statements in Microsoft Dynamics 365 Commerce.

After running P-jobs and posting the retail statement, NFC-e (Nota Fiscal do Consumidor eletrônica) fiscal documents issued through Commerce POS terminals can be viewed in Commerce headquarters on the **View XML message** form. 

## Post retail statement

NFC-e documents issued on POS are posted into Commerce headquarters through the posting of open retail statements in the **Retail and Commerce** module. Retail statements can contain both NFC-e and NF-e (Nota Fiscal eletrônica) transactions for returns. 

In order to post a NFC-e document issued on POS, follow these steps. 

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Run the **P-job** for the channel database.
1. Expand **Retail and Commerce \> Retail and Commerce IT \> POS posting**. 
1. Run the **Validate store transactions** batch job.
1. Run the **Calculate transactional statements in batch** batch job.
1. Run the **Post transactional statements in batch** job.
1. Go to **Retail and Commerce \> Inquiries and reports \> Posted statements** and verify that the statement has been posted.

> [!NOTE]
> The steps above perform trickle feed-based posting as described in [Trickle feed-based order creation for retail store transactions](../trickle-feed.md). 

For more information, see [Retail statements](../retail-statements.md). 

## View fiscal document details in Commerce headquarters

To view fiscal document details in Commerce headquarters, follow these steps. 
 
1. To view a NFC-e document in Commerce headquarters, go to **Retail and Commerce \> Inquires and reports \> All fiscal documents**. The **All fiscal documents** form displays the same format seen when viewing a NF-e fiscal document model 55, showing the header, lines, and all attributes. For more information, see [Fiscal documents and fiscal document framework for Brazil](../../finance/localizations/latam-bra-fiscal-documents-fiscal-document-framework.md). 

    > [!NOTE]
    > When viewed in Commerce headquarters, by default the **All fiscal documents** form only lists NFC-e model 65 fiscal documents. To view returns having NFC-e model 55 fiscal documents, the filter criteria must be changed. However, when viewed from the **General ledger** module, the **All fiscal documents** form lists all incoming and outgoing fiscal document models, including model 55 and model 65.
    
1. On the **All fiscal documents** form, check the **Status** column for the fiscal documents you want to view. The **Status** column will display **Approved** for sales authorized by the tax authority of the state.
1. Select the needed fiscal document(s), and then under the **NF-e federal** tab, select **XML document**.
1. On the **NF-e** and **NF-e return** tabs of the **View XML message** form, validate the XML requests and responses that are available.
1. On the **Cancel** tab of the **View XML message** form, validate any cancelled XML requests and responses that are available.

## Additional resources

[Set up and deploy Commerce localization for Brazil](latam-bra-deployment.md) 

[Commerce localization for Brazil](latam-bra-commerce-localization.md) 

[NFC-e fiscal document functionality in Commerce POS for Brazil](latam-bra-nfce.md)

[Manage customer information in POS for Brazil](latam-bra-customer-information.md)

[Cancellation and return of NFC-e documents in Commerce POS for Brazil](latam-bra-nfce-cancel-return.md)

[Postponed registration of NFC-e documents issued in offline contingency mode](latam-bra-nfce-contingency-mode.md)
