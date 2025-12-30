---
title: Generate emails for approved NF-e and attach DANFE PDF files and NF-e XML files to the emails (Brazil)
description: This article describes how to generate a PDF file from the Documento Auxiliar da Nota Fiscal Eletrônica (DANFE) for a Nota Fiscal eletrônica (NF-e) in Brazil with Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Generate emails for approved NF-e and attach DANFE PDF files and NF-e XML files to the emails (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to generate a PDF file from the Documento Auxiliar da Nota Fiscal Eletrônica (DANFE) for a Nota Fiscal eletrônica (NF-e) in Brazil with Microsoft Dynamics 365 Finance.

You can generate the DANFE for an NF-e as a PDF file and then email the DANFE PDF file and the NF-e XML files that are generated for an approved NF-e to a third-party customer or vendor. Before you create an email message for approved electronic fiscal documents, you must first create an email template. 

The following procedure uses the BRMF demo company.

to generate a PDF file from the DANFE for an NF-e, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Fiscal documents \> Electronic fiscal documents \> Generate emails for NF-e**.
1. Expand the **Run in the background** section.
1. In the **Batch processing** field, select **Yes**.
1. In the **Batch group** field, enter or select a value.
1. Select **Recurrence**.
1. Select the **No end date** option.
1. In the **Count** field, enter a number.
1. Select **OK**.
9. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
