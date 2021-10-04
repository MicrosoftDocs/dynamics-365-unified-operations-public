---
# required metadata

title: VAT return of the United Kingdom to support multiple VAT registration numbers
description: This topic explains how to support multiple VAT registration numbers in VAT return of the United Kingdom
author: liza-golub
ms.date: 10/04/2021
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

# VAT return of the United Kingdom to support multiple VAT registration numbers

[!include [banner](../includes/banner.md)]

On July 13, 2017, the Financial Secretary to the Treasury and Paymaster General in the UK announced that MTD for VAT would take effect on April 1, 2019.

For more information about MTD for VAT, see [Making Tax Digital for VAT: legislation overview](https://www.gov.uk/government/consultations/making-tax-digital-reforms-affecting-businesses/making-tax-digital-for-vat-legislation-overview).

For more information about the MTD VAT feature setup and usage in Microsoft Dynamics 365 Finance, see the [Making Tax Digital – VAT return submission in the United Kingdom](emea-gbr-mtd-vat-integration.md).

The MTD VAT feature in Finance supports filing a VAT return for [Multiple VAT registrations](emea-multiple-vat-registration-numbers.md), starting from version 10.0.20 and for companies that report as a [VAT group](https://www.gov.uk/hmrc-internal-manuals/vat-groups) in the same system database, starting from version 10.0.7.

To be able to report VAT return of the United Kingdom from a legal entity with primary address outside of the United Kingdom, we recommend using the [Tax service](global-tax-calcuation-service-overview.md), enable the [**Support multiple VAT registration numbers**](emea-multiple-vat-registration-numbers.md) feature is enabled in the **Feature management** workspace and make sure you set up VAT registration number that should be used to send the VAT return to HMRC in **Tax registration number** additional field of your production **UK MTD VAT returns** processing in **Electronic messages** setup. For more information about VAT registration number setup, see [Set up the VAT registration number of the company that is reporting VAT](emea-gbr-mtd-vat-integration-setup.md#vrn)
