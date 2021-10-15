---
# required metadata
title: Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil
description: This topic provides an overview of Microsoft Dynamics 365 Payment Connector for Adyen functionality in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.
author: akviklis
ms.date: 09/09/2021
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

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

This topic provides an overview of Microsoft Dynamics 365 Payment Connector for Adyen functionality in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.

The Dynamics 365 Payment Connector for Adyen is an out-of-box payment connector that supports various payment instruments globally.

The following Brazil-specific features of the Dynamics 365 Payment Connector for Adyen are enabled after the Commerce localization for Brazil is set up and deployed:

- Support for sales that are made by using dual-purpose cards. A dual-purpose card is both a debit card and a credit card.
- Saving of payment-related data in sales transactions. This data includes the card type, the transaction code (Número Sequencial Único \[NSU\]), and the acquirer's Cadastro Nacional da Pessoa Jurídica (CNPJ) number. The data is then reported in the following electronic fiscal documents:

    - Nota Fiscal de Consumidor Eletrônica (NFC-e)
    - Nota Fiscal Eletrônica (NF-e)
    - Cupom Fiscal Eletrônico (CF-e)

## Dual-purpose cards

Dual-purpose cards (cards that are both debit cards and credit cards) are common in Brazilian retail. When customers pay by card at a store, they select whether they prefer to pay by debit or credit. The card payment preference (debit or credit) is then registered with Adyen.

## Saving of payment-related data

When a retail sale is paid by card, the following card payment information is stored in the card payment data block of the electronic fiscal document and transmitted to the Secretaria de Estado de Fazenda (SEFAZ):

- **Accreditation** – The CNPJ number of the payment transfer acquiring company.
- **Card banner** – The card type (for example, Visa or MasterCard).
- **Transaction code (NSU)** – The identification number of the sales transaction that uses cards.

## Configure the Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil

To configure the Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil, follow these steps.

1. Complete the configuration steps that are described in [Set up Dynamics 365 Payment Connector for Adyen](../dev-itpro/adyen-connector-setup.md).
1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> Payment methods \> Card processors**.
1. Create a record, and enter the CNPJ number for the card processor acquiring company.
1. Go to **Retail and Commerce \> Channel setup \> Payment methods \> Card types**.
1. Specify the card processor CNPJ number that you entered earlier for the desired electronic payment types. You must select a payment system.
1. Select **Electronic payment setup** to add the electronic payment types that you created earlier to your store's payment methods.

## Additional resources

[Dynamics 365 Payment Connector for Adyen overview](../dev-itpro/adyen-connector.md)

[Set up Dynamics 365 Payment Connector for Adyen](../dev-itpro/adyen-connector-setup.md)
