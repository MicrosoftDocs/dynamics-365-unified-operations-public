---
# required metadata
title: Adyen payment connector for Brazil
description: This topic gives an overview of Adyen payment connector in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.
author: akviklis
ms.date: 06/10/2021
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
ms.dyn365.ops.version: 10.0.20

---

# Adyen payment connector in Commerce POS for Brazil

[!include[banner](../includes/banner.md)]

The Dynamics 365 Payment Connector for Adyen is an out-of-the-box payment connector that supports various payment instruments globally. 

The following Brazil-specific Dynamics 365 Payment Connector for Adyen features are enabled after the Commerce localization for Brazil has been set up and deployed:

- Support for sales with credit and debit cards (that is, double-purpose cards).
- Saving payment-related data, such as card type, transaction code (NSU - Número Sequencial Único), and acquirer's CNPJ (Cadastro Nacional da Pessoa Jurídica) in sales transactions and reporting it in electronic fiscal documents:
NFC-e (Nota Fiscal de Consumidor Eletrônica),
NF-e (Nota Fiscal Eletrônica),
CF-e (Cupom Fiscal Eletrônico).

## Double-purpose cards

Double-purpose cards wich are both debit and credit at the same time are widespread in Brazilian retail. 
While paying by card at a store, customers should choose if they prefer to pay by debit or credit funding source.
As a result, the card payment is registered in Adyen with selected payment preference: debit or credit.

## Saving payment-related data

When a retial sale is paid by card, the following card payment information is being stored in electronic fiscal document in the card payment data block and transmitted to SEFAZ (Secretaria de Estado de Fazenda):
- Accreditation - CNPJ of the payment transfer aquiring company,
- Card banner - card type such as Visa, MasterCard, etc.
- Transaction code (NSU) - identification number of a sales transaction using cards.


## Setup
To configure Adyen payment connector in Commerce POS for Brazil, follow these steps:

1. Complete the setup described in [Set up Dynamics 365 Payment Connector for Adyen](../dev-itpro/adyen-connector-setup.md).
1. Go to **Retail and Commerce \> Channel setup \> Payment methods \> Card processors**.
1. Create a record and specify CNPJ for the card processor aquiring company.
1. Go to **Retail and Commerce \> Channel setup \> Payment methods \> Card types**.
1. Specify the card processor code created in the step above for the desired electronic payment types. Also it is required to choose a payment system.
1. Add the electronic payment types created in the step above to your stores payment methods by clicking on the **Electronic payment setup** button.

## Additional resources

[Dynamics 365 Payment Connector for Adyen overview](../dev-itpro/adyen-connector.md)

[Set up Dynamics 365 Payment Connector for Adyen](../dev-itpro/adyen-connector-setup.md)