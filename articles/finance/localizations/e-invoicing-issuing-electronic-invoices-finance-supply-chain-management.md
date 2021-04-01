---
# required metadata

title: Issue electronic invoices in Finance and Supply Chain Management
description: This topic explains how to issue electronic invoices in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management through Electronic invoicing.
author: gionoder
ms.date: 03/29/2021
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

This topic explains how to issue electronic invoices in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management through Electronic invoicing.


## Feature activation

To issue electronic invoices through Electronic invoicing, you must activate the Feature in Finance and Supply Chain Management.

Each feature corresponds to a specific electronic invoicing feature that complies with the electronic invoicing requirements for a country/region.

The following table shows the list of features that Electronic invoicing may support.

| Name                                              | Country/region |
|---------------------------------------------------|----------------|
|Austrian electronic invoice                        |Austria         |
|Belgian electronic invoice                         |Belgium         |
|NF-e  Federal - Brazilian electronic invoice       |Brazil          |
|NFS-e - Brazilian service (city) electronic invoice|Brazil          |
|Danish electronic invoice                          |Denmark         |
|Egyptian electronic invoice                        |Egypt           |
|Estonian electronic invoice                        |Estonia         |
|Finnish electronic invoice                         |Finland         |
|French electronic invoice                          |France          |
|German electronic invoice                          |Germany         |
|PEPPOL - Global electronic invoice                 |Global          |
|Italian electronic invoice                         |Italy           |
|CFDI - Mexican electronic invoice                  |Mexico          |
|Dutch electronic invoice                           |Netherlands     |
|Norwegian electronic invoice                       |Norway          |
|Spanish electronic invoice                         |Spain           |

When there is a legacy Electronic invoicing feature that is supported in a country/region's localizations scope, activating one of these features turns off the legacy feature and enables electronic invoices to be issued through Electronic invoicing.

> [!IMPORTANT]
> After the Electronic invoicing integration feature is enabled, the new Electronic invoicing experience is turned off by default. You can use the feature concept to selectively enable new experiences for legal entities using country/region-specific functionality. The **Global** option controls the new experience for the remaining county/regions that aren't specifically listed in the table.

## Submit electronic documents

The process of submitting electronic documents represents the single point of communication between Finance and Supply Chain Management and Electronic invoicing. During each submission event, the communication flows in both directions:

- **From Finance and Supply Chain Management to the Electronic invoicing** – Finance and Supply Chain Management send the abstract invoices to Electronic invoicing. As required, they also send the contents of variables that were configured as part of the electronic invoicing features.
- **From the Electronic invoicing to Finance and Supply Chain Management** – Depending on the electronic invoicing feature, Finance and Supply Chain Management receive updates from Electronic invoicing about the processing results of invoices that were previously submitted. They also receive the contents of variables that were configured as part of the electronic invoicing features.

To submit electronic documents to Electronic invoicing, in Finance and Supply Chain Management, go to **Organization administration &gt; Periodic &gt; Electronic documents &gt; Submit electronic documents**.

The starting point is a posted invoice. This invoice can come from different origins, such as sales orders, project invoices, or free text invoices.

The submission process can be run manually or in the background.

- **Manual execution** – For manual execution, you must use the **Filter** option to define the range of documents that must be submitted. On the **Filters** page, you can configure your own query to select the posted invoices that must be submitted. After the selection is made, you must manually start execution of the processing and wait for it to finish running. When the processing is completed, a message in the Action center shows the number of electronic documents that have been successfully submitted.
- **Background execution** – Background execution runs without requiring that you be signed in or keep the submission dialog box open. You can schedule the process to run and define the frequency of execution.

## View the submission logs

In Finance and Supply Chain Management, you can use the submission logs to view the results of processing the submission to Electronic invoicing. Go to **Organization administration &gt; Periodic &gt; Electronic documents &gt; Electronic document submission**, and then, in the **Document type** field, select a value to filter the type of invoices that the logs show.

There are three possible submission statuses:

- **Scheduled** – Electronic invoicing received the submission from Finance and Supply Chain Management, and processing of the electronic invoicing feature is in progress.
- **Completed** – Electronic invoicing successfully processed the electronic invoicing feature as it was configured to run it.
- **Failed** – Electronic invoicing encountered an error or was stopped by an exception during processing of the electronic invoicing feature.

> [!IMPORTANT]
> The submission status refers to the status of the processing that Electronic invoicing does on the electronic invoicing feature. It doesn't refer to the final status of the electronic invoice itself.
>
> For example, if an electronic invoice must be submitted to an external web service for approval, the submission status might be **Completed**, but the status of the electronic invoice might be **Rejected**. In this case, Electronic invoicing was able to successfully process the electronic invoicing feature as it's configured to process that feature. However, the electronic invoice was rejected because it didn't meet the criteria that the web service established for invoice approval.

The submission logs include the following additional functions:

- **Submission details** – View the details of the main submission. The visualization shows the complete execution log of the actions that are configured in the electronic invoicing feature. It also lets users download the files that are created during the processing. In scenarios where the invoice must be approved by an external web service, it lets users view the status of the invoice.
- **Related submissions** – View the details of child submissions.
- **Cancel submissions** – This function enables a special submission process in scenarios where the electronic invoice must be approved by an external web service. It instructs Electronic invoicing to send the web service a specific message that is intended to cancel the status of an approved electronic invoice in the web service database.
- **Resubmit document** – Resubmit an electronic document that has already been submitted to Electronic invoicing. A new log is created on the **Submission details** page.
- **Send related submission**


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
