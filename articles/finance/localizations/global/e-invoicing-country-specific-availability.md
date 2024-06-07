---
title: Availability of Electronic invoicing Service features by country or region
description: Learn about the out-of-box features that are available for each country or region, including overviews on generally available features.
author: ilikond
ms.author: ikondratenko
ms.topic: article
ms.date: 02/12/2024
ms.custom:
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: 
ms.search.validFrom:
ms.search.form: 
ms.dyn365.ops.version: 
---

# Availability of Electronic invoicing Service features by country or region

[!include [banner](../../includes/banner.md)]

The availability of Electronic invoicing Service globalization features depends on the country or region where you're located. Although some features are generally available, others are still in preview.

> [!NOTE]
> This article is related only to the globelization features introduced in scope of Electronic Invoicing Service and doesn't cover other approaches for supported e-Invoicing capabilities for some countries designed based on built-in X++ code and Electronic Messaging framework.
> For more information, see [Electronic Invoicing](gs-e-invoicing-service-overview).

## Generally available features

The following table shows the Electronic invoicing features that are generally available.

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
| Netherlands | Dutch electronic invoice (NL) | Sales invoices and project invoices |
| New Zealand | [Electronic invoicing for Australia and New Zealand](../apac/GS-apac-aus-nzl-electronic-invoices.md) | Sales invoices and project invoices |
| Norway | Norwegian electronic invoice (NO) | Sales invoices and project invoices |
| Panama | LATAM e-invoice PA | Sales invoices and project invoices |
| Saudi Arabia | Saudi Arabian electronic invoice (SA) | Phase 1: Sales invoices and project invoices |
| Saudi Arabia | Saudi Arabian Zatca submission (SA) | Phase 2: Sales invoices and project invoices |
| Saudi Arabia | Saudi Arabian Zatca compliance check (SA) | Phase 2: Onboarding process |
| Spain | Spanish electronic invoice (ES) | Sales invoices and project invoices |

> [!IMPORTANT]
> In current implementations in Chile, Costa Rica, and Panama, the standard submission procedure described above only generates electronic invoices and stores their XML files on the service side, but it doesn’t submit the invoices. For the submission of Chilean, Costa Rican, and Panamanian electronic invoices, integration with the [Electronic Invoicing service ISV last-mile connector](../global/e-invoicing-isv-connector.md) is required. However, the integration hasn’t been released yet for these countries.

## Preview features

The following table shows the Electronic invoicing Service globalization features that are currently in preview.

| Country or region | Globalization feature name | Business documents |
|-------------------|----------------------------|--------------------|
| Brazil | Brazilian NF-e (BR)| Fiscal document model 55, correction letters, cancellations, and discards |
| Brazil | Brazilian NFS-e ABRASF Curitiba (BR) | Service fiscal documents |
| Brazil | Brazilian NF-e import from e-mail (BR) | Fiscal document model 55 |
| Malaysia | (Preview) Malaysian electronic invoicing (MY) | Sales invoices, project invoices, and self invoices |
| Mexico | Mexican CFDI Interfactura (MX) | Sales invoices, packing slips, inventory transfers, payment complements, and cancellations |
| Poland | Polish KSeF submission (PL) | Sales invoices, project invoices, and advance invoices |
