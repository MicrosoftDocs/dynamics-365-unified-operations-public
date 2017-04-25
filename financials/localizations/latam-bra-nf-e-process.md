---
# required metadata

title: NF-e process overview for Brazil
description: This topic provides an overview of the process for setting up and submitting a Nota fiscal eletrônica (NF-e) to register the movement of items and services between two parties.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: EFDocContingencyMode_BR, EFDocContingencyModeHistory_BR, EFDocCorrectionLetter_BR, EFDocEmailAccountConfiguration_BR, EFDocEmailStatus_BR, EFDocHist_BR, EFDocParameters_BR, EFDocServiceInquire_BR, FiscalDocument_BR
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2231
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 269114
ms.assetid: 7cb522a4-2f84-4399-a60d-8692df6e08f3
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# NF-e process overview for Brazil

[!include[banner](../includes/banner.md)]


This topic provides an overview of the process for setting up and submitting a Nota fiscal eletrônica (NF-e) to register the movement of items and services between two parties.

You can use a Nota fiscal eletrônica (NF-e) to register the movement of items and services between two parties. You can generate an NF-e from any of the following fiscal documents:

-   Sales orders
-   Purchase orders for non-taxpayer vendors
-   Project invoices
-   Tax fiscal documents
-   Free text invoices

Before you can generate an NF-e, you must complete the following tasks:

-   Set up web services, rejection codes, and schemas for a domain.
-   For each fiscal establishment, set up a certificate, an environment, an NF-e version, an authority, a template, schema validation, and a contingency mode for NF-e. Additionally, set up automatic printing of the Documento auxiliar da Nota fiscal eletrônica (DANFE), so that the DANFE is automatically printed after NF-e approval.
-   Set up web services that are related to a fiscal authority.
-   Set up a fiscal document type for an NF-e.

After you generate an NF-e, you can submit the digitally signed NF-e to the Secretaria da Fazenda (SEFAZ) in an XML message. The items can be delivered after the NF-e is electronically approved by SEFAZ. The NF-e process includes the following steps:

1.  The fiscal establishment posts a fiscal document by using a fiscal document type that is set up for fiscal document model 55 to generate an NF-e.
2.  The NF-e export or import process detects the posted fiscal document for the fiscal document model 55 and generates an XML message in the specified format. A separate XML message is generated for each NF-e. The XML message is transmitted to SEFAZ.
3.  SEFAZ processes the XML message and returns a protocol and status for each NF-e. The NF-e status and protocol are then assigned to the NF-e that is used in the NF-e export or import process. The status that is returned can be **Approved**, **Denied**, **Discarded**, **Canceled**, **Rejected non fixable**, or **Rejected**. This information is used to update the fiscal document status in Microsoft Dynamics 365 for Operations.

After the status of the NF-e is received from SEFAZ, you can perform the following tasks, depending on the status:

-   If the NF-e is approved, you can print the DANFE. Alternatively, if the **Print DANFE when NF-e is approved** option is selected on the **NF-e federal** FastTab of the **Fiscal establishments** page, the DANFE is printed automatically.
-   If the NF-e is denied, you must cancel the NF-e.
-   If the NF-e is rejected and can be fixed, you can correct the incorrect information, and then click **Resend** on the **NF-e federal** tab of the **Fiscal document** page to resend the NF-e to SEFAZ.
-   If the NF-e is rejected and can't be fixed, you must cancel the discarded NF-e that has discarded number. The NF-e export or import process detects the fiscal document that is posted and marked for discard, and then generates an XML message in the specified format for the discarded NF-e number. This XML message is then transmitted to SEFAZ, and the fiscal document status is set to **Discarded**.




