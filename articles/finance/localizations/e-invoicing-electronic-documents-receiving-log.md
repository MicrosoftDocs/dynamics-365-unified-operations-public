---
# required metadata

title: Work with Electronic documents receiving log
description: This topic provides description of electronic documents receiving log
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

# Work with Electronic documents receiving log

[!include [banner](../includes/banner.md)]

In Finance and Supply Chain Management, you can use the receipt logs to view the results of processing of incoming documents. 

Go to **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document receipt log** to open the log.

> [!NOTE]
> By default, there is a filter for the Submission status, that doesn't show sucessful submissions, or submissions in progress. The main focus is to show failures. You can clean up the filter to reflect your expectations.

There are three possible submission statuses:
 - **Scheduled** – Electronic invoicing received the submission from Finance and Supply Chain Management, and processing of the electronic invoicing feature is in progress.
 - **Completed** – Electronic invoicing successfully processed the electronic invoicing feature as it was configured to run it.
 - **Failed** – Electronic invoicing encountered an error or was stopped by an exception during processing of the electronic invoicing feature.

Receipt status is updated only when you send a request to Electronic invoicing service to receive and process new electronic documents, or functions and inquires.

The receipt logs include the following additional functions:
 - **Functions** > **Cancel submissions** – This function enables a special submission process in scenarios where the electronic invoice must be approved by an external web service. It instructs Electronic invoicing to send the web service a specific message that is intended to cancel the status of an approved electronic invoice in the web service database.
 - **Functions** > **Resubmit document** – Resubmit the request to Electronic invoicing service to run the receipt process. A new log is created on the Submission details page. 
 - **Inquires** > **Submission details** – View the details of the main submission. The visualization shows the complete execution log of the actions that are configured in the electronic invoicing feature. It also lets users download the files that are created during the processing as the result of each action. In scenarios where the invoice must be approved by an external web service, it lets users view the status of the invoice.
	Processing data contains variables that are sent to Electronic invoicing service, or return back. You can review the value of these variables. 
