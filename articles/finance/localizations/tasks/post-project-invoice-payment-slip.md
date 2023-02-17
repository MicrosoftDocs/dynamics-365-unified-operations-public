--- 
# required metadata 
 
title: Post a project invoice with a payment slip
description: This article explains how to post a project invoice with a payment slip in a specified format. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustTable, ProjProjectContractsListPage, ProjInvoiceTableCreate, ProjInvoiceTable, ProjProjectsListPage, ProjTableCreate, ProjGroupLookUp, ProjTable,  ProjTransOnAcc, ProjInvoiceProposalListPage, ProjInvoiceProposalCreateLines, ProjInvoiceProposalDetail, ProjInvoiceEditLines   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Denmark
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Post a project invoice with a payment slip

[!include [banner](../../includes/banner.md)]

You can post a project invoice with a payment slip attachment in a specified format. The payment slip is printed with the creditor identification number and invoice number to identify the payment.

Before you can complete this procedure, you must first set up a payment slip format and set up payment slips for customer invoices. 



This functionality is available for legal entities whose primary address is in Denmark. 

This procedure was created using the demo data company DEMF.

1. Go to Accounts receivable > Customers > All customers.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Expand or collapse the Invoice and delivery section.
5. Click Edit.
6. In the On a project invoice field, select an option.
    * o    None – Do not print a payment slip. Choose this option if the payment amount is in a currency other than Danish kroner (DKK).   o    FIK 751 – Print an FIK 751 payment slip if you intend to write the payment amount and due date on the payment slip manually.   o    FIK 752 – Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.     
7. Click Save.
8. Click the TabPageGrid tab.
9. Close the page.
10. Go to Project management and accounting > Projects > Project contracts.
11. Click New.
12. In the Name field, type a value.
13. In the Funding source field, click the drop-down button to open the lookup.
14. In the list, click the link in the selected row.
15. In the Sales currency field, click the drop-down button to open the lookup.
16. In the list, find and select the desired record.
17. In the list, click the link in the selected row.
18. In the Sales currency field, click the drop-down button to open the lookup.
19. In the list, find and select the desired record.
    * The payment slip can be printed only for a project invoice with the currency Danish kroner (DKK).  
20. In the list, click the link in the selected row.
21. Click OK.
22. Click Save.
23. Go to Project management and accounting > Projects > All projects.
24. Click New.
25. In the Project type field, select an option.
26. In the Project name field, type a value.
27. In the Project group field, click the drop-down button to open the lookup.
28. In the list, click the link in the selected row.
29. In the Project contract ID field, click the drop-down button to open the lookup.
30. In the list, find and select the desired record.
31. In the list, click the link in the selected row.
32. Click Create project.
33. On the Action Pane, click Project.
34. Click Project stage.
35. Click In process.
36. Click OK.
37. Click Save.
38. On the Action Pane, click Manage.
39. Click On-account transactions.
40. Click New.
41. In the list, mark the selected row.
42. In the Sales price field, enter a number.
43. Click Save.
44. Close the page.
45. On the Action Pane, click Manage.
46. Click Project invoice proposals.
47. Click New.
48. Click Invoice proposal.
49. In the Project field, click the drop-down button to open the lookup.
50. Close the page.
51. In the Project contract field, click the drop-down button to open the lookup.
52. In the list, find and select the desired record.
53. In the list, click the link in the selected row.
54. Click OK.
55. Click Post.
56. Click OK.
57. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
