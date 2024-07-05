---
title: Set up default descriptions for posting of Tax fiscal documents
description: Learn how to set up default descriptions for voucher transactions that are posted from Tax fiscal documents, including a step-by-step process.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/27/2024
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2022-01-31
ms.search.form: FBTaxAssessmentPayment_BR, FBTaxAssessmentPaymentOtherDebits_BR
ms.dyn365.ops.version: 10.0.25
ms.assetid: 92223189-69a8-4a40-b867-ef9b4f14c23d
---

# Set up default descriptions for posting of Tax fiscal documents

[!include [banner](../../includes/banner.md)]

Follow these steps to set up default descriptions for voucher transactions that are posted from Tax fiscal documents.

1. Go to **Organization administration** > **Setup** > **Default descriptions**.
2. Select **New**.
3. In the **Description** field, select **Tax fiscal document**.
4. In the **Language** field, select a language.
5. In the **Text** field, enter the default description text. The text supports the following placeholder variables:

    - **%1** – The transaction date.
    - **%2** – An identifier that corresponds to the document type that is being posted to the general ledger. For example, if a transaction type is related to an invoice, the %2 variable adds the invoice number.
    - **%3** – An identifier that is related to the document type that is being posted to the general ledger. For example, if a transaction type is related to an invoice, the %3 variable adds the customer account number.

For more information, see [Set up default descriptions for automatic posting](../../general-ledger/set-up-default-descriptions-for-automatic-posting.md#set-up-default-descriptions)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
