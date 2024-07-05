--- 
title: Update vendor invoice declarations and generate the report
description: Learn about posting a vendor invoice with invoice declaration information attached and generating an invoice declaration report.
author: mrolecki
ms.author: mrolecki
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: johnmichalak   
audience: Application User 
ms.search.region: Iceland
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransVendInvoice
ms.dyn365.ops.version: Version 7.0.0 
---

# Update vendor invoice declarations and generate the report

[!include [banner](../../includes/banner.md)]

This procedure walks you through posting a vendor invoice with invoice declaration information attached and generating an invoice declaration report. The demo data company used to create this procedure is DEMF with the country/region of legal entity primary address updated to Iceland.


## Post a vendor invoice
1. Go to Accounts payable > Invoices > Invoice journal.
2. Click New.
3. In the Name field, In the Name field, select 'APInvoice'.
4. Click Lines.
5. In the Account field, specify the values 'IS-001'.
6. In the Invoice field, type 'IS-001-01'.
7. In the Credit field, enter a number.
8. In the Offset account field, specify the values '200130--'.
9. Click the Invoice tab.
10. In the Document field, type a value.
11. In the Invoice date field, enter today's date.
12. In the Invoice declaration field, click the drop-down button to open the lookup.
13. In the list, select the Invoice declaration category.
14. Click Post.

## Generate an invoice declaration
1. Go to Accounts payable > Inquiries and reports > Invoice > Vendor invoice declaration report.
2. In the Authority field, click the drop-down button to open the lookup.
3. In the list, click the link in the selected row.
4. In the From date field, enter a date.
5. In the To date field, enter a date.
6. Check the Create report file checkbox.
7. In the Name field, select 'Vendor invoice declaration report (IS)'..
8. Check the Create text file checkbox.
9. In the Name field, select 'Vendor invoice declaration (IS)'.
10. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]