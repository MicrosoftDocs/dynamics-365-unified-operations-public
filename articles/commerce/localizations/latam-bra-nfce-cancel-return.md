---
title: Cancellation and return of NFC-e documents in Commerce POS for Brazil
description: This article gives an overview of the cancellation and return functionality for NFC-e documents in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.
author: EvgenyPopovMBS
ms.date: 12/03/2021
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

# Cancellation and return of NFC-e documents in Commerce POS for Brazil

[!include[banner](../includes/banner.md)]

This article gives an overview of the cancellation and return functionality for NFC-e (Nota Fiscal do Consumidor eletrônica) documents in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.

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

In addition to the [common list of custom fields for DANFE](latam-bra-nfce.md#custom-fields-for-danfe-fiscal-receipts), a simplified DANFE for model 55 fiscal receipt can include the custom fields that are described in this section.

### Configure custom fields so that they can be used in receipt formats for sales receipts

Add the following POS labels to the **POS** section of the **Language text** page.

| Language ID | Text ID | Text                                      |
|-------------|---------|-------------------------------------------|
| en-US       | 900101  | Barcode                                   |
| en-US       | 900102  | Barcode block 1 (22 digits)               | 
| en-US       | 900103  | Barcode block 2 (22 digits)               | 

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. The **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                            | Type    | Caption text ID |
|---------------------------------|---------|-----------------|
| BARCODE\_BR  					  | Receipt | 900101          |
| FISCALDOCUMENTBARCODEFIRST\_BR  | Receipt | 900102          |
| FISCALDOCUMENTBARCODESECOND\_BR | Receipt | 900103          |

### Configure receipt formats

For every receipt format that is required, change the value of the **Print behavior** field to **Always print**.

In the receipt format designer, add the following custom fields to the appropriate receipt sections. Note that the field names correspond to the language text values that you defined in the previous section.

- **Header:** Add the following fields:

    - **Barcode (Código de barras)** – You can add a bar code field to simplified DANFE for model 55 fiscal receipts for returns.
    - **Barcode block 1**, **Barcode block 2** – You can add 22-digit bar code fields to simplified DANFE for model 55 fiscal receipts for returns that are printed on the till roll. The bar code is a graphical representation of the **Access key (Chave de acesso)** value that is divided into two parts, each of which has 22 digits.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

## Additional resources

[Set up and deploy Commerce localization for Brazil](latam-bra-deployment.md)

[Commerce localization for Brazil](latam-bra-commerce-localization.md)

[NFC-e fiscal document functionality in Commerce POS for Brazil](latam-bra-nfce.md)

[Manage customer information in POS for Brazil](latam-bra-customer-information.md)

[Postponed registration of NFC-e documents issued in offline contingency mode](latam-bra-nfce-contingency-mode.md)

[Post Brazilian fiscal documents via retail statements in Commerce headquarters](latam-bra-retail-statements.md)

[Set up and design receipt formats](../receipt-templates-printing.md).
