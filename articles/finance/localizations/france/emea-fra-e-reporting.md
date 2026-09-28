--- 
title: France e-reporting (electronic reporting of transactions)
description: Learn how to set up and report electronically transaction in France. 
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 09/28/2026
ms.custom:
  - bap-template
ms.reviewer: johnmichalak 
ms.search.region: France
ms.search.validFrom: 2026-06-30
ms.search.form: CustTable, VendTable, OMLegalEntity
ms.dyn365.ops.version: Version 7.0.0 
---

# France e-reporting (electronic reporting of transactions) overview

[!INCLUDE [banner](../../includes/banner.md)]

France e-reporting (transmission des données de transaction) is part of the French continuous transaction control (Réforme de la facturation électronique) reform that requires companies to report specific business transactions to the French tax authorities through an approved intermediary platform.

This feature complements [electronic invoicing (e-invoicing)](emea-fra-einv-ereport.md) requirements and relies on the same core concepts, including registration identifiers and establishment-based reporting.

In Dynamics 365 Finance, the France e-reporting feature enables organizations to:

- Collect required transaction data from Finance documents
- Transform data into the French-compliant formats by using Electronic reporting (ER)

Dynamics 365 Finance also provides an optional direct submission integration with EDICOM, a partner dematerialization platform (PDP). When this integration is enabled, you can submit your generated France e-reporting documents to the French tax authorities directly from Finance and retrieve their processing status, without transmitting the files through a separate channel. To set up the integration, see [Set up the EDICOM integration for France e-Reporting](emea-fra-e-reporting-edicom-integration-guide.md). To submit and track e-reports through it, see [How to use France e-reporting in Dynamics 365 Finance to submit using EDICOM connection](emea-fra-e-reporting-edicom-submission.md).

## Scope of e-reporting

France e-reporting applies to the electronic transmission of data for transactions that are outside the scope of mandatory e-invoicing.
This restriction includes:

- B2C (business-to-consumer) transactions
- Cross-border B2B and B2C transactions
- Payment data for transactions where VAT is due upon payment

E-reporting complements e-invoicing by ensuring that the tax authorities receive data for all VAT-relevant transactions.

### Reporting periods

France e-reporting data is transmitted per reporting period. The declarant's **VAT regime** and the date of the operation (transaction data) or collection (payment data) determine the period:

- Standard VAT regime - Monthly – transaction data in ten-day periods; payment data monthly.
- Simplified VAT regime - Quarterly – monthly periods.
- Franchise in base VAT regime – bimonthly (two-month civil) periods.
  
Each transmission covers a single period. A previously submitted period is corrected through a rectifying transmission. This alignment ensures that reports meet the platform's period-consistency requirements. Select the **VAT regime** when you configure report generation. For more information, see [How to prepare your Dynamics 365 Finance for French e-Reporting](emea-fra-e-reporting-preparation.md).

## Feature availability

France e-reporting functionality is available starting from Finance version **10.0.49**.

You can also access this feature in earlier versions 10.0.47 and 10.0.48 through specific application builds. Availability in these versions depends on the deployed build and update level.

| Finance version | Build |
| --------------- | ----- |
| 10.0.48 | 10.0.2645.**55** |
| 10.0.47 | 10.0.2527.**135** |

## Registration IDs and establishments

Accurate identification of legal entities and their establishments is required for compliant reporting.

Before you configure e-reporting:

- Set up registration IDs, such as VAT ID, SIREN, and SIRET numbers.
- Configure the establishment structure.
- Ensure that transactions are associated with the correct establishment.

For more information, see [Registration IDs set up for France](emea-fra-registration-numbers-setup-for-france.md) and [Use establishments in France](emea-fra-establishments-for-france.md).

## Direct submission of E-Report for France through the EDICOM integration

Dynamics 365 Finance includes a direct integration with EDICOM that you can use to submit the generated France e-reporting files to the tax authorities through EDICOM, and retrieve their processing status, without leaving Finance. The integration adds dedicated **Electronic messages** actions for submitting a report, requesting its status, importing the status, and confirming the received status.

You enable the integration through specific application builds:

| Finance version | Build |
| --------------- | ----- |
| 10.0.49 | 10.0.2790.**61** |
| 10.0.48 | 10.0.2645.**135** |
| 10.0.47 | 10.0.2527.**212** |

Using the EDICOM integration is optional. You can continue to only generate the France e-reporting file in Finance and transmit it by your own means. For the prerequisites, setup package, and step-by-step configuration of the integration, see [Set up and use the EDICOM integration for France e-Reporting](emea-fra-e-reporting-edicom-integration-guide.md).

### Privacy notice

When you enable Finance to interoperate with EDICOM for e-Reporting, the system shares customer content with EDICOM to process and submit e-Reports. This content might include sales, purchase, and payment information, as well as e-Reporting status acknowledgement details. To learn more about the information required for e-Reporting submissions, review [EDICOM's documentation](https://go.microsoft.com/fwlink/?LinkId=2378296). A system administrator can disable the EDICOM interoperation in Finance by going to **Tax** > **Setup** > **Electronic Messages**. Your privacy is important to us. To learn more, read our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=521839).
