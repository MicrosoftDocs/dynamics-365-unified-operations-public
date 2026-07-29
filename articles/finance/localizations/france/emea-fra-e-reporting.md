--- 
title: France e-reporting (electronic reporting of transactions)
description: Learn how to set up and report electronically transaction in France. 
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 07/28/2026
ms.custom:
  - bap-template
ms.reviewer: johnmichalak 
ms.search.region: France
ms.search.validFrom: 2026-06-30
ms.search.form: CustTable, VendTable, OMLegalEntity
ms.dyn365.ops.version: Version 7.0.0 
---

# France e-reporting (electronic reporting of transactions) overview

[!include [banner](../../includes/banner.md)]

France e-reporting (transmission des données de transaction) is part of the French continuous transaction control (Réforme de la facturation électronique) reform that requires companies to report specific business transactions to the French tax authorities through an approved intermediary platform.
In Dynamics 365 Finance, the France e-reporting feature enables organizations to:

- Collect required transaction data from Finance documents
- Transform data into the French-compliant formats by using Electronic reporting (ER)

This feature complements [electronic invoicing (e-invoicing)](emea-fra-einv-ereport.md) requirements and relies on the same core concepts, including registration identifiers and establishment-based reporting.

## Scope of e-reporting

France e-reporting applies to the electronic transmission of data for transactions that are outside the scope of mandatory e-invoicing.
This restriction includes:

- B2C (business-to-consumer) transactions
- Cross-border B2B and B2C transactions
- Payment data for transactions where VAT is due upon payment

E-reporting complements e-invoicing by ensuring that the tax authorities receive data for all VAT-relevant transactions.

## Feature availability

France e-reporting functionality is available starting from Finance version **10.0.49**.

You can also access this feature in earlier versions 10.0.47 and 10.0.48 through specific application builds. Availability in these versions depends on the deployed build and update level.

| Finance version | Build |
|--------------|-------|
| 10.0.48 | 10.0.2645.**55** |
| 10.0.47 | 10.0.2527.**135** |

## Registration IDs and establishments

Accurate identification of legal entities and their establishments is required for compliant reporting.

Before you configure e-reporting:

- Set up registration IDs, such as VAT ID, SIREN, and SIRET numbers.
- Configure the establishment structure.
- Ensure that transactions are associated with the correct establishment.

For more information, see [Registration IDs set up for France](emea-fra-registration-numbers-setup-for-france.md) and [Use establishments in France](emea-fra-establishments-for-france.md).
