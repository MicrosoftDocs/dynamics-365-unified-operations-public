---
# required metadata

title: Open financial journal templates in Office 
description: This topics describes issues that can arise when you create custom financial journals using an Excel template.
author: kweekley
ms.date: 05/14/2021
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2020-05-14
ms.dyn365.ops.version: 10.0.14

---

# Open financial journal templates in Office

[!include [banner](../includes/banner.md)]

This topics describes issues that can arise when you create custom financial journals using an Excel template. 

## Symptom

I created a custom financial journal office excel template, and it doesn't show up under Open lines in Excel, or it shows but opens a different template when I select it.  What is the issue?

## Resolution

The default **Open in Excel** functionality uses the root data source (table) of the current page to determine which Office templates or data entities will display as an option under the **Open in Excel** menu. This is not an ideal experience for Financial journals which share the same tables (LedgerJournalTable/LedgerJournalTrans) as the root data source for many different types of journals.  

The **Open Lines in Excel** feature for Financial journals is intended to show templates which are designed for the journal you are currently working with the context of the General journal, Payment journal, and so on.  For example, if you create a template that is designed for use with a vendor payment journal, the template would be designed to enforce your primary account as a vendor account.  

To promote a template so that it’s available in the **Open lines in Excel** menu and the **Open in Excel** menu, there is a simple developer experience to implement the **LedgerIJournalExcelTemplate** interface and extend the **DocuTemplateRegistrationBase** class.  There are a number of examples implemented in the system. One example that can be used for reference is the **LedgerDailyJournalExcelTemplate** created for the General journal (or Daily journal).

By implementing the **LedgerIJournalExcelTemplate** interface for your template, the **Open Lines in Excel** menu will filter the templates available to your journal by filtering templates by your Journal type.  The interface also provides a method to validate that a template cannot be opened for a journal if it does not meet the account type requirements. For example, you can specify that the account type must be of Vendor type or Ledger type.

Additional documentation is available to support this functionality. For more information, see [Add templates to the Open lines in Excel menu](../../fin-ops-core/dev-itpro/user-interface/add-templates-open-lines-excel-menu.md).
