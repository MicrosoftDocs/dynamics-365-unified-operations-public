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
- Saving payment-related data, such as cart type and transaction code (NSU), in sales transactions and reporting it in electronic fiscal documents NFC-e/NF-e/CF-e.

## Double-purpose cards

Double-purpose cards wich are both debit and credit at the same time are widespread in Brazilian retail. 
While paying by card at a store, customers should choose if they prefer to pay by debit or credit.
As a result, the card payment is registered in Adyen with selected payment preference (Debit or Credit).




## Saving payment-related data, such as cart type and transaction code (NSU), in sales transactions and reporting it in electronic fiscal documents NFC-e/NF-e/CF-e
		Card type in electronic fiscal receipt (find out that data is needed for cards: payment reference, card type, etc.) - generate the data in builder.
	a. Card type name of a bank card has to be populated in sales transactions registered using the EFT service
	b. EFT-related data needs to be reported in EFDs (card payment data must be transmitted to Sefaz): 
	Accreditation - an acquirer CNPJ, code of the TEF creditor
	Card banner - Visa, MasterCard, etc.
Transaction code (NSU) - the code that is displayed on the printed form by the card machine

## Setup
To configure Adyen payment connector in Commerce POS for Brazil, follow these steps:

1. Complete the setup described in [Setup and configuration](../dev-itpro/adyen-connector.md#setup-and-configuration).
1. Go to ****

	• Go to card processor setup: https://usnconeboxax1aos.cloud.onebox.dynamics.com/?cmp=brmf&mi=CardProcessor_BR
	Add new record:

specify CNPJ of the card processor aquiring company

CNPJ as an acquirer on 

an acquirer CNPJ must be transmitted to Sefaz through NFC-e in the card payment data block (Accreditation - an acquirer CNPJ, code of the EFT creditor).




## Additional resources

[Dynamics 365 Payment Connector for Adyen](../dev-itpro/adyen-connector.md)