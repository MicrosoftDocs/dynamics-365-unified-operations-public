--- 
# required metadata 
 
title: Post vouchers from the general journal (China)
description: This procedure walks you through posting Chinese vouchers using the general journal. 
author: ShylaThompson
manager: AnnBe 
ms.date: 10/27/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: China (PRC)
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Post vouchers from the general journal (China)

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure walks you through posting Chinese vouchers using the general journal.  Before you can complete this procedure, be sure that you’ve created all of the necessary fiscal calendars. 

This procedure was created using the demo data company CNMF. For the CNMF demo data, you must create fiscal years through the current year in the fiscal calendar ‘Fiscal_CN’. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Post vouchers from general ledger journals
1. Go to General ledger > Journal entries > General journals.
2. Click New.
3. In the list, mark the selected row.
4. In the Name field, enter or select a value.
5. In the list, click the link in the selected row.
6. In the Voucher type field, enter or select a value.
7. In the Account field, specify the desired values.
8. In the Description field, enter or select a value.
9. In the Description field, type a value.
10. In the Debit field, enter a number.
11. In the Offset account type field, select an option.
12. In the Offset account field, specify the desired values.
13. Click Financial dimensions.
14. Click Offset account.
15. In the Cashflow_CN field, enter or select a value.
16. Click OK.
17. Click Validate.
    * For this example, the criteria for the voucher of type Pay must be met. This means that one of the debit and credit accounts must be a bank account that is a cash account, otherwise the validation will not pass.  
18. Click Validate.
19. Click Post.
20. Click Print.
21. Click Voucher.
22. In the Print layout code field, enter or select a value.
23. Select the Print account dimension check box.
24. Click OK.

