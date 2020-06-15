--- 
# required metadata 
 
title: Set up postdated checks
description: This topic explains how to specify whether to post journal entries for postdated checks and which posting journals to use for clearing entries and vendor payments. 
author: kweekley
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: BankParameters, VendPaymMode, CustPaymMode   
audience: Application User 
# ms.devlang:  
ms.reviewer: roschlom
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up postdated checks

[!include [banner](../../includes/banner.md)]

This topic explains how to specify whether to post journal entries for postdated checks and which posting journals to use for clearing entries and vendor payments. You can also specify clearing accounts for issued checks, received checks, and withholding tax. Postdated checks that are issued to make and receive payments on a future date. You can specify whether the check must be reflected in the accounting books before its maturity date.



The role of this procedure is Treasurer. This procedure uses the USMF demo company.


## Set up postdated checks
1. Go to Cash and bank management > Setup > Cash and bank management parameters.
2. Click the Postdated checks tab.
3. Select or clear the Enable postdated checks check box.
4. Select or clear the Post journal entries for postdated checks check box.
5. In the Clearing account for issued checks field, specify the desired values.
6. In the Clearing account for received checks field, specify the desired values.
7. In the General journal for clearing entries field, type a value.
8. In the Transfer postdated checks to this vendor payment journal field, type a value.
9. In the Withholding tax clearing account field, specify the desired values.
10. Click Save.
11. Close the page.
12. Go to Accounts payable > Payment setup > Methods of payment.
13. Click New.
14. In the Method of payment field, type a value.
15. Select the Postdated check clearing posting option to indicate that the check amount is posted to a clearing account.
16. In the Account type field, select 'Bank'.
    * The offset account of the payment method will be a bank.  
17. In the Payment account field, specify the desired values.
    * Select the bank account that is used to deduct the invoice amount.  
18. Click Save.
19. Close the page.

