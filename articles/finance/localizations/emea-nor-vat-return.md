---
# required metadata

title: VAT return with direct submission to Altinn
description: This topic explains how to set up the VAT return with direct submission to Altinn and use it to submit a VAT return in Norway. 
author: liza-golub
ms.author: elgolu
ms.date: 11/22/2021
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

This topic explains how to set up the VAT return with direct submission to Altinn in Microsoft Dynamics 365 Finance and use it to submit a VAT return in Norway.

Within Skatteinfo no. 11/2020, the Norwegian Tax Administration introduced a requirement of VAT return reporting that includes direct digital submission from accounting systems to the Altinn tax portal to replace the manual VAT return filing for periods starting from January 1, 2022. 
For more information about VAT return with direct submission to Altinn, see [Mva-meldingen](https://skatteetaten.github.io/mva-meldingen/english/).

The **VAT return with direct submission to Altinn** feature in Finance supports filing a VAT return for [Multiple VAT registrations](emea-multiple-vat-registration-numbers.md) and for companies that report as a [VAT group](emea-nor-vat-return-setup.md#vat-group) in the same system database.

For more information about how to prepare a VAT return with direct submission to Altinn, see the following topics:

-	[Register an integration point in ID-porten web portal](emea-nor-vat-return-integration-point.md)
-	[Prepare your environment to interoperate with ID-porten and Altinn web services](emea-nor-vat-return-setup.md)
-	[Checklist for Electronic messages setup for VAT return](emea-nor-vat-return-checklist.md)
-	[Authorize your Finance environment to interoperate with ID-Porten and Altinn web services](emea-nor-vat-return-authorization.md)
-	[Submit a VAT return to Altinn web service](emea-nor-vat-return-submission.md)

## Privacy notice

When you enable Finance to interoperate with the Norwegian Tax Authority’s VAT API, both customer content and personal data will be shared with the Norwegian Tax Authority as part of the submission of your VAT declaration. This information may include the name of the individual who submitted the VAT declaration. To learn more about the kinds of information that is included in your submission, you can view the Norwegian Tax Authority’s requirements [here](https://go.microsoft.com/fwlink/?linkid=2178205). A system administrator can disable the interoperation with the Norwegian Tax Authority’s web service in Finance by going to **Tax** > **Setup** > **Electronic Messages**.
Your privacy is important to us. To learn more, read our [Privacy notice](https://go.microsoft.com/fwlink/?LinkId=521839).

