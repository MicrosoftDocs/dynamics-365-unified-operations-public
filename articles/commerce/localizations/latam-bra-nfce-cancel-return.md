---
# required metadata
title: Cancellation and return of NFC-e documents in Commerce POS for Brazil
description: This topic gives an overview of cancellation and return functionality for NFC-e (Nota Fiscal do Consumidor eletrônica) documents in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.
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

# Cancellation and return of NFC-e documents in Commerce POS for Brazil

[!include[banner](../includes/banner.md)]

This topic gives an overview of cancelation and return functionality for NFC-e (Nota Fiscal do Consumidor eletrônica) documents in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.

Commerce functionality for Brazil supports cancelation and return of sales issued with NFC-e documents. NFC-e document formats are based on the national technical standards of the electronic fiscal documents, including cancellation events and NF-e (Nota Fiscal eletrônica) model 55 for returns. 

An NF-e is an electronic fiscal document that is generated and printed to register the return of goods sold to a customer. It enables tax and fiscal control from tax authorities and allows customers to verify the validity and authenticity of the received fiscal documents. For more information about the NF-e process, see [Brazil NF-e process overview](../../finance/localizations/latam-bra-nf-e-process.md).

It is only possible to cancel an NFC-e document if it is already authorized by the tax authority and if the goods and the customer are still in the establishment. The maximum deadline for canceling an NFC-e document is up to 30 minutes after the granting of authorization for use. Once the NFC-e document cancellation time runs out, a return NF-e document must be issued to cancel a sale.

## Limitations

The following limitations apply to cancellation and return functionality for NFC-e documents.

- Cancellations and returns are only allowed for sales made within the same state. Interstate operations are prohibited.
- The cancellation of NFC-e documents authorized by POS terminals from other stores is not supported. Only authorized NFC-e documents issued by POS terminals within the same store can be canceled. 
- Cancellation and returns issued by POS terminals without internet access or issued when the tax authority authorization service is down (offline contingency mode) are not supported.
- The simplified DANFE (Documento Auxiliar da Nota Fiscal Eletrônica) for model 55 format is the only layout supported for returns.
- Sales and returns of services are not supported.

## Supported scenarios

The following example scenarios show how to initiate cancellations and returns in Commerce POS for Brazil.

### Scenario 1: Initiate a cancellation of sold goods

To initiate a cancellation of sold goods, follow these steps.

1. Sign in to POS.
1. Open **Show journal** form.
1. Find the sale that needs to be canceled.
1. Select **Cancel transaction**.
1. Enter a justification for the cancellation, and then select **OK**.
1. Add a named customer or specify customer information manually. For more information, see [Manage customer information in POS for Brazil](latam-bra-customer-information.md).
1. Register payments refund for the transaction, and then finalize the transaction.

### Scenario 2: Initiate a return of sold goods

To initiate a return of sold goods, follow these steps.

1. Sign in to POS.
1. Open the **Show journal** form.
1. Find the sale that needs to be fully or partially returned.
1. Select **Return**, select the returnable product(s) as needed, and then select **Return**.
1. Add a named customer or specify customer information manually. For more information, see [Manage customer information in POS for Brazil](latam-bra-customer-information.md).
1. Register payments for the transaction.
1. Verify that the information (including the barcode) on the printed simplified DANFE for model 55 fiscal receipt corresponds to the sale.

## Simplified DANFE for model 55 fiscal receipt

In addition to the [common list of custom fields for DANFE](latam-bra-nfce.md#danfe-fiscal-receipt-custom-fields), a simplified DANFE for model 55 fiscal receipt can include the following custom field:
- **Barcode (Código de barras)** – You can add a barcode field for simplified DANFE for model 55 for returns.

## Additional resources

[Set up and deploy Commerce localization for Brazil](latam-bra-deployment.md) 

[Commerce localization for Brazil](latam-bra-commerce-localization.md) 

[NFC-e fiscal document functionality in Commerce POS for Brazil](latam-bra-nfce.md)

[Manage customer information in POS for Brazil](latam-bra-customer-information.md)

[Postponed registration of NFC-e documents issued in offline contingency mode](latam-bra-nfce-contingency-mode.md)

[Post Brazilian fiscal documents via retail statements in Commerce headquarters](latam-bra-retail-statements.md)
