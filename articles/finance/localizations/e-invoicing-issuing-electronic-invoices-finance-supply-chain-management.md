---
# required metadata

title: Issue electronic invoices in Finance and Supply Chain Management
description: This topic explains how to issue electronic invoices in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management through the Electronic invoicing add-on.
author: gionoder
manager: AnnBe
ms.date: 01/22/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Issue electronic invoices in Finance and Supply Chain Management

[!include [banner](../includes/banner.md)]

This topic explains how to issue electronic invoices in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management through the Electronic invoicing add-on.

Before you can start to issue electronic invoices through the Electronic invoicing add-on, you must complete these tasks:

1. Configure the integration between Finance and Supply Chain Management and the Electronic invoicing add-on.
2. Activate the process of issuing electronic invoices through the Electronic invoicing add-on service.

Activation must be done only one time and by electronic invoice, given by its feature reference code. Each feature reference code is associated with an electronic invoicing feature requirement for a country or region.

If a feature reference code is associated with an old process for issuing electronic invoices, activation automatically turns off the old process in the Finance and Supply Chain Management instances. Therefore, Finance and Supply Chain Management no longer issue electronic invoices through X++ code. Instead, they communicate with the service, and the service issues the electronic invoice.

The following table shows the list of feature references that the Electronic invoicing add-on supports.

| Feature reference | Name                                              | Country/region |
|-------------------|---------------------------------------------------|----------------|
| BR-00095          | NFS-e Brazilian electronic invoices               | Brazil         |
| BR-00053          | NF-e Federal - Brazilian electronic invoice       | Brazil         |
| DK-00001          | E-invoicing to the public sector (OIOUBL) – DK    | Denmark        |
| EG-00008          | E-invoicing for Egypt                             | Egypt          |
| EUR-00023         | European Union E-invoicing to Public sector       | Europe         |
| ITA-00036         | IT - E-invoicing to the public sector (FatturaPA) | Italy          |
| MX-00010          | E-invoicing CFDI                                  | Mexico         |
| MX-00016          | E-invoicing CFDI - cancellation process           | Mexico         |
| ES-00025          | Electronic Invoice to the public sector           | Spain          |

## Submit electronic documents

The process of submitting electronic documents represents the single point of communication between Finance and Supply Chain Management and the Electronic invoicing add-on. During each submission event, the communication flows in both directions:

- **From Finance and Supply Chain Management to the Electronic invoicing add-on** – Finance and Supply Chain Management send the abstract invoices to the Electronic invoicing add-on. As required, they also send the contents of variables that were configured as part of the electronic invoicing features.
- **From the Electronic invoicing add-on to Finance and Supply Chain Management** – Depending on the electronic invoicing feature, Finance and Supply Chain Management receive updates from the Electronic invoicing add-on about the processing results of invoices that were previously submitted. They also receive the contents of variables that were configured as part of the electronic invoicing features.

To submit electronic documents to the Electronic invoicing add-on, in Finance and Supply Chain Management, go to **Organization administration &gt; Periodic &gt; Electronic documents &gt; Submit electronic documents**.

The starting point is a posted invoice. This invoice can come from different origins, such as sales orders, project invoices, or free text invoices.

The submission process can be run manually or in the background.

- **Manual execution** – For manual execution, you must use the **Filter** option to define the range of documents that must be submitted. On the **Filters** page, you can configure your own query to select the posted invoices that must be submitted. After the selection is made, you must manually start execution of the processing and wait for it to finish running. When the processing is completed, a message in the Action center shows the number of electronic documents that have been successfully submitted.
- **Background execution** – Background execution runs without requiring that you be signed in or keep the submission dialog box open. You can schedule the process to run and define the frequency of execution.

## View the submission logs

In Finance and Supply Chain Management, you can use the submission logs to view the results of processing the submission to the Electronic invoicing add-on. Go to **Organization administration &gt; Periodic &gt; Electronic documents &gt; Electronic document submission**, and then, in the **Document type** field, select a value to filter the type of invoices that the logs show.

There are three possible submission statuses:

- **Scheduled** – The Electronic invoicing add-on received the submission from Finance and Supply Chain Management, and processing of the electronic invoicing feature is in progress.
- **Completed** – The Electronic invoicing add-on successfully processed the electronic invoicing feature as it was configured to run it.
- **Failed** – The Electronic invoicing add-on encountered an error or was stopped by an exception during processing of the electronic invoicing feature.

> [!IMPORTANT]
> The submission status refers to the status of the processing that the Electronic invoicing add-on does on the electronic invoicing feature. It doesn't refer to the final status of the electronic invoice itself.
>
> For example, if an electronic invoice must be submitted to an external web service for approval, the submission status might be **Completed**, but the status of the electronic invoice might be **Rejected**. In this case, the Electronic invoicing add-on was able to successfully process the electronic invoicing feature as it's configured to process that feature. However, the electronic invoice was rejected because it didn't meet the criteria that the web service established for invoice approval.

The submission logs include the following additional functions:

- **Submission details** – View the details of the main submission. The visualization shows the complete execution log of the actions that are configured in the electronic invoicing feature. It also lets users download the files that are created during the processing. In scenarios where the invoice must be approved by an external web service, it lets users view the status of the invoice.
- **Related submissions** – View the details of child submissions.
- **Cancel submissions** – This function enables a special submission process in scenarios where the electronic invoice must be approved by an external web service. It instructs the Electronic invoicing add-on to send the web service a specific message that is intended to cancel the status of an approved electronic invoice in the web service database.
- **Resubmit document** – Resubmit an electronic document that has already been submitted to the Electronic invoicing add-on. A whole new log is created on the **Submission details** page.
- **Send related submission**
