---
# required metadata

title: Processing incoming electronic documents
description: This topic provides an overview of processing incoming electronic documents.
author: dkalyuzh
ms.date: 02/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 
---

[!include [banner](../includes/banner.md)]

Incoming electronic documents, such as vendor electronic invoices, can be imported and processed by:

 - Retrieving files from external channels and passing them directly to the connected application for further transformation and import to the database.
 - Preprocessing the files within the Electronic invoicing service, and then passing the files over to your connected applications. 

Electronic invoicing supports two channels for incoming documents, e-mail and SharePoint folders.
You can set up the option of preprocessing or direct passing to your connected application by using a selected **Setup type**.

 - **Data channel** - The system will pass the document directly to the connected application.
 - **Data channel with processing pipeline** - Set up additional actions to execute before the document is passed to the connected application.

To set up the scenarios of processing incoming electronic documents for the channels, see, [Configure an email channel](e-invoicing-configure-email.md) and [Configure SharePoint channel](e-invoicing-configure-sharepoint-channel.md).
