---
# required metadata
title: Adyen payment connector for Brazil
description: This topic gives an overview of Adyen payment connector in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.
author: akviklis
ms.date: 09/07/2021
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

# Adyen payment connector in Commerce POS for Brazil

[!include[banner](../includes/banner.md)]

The Dynamics 365 Payment Connector for Adyen is an out-of-the-box payment connector that supports various payment instruments globally. 

The following Brazil-specific Dynamics 365 Payment Connector for Adyen features are enabled after the Commerce localization for Brazil has been set up and deployed:

- Support for sales with credit and debit cards (that is, double-purpose cards).
- Saving payment-related data, such as card type, transaction code (NSU - Número Sequencial Único), and acquirer's CNPJ (Cadastro Nacional da Pessoa Jurídica) in sales transactions and reporting it in the following electronic fiscal documents:
    - NFC-e (Nota Fiscal de Consumidor Eletrônica).
    - NF-e (Nota Fiscal Eletrônica).
    - CF-e (Cupom Fiscal Eletrônico).

## Double-purpose cards

Double-purpose cards that are both debit and credit cards are common in Brazilian retail. While paying by card at a store, customers choose if they prefer to pay by debit or credit. The card payment preference (debit or credit) is then registered with Adyen.

## Saving payment-related data

When a retail sale is paid by card, the following card payment information is stored in the card payment data block of the electronic fiscal document and is transmitted to SEFAZ (Secretaria de Estado de Fazenda):
- Accreditation - The CNPJ number of the payment transfer acquiring company.
- Card banner - Card type (for example, Visa or MasterCard).
- Transaction code (NSU) - The identification number of a sales transaction using cards.

## Setup 

To configure the Dynamics 365 Payment Connector for Adyen for POS for Brazil, follow these steps.

Adyen payment connector in Commerce POS for Brazil, follow these steps:

1. Complete the setup described in [Set up Dynamics 365 Payment Connector for Adyen](../dev-itpro/adyen-connector-setup.md).
1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> Payment methods \> Card processors**.
1. Create a record and specify the CNPJ number for the card processor acquiring company.
1. Go to **Retail and Commerce \> Channel setup \> Payment methods \> Card types**.
1. Specify the card processor CNPJ number entered above for the desired electronic payment types. It is required to choose a payment system.
1. Select **Electronic payment setup** to add the electronic payment types created above to your store's payment methods.

## Additional resources

[Dynamics 365 Payment Connector for Adyen overview](../dev-itpro/adyen-connector.md)

[Set up Dynamics 365 Payment Connector for Adyen](../dev-itpro/adyen-connector-setup.md)
