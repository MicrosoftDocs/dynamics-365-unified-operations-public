---
# required metadata

title: Submit a VAT return to Altinn web service
description: This topic explains how to submit a VAT return to Altinn web service of Norway.
author: liza-golub
ms.date: 11/18/2021
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
ms.search.validFrom: 2021-11-18
ms.dyn365.ops.version: AX 10.0.22

---

# Submit a VAT return to Altinn web service

When you successfully obtained an access token for Altinn, your Finance is ready to interoperate with Altinn web service to submit VAT return.
Process of VAT return submission to Altinn is composed of lots of steps. For full description of the submission process, see [API](https://skatteetaten.github.io/mva-meldingen/english/api/) page.
The process of VAT return generation and direct submission to Altinn from Finance is supported by using [Electronic Messaging](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/electronic-messaging) (EM) functionality. When you [Import a package of data entities that includes a predefined Electronic messaging (EM) setup](/emea-nor-vat-return-setup#em-setup) to your legal entity, all the necessary actions are imported to you system to submit VAT return to Altinn. The following diagram represents simplified schema of the EM processing delivered with NO VAT return – Altinn setup file.
