---
title: Receive electronic documents
description: Learn how to work with incoming electronic documents, including a step-by-step process for receiving electronic invoices.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.date: 03/13/2026
ms.reviewer: johnmichalak
ms.custom: 
  - bap-template
---

# Receive electronic documents 

[!include [banner](../../includes/banner.md)]

In Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management, follow these steps to receive electronic invoices.

1. Go to **Organization administration** > **Periodic** > **Electronic documents** > **Receive electronic documents**.
1. Select **OK**, and then close the page.

Use the receipt log to view the results of processing incoming documents.

To open the log, go to **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document receipt log**.

> [!NOTE]
> By default, the system sets a filter for the **Submission status** value so that you see only failed receipt submissions. In-progress and successful receipt submissions aren't shown. However, you can adjust the filter to fit your needs.

There are three possible submission statuses:

- **Scheduled** – Electronic invoicing received the submission from Finance or Supply Chain Management, and is currently processing the electronic invoicing feature.
- **Completed** – Electronic invoicing successfully processed the electronic invoicing feature in the way that it was configured to process it.
- **Failed** – Electronic invoicing encountered an error or was stopped by an exception while it was processing the electronic invoicing feature.

The system updates the receipt status only when you send a request to the Electronic invoicing service to receive and process new electronic documents, or to receive and process functions and inquiries.

The receipt log includes the following additional commands:

- **Functions** > **Cancel submissions** – This function enables a special submission process when the electronic invoice must be approved by an external web service. It instructs Electronic invoicing to send the web service a specific message that is intended to cancel the status of an approved electronic invoice in the web service database.
- **Functions** > **Resubmit document** – Resubmit the request to the Electronic invoicing service to run the receipt process. A new log is created on the **Submission details** page. 
- **Inquiries** > **Submission details** – View the details of the main submission. The visualization shows the complete execution log of the actions that are configured in the electronic invoicing feature. You can download the files that are created as a result of each action during the processing. When the invoice must be approved by an external web service, you can view the status of the invoice.

Processing data contains variables that are sent to the Electronic invoicing service or returned from it. You can review the value of these variables.

To view successfully received invoices, go to **Accounts payable** > **Invoices** > **Pending vendor invoices**.

[!INCLUDE [footer-include](../../../includes/footer-banner.md)]