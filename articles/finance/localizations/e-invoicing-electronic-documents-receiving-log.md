---
# required metadata

title: Work with the Electronic documents receiving log
description: This topic provides information about how to work with the electronic documents receiving log.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: 
# ms.search.industry: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Work with the Electronic documents receiving log

[!include [banner](../includes/banner.md)]

In Dynamics 365 Finance and Dynamics 365 Supply Chain Management, you can use receipt logs to view the results of processing of incoming documents. 

Go to **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document receipt log** to open the log.

> [!NOTE]
> By default, there is a filter for the **Submission status**, that doesn't show sucessful or in progress submissions. The main focus of this filter is to show failures. You can clean up the filter to reflect your expectations.

There are three possible submission statuses:
 - **Scheduled** – Electronic invoicing received the submission from Finance or Supply Chain Management, and is currently processing the electronic invoicing feature.
 - **Completed** – Electronic invoicing has successfully processed the electronic invoicing feature as it was configured to run it.
 - **Failed** – Electronic invoicing encountered an error or was stopped by an exception during processing of the electronic invoicing feature.

Receipt status is updated only when you send a request to the Electronic invoicing service to receive and process new electronic documents or functions and inquires.

The receipt logs include the following additional functions:
 - **Functions** > **Cancel submissions** – This function enables a special submission process in scenarios where the electronic invoice must be approved by an external web service. Electronic invoicing is instructed to send a specific message the web service that is intended to cancel the status of an approved electronic invoice in the web service database.
 - **Functions** > **Resubmit document** – Resubmit the request to Electronic invoicing service to run the receipt process. A new log is created on the **Submission details** page. 
 - **Inquires** > **Submission details** – View the details of the main submission. The visualization shows the complete execution log of the actions that are configured in the electronic invoicing feature. You can download the files that are created during the processing as the result of each action. When the invoice must be approved by an external web service, you can view the status of the invoice.

Processing data contains variables that are sent to the Electronic invoicing service or returned back. You can review the value of these variables. 
