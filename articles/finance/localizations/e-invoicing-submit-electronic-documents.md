---
# required metadata

title: Submit electronic documents to Electronic invoicing
description: This topic provides information about how to submit electronic documents to the Electronic invoicing service.
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

# Submit electronic documents to Electronic invoicing

[!include [banner](../includes/banner.md)]

Submitting electronic documents represents the single point of communication between Dynamics 365 Finance or Dynamics 365 Supply Chain Management and Electronic invoicing. During each submission event, the communication flows in both directions:
 
 - From Finance or Supply Chain Management to the Electronic invoicing: Finance or Supply Chain Management sends the financial data in a unified structure to Electronic invoicing. As required, they also send the contents of variables that were configured as part of the electronic invoicing features.
 - From the Electronic invoicing to Finance or Supply Chain Management: Depending on the electronic invoicing feature, Finance or Supply Chain Management receive updates from Electronic invoicing about the processing results of invoices that were previously submitted. They also receive the contents of variables that were configured as part of the electronic invoicing features.
	
To submit electronic documents to Electronic invoicing in Finance or Supply Chain Management, complete the following steps.

 1. Go to **Organization administration** > **Periodic** > **Electronic documents** > **Submit electronic documents**.
 2. The starting point is a posted invoice. This invoice can come from different origins, such as sales orders, project invoices, or free text invoices. 
	
The submission process can be run manually or in the background.
 - Manual: Use the **Filter** option to define the range of documents that must be submitted. On the **Filters** page, you can configure your own query to select the posted invoices that must be submitted. After the selection is made, manually start execution of the processing and wait for it to finish running. When the processing is complete, a message in the Action center shows the number of electronic documents that have been successfully submitted.
 - Background: Background execution runs without requiring that you be signed in or keep the **Submission** dialog box open. You can schedule the process to run and define the frequency of execution.
