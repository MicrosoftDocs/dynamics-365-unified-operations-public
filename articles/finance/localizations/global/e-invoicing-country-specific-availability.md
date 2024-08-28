---
title: Availability of Electronic Invoicing Service features by country or region
description: Learn about the out-of-box features that are available for each country or region, including overviews on generally available features.
author: ilikond
ms.author: ikondratenko
ms.topic: article
ms.date: 07/29/2024
ms.custom:
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: 
ms.search.validFrom:
ms.search.form: 
ms.dyn365.ops.version: 
---

# Availability of Electronic Invoicing Service features by country or region

[!include [banner](../../includes/banner.md)]

The availability of Electronic invoicing Service globalization features depends on the country or region where you're located. Although some features are generally available, others are still in preview.

> [!NOTE]
> This article is related only to the globalization features introduced in the scope of the Electronic Invoicing Service. This article doesn't cover other approaches for supported e-Invoicing capabilities for some countries designed based on built-in X++ code and the Electronic Messaging framework.
> For more information, see [Electronic Invoicing](gs-e-invoicing-service-overview.md) and [Electronic messaging](../../general-ledger/electronic-messaging.md).

> [!IMPORTANT]
> It's important to note that we had planned to transition NF-e/NFS-e and CFDI to our Electronic Invoicing Service and the features and formats have been under preview for quite a while in Brazil and Mexico, respectively. However, due to lack of interest for adoption and transition to the new approach, we are still evaluating the timing of the switch to the Electronic Invoicing Service platform in these countries. The documents' formats will not contain the latest compliance changes published since the preview release. 
> In the meantime, **we recommend continuing to use our built-in X++ implementation in Brazil and Mexico, which are kept up to date with the legislation**.
> For more information, see [NF-e process overview](../brazil/latam-bra-nf-e-process.md) and [Electronic invoices (CFDI)](../iberoamerica/latam-mex-CFDI-electronic-invoices.md).

## Generally available features

The following table shows the Electronic invoicing globalization features that are generally available.

| Country or region | Globalization feature name | Business documents |
|-------------------|----------------------------|--------------------|
| Australia | [Electronic invoicing for Australia and New Zealand](../apac/GS-apac-aus-nzl-electronic-invoices.md) | Sales invoices and project invoices |
| Austria | Austrian electronic invoices (AT) | Sales invoices and project invoices |
| Belgium | Belgian electronic invoice (BE) | Sales invoices and project invoices |
| Chile | LATAM e-invoice CL | Sales invoices, project invoices, and packing slips |
| Costa Rica | LATAM e-invoice CR | Sales invoices and project invoices |
| Denmark | Danish electronic invoice (DK) | Sales invoices and project invoices |
| Egypt | Egyptian electronic invoice (EG) | Sales invoices and project invoices |
| Estonia | Estonian electronic invoice (EE) | Sales invoices and project invoices |
| Europe | PEPPOL electronic invoice | Pan-European Public Procurement Online (PEPPOL) sales invoices and project invoices |
| Europe | PEPPOL vendor invoice | PEPPOL import vendor invoices |
| Finland | Finnish electronic invoice (FI) | Sales invoices and project invoices |
| France | French electronic invoice (FR) | Sales invoices and project invoices |
| Germany | German electronic invoice (DE) | Sales invoices and project invoices |
| Indonesia | Indonesian electronic invoice (ID) | Sales invoices, project invoices, and vendor invoices |
| Italy | FatturaPA (IT) | Sales invoices and project invoices |
| Malaysia | [Malaysian electronic invoicing (MY)](../malaysia/apac-mys-e-invoices.md) | Sales invoices, project invoices, and self invoices |
| Netherlands | Dutch electronic invoice (NL) | Sales invoices and project invoices |
| New Zealand | [Electronic invoicing for Australia and New Zealand](../apac/GS-apac-aus-nzl-electronic-invoices.md) | Sales invoices and project invoices |
| Norway | Norwegian electronic invoice (NO) | Sales invoices and project invoices |
| Panama | LATAM e-invoice PA | Sales invoices and project invoices |
| Saudi Arabia | [Saudi Arabian Zatca submission (SA)](../mea/gs-e-invoicing-sa-get-started.md) | Sales invoices and project invoices |
| Saudi Arabia | [Saudi Arabian Zatca compliance check (SA)](../mea/gs-e-invoicing-sa-onboarding.md) | Onboarding process |
| Spain | Spanish electronic invoice (ES) | Sales invoices and project invoices |

> [!NOTE]
> In current implementations in Costa Rica and Panama, the globalization features in the preceding table only generate electronic invoices and store their XML files on the service side. They don't submit the invoices. The submission of Costa Rican and Panamanian electronic invoices requires integration with the [Electronic Invoicing service ISV last-mile connector](../global/e-invoicing-isv-connector.md). However, the integration hasn't yet been released for those countries.

## Preview features

The following table shows the Electronic invoicing Service globalization features that are currently in preview.

| Country or region | Globalization feature name | Business documents |
|-------------------|----------------------------|--------------------|
| Brazil | Brazilian NF-e (BR)| Fiscal document model 55, correction letters, cancellations, and discards |
| Brazil | Brazilian NFS-e ABRASF Curitiba (BR) | Service fiscal documents |
| Brazil | Brazilian NF-e import from e-mail (BR) | Fiscal document model 55 |
| Mexico | Mexican CFDI Interfactura (MX) | Sales invoices, packing slips, inventory transfers, payment complements, and cancellations |
| Poland | [Polish electronic invoice (PL)](../poland/gs-e-invoicing-pol-get-started.md) | Sales invoices, project invoices, and advance invoices |
