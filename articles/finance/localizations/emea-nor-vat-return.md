---
# required metadata

title: VAT return with direct submission to Altinn
description: This topic provides information about the VAT return with direct submission to Altinn feature that can be used to submit value-added tax (VAT) returns in Norway.
author: liza-golub
ms.author: elgolu
ms.date: 03/21/2022
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
ms.search.region: Norway
# ms.search.industry: 
ms.search.validFrom: 2022-11-15

---

# VAT return with direct submission to Altinn

[!include [banner](../includes/banner.md)]

This topic provides information about the **VAT return with direct submission to Altinn** feature in Microsoft Dynamics 365 Finance. This feature can be used to submit value-added tax (VAT) returns in Norway.

In Skatteinfo no. 11/2020, the Norwegian Tax Administration introduced a requirement for VAT return reporting that includes direct digital submission from accounting systems to the Altinn tax portal. This digital submission process replaces the manual process for filing VAT returns for periods as of January 1, 2022. For more information about VAT returns with direct submission to Altinn, see [Mva-meldingen](https://skatteetaten.github.io/mva-meldingen/english/).

The **VAT return with direct submission to Altinn** feature in Finance supports filing a VAT return for [multiple VAT registrations](emea-multiple-vat-registration-numbers.md) and for companies that report as a [VAT group](emea-nor-vat-return-setup.md#vat-group) in the same system database.

For more information about how to prepare a VAT return with direct submission to Altinn, see the following topics:

- [Register an integration point in the ID-porten web portal](emea-nor-vat-return-integration-point.md)
- [Prepare your environment to interoperate with ID-porten and Altinn web services](emea-nor-vat-return-setup.md)
- [Checklist for Electronic messages setup for VAT returns with direct submission to Altinn](emea-nor-vat-return-checklist.md)
- [Authorize your Finance environment to interoperate with ID-porten and Altinn web services](emea-nor-vat-return-authorization.md)
- [Submit a VAT return to the Altinn web service](emea-nor-vat-return-submission.md)

> [!NOTE]
> VAT returns for periods before January 1, 2022, and corrections that are made to those VAT returns, must be reported in the format that is described in [VAT statement for Norway](emea-nor-sales-tax-payment-report.md).

## Privacy notice

When you enable Finance to interoperate with the Norwegian Tax Administration's VAT application programming interface (API), both customer content and personal data will be shared with the Norwegian Tax Administration as part of the submission of your VAT declaration. This information might include the name of the individual who submitted the VAT declaration. To learn more about the kinds of information that are included in your submission, you can view the Norwegian Tax Administration's [requirements](https://go.microsoft.com/fwlink/?linkid=2178205). A system administrator can disable the interoperation with the Norwegian Tax Administration's web service in Finance by going to **Tax** \> **Setup** \> **Electronic Messages**.

Your privacy is important to us. To learn more, read our [Privacy notice](https://go.microsoft.com/fwlink/?LinkId=521839).
