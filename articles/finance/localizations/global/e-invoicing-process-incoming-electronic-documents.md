---
title: Process incoming electronic documents
description: Learn about the processing for incoming electronic documents, which can be processed via being imported or preprocessign when passing applications.
author: ilikond
ms.author: ikondratenko
ms.topic: article
ms.date: 03/13/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# Process incoming electronic documents

[!include [banner](../../includes/banner.md)]

You can import and process incoming electronic documents, such as vendor electronic invoices, in two ways:

- Retrieve files from external channels and pass them directly to your connected application. In the connected application, files undergo additional transformation before you import them into the database.
- Preprocess files in the Electronic Invoicing service before passing them to your connected application.

Electronic invoicing supports two channels for incoming documents: email and Microsoft SharePoint folders.

Use two setup types to specify whether documents undergo preprocessing or are passed directly to your connected application:

- **Import channel** – The system passes the document directly to the connected application.
- **Import channel with processing pipeline** – Set up additional actions that run before the document is passed to the connected application.

For information about how to set up the scenarios for processing incoming electronic documents for the different channels, see [Configure an email channel](e-invoicing-configure-email.md) and [Configure a SharePoint channel](e-invoicing-configure-sharepoint-channel.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
