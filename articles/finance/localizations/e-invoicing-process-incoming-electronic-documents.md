---
# required metadata

title: Process incoming electronic documents overview
description: This topic provides overview of the processing of incoming electronic documents.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

[!include [banner](../includes/banner.md)]

Incoming electronic documents, such as vendor electronic invoices, can be imported and processed by mean of retrieving files from external channels and passing them over directly to the connected application for further transformation and import to the data base, or with the preprocessing within Electronic invoicing service first, and then passing over to your connected applications. 

Electronic invoicing supports two channels for the incoming documents - e-mail, and SharePoint folders.
You can setup the option of preprocessing or direct passing over to your connected application via **Setup type**:
 - **Data channel** - system will pass over the document directly to the connected application
 - **Data channel with processing pipeline** - you can setup additional actions to execute before the document will be passed over to the connected application

To setup the scenarios of processing incoming electronic documents for the channels, follow the articles:
 - [Configure an email channel](e-inv_tut-setup-electronic-invoicing_process-incoming_e-mail.md) to setup e-mail channel.
 - [Configure SharePoint channel](e-inv_tut-setup-electronic-invoicing_process-incoming_sharepoint.md) to setup SharePoint folders.
