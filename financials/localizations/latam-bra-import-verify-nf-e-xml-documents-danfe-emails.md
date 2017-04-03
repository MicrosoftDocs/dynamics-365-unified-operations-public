---
# required metadata

title: Import and verify NF-e XML documents and DANFE files for Brazil
description: This topic answers questions about the process for importing and verifying Nota fiscal eletrônica (NF-e) XML documents and Documento auxiliar da Nota fiscal eletrônica (DANFE) that you receive in emails.
author: ShylaThompson
manager: AnnBe
ms.date: 2017-04-04
ms.topic: 
ms.prod: 
ms.service: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 101
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 269134
ms.assetid: d4c1d39b-64ec-4ddf-ba27-c0446f80f031
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Import and verify NF-e XML documents and DANFE files for Brazil

This topic answers questions about the process for importing and verifying Nota fiscal eletrônica (NF-e) XML documents and Documento auxiliar da Nota fiscal eletrônica (DANFE) that you receive in emails.

You can perform the following tasks to import Nota fiscal eletrônica (NF-e) XML documents and Documento auxiliar da Nota fiscal eletrônica (DANFE) files that you receive in emails:

-   Set up email accounts to import XML documents and DANFE files for electronic fiscal documents.
-   Set up the Instituto Brasileiro de Geografia e Estatistica (IBGE) code for a state, and then set up a state authority.
-   Import the NF-e XML documents and DANFE files that you receive in emails, and then perform the following tasks:
    -   View the XML document for an NF-e.
    -   View the DANFE for the NF-e XML document.
    -   Use an access key to inquire about the current status of the NF-e at the Secretaria da Fazenda (SEFAZ).
-   Manually enter an access key for an NF-e that you didn't receive an XML document for.
-   Post electronic fiscal documents that have access keys that aren't validated by SEFAZ. Alternatively, you can set up Microsoft Dynamics 365 for Operations to post only electronic fiscal documents that have access keys that are validated by SEFAZ.
-   If you post electronic fiscal documents for which the access keys aren't available on the **Received NF-e XML documents** page, you can update the access keys or XML documents for the electronic fiscal documents after posting is completed. You can view the following posted NF-e documents that require access keys or XML documents:
    -   NF-e documents that have access keys that aren't validated by SEFAZ.
    -   NF-e documents for which the status is updated from **Approved** to **Canceled**.
    -   NF-e documents that XML attachments aren't available for.
    -   NF-e documents for which the access keys aren't available in the received NF-e XML documents.
-   View electronic fiscal documents that aren't posted, but that you received the access keys for.

You can set up Dynamics 365 for Operations to inquire about the status of NF-e access keys at SEFAZ multiple times. In this case, the last inquiry is made after the amount of time that the vendor has to cancel an approved NF-e has passed.

## How do I import XML documents and DANFE files from emails?
You can use the **Import XML files from email** page to import the XML documents and DANFE files for NF-e documents from emails. Before you can import the files, you must set up email accounts that are used to import NF-e XML documents and DANFE files.

## Can I manually update the access key for an NFe that I didn't receive the XML document for?
Yes, you can manually update the access key for an NF-e that you didn't receive the XML document for. You can first generate the list of NF-e documents for which the access keys aren't available for in the NF-e XML documents. To generate this list, on the **Posted NF-e with pending validation** page, select the **Access keys are not found in received NF-e XML documents** option. Then, on the **Received NF-e XML documents** page, update the access key in the **NF-e in the Access key** field.

## Can I post an NFe document without validating the access key?
Yes, you can post an NF-e document without validating the access key. You can validate the access keys for these NF-e documents after posting is completed. To generate a list of NF-e documents that have access keys that aren't validated by SEFAZ, on the **Posted NF-e with pending validation** page, select the **SEFAZ status not inquired** option. Alternatively, to post only the electronic fiscal documents that have access keys that are validated by the SEFAZ, on the **Fiscal establishments** page, on the **NF-e federal** FastTab, select the **Post only NF-e that have valid access keys** option.

## How do I inquire about the status of NFe access keys at the SEFAZ?
You can use the **Received XML inquiry** page to inquire about the status of NF-e access keys at SEFAZ. Inquiries about the status of the access keys are made multiple times before the NF-e is approved. Additionally, a final inquiry about the status us made after the amount of time that the vendor has to cancel an approved NF-e has passed.

## How do I generate a list of NFe documents that weren't posted, but that I received the XML documents for?
You can use the **Posted** option on the **Received NF-e XML documents** page to verify the NF-e documents that weren't posted, but that you received the XML documents for.

