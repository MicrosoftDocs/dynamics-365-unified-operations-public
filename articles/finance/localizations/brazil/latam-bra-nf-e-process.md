---
title: Brazil NF-e process overview
description: This article provides an overview of the process for setting up and submitting a Nota fiscal eletrônica (NF-e) to register the movement of items and services between two parties.
author: ankviklis
ms.author: ankviklis
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 03/04/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-11-30
ms.search.form: EFDocContingencyMode_BR, EFDocContingencyModeHistory_BR, EFDocCorrectionLetter_BR, EFDocEmailAccountConfiguration_BR, EFDocEmailStatus_BR, EFDocHist_BR, EFDocParameters_BR, EFDocServiceInquire_BR, FiscalDocument_BR
ms.assetid: 7cb522a4-2f84-4399-a60d-8692df6e08f3
---

# Brazil NF-e process overview

[!include [banner](../../includes/banner.md)]

This article provides an overview of the process for setting up and submitting a Nota fiscal eletrônica (NF-e) to register the movement of items and services between two parties.

You can use a Nota fiscal eletrônica (NF-e) to register the movement of items and services between two parties. You can generate an NF-e from any of the following fiscal documents:

- Sales orders
- Purchase orders for non-taxpayer vendors
- Project invoices
- Tax fiscal documents
- Free text invoices

Before you can generate an NF-e, complete the following tasks:

- Set up web services, rejection codes, and schemas for a domain.
- For each fiscal establishment, set up a certificate, an environment, an NF-e version, an authority, a template, schema validation, and a contingency mode for NF-e. Additionally, set up automatic printing of the Documento auxiliar da Nota fiscal eletrônica (DANFE), so that the DANFE is automatically printed after NF-e approval.
- Set up web services that are related to a fiscal authority.
- Set up a fiscal document type for an NF-e.

After you generate an NF-e, you can submit the digitally signed NF-e to the Secretaria da Fazenda (SEFAZ) in an XML message. You can deliver the items after SEFAZ electronically approves the NF-e. The NF-e process includes the following steps:

1. The fiscal establishment posts a fiscal document by using a fiscal document type that is set up for fiscal document model 55 to generate an NF-e.
1. The NF-e export or import process detects the posted fiscal document for the fiscal document model 55 and generates an XML message in the specified format. It generates a separate XML message for each NF-e. The process transmits the XML message to SEFAZ.
1. SEFAZ processes the XML message and returns a protocol and status for each NF-e. The NF-e export or import process assigns the NF-e status and protocol to the NF-e. The status that SEFAZ returns can be **Approved**, **Denied**, **Discarded**, **Canceled**, **Rejected non fixable**, or **Rejected**. The process uses this information to update the fiscal document status.

After you receive the status of the NF-e from SEFAZ, perform the following tasks depending on the status:

- If the NF-e is approved, you can print the DANFE. Alternatively, if you select the **Print DANFE when NF-e is approved** option on the **NF-e federal** FastTab of the **Fiscal establishments** page, the process prints the DANFE automatically.
- If the NF-e is denied, you must cancel the NF-e.
- If the NF-e is rejected and can be fixed, you can correct the incorrect information, and then select **Resend** on the **NF-e federal** tab of the **Fiscal document** page to resend the NF-e to SEFAZ.
- If the NF-e is rejected and can't be fixed, you must cancel the discarded NF-e that has discarded number. The NF-e export or import process detects the fiscal document that is posted and marked for discard, and then generates an XML message in the specified format for the discarded NF-e number. The process transmits this XML message to SEFAZ, and sets the fiscal document status to **Discarded**.

## Additional resources

[NF-e certificates](latam-bra-nfe-certs.md)

[Set up NF-e federal parameters (Brazil)](br-00053-1-set-up-nf-e-federal-parameters.md)

[Set up NF-e parameters for a fiscal establishment (Brazil)](br-00053-2-set-up-nf-e-parameters-fiscal-establishment.md)

[Generate emails for approved NF-e and attach DANFE PDF files and NF-e XML files to the emails (Brazil)](br-00053-3-generate-emails-approved-nf-e-attach-danfe-pdf-files-nf-e-xml-files-emails.md)

[NF-e 3.10 (Brazil)](br-00053-nf-e-3-10.md)

[Automatic transmission of NF-e fiscal documents (Brazil)](br-00058-automatic-transmission-nf-e-fiscal-documents.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
