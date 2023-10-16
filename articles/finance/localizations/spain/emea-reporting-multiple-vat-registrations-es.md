---
title: Support for multiple VAT registration numbers in reporting for Spain
description: This article explains how to support multiple value-added tax (VAT) registration numbers in reporting for Spain.
author: liza-golub
ms.date: 7/13/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Spain
ms.author: egolub
ms.search.validFrom: 2023-04-10
ms.dyn365.ops.version: AX 10.0.13
---

# Support for multiple VAT registration numbers in reporting for Spain

[!include [banner](../../includes/banner.md)]

This article provides information about the regulatory reports for Spain that are available for legal entities that use multiple value-added tax (VAT) registration numbers functionality. For more information about **Multiple VAT registration numbers** functionality, the prerequisites that must be met before it's used, and the required setup, see [Multiple VAT registration numbers](../global/emea-multiple-vat-registration-numbers.md)

For general information about reporting for multiple VAT registrations, see [Reporting for multiple VAT registrations](../global/emea-reporting-for-multiple-vat-registrations.md).

When your legal entity is configured for reporting for multiple VAT registrations, the following reports are available for reporting for Spain:

| Report name     | Release | Electronic reporting (ER) format, version                |
|-----------------|---------|-----------------------------------|
| [Intrastat](emea-esp-intrastat.md)       | 10.0.21 | Intrastat (ES), version 16.7      |
| [EU sales list](emea-esp-sales-list.md)   | 10.0.21 | 	EU Sales list (ES), version 9.2 |
| [VAT declaration](emea-esp-vat-declaration-spain.md) | 10.0.23 | VAT Declaration TXT(ES), version 101.28<br>VAT Declaration Excel (ES), version 101.28.17 |
| [Immediate Supply of Information on VAT (SII)](emea-esp-sii.md)(*) | 10.0.22 | SII Invoice Received Format (ES), version 107.45<br>SII Invoice Issued Format (ES), version 107.51 |

> [!NOTE]
> (*) As of Finance version 10.0.22, if you're using the [Tax Calculation](../global/global-tax-calcuation-service-overview.md) service, and the [Support multiple VAT registration numbers](../global/emea-multiple-vat-registration-numbers.md) feature is enabled in the **Feature management** workspace, you can [report the following reports to the SII system of Spain from a legal entity that has a primary address outside Spain](emea-esp-sii.md#multiple-vat):
> - 'Libro de registro de facturas Expedidas': **Record book of issued invoices**
> - 'Libro de registro de facturas Recibidas': **Record book of received invoices**



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
