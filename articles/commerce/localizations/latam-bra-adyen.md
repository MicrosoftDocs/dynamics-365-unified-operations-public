---
# required metadata
title: Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil
description: This topic provides an overview of Microsoft Dynamics 365 Payment Connector for Adyen functionality in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.
author: akviklis
ms.date: 03/04/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
ms.search.industry: Retail
ms.author: akviklis
ms.search.validFrom: 2021-08-01
ms.dyn365.ops.version: 10.0.22

---

# Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil

[!include [banner](../includes/banner.md)]

This topic provides an overview of Microsoft Dynamics 365 Payment Connector for Adyen functionality in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.

The Dynamics 365 Payment Connector for Adyen is an out-of-box payment connector that supports various payment instruments globally.

The following Brazil-specific features of the Dynamics 365 Payment Connector for Adyen are enabled after you set up and deploy the Commerce localization for Brazil:

- Support for sales that are made by using dual-purpose cards. A dual-purpose card is both a debit card and a credit card.
- Saving of payment-related data in sales transactions. This data includes the card type, the transaction code (Número Sequencial Único \[NSU\]), and the acquirer's Cadastro Nacional da Pessoa Jurídica (CNPJ) number. The data is then reported in the following electronic fiscal documents:

    - Nota Fiscal de Consumidor Eletrônica (NFC-e)
    - Nota Fiscal Eletrônica (NF-e)
    - Cupom Fiscal Eletrônico (CF-e)

- Support for payment in installments. This payment option is popular in Brazil, because shoppers can receive goods or services immediately but spread the cost over multiple months.

## Dual-purpose cards

Dual-purpose cards (in other words, cards that are both debit cards and credit cards) are common in Brazilian retail. When customers pay by card at a store, they select whether they prefer to pay by debit or credit. The card payment preference is then registered with Adyen.

## Saving of payment-related data

When a retail sale is paid by card, the following payment information is stored in the card payment data block of the electronic fiscal document. It is also transmitted to the Secretaria de Estado de Fazenda (SEFAZ).

- **Accreditation** – The CNPJ number of the payment transfer acquiring company.
- **Card banner** – The card type (for example, Visa or MasterCard).
- **Transaction code (NSU)** – The identification number of the sales transaction that uses cards.

## Payment in installments

This feature takes advantage of the connector's built-in [credit card installments](https://docs.adyen.com/payment-methods/cards/credit-card-installments) capability. It extends the payment connector so that it supports payment in installments in stores that are located in Brazil.

A retail customer who is paying by card can choose to pay in installments. The cashier can then select **Installments** as the payment preference type and specify the number of payments that the customer is requesting. The payment preference information is passed to Adyen, together with other credit card payment data. Further installment processing is handled by Adyen and the customer's bank. The purchase amount is split into the specified number of equal monthly payments. These payments are charged to the customer's credit card every 30 days until the purchase is paid in full.

## Configure the Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil

To configure the Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil, follow these steps.

1. Complete the configuration steps that are described in [Set up Dynamics 365 Payment Connector for Adyen](../dev-itpro/adyen-connector-setup.md).
1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> Payment methods \> Card processors**.
1. Create a record, and enter the CNPJ number for the card processor acquiring company.
1. Go to **Retail and Commerce \> Channel setup \> Payment methods \> Card types**.
1. Specify the card processor CNPJ number that you entered earlier for the required electronic payment types. You must select a payment system.
1. Select **Electronic payment setup** to add the electronic payment types that you created earlier to your store's payment methods.
1. Configure the Hardware station extension component for the Payment Connector for Adyen in POS for Brazil. For more information about how to set up this extension, see [Payments.Connector.Adyen.Device.Brazil component](latam-bra-deployment.md#paymentsconnectoradyendevicebrazil-component).

## Additional resources

[Dynamics 365 Payment Connector for Adyen overview](../dev-itpro/adyen-connector.md)

[Set up Dynamics 365 Payment Connector for Adyen](../dev-itpro/adyen-connector-setup.md)

[Adyen payment connector for Dynamics 365](https://docs.adyen.com/plugins/microsoft-dynamics)

[Adyen documentation: credit card installments](https://docs.adyen.com/payment-methods/cards/credit-card-installments)
