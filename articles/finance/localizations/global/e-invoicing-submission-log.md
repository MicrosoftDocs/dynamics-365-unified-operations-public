---
title: Work with the Electronic document submission log
description: Learn how to work with the Electronic document submission log, including outlines on the Schedule, Completed, and Failed submission statuses.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/30/2025
ms.reviewer: johnmichalak

---

# Work with Electronic document submission log

[!include [banner](../../includes/banner.md)]

In Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management, you can use the submission log to view the results of the processing of submissions to Electronic invoicing.

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log** to open the log.
2. In the **Document type** field, select a value to filter the type of invoices that the log shows.

There are possible submission statuses:

- **Scheduled** – Electronic invoicing received the submission from Finance or Supply Chain Management, and scheduled it for further processing by the related electronic invoicing feature.
- **Executing** – Electronic invoicing started processing according to the applicable electronic invoicing feature's pipeline.
- **Pending** – Electronic invoicing is waiting for the response from external web-services involved into the related pipeline action's processing.
- **Completed** – Electronic invoicing successfully processed the electronic invoicing feature in the way that it was configured to process it.
- **Failed** – Electronic invoicing encountered an error or was stopped by an exception while it was processing the electronic invoicing feature.
- **Canceled** – The submission has been explicitly cancelled by a user from Finance or Supply Chain Management using the **Cancel submissions** functionality. For more information, refer to [Cancel submissions](#Cancel).

> [!IMPORTANT]
> The submission status refers to the processing status of the electronic invoicing feature by Electronic invoicing. It doesn't refer to the final status of the electronic invoice itself. For example, if an electronic invoice must be submitted to an external web service for approval, the submission status might be **Completed**, but the status of the electronic invoice might be **Rejected**. In this case, Electronic invoicing was able to successfully process the electronic invoicing feature as it was configured to process that feature. However, the electronic invoice was rejected because it didn't meet the criteria that the web service established for invoice approval.

The submission status is updated only when you send a request to the Electronic invoicing service by submitting new electronic documents, or by submitting functions and inquiries.

The submission log includes the following additional commands:

- <a id="Cancel"></a>**Functions** \> **Cancel submissions** – This function enables a special submission process when the electronic invoice must be approved by an external web service. It instructs Electronic invoicing to send the web service a specific message that is intended to cancel the status of an approved electronic invoice in the web service database.
   > [!NOTE]
   > The cancellation functionality is controlled by the **BusinessDocumentEnableCancelForCompleteSubmissionFlight** flight which is disabled by default. The flight must be intentionally enabled per request to activate the functionality.
- **Functions** \> **Resubmit document** – Resubmit an electronic document that has already been submitted to Electronic invoicing. A new log is created on the **Submission details** page. In this case, no data is sent to the Electronic invoicing service. Instead, the Electronic invoicing service reruns the processing of previously submitted data.
- **Functions** \> **Send related submission** – Send the same document from Finance or Supply Chain Management.
- **Inquiries** \> **Submission details** – View the details of the main submission. The visualization shows the complete execution log of the actions that are configured in the electronic invoicing feature. You can download the files that are created as a result of each action during the processing. When the invoice must be approved by an external web service, you can view the status of the invoice.

    Processing data contains variables that are sent to the Electronic invoicing service or returned from it. You can review the value of these variables. For example, the **BusinessDocumentDataModel** variable contains financial data that is submitted to the Electronic invoicing service in a unified structure (JavaScript Object Notation \[JSON\] format). You can use this information to troubleshoot the correctness of the data that was passed for further processing.

- **Inquiries** \> **Related submissions** – View the details of child submissions or the submission of related documents.
- **Electronic document** \> **Download file** – For a single electronic document or a selected range of the documents, download a ZIP archive that contains generated electronic files. Because the processing pipeline of the electronic invoicing feature might contain several actions that generate different files, set the **Export result** parameter for a specific action to ensure that the result of that action is exported.
