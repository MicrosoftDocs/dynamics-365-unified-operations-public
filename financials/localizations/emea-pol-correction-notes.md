---
# required metadata

title: Correction notes
description: This topic provides information about correction notes. A correction note is a document that is required by local regulations in Poland. It's used to correct errors on a vendor invoice. 
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 263404
ms.assetid: c66b3a3d-f199-4da5-965a-b69377c5dd22
ms.search.region: Poland
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Correction notes

[!include[banner](../includes/banner.md)]


This topic provides information about correction notes. A correction note is a document that is required by local regulations in Poland. It's used to correct errors on a vendor invoice. 

If a vendor issues a sales document to a company, but makes a mistake about the company’s address or value-added tax (VAT) identification number, local regulations in Poland require that the company issue a correction note to the vendor. A correction note contains both the original text and the corrected text. You can create, post, and print a correction note from the Correction notes journal. The following fields are available on the Correction notes journal.
| Field           | Description                                                                                                                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Show            | Select which correction note documents to show, based on their posting status.                                                                                                                                                                                           |
| Invoice account | Select the vendor account number for the corrected invoice.                                                                                                                                                                                                              |
| Invoice         | Select the invoice ID for the invoice that must be corrected.                                                                                                                                                                                                            |
| Date            | The invoice transaction date.                                                                                                                                                                                                                                            |
| Correction note | Enter a unique identification number for the correction note. If a number sequence code is set up for references to correction notes, the correction note number is automatically generated. Number sequences can be set up on the **Accounts payable parameters** page. |
| Document date   | Enter a date for the correction note. If you don't specify a document date, the current date is used as the posting date.                                                                                                                                                |
| Posted          | A selected option indicates that the selected correction note has been posted.                                                                                                                                                                                           |
| Original text   | Enter the original text from the invoice that must be corrected.                                                                                                                                                                                                         |
| Corrected text  | Enter the correct text for the invoice.                                                                                                                                                                                                                                  |





