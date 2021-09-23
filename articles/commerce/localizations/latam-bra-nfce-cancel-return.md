---
# required metadata
title: Cancellation and return of NFC-e documents in Commerce POS for Brazil
description: This topic gives an overview of the cancellation and return functionality for NFC-e documents in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.
author: akviklis
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
ms.author: akviklis
ms.search.validFrom: 2021-01-01
ms.dyn365.ops.version: 10.0.18

---

# Cancellation and return of NFC-e documents in Commerce POS for Brazil

[!include[banner](../includes/banner.md)]

This topic gives an overview of the cancellation and return functionality for NFC-e (Nota Fiscal do Consumidor eletrônica) documents in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.

Commerce functionality for Brazil supports the cancellation and return of sales that were issued by using NFC-e documents. NFC-e document formats are based on the national technical standards for electronic fiscal documents. These standards also include a format for cancellation events and NF-e (Nota Fiscal eletrônica) model 55 for returns.

An NF-e is an electronic fiscal document that is generated and printed to register the return of goods that were sold to a customer. It enables tax and fiscal control by tax authorities. It also lets customers verify the validity and authenticity of the fiscal documents that they receive. For more information about the NF-e process, see [Brazil NF-e process overview](../../finance/localizations/latam-bra-nf-e-process.md).

An NFC-e document can be canceled only if it has already been authorized by the tax authority, and if the goods and the customer are still in the establishment. The deadline for canceling an NFC-e document is 30 minutes after the authorization for use was granted. After this cancellation deadline expires, a return NF-e document must be issued to cancel a sale.

## Limitations

The following limitations apply to the cancellation and return functionality for NFC-e documents:

- Cancellations and returns are allowed only for sales that are made within the same state. Interstate operations are prohibited.
- Cancellation of NFC-e documents that are authorized by POS terminals in other stores isn't supported. Only authorized NFC-e documents that are issued by POS terminals in the same store can be canceled.
- Cancellations and returns that are issued in offline contingency mode aren't supported. In other words, cancellations and returns can't be issued by POS terminals that don't have internet access, or when the tax authority's authorization service is down.
- The simplified DANFE (Documento Auxiliar da Nota Fiscal Eletrônica) for model 55 format is the only layout that is supported for returns.
- Sales and returns of services aren't supported.

## Supported scenarios

The following example scenarios show how to initiate cancellations and returns in Commerce POS for Brazil.

### Scenario 1: Initiate a cancellation of sold goods

To initiate a cancellation of sold goods, follow these steps.

1. Sign in to POS.
1. Open **Show journal** page.
1. Find the sale that must be canceled.
1. Select **Cancel transaction**.
1. Enter a justification for the cancellation, and then select **OK**.
1. Add a named customer, or manually enter customer information. For more information, see [Manage customer information in POS for Brazil](latam-bra-customer-information.md).
1. Register payment refunds for the transaction, and then finalize the transaction.

### Scenario 2: Initiate a return of sold goods

To initiate a return of sold goods, follow these steps.

1. Sign in to POS.
1. Open the **Show journal** page.
1. Find the sale that must be fully or partially returned.
1. Select **Return**, select the returnable products as required, and then select **Return**.
1. Add a named customer, or manually enter customer information. For more information, see [Manage customer information in POS for Brazil](latam-bra-customer-information.md).
1. Register payments for the transaction.
1. Verify that the information (including the barcode) on the printed simplified DANFE for model 55 fiscal receipt corresponds to the sale.

## Simplified DANFE for model 55 fiscal receipt

In addition to the [common list of custom fields for DANFE](latam-bra-nfce.md), a simplified DANFE for model 55 fiscal receipt can include the following custom field:

- **Barcode (Código de barras)** – You can add a bar code field to simplified DANFE for model 55 fiscal receipts for returns.

## Additional resources

[Set up and deploy Commerce localization for Brazil](latam-bra-deployment.md)

[Commerce localization for Brazil](latam-bra-commerce-localization.md)

[NFC-e fiscal document functionality in Commerce POS for Brazil](latam-bra-nfce.md)

[Manage customer information in POS for Brazil](latam-bra-customer-information.md)

[Postponed registration of NFC-e documents issued in offline contingency mode](latam-bra-nfce-contingency-mode.md)

[Post Brazilian fiscal documents via retail statements in Commerce headquarters](latam-bra-retail-statements.md)
