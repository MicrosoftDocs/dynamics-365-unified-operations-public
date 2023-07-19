---
# required metadata

title: Documents pending accounting
description: This article describes how to use the functionality on the Documents pending accounting page.
author: ryanCCarlson2
ms.date: 07/19/2023
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
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

This article describes how to use the functionality on the **Documents pending accounting** page.

In Microsoft Dynamics 365 Finance 10.0.30, the **Enhanced performance for source document accounting framework** feature is available and starting with 10.0.36 the feature is now on by default. This feature improves the posting processes for source document–enabled document postings, starting with the posting process for free text invoices.

When this feature is enabled, posting of the subledger document is done separately from the accounting generation or *journalization* process that creates the full accounting detail that is transferred to the general ledger. For example, in the free text invoice posting process, the customer invoice in the **Accounts receivable** module is recorded before the full accounting is generated. This enhanced performance feature enables customer invoices to be recorded more quickly while accounting generation is delayed.

The following buttons are available on the **Documents pending accounting** page.

- **Generate accounting** – Submit a document that is currently pending account generation for journalization.
- **View distributions** – View the accounting distributions for a selected document in the list.
- **View error log** – View any error message details that exist for a document where the accounting state indicates errors. You can view the same error message details by selecting the **Error log** link on the document line.

Accounting generation is done by a process automation background process that is named **Accounting framework processor**. For more information about the setup and configuration of all process automations, see [Process automation](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
