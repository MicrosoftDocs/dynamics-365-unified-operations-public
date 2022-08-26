---
# required metadata

title: Documents Pending Accounting
description: This article describes the use of the form documents pending accounting. 
author: RyanCCarlson2
ms.date: 08/28/2022
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: RyanCCarlson2
ms.search.validFrom: 2022-08-28
ms.dyn365.ops.version: 10.0.30

---

# Documents pending accounting

[!include [banner](../includes/banner.md)]

This article provides information about the documents pending accounting page and actions to be taken from this page.  

There is a new feature released in 10.0.30 titled **Enhanced performance for source document accounting framework**. This feature helps improve the posting processes for source document enabled document postings starting with the Free Text Invoice posting process for 10.0.30. Future releases will add additional source document enabled posting processes. 

When this feature is enabled, the posting of the subledger document is performed seperately from the accounting generation or *journalization* process that creates the full accounting detail to be transferred to the general ledger. For example in the Free Text invoice posting process, the customer invoice in the accounts receivable module will be recorded prior to the full accounting being generated. This enhanced performance feature will allow faster recording of the customer invoices while the accounting generation is delayed*. 

The following options are available from the **Documents Pending Accounting** page. 

- Generate accounting - Use the generate accounting button to sumbmit a document for journalization that is currently pending accounting generation. 
- View distributions - Use the view distributions button to view the accounting distributions for a selected document in the list. 
- view error log - Use the view error log button to view the detailed error message details if they exist for a document with the accounting state in error.  You may also click the Error log link directly on the document line to view the same error message details. 

*Accounting generation is accomplished by a process automation background process called **Accounting framework processor**.  The documenataion about [process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md) will provide more information about the setup and configuration of all process automations. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
