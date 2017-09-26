--- 
# required metadata 
 
title: Assign a free text invoice template to a customer
description: This task demonstrates how to assign a free text invoice template to a customer. 
author: ShivamPandey-msft
manager: AnnBe 
ms.date: 11/10/2016
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
# Assign a free text invoice template to a customer

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task demonstrates how to assign a free text invoice template to a customer. This task uses the USMF demo company and is intended for the user who is responsible for managing and processing A/R invoices.

1. Go to Accounts receivable > Customers > All customers.
2. In the list, find and select the desired record.
3. On the Action Pane, click Invoice.
4. Click Recurring invoices.
    * Use this page to assign free text invoice templates to customers and specify how frequently invoices will be sent to the customer.  
5. Click New to assign a new template to the customer.
6. Select the free text invoice template you want to assign to the customer.
7. In the list, find and select the desired record.
8. In the list, click the link in the selected row.
9. Enter the date when the first invoice will be generated.
    * Enter a recurring end date.  
    * Select one of the following: No end date – Invoices will be generated indefinitely until the template is removed from the customer account.  Billing end date – Select this option and enter the last date that the invoice can be generated.  
    * Maximum cumulative amount after which invoice generation will stop.  
    * Enter the maximum cumulative amount that can be reached using the selected template. For example, if you enter 1,000.00 and generate monthly invoices for 100.00 each, invoices will stop generating after the tenth invoice is generated.  
    * Generate recurring invoices by using the default values from either free text invoice template or the customer account.  
    * Select whether to use the free text invoice template or the customer account to determine the default values for the language, posting profile, sales tax group, item sales tax group, list code, country/region for delivery, currency, terms of payment, method of payment, payment specification, payment schedule, cash discount, financial dimensions, and giro money transfer slip when invoices are created.  
10. Select the recurrence pattern.
    * Daily – Select this option and enter the number of days in the Per field. For example, if you enter 15, an invoice will be generated every 15 days for this customer.  Weekly - Select this option and enter the number of weeks in the Per field. For example, if you enter 2, an invoice will be generated every two weeks for this customer.  Monthly - Select this option and enter the number of months in the Per field. For example, if you enter 6, an invoice will be generated every six months for this customer.  Yearly – Select this option and enter the number of years in the Per field. For example, if you enter 2, an invoice will be generated every two years for this customer.  
11. In the Per field, enter a number.

