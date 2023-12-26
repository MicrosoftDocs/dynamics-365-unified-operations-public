--- 
# required metadata 
 
title: Set up postdated checks
description: This article explains how to specify whether to post journal entries for postdated checks and which posting journals to use for clearing entries and vendor payments. 
author: kweekley
ms.date: 11/15/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: BankParameters, VendPaymMode, CustPaymMode   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
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

This article explains how to specify whether to post journal entries for postdated checks and which posting journals to use for clearing entries and vendor payments. You can also specify clearing accounts for issued checks, received checks, and withholding tax. Postdated checks that are issued to make and receive payments on a future date. You can specify whether the check must be reflected in the accounting books before its maturity date.



The role of this procedure is Treasurer. This procedure uses the USMF demo company.


## Set up postdated checks
1. Go to **Cash and bank management > Setup > Cash and bank management parameters**.
2. Click the **Postdated checks** tab.
3. Select or clear the **Enable postdated checks** checkbox.
4. Select or clear the **Post journal entries for postdated checks** checkbox.
5. In the **Clearing account for issued checks** field, specify the desired values.
6. In the **Clearing account for received checks** field, specify the desired values.
7. In the **General journal for clearing entries** field, type a value.
8. In the **Transfer postdated checks to this vendor payment journal** field, type a value.
9. In the **Withholding tax clearing account** field, specify the desired values.
10. Click **Save**.
11. Close the page.
12. Go to **Accounts payable > Payment setup > Methods of payment**.
13. Click **New**.
14. In the **Method of payment** field, type a value.
15. Select the **Postdated check clearing posting** option to indicate that the check amount is posted to a clearing account.
16. In the **Account type** field, select **Bank**.
    * The offset account of the payment method will be a bank.  
17. In the **Payment account** field, specify the desired values.
    * Select the bank account that is used to deduct the invoice amount.  
18. Click **Save**.
19. Close the page.
> [!NOTE]
> To be able to post a postdated check to a bank account when the session date is greater than or equal to the maturity date, you must enable the feature **Maturity date validation of posting payment journal with postdated checks to bank account**. This feature allows you to post payment journals for vendors or customers with postdated checks, when the session date is greater than or equal to the maturity date.
> 
> When setting the **Method of payment** (**Accounts payable > Payment setup > Methods of payment**), don't fill in **Bridging account**. In this case, the offset account is filled in with the bank account, which is set up in the **Method of payment**.
>  
> When the feature is enabled and the session date is less than the maturity date, the following error message is displayed when posting a payment journal, **Maturity date must be less or equal to the session date if offset account type is Bank**. If the feature is not enabled, you can post a payment journal with a postdated check when the session date is less than the maturity date.
> This feature is available in version 10.0.21 or later.    

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
