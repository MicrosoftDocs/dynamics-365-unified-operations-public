---
# required metadata

title: Retail customer invoices and return sales orders in Eastern European countries
description: 
author:  
manager: epopov
ms.date: 10/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Eastern Europe
ms.search.industry: Retail
ms.author: v-kikozl
ms.search.validFrom: 2018-10-01
ms.dyn365.ops.version: 8.1
---
# Retail customer invoices and return sales orders in Eastern European countries

*Applies To: Dynamics 365 for Retail and Dynamics 365 for Finance and Operations*

You can set up the following information for customer invoices and return sales orders that are generated in Retail POS:
- Use sales tax groups to process returns by using return sales orders. Click **_Retail > Headquarters setup > Parameters > Retail parameters_**. Open tab **_Posting > Invoice_**, and then toggle the **Use sales tax group for returns** to Yes. 

  * To specify the sales tax group for returns that are made by a customer, in the **Customers** form, on the **_Retail_** FastTab, in the **Sales tax group for returns** field, select a sales tax group. When you post a return sales order for a customer, the return sales order line is updated with the sales tax group for returns that is specified in the **Customers** form.
  
     or

   * To specify a sales tax group for returns that are made at a retail POS by a customer, in the **Stores** form, on the **_General_** FastTab, in the **Sales tax group for returns** field, select a sales tax group. When you post a return sales order for a customer of a retail store, the return sales order line is updated with the sales tax group for returns that is specified in the Stores form.

- Use the posting date of a retail customer invoice or a return sales order as the sales date of the invoice or return if the invoice or return does not have a default sales date. Click **_Retail > Headquarters setup > Parameters > Retail parameters_**. Open tab **_Posting > Invoice_**, and then toggle the **Use posting date as sales date** to Yes.

- Use the number range that is provided by the tax authorities to number Latvian and Lithuanian customer invoices and return sales orders. 

  * Click **_Organization administration > Number sequences > Counters management_**, there should be a record with Module = Sales and Type = Invoice.

  * Click **_Organization administration > Number sequences > Invoice numbering setup_**. Mark the **Retail** check box for the number sequence line that is used to number the customer invoices.
