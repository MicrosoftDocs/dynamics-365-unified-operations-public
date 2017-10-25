--- 
# required metadata 
 
title: Create a direct debit mandate for a customer
description: This task guide demonstrates how to create a direct debit mandate and use it on an invoice. 
author: ShivamPandey-msft
manager: AnnBe 
ms.date: 10/23/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a direct debit mandate for a customer

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide demonstrates how to create a direct debit mandate and use it on an invoice.


## Create a bank account
1. Go to Accounts receivable > Customers > All customers.
2. For example, select US-001
3. On the Action Pane, click Customer.
4. Click Bank accounts.
5. Click New.
6. In the Bank account field, type a value.
7. In the Name field, type a value.
8. In the IBAN field, type a value.
9. In the Currency field, type a value.
10. Click Save.
11. Close the page.
12. Go to Cash and bank management > Bank accounts > Bank accounts.
13. In the list, find and select the desired record.
14. In the list, click the link in the selected row.
15. Click Edit.
16. Expand the Additional identification section.
17. In the Direct debit ID field, type a value.
18. In the IBAN field, type a value.
19. Close the page.
20. Close the page.

## Define the electronic payment method
1. Go to Accounts receivable > Payments setup > Methods of payment.
2. Click New.
3. In the Method of payment field, type a value.
4. In the Description field, type a value.
5. The payment type for a direct debit mandate method of payment must be Electronic payment.
6. Select Yes in the Require mandate field.
7. Close the page.

## Add a direct debit mandate to a customer.
1. Go to Accounts receivable > Customers > All customers.
2. For example, select US-001
3. Click Edit.
4. Expand the Payment defaults section.
5. In the Method of payment field, enter or select a value.
6. Expand the Payment defaults section.
7. Expand the Direct debit mandates section.
8. Click Add.
9. In the Bank account field, enter or select a value.
10. In the Creditor bank account field, enter or select a value.
11. Enter the number of payments that you expect to process for this mandate.
12. Click OK.
13. Click Print.
14. Click Mandate report.
15. Close the page.
16. Click Edit.
17. In the Signature date field, enter a date.
18. Click Yes.
19. Enter the location where the mandate was signed.
20. Click OK.
21. Close the page.

## Create a free text invoice with mandate
1. Go to Accounts receivable > Invoices > All free text invoices.
2. Click New.
3. Select the customer that you added the mandate to.
4. In the Direct debit mandate ID field, enter or select a value.

