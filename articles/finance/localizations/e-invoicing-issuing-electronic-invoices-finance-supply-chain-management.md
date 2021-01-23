---
# required metadata

title: # Issue electronic invoices in Finance and Supply chain management
description:  
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

# Issue electronic invoices in Finance and Supply chain management

[!include [banner](../includes/banner.md)]

This topic provides you information about the issuing of electronic invoices in Finance and Supply Chain Management through the Electronic invoicing add-on.

After accomplishing the configuration of the integration between Finance and Supply Chain Management and the Electronic invoicing add-on, to start issuing electronic invoices through the add-on, it is necessary to activate the process of issuing electronic invoices through the service.

The activation must be done only once and by electronic invoice, given by its Feature reference code, where each feature reference code is associated to an electronic invoicing feature requirement from a country or region.

When a Feature reference code is associated to a legacy electronic invoice issuing process, the activation automatically turns-off the legacy process of issuing electronic invoices in the Finance and Supply Chain Management instance. That means instead of issuing electronic invoices through the X++ code, Finance and Supply Chain Managements communicates with the service, which then issues the electronic invoice.

The following table shows the list of feature references supported by Electronic invoicing add-on:

Feature reference              | Name                                                | Country/region  |
|------------------------------|-----------------------------------------------------|-----------------|
| BR-00095                     | NFS-e Brazilian electronic invoices                 | Brazil          |
| BR-00053                     | NF-e Federal - Brazilian electronic invoice         | Brazil          |
| DK-00001                     | E-invoicing to the public sector (OIOUBL) – DK      | Denmark         |
| EG-00008                     | E-invoicing for Egypt                               | Egypt           |
| EUR-00023                    | European Union E-invoicing to Public sector         | Europe          |
| ITA-00036                    | IT - E-invoicing to the public sector (FatturaPA)   | Italy           |
| MX-00010                     | E-invoicing CFDI                                    | Mexico          |
| MX-00016                     | E-invoicing CFDI - cancellation process             | Mexico          |
| ES-00025                     | Electronic Invoice to the public sector             | Spain           |

## Submit electronic documents

The process of submission of electronic documents is the single point of communication between Finance and Supply Chain Management and the Electronic invoicing add-on. During each event of submission, the communication flows in both directions:

   - From Finance and Supply Chain Management to Electronic invoicing add-on: On this direction, Finance and Supply Chain Management sends the abstract invoices to Electronic invoicing add-on, and when necessary, sends contents of variables configured as part of electronic invoicing features.
   - From Electronic invoicing add-on to Finance and Supply Chain Management: On this direction, depending on the electronic invoicing feature, Finance and Supply Chain Management receives from Electronic invoicing add-on updates about the processing results of invoices submitted previously, as well receives contents of variables configured as part of the electronic invoicing features.

In Finance and Supply Chain Management, use **Organization administration &gt; Periodic &gt; Electronic documents &gt; Submit electronic documents** to submit electronic documents to the Electronic invoicing add-on.

The starting point is a posted invoice, which can come from difference origins, such as Sales orders, Project invoices, Free text invoices etc.

The submission process can be executed manually or in background.

   - Manual execution: In the manual execution, you must define the range of documents to be submitted through the option Filter. On Filters, you can configure your own query to select the posted invoices to be submitted. And once the selection is done, you must kick-off the execution manually and wait the processing finishing. When finished, a message in the Action center panel shows how many electronic documents have been effectively submitted.
   - Background execution: In another hand, the background execution runs without the need you to be logged or keep the submission form opened. The process can be scheduled to run, as well the frequency of execution.

## View submission log

In Finance and Supply Chain Management, use **Organization administration &gt; Periodic &gt; Electronic documents &gt; Electronic document submission** log to view the results of the processing the submission to Electronic invoicing add-on.

The visualization of the submission logs requires first selecting the Document type. That field filters the type of invoice you can view through logs.

There are 3 possible Submission status:

   - Scheduled: The Electronic invoicing add-on received the submission from Finance and Supply Chain Management, and the execution of the electronic invoicing feature is in progress.
    - Completed: When the electronic invoicing feature was successfully executed by Electronic invoicing add-on as it was configured.
    - Failed: The Electronic invoicing add-on encountered an error or was stopped by an exception during the processing of the electronic invoicing feature.

> [!IMPORTANT]
> The submission status refers to the status of processing the Electronic invoicing feature by the Electronic invoicing add-on. It does not refer to the final status of the electronic invoice itself.
> 
> For example, in the cases where the electronic invoice must be submitted to an external web services for approval, it is possible to get the Submission status as Completed, and at the same time getting the status of the electronic invoice as Rejected. Such scenarios must be interpreted as the Electronic invoicing add-on was able to successfully run the electronic invoicing feature until its end, as configured, but the electronic invoice was rejected for not attending the criteria established by the web service to approve the invoice.

The visualization of the submission logs has additional functions.

   - Submission details: It allows the visualization the details of the main submission, showing the complete execution log of the actions configured in the electronic invoicing feature, permitting downloading the files created along the processing as well visualizing the status of the invoice in the scenarios where the invoice needs to be approved by an external web service.
   - Related submissions: It allows the visualization the details of child submissions.
   - Cancel submissions: It allows a special submission process in the scenarios where the electronic invoice must be approved by an external web service. In this case, this function tells to the Electronic invoicing add-on to send to the web service a specific message aimed to cancel the status of an approved electronic invoice in the web service database.
   - Resubmit document: It allows resubmitting an electronic document already submitted to Electronic invoicing add-on. An entire new log is created in Submission details form.
   - Send related submission


