---
# required metadata

title: Support for multiple VAT registration numbers in Immediate Supply of Information on VAT (SII) of Spain
description: This topic describes the scope of the Immediate Supply of Information on VAT (Suministro Inmediato de Información del IVA, SII) feature of Spain to support multiple VAT registration numbers.
author: liza-golub
ms.date: 10/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Spain
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 2021-01-11
ms.dyn365.ops.version: 10.0.24

---

# Support for multiple VAT registration numbers in Immediate Supply of Information on VAT (SII) of Spain

[!include [banner](../includes/banner.md)]

According to R.D. 596/2016 in Spain, a new value-added tax (VAT) management system that is based on the Immediate Supply of Information on VAT (Suministro Inmediato de Información del IVA \[SII\]) allows for a two-way, automated relationship between the Spanish Tax Agency (La Agencia Estatal de Administración Tributaria \[AEAT\]) and the taxpayer. In this topic, this system is referred to as the SII system. As of July 1, 2017, taxpayers who are subject to SII, and others who voluntarily adopt it, must send details of their billing records within four days through online filing on the AEAT website.

For more information about the SII system of Spain, see the [Immediate Supply of Information on VAT (SII) official website](https://www.agenciatributaria.es/AEAT.internet/en_gb/Inicio/La_Agencia_Tributaria/Campanas/Suministro_Inmediato_de_Informacion_en_el_IVA__SII_/Suministro_Inmediato_de_Informacion_en_el_IVA__SII_.shtml).

For more information about how to set up and use the SII feature in Microsoft Dynamics 365 Finance, see [Immediate Supply of Information on VAT (Suministro Inmediato de Información del IVA, SII)](emea-esp-sii.md).

As of Finance version 10.0.22, if you're using the [Tax Calculation](global-tax-calcuation-service-overview.md) service, and the [Support multiple VAT registration numbers](emea-multiple-vat-registration-numbers.md) feature is enabled in the **Feature management** workspace, you can [report the following reports to the SII system of Spain from a legal entity that has a primary address outside Spain](emea-esp-sii.md#multiple-vat):

- 'Libro de registro de facturas Expedidas': **Record book of issued invoices**
- 'Libro de registro de facturas Recibidas': **Record book of received invoices**
