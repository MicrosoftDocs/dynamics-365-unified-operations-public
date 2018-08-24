--- 
# required metadata 
 
title: Create a free text invoice
description: This article demonstrates how to create a free text invoice. 
author: mikefalkner
manager: AnnBe 
ms.date: 08/24/2018
ms.topic: article 
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
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 2018-08-30 
ms.dyn365.ops.version: 8.0.4

---

# Create a free text invoice

[!include [banner](../includes/banner.md)]

This article demonstrates how to create a free text invoice. For this procedure, use the USMF demo company.

## Create a free text invoice

1. Go to Accounts receivable > Invoices > All free text invoices.
2. Click New.
3. In the Customer account field, select a value.
    * The invoice account will default to the same account used for the customer account.   
    * The accounting status starts with In process if the invoice is not posted.   
    * The invoice number will be assigned when the invoice is posted.  
    * If you are using SEPA mandates, the direct debit mandate will be automatically populated with a mandate when you select the customer account.  
4. In the Description field, type a value.
5. In the Main account field, specify an account number without dimensions.
    * You can also enter one or more characters for the main account and use the lookup to find your account. You will enter dimensions later on in this guide.  
6. Expand the Line details fasttab so you can add dimensions to your main account.
7. Click the Financial dimensions line tab.
    * The dimensions are for the selected line only.    
    * The sales tax group is populated from the customer. If the customer does not have a sales tax group, the sales tax group from the main account is used.  
    * The items sales tax group is populated from the main account. If the main account does not have an item sales tax group, then the item sales tax group in the General ledger sales tax parameters is used.    
8. In the Quantity field, enter a number.
    * The quantity is optional.  
9. In the Unit price field, enter a number.
    * The unit price is optional.  
    * The amount is calculated as the quantity times the unit price. However, you can override that calculation and enter an amount.  
10. Click on Sales tax to view the sales tax calculated for your invoice.
    * View the sales tax amounts in this page or you can override the amounts on the Adjustment tab.  
11. Click OK.
12. Click Charges to add a charge to your invoice. 
13. In the Charges code field, type a value.
14. In the Charges value field, enter a number.
15. Close the page.
16. Click Totals to view the summary invoice details and totals.
17. Click Close.
18. Click Post to post the invoice. You will be able to cancel before you post.
    * To change the timing of your invoice printing:  Select Current to print each invoice as it is updated   or  Select After to print after all invoices have been updated.  
    * If you want to change how the customer's credit limit is checked before posting, change the Credit limit type.  
    * If you want to print the invoice, select Yes.  
    * If you want to post the invoice, select Yes. You can print the invoice without posting.  
19. Click OK.

## Copy lines
To copy lines on the free text invoice, select one or more lines and then click Copy selected lines. You can specify the number of copies that you want to make, and you can also copy notes and attachments. You can copy the distributions or allow them to be recreated when you post. Once you copy the lines, you can edit the information as needed. 

## Create a free text invoice from a template
You can create a free text invoice from a template. When you select New from template from the Invoice tab, you can select a template name and the customer account for the new free text invoice. You can also choose to default values such as the terms of payment and method of payment from the customer or use the values that were saved with the template. A new free text invoice will be created and you can edit the values in that invoice. 
