---
title: Process incoming electronic documents
description: Learn about the processing for incoming electronic documents, which can be processed via being imported or preprocessign when passing applications.
author: ilikond
ms.author: ikondratenko
ms.topic: article
ms.date: 02/12/2024
ms.custom: 
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom:
ms.search.form: 
ms.dyn365.ops.version:
---

# Process incoming electronic documents

[!include [banner](../../includes/banner.md)]

Incoming electronic documents, such as vendor electronic invoices, can be imported and processed in two ways:

- Files are retrieved from external channels and passed directly to your connected application. There, they undergo additional transformation and are then imported into the database.
- Files undergo preprocessing in the Electronic Invoicing service and are then passed to your connected application.

Electronic invoicing supports two channels for incoming documents: e-mail and Microsoft SharePoint folders.

There are two setup types to specify whether documents undergo preprocessing or are passed directly to your connected application:

- **Import channel** – The system will pass the document directly to the connected application.
- **Import channel with processing pipeline** – You can set up additional actions that will be run before the document is passed to the connected application.

For information about how to set up the scenarios for processing incoming electronic documents for the different channels, see [Configure an email channel](e-invoicing-configure-email.md) and [Configure a SharePoint channel](e-invoicing-configure-sharepoint-channel.md).
