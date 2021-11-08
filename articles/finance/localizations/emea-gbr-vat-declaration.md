---
# required metadata

title: Support for multiple VAT registration numbers in the VAT return of the United Kingdom
description: This topic explains how to support multiple value-added tax (VAT) registration numbers in a VAT return of the United Kingdom.
author: liza-golub
ms.date: 10/12/2021
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
ms.search.region: United Kingdom
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 2021-04-10
ms.dyn365.ops.version: AX 10.0.21

---

# Support for multiple VAT registration numbers in the VAT return of the United Kingdom

[!include [banner](../includes/banner.md)]

On July 13, 2017, the Financial Secretary to the Treasury and Paymaster General in the United Kingdom announced that Making Tax Digital (MTD) for VAT would take effect on April 1, 2019.

For more information about MTD for VAT, see [Making Tax Digital for VAT: legislation overview](https://www.gov.uk/government/consultations/making-tax-digital-reforms-affecting-businesses/making-tax-digital-for-vat-legislation-overview).

For more information about how to set up and use the MTD VAT feature in Microsoft Dynamics 365 Finance, see [Making Tax Digital – VAT return submission in the United Kingdom](emea-gbr-mtd-vat-integration.md).

As of Finance version 10.0.20, the MTD VAT feature lets you file a VAT return for [multiple VAT registrations](emea-multiple-vat-registration-numbers.md). As of Finance version 10.0.7, the feature supports companies that report as a [VAT group](https://www.gov.uk/hmrc-internal-manuals/vat-groups) in the same system database.

If you want to be able to report a VAT return of the United Kingdom from a legal entity that has a primary address outside of the United Kingdom, we recommend that you use the [Tax Calculation](global-tax-calcuation-service-overview.md) service, and that you enable the [Support multiple VAT registration numbers](emea-multiple-vat-registration-numbers.md) feature in the **Feature management** workspace. Additionally, make sure that you set up a VAT registration number in the **Tax registration number** additional field of your production **UK MTD VAT returns** processing in the Electronic messages setup. This number will be used to send the VAT return to Her Majesty's Revenue and Customs (HMRC). For more information about how to set up a VAT registration number, see [Set up the VAT registration number of the company that is reporting VAT](emea-gbr-mtd-vat-integration-setup.md#vrn).
