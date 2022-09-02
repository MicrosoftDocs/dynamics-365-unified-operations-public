---
# required metadata

title: Documents pending accounting
description: This article describes how to use the Documents pending accounting page. 
author: ryanCCarlson2
ms.date: 09/02/2022
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
ms.author: rcarlson
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30

---

# Documents pending accounting

[!include [banner](../includes/banner.md)]

This article provides information about the how to use the functionality on the **Documents pending accounting** page.  

With the release of Dynamics 365 Finance 10.0.30, the feature **Enhanced performance for source document accounting framework** is available. Starting with the Free text invoice posting process, this feature improves the posting processes for source document enabled document postings 

When this feature is enabled, posting the subledger document is performed seperately from the accounting generation or *journalization* process that creates the full accounting detail that's transferred to the general ledger. For example, in the Free text invoice posting process, the customer invoice in the **Accounts receivable** module is recorded prior to the full accounting being generated. This enhanced performance feature allows for faster recording of the customer invoices while the accounting generation is delayed. 

The following options are available from the **Documents pending accounting** page. 

- **Generate accounting** - Select this button to sumbmit a document that's currently pending account generation for journalization. 
- **View distributions** - Select this button to view the accounting distributions for a selected document in the list. 
- **View error log** - Select this button to view the detailed error message details if they exist for a document with the accounting state in error. Or, select the **Error log** link directly on the document line to view the same error message details. 

Accounting generation is accomplished by a process automation background process called **Accounting framework processor**. For more details about the setup and configuration of all process automations, see [Process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md). 

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
