---
title: Submit electronic documents
description: Learn how to submit electronic documents to the Electronic invoicing service, including overviews on communication flows during submission events.
author: ilikond
ms.author: ikondratenko
ms.topic: article
ms.date: 02/12/2024
ms.custom: 
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: 
ms.search.validFrom:
ms.search.form: 
ms.dyn365.ops.version:
---

# Submit electronic documents

[!include [banner](../../includes/banner.md)]

Submission of electronic documents represents the single point of communication between Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management and Electronic invoicing. During each submission event, the communication flows in both directions:

- **From Finance or Supply Chain Management to Electronic invoicing** – Finance or Supply Chain Management sends the financial data to Electronic invoicing in a unified structure. As required, it also sends the contents of variables that were configured as part of the electronic invoicing features.
- **From Electronic invoicing to Finance or Supply Chain Management** – Depending on the electronic invoicing features, Finance or Supply Chain Management receive updates from Electronic invoicing about the processing results of invoices that were previously submitted. It also receives the contents of variables that were configured as part of the electronic invoicing features.

To submit electronic documents to Electronic invoicing from Finance or Supply Chain Management, go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**.

The starting point is a posted invoice. This invoice can come from different origins. For example, it can come from sales orders, project invoices, or free text invoices.

The submission process can be run manually or in the background.

- **Manual** – In the **Submit electronic documents** dialog box, on the **Records to include** FastTab, select **Filter** to define the range of documents that must be submitted. In the **Inquiry** dialog box, you can configure your own query to select the posted invoices that must be submitted. After you've made your selection, manually start execution of the processing, and wait for it to finish running. When the processing is completed, a message in the Action center shows the number of electronic documents that have been successfully submitted.
- **Background** – Background execution doesn't require that you be signed in or keep the **Submit electronic documents** dialog box open. You can schedule the process to run, and you can define the execution frequency.

> [!NOTE]
> In some specific scenarios, the standard submission procedure that was described earlier only generates electronic invoices and stores them on the service side. The invoices aren't submitted. Submission of electronic invoices requires that you complete the following additional steps.

To submit the generated electronic invoices in batch mode, follow these steps.

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Run submission process in export channels**.
2. In the **Channel** field, select the export channel, and then select **OK**. The export channel must be created in advance.

You can inquire about the results of the submission by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log**. For more information, see [Work with Electronic document submission log](e-invoicing-submission-log.md).  
