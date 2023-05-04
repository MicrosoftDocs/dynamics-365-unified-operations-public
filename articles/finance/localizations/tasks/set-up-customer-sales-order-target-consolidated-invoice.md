---
title: Set up a customer and sales order to be target of consolidated invoice
description: In Japan, the customers usually use consolidated invoices for all transactions.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: CustTable, SalesTableListPage, SalesTable
---
# Set up a customer and sales order to be target of consolidated invoice

[!include [banner](../../includes/banner.md)]

In Japan, the customers usually use consolidated invoices for all transactions. 



Use this task to learn how to set up a customer and a sales order to use consolidated invoices. 



This task uses the JPMF demo company data.


## Set up a customer to be a target of consolidated invoice
1. Go to Accounts receivable > Customers > All customers.
2. In the list, click the link in the selected row.
3. Expand the Payment defaults section.
    * Verify that the Terms of payment uses the Cutoff day method.  
    * If the method is not "Cutoff day", unlock the task guide and then click Edit to update this field.  
    * Specify a consolidation day for the customer.  
    * You might need to click Edit before you can update this field.  

## Set a sales order to be target of consolidated invoice
1. Go to Accounts receivable > Orders > All sales orders.
2. In the list, click the link in the selected row.
3. Click Header.
    * Verify that the Target of consolidation slider is set to 'Yes'.  
    * If the slider is set to "No", unlock the task guide and then click Edit to update the field.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
