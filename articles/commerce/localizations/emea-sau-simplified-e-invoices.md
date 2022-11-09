---
title: Generate and submit simplified electronic invoices for Saudi Arabia
description: This article provides an overview and setup guidelines for the functionality of simplified electronic invoices that is available for Saudi Arabia in Microsoft Dynamics 365 Commerce.
author: EvgenyPopovMBS
ms.date: 11/14/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Saudi Arabia
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2022-11-21

---
# Generate and submit simplified electronic invoices for Saudi Arabia

[!include[banner](../includes/banner.md)]

This article provides an overview of the functionality of simplified electronic invoices (e-invoices) that is available for Saudi Arabia in Microsoft Dynamics 365 Commerce. It also provides guidelines for setting up the functionality.

## Overview of the electronic invoicing functionality for Saudi Arabia

The electronic invoicing functionality that is available for Saudi Arabia in Commerce provides the following capabilities:

- Generation of an XML file of a simplified e-invoice upon concluding a sales transaction in Commerce point of sale (POS).
- Generation of a cryptographic stamp for the simplified e-invoice.
- Generation and printing of QR code for the simplified e-invoice that includes the cryptographic stamp.
- Submission of the simplified e-invoice from Commerce headquarters to Saudi Arabian tax authorities (Zakat, Tax and Customs Authority - ZATCA) for reporting purposes.

For more information about the electronic invoicing requirements for Saudi Arabia, see [E-Invoicing portal by ZATCA](https://zatca.gov.sa/en/E-Invoicing/Pages/default.aspx).

The XML format of e-invoice for Saudi Arabia is implemented by using [Electronic reporting (ER)](../../dev-itpro/analytics/general-electronic-reporting.md). The format is common for simplified e-invoices in Commerce and regular tax e-invoices in Dynamics 365 Finance.

The submission of simplified e-invoices for Saudi Arabia is done from Commerce headquarters (HQ) by means of integration with the [Electronic Invoicing service](../../finance/localizations/e-invoicing-sa-get-started.md). For more information about the common electronic invoicing capabilities available for Saudi Arabia, see [Customer electronic invoices in Saudi Arabia](../../finance/localizations/emea-sau-e-invoices.md).
