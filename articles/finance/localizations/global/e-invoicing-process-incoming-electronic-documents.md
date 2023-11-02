---
title: Processing of incoming electronic documents
description: This article provides an overview of the processing for incoming electronic documents.
author: gionoder
ms.date: 02/28/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: gionoder
ms.search.validFrom: 
ms.dyn365.ops.version: 
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Processing of incoming electronic documents

[!include [banner](../../includes/banner.md)]

Incoming electronic documents, such as vendor electronic invoices, can be imported and processed in two ways:

- Files are retrieved from external channels and passed directly to your connected application. There, they undergo additional transformation and are then imported into the database.
- Files undergo preprocessing in the Electronic Invoicing service and are then passed to your connected application.

Electronic invoicing supports two channels for incoming documents: e-mail and Microsoft SharePoint folders.

There are twp setup types to specify whether documents undergo preprocessing or are passed directly to your connected application:

- **Data channel** – The system will pass the document directly to the connected application.
- **Data channel with processing pipeline** – You can set up additional actions that will be run before the document is passed to the connected application.

For information about how to set up the scenarios for processing incoming electronic documents for the different channels, see [Configure an email channel](e-invoicing-configure-email.md) and [Configure a SharePoint channel](e-invoicing-configure-sharepoint-channel.md).
