--- 
# required metadata 
 
title: FR-00004 Update method of payment on customer
description: This procedure walks you through adding a bank account to a customer record in France and updating a method of payment for the same customer. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustTable, CustBankAccounts, LogisticsPostalAddress, LogisticsPostalAddressGrid, SysLookupMultiSelectGrid   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: France
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# FR-00004 Update method of payment on customer

[!include [banner](../../includes/banner.md)]

This procedure walks you through adding a bank account to a customer record in France and updating a method of payment for the same customer.



Before you can complete this procedure, you must import the following electronic reporting configurations: payments.initial.version.xml and BillsOfExchangeRemittance_FR.xml.



This procedure was created using the demo data company FRSI.

1. Go to Accounts receivable > Customers > All customers.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. On the Action Pane, click Customer.
5. Click Bank accounts.
6. Click New.
7. In the Bank account field, type a value.
8. In the Name field, type a value.
9. In the Bank account number field, type a value.
10. In the Routing number field, type a value.
11. Expand the Address section.
12. Click New.
13. In the Name or description field, type a value.
14. In the Country/region field, enter or select a value.
15. In the list, click the link in the selected row.
    * Select FRA  
16. Click OK.
17. Close the page.
18. Expand the Addresses section.
19. Click Edit.
20. In the list, click the link in the selected row.
21. Click OK.
22. Expand the Payment defaults section.
23. Click Edit.
24. In the Method of payment field, enter or select a value.
25. In the list, find and select the desired record.
    * Set Method of payment = BOEPDF  
26. In the list, click the link in the selected row.
27. In the Bank account field, enter or select a value.
28. In the list, click the link in the selected row.
    * Change to Bank account = 1  
29. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]