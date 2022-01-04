---
# required metadata

title: Support for multiple VAT registration numbers in the VAT return of Norway
description: This topic explains how to support multiple value-added tax (VAT) registration numbers in a VAT return of Norway.
author: liza-golub
ms.date: 01/04/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Norway
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 2021-22-12
ms.dyn365.ops.version: AX 10.0.21

---

# Support for multiple VAT registration numbers in the VAT return of Norway

[!include [banner](../includes/banner.md)]

In Skatteinfo no. 11/2020, the Norwegian Tax Administration introduced a requirement for VAT return reporting that includes direct digital submission from accounting systems to the Altinn tax portal. This digital submission process replaces the manual process for filing VAT returns for periods as of January 1, 2022. For more information about VAT returns with direct submission to Altinn, see [Mva-meldingen](https://skatteetaten.github.io/mva-meldingen/english/). For more information about how to set up and use the **VAT return with direct submission to Altinn** feature in Microsoft Dynamics 365 Finance, see [VAT return with direct submission to Altinn](emea-nor-vat-return.md).

If you want to report a VAT return of Norway from a legal entity that has a primary address outside Norway, we recommend that you use the [Tax Calculation](global-tax-calcuation-service-overview.md) service, and that you enable the [Support multiple VAT registration numbers](emea-multiple-vat-registration-numbers.md) feature in the **Feature management** workspace. Additionally, make sure that you set up a VAT registration number in the **Tax registration number** additional field of your production **NO VAT return** processing in the Electronic messages setup. This number is used to send the VAT return to the Norwegian Tax Administration. For more information about how to set up a VAT registration number, see [Set up the VAT registration number of the company that is reporting a VAT return](emea-nor-vat-return-setup.md#vat-registration-number).
