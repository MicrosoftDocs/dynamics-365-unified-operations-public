---
# required metadata

title: Set up default descriptions for posting of Tax fiscal documents
description: This topic explains how to set up default descriptions for voucher transactions that are posted from Tax fiscal documents.
author: gionoder
ms.date: 03/18/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: FBTaxAssessmentPayment_BR, FBTaxAssessmentPaymentOtherDebits_BR
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 270254
ms.assetid: 92223189-69a8-4a40-b867-ef9b4f14c23d
ms.search.region: Brazil
# ms.search.industry: 
ms.author: gionoder
ms.search.validFrom: 2022-01-31
ms.dyn365.ops.version: 10.0.25

---

# Set up default descriptions for posting of Tax fiscal documents

[!include [banner](../includes/banner.md)]

Follow these steps to set up default descriptions for voucher transactions that are posted from Tax fiscal documents.

1. Go to **Organization administration** > **Setup** > **Default descriptions**.
2. Select **New**.
3. In the **Description** field, select **Tax fiscal document**.
4. In the **Language** field, select a language.
5. In the **Text** field, enter the default description text. The text supports the following placeholder variables:

    - **%1** – The transaction date.
    - **%2** – An identifier that corresponds to the document type that is being posted to the general ledger. For example, if a transaction type is related to an invoice, the %2 variable adds the invoice number.
    - **%3** – An identifier that is related to the document type that is being posted to the general ledger. For example, if a transaction type is related to an invoice, the %3 variable adds the customer account number.

For more information, see [Set up default descriptions for automatic posting](../general-ledger/set-up-default-descriptions-for-automatic-posting.md#set-up-default-descriptions)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
