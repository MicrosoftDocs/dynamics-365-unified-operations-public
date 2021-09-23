---
# required metadata

title: Open financial journal templates in Office 
description: This topic describes issues that might occur when you create custom financial journals by using a Microsoft Excel template.
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

This topic describes issues that might occur when you create custom financial journals by using a Microsoft Excel template.

## Symptom

You created a custom Excel template for financial journals, but it doesn't appear on the **Open lines in Excel** menu. Alternatively, it does appear on the menu, a different template is opened but when you select it.

## Resolution

The default Open in Excel functionality uses the root data source (table) of the current page to determine which Office templates or data entities appear as options on the **Open in Excel** menu. This behavior isn't an ideal experience for financial journals, because financial journals use the same tables (LedgerJournalTable and LedgerJournalTrans) as the root data source of many other types of journals.

For financial journals, the Open Lines in Excel functionality is intended to show templates that are designed for the journal that you're currently working in the context of, such as the general journal or a payment journal. For example, a template that is intended to be used with a vendor payment journal will be designed to enforce your primary account as a vendor account.

If you want to promote a template so that it's available on the **Open lines in Excel** and **Open in Excel** menus, an easy developer experience is to implement the **LedgerIJournalExcelTemplate** interface and extend the **DocuTemplateRegistrationBase** class. Many examples of this approach are implemented in the system. One example that can be used for reference is the **LedgerDailyJournalExcelTemplate** interface that was created for the general journal (or daily journal).

When the **LedgerIJournalExcelTemplate** interface is implemented for your template, the **Open Lines in Excel** menu will filter templates by the journal type of your journal and will show only the templates that are available for that journal. The interface also provides a validation method that ensures that a template can't be opened for a journal if it doesn't meet the account type requirements. For example, you can specify that the account type must be of the **Vendor** or **Ledger** type.

For more information about this functionality, see [Add templates to the Open lines in Excel menu](../../fin-ops-core/dev-itpro/user-interface/add-templates-open-lines-excel-menu.md).
