---
title: Import and verify NF-e XML documents and DANFE files for Brazil
description: Learn how to import and verify received Nota fiscal eletrônica (NF-e) XML documents and Documento auxiliar da Nota fiscal eletrônica (DANFE).
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/04/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.assetid: d4c1d39b-64ec-4ddf-ba27-c0446f80f031
---

# Import and verify NF-e XML documents and DANFE files for Brazil

[!include [banner](../../includes/banner.md)]

This article provides information about how to import and verify received Nota fiscal eletrônica (NF-e) XML documents and Documento auxiliar da Nota fiscal eletrônica (DANFE) files.

To import Nota fiscal eletrônica (NF-e) XML documents and Documento auxiliar da Nota fiscal eletrônica (DANFE) files that you receive in emails, perform the following tasks:

- Set up email accounts to import XML documents and DANFE files for electronic fiscal documents.
- Set up the Instituto Brasileiro de Geografia e Estatistica (IBGE) code for a state, and then set up a state authority.
- Import the NF-e XML documents and DANFE files that you receive in emails, and then perform the following tasks:
  - View the XML document for an NF-e.
  - View the DANFE for the NF-e XML document.
  - Use an access key to check the status of the NF-e at the Secretaria da Fazenda (SEFAZ).
- Manually enter an access key for an NF-e that you didn't receive an XML document for.
- Post electronic fiscal documents that have access keys that SEFAZ didn't validate. You can also set up Dynamics 365 Finance to post only electronic fiscal documents that have access keys that SEFAZ validated.
- If you post electronic fiscal documents and the access keys aren't available on the **Received NF-e XML documents** page, update the access keys or XML documents after posting. You can view posted NF-e documents that require access keys or XML documents. These documents include:
  - NF-e documents that have access keys that SEFAZ didn't validate.
  - NF-e documents for which the status is updated from **Approved** to **Canceled**.
  - NF-e documents that XML attachments aren't available for.
  - NF-e documents for which the access keys aren't available in the received NF-e XML documents.
- View electronic fiscal documents that aren't posted, but that you received the access keys for.

You can set up Finance to check the status of NF-e access keys at SEFAZ multiple times. In this case, the last inquiry is made after the amount of time that the vendor has to cancel an approved NF-e passes.

## How do I import XML documents and DANFE files from emails?

Use the **Import XML files from email** page to import the XML documents and DANFE files for NF-e documents from emails. Before you can import the files, you must set up email accounts that are used to import NF-e XML documents and DANFE files.

## Can I manually update the access key for an NF-e that I didn't receive the XML document for?

Yes, you can manually update the access key for an NF-e that you didn't receive the XML document for. You can generate the list of NF-e documents that don't have access keys in the NF-e XML documents. To generate this list, select the **Access keys are not found in received NF-e XML documents** option on the **Posted NF-e with pending validation** page. Then, on the **Received NF-e XML documents** page, update the access key in the **NF-e in the Access key** field.

## Can I post an NF-e document without validating the access key?

Yes, you can. You can validate the access keys for these NF-e documents after posting is complete. To generate a list of NF-e documents with access keys that aren't validated, select **SEFAZ status not inquired** on the **Posted NF-e with pending validation** page. To post only the electronic fiscal documents that have validated access keys, select **Post only NF-e that have valid access keys** on the **Fiscal establishments** page.

## How do I check the status of NF-e access keys at the SEFAZ?

Use the **Received XML inquiry** page to check the status of NF-e access keys at SEFAZ. The system makes multiple inquiries about the status of the access keys before the NF-e is approved. Additionally, the system makes a final inquiry about the status after the amount of time that the vendor has to cancel an approved NF-e has passed.

## How do I generate a list of NF-e documents that weren't posted, but that I received the XML documents for?

On the **Received NF-e XML documents** page, select **Posted** to verify the NF-e documents that you received XML documents for, but weren't posted.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
