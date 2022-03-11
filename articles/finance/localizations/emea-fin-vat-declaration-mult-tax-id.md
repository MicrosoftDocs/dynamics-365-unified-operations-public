---
# required metadata

title: Support for multiple VAT registration numbers in the VAT return of Finland
description: This topic explains how to support multiple value-added tax (VAT) registration numbers in a VAT return of Finland.
author: liza-golub
ms.date: 12/03/2022
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
ms.search.region: Finland
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 2022-03-12
ms.dyn365.ops.version: AX 10.0.24

---

# VAT declaration (Finland)

[!include [banner](../includes/banner.md)]

If you want to report a VAT return of Finland from a legal entity that has a primary address outside Finland, we recommend that you use the [Tax Calculation](global-tax-calcuation-service-overview.md) service, and that you enable the [Support multiple VAT registration numbers](emea-multiple-vat-registration-numbers.md) feature in the **Feature management** workspace. Additionally, make sure that you set up a VAT registration number in the **Tax registration number** additional field of your production **NO VAT return** processing in the Electronic messages setup. This number is used to send the VAT return to the Norwegian Tax Administration. For more information about how to set up a VAT registration number, see [Set up the VAT registration number of the company that is reporting a VAT return](emea-nor-vat-return-setup.md#vat-registration-number).
