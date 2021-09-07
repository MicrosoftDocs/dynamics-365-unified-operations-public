---
# required metadata
title: Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil
description: This topic provides an overview of Microsoft Dynamics 365 Payment Connector for Adyen functionality in Microsoft Dynamics 365 Commerce POS for Brazil.
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

# Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil

[!include[banner](../includes/banner.md)]

This topic provides an overview of Microsoft Dynamics 365 Payment Connector for Adyen functionality in Microsoft Dynamics 365 Commerce POS for Brazil.

The Dynamics 365 Payment Connector for Adyen is an out-of-the-box payment connector that supports various payment instruments globally. 

The following Brazil-specific Dynamics 365 Payment Connector for Adyen features are enabled after the Commerce localization for Brazil has been set up and deployed:

- Support for sales with dual-purpose credit and debit cards (that is, cards that are both debit and credit cards).
- Saving of payment-related data such as card type, transaction code (NSU - Número Sequencial Único), and acquirer's CNPJ (Cadastro Nacional da Pessoa Jurídica) number in sales transactions and reporting the data in the following electronic fiscal documents:
    - NFC-e (Nota Fiscal de Consumidor Eletrônica).
    - NF-e (Nota Fiscal Eletrônica).
    - CF-e (Cupom Fiscal Eletrônico).

## Dual-purpose cards

Dual-purpose cards that are both debit and credit cards are common in Brazilian retail. When paying by card at a store, customers choose if they prefer to pay by debit or credit. The card payment preference (debit or credit) is then registered with Adyen.

## Saving of payment-related data

When a retail sale is paid by card, the following card payment information is stored in the card payment data block of the electronic fiscal document and is transmitted to SEFAZ (Secretaria de Estado de Fazenda):
- Accreditation - The CNPJ number of the payment transfer acquiring company.
- Card banner - Card type (for example, Visa or MasterCard).
- Transaction code (NSU) - The identification number of a sales transaction using cards.

## Configure the Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil

To configure the Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil, follow these steps.

1. Complete the configuration steps described in [Set up Dynamics 365 Payment Connector for Adyen](../dev-itpro/adyen-connector-setup.md).
1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> Payment methods \> Card processors**.
1. Create a record and specify the CNPJ number for the card processor acquiring company.
1. Go to **Retail and Commerce \> Channel setup \> Payment methods \> Card types**.
1. Specify the card processor CNPJ number entered above for the desired electronic payment types. It is required to choose a payment system.
1. Select **Electronic payment setup** to add the electronic payment types created above to your store's payment methods.

## Additional resources

[Dynamics 365 Payment Connector for Adyen overview](../dev-itpro/adyen-connector.md)

[Set up Dynamics 365 Payment Connector for Adyen](../dev-itpro/adyen-connector-setup.md)
