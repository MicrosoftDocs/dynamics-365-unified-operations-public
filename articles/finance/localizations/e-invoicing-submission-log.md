---
# required metadata

title: Work with Electronic invoicing submission log
description: This topic provides description of reviewing submission log details
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

# Work with Electronic invoicing submission log

[!include [banner](../includes/banner.md)]

In Finance and Supply Chain Management, you can use the submission logs to view the results of processing the submission to Electronic invoicing. 

Go to **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document submission log** to open the log.
In the **Document type** field, select a value to filter the type of invoices that the logs show. 

There are three possible submission statuses:
 - **Scheduled** – Electronic invoicing received the submission from Finance and Supply Chain Management, and processing of the electronic invoicing feature is in progress.
 - **Completed** – Electronic invoicing successfully processed the electronic invoicing feature as it was configured to run it.
 - **Failed** – Electronic invoicing encountered an error or was stopped by an exception during processing of the electronic invoicing feature.
 
> [!IMPORTANT]
> The submission status refers to the status of the processing that Electronic invoicing does on the electronic invoicing feature. It doesn't refer to the final status of the electronic invoice itself.
> 
> For example, if an electronic invoice must be submitted to an external web service for approval, the submission status might be Completed, but the status of the electronic invoice might be Rejected. In this case, Electronic invoicing was able to successfully process the electronic invoicing feature as it's configured to process that feature. However, the electronic invoice was rejected because it didn't meet the criteria that the web service established for invoice approval.

Submission status is updated only when you send a request to Electronic invoicing service by submitting new electronic documents, or functions and inquires.

The submission logs include the following additional functions:
 - **Functions** > **Cancel submissions** – This function enables a special submission process in scenarios where the electronic invoice must be approved by an external web service. It instructs Electronic invoicing to send the web service a specific message that is intended to cancel the status of an approved electronic invoice in the web service database.
 - **Functions** > **Resubmit document** – Resubmit an electronic document that has already been submitted to Electronic invoicing. A new log is created on the Submission details page. In this case no data is sent to Electronic invoicing service, but it reruns processing of already submitted data.
 - **Functions** > **Send related submission** - Sends the same document from Finance and Supply Chain management. 
 - **Inquires** > **Submission details** – View the details of the main submission. The visualization shows the complete execution log of the actions that are configured in the electronic invoicing feature. It also lets users download the files that are created during the processing as the result of each action. In scenarios where the invoice must be approved by an external web service, it lets users view the status of the invoice.
Processing data contains variables that are sent to Electronic invoicing service, or return back. You can review the value of these variables. For example, variable BusinessDocumentDataModel contains financial data in unified structure submitted to Electronic invoicing service (in JSON structure). You can use this information to troubleshoot the correctness of the data passed for further processing.
 - **Inquires** > **Related submissions** – View the details of child submissions, or the submission of the related documents.
 - **Electronic document** > **Download file** - for a single electronic document or a selected range of the documents returns a ZIP archive with generated electronic files. As Electronic invoicing feature may contain several Actions in the Processing pipeline, that generate different files, you should specify exact Action with the parameter **Export result** to make sure that the result of exactly this Action is exported.
	
