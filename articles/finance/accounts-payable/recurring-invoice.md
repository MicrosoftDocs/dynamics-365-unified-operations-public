---
# required metadata

title: Recurring vendor invoices
description: This article explains how to set up and process recurring vendor invoices in Dynamics 365 Finance.
author: sunfzam
ms.date: 2/1/2024
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2024-02-30
ms.dyn365.ops.version: 10.0.38

---

# Recurring vendor invoices

[!include [banner](../includes/banner.md)]

This article explains how to set up and process recurring vendor invoices in Dynamics 365 Finance. You can use recurring vendor invoices if you receive the vendor invoices with the same services, qty and price on 
a regular basis. Before starting, you have to enable the feature "Enable AP recurring invoice" in the feature management.  

## Create a recurring vendor invoice template 

To create the vendor invoice for the same services on a regular basis, you must define a vendor invoice template by defining the following: 
 - Header information, such as posting profile, sales tax groups, terms of payment, and the method of payment.
 - Line information, such as the service item number, procurement category code, quanity, unit price, and invoice amount.
 - Charges for shipping or handling.
 - Accounting distributions together with financial dimension information, such as cost centers and business units. 

In pending vendor invoice form, you can also save an entire invoice as a template. 

### Assign a vendor invoice template to a vendor and enter recurrence details 

After the template is created, you must assign the template to the vendors that you want to invoice. Additionally, you must specify when and how often the invoice will be used. You can assign the templates on 
the Invoice tab of the Vendor page. Add the template to the list, and update the following information: 
 - The start date and, optionally, the end date for the recurring billing
 - The frequency of the recurring billing (for example, every day or once a month)
 - The maximum billing amount (if this information is required)
 - A vendor can have multiple templates that have different frequencies. 

### Generate the recurring vendor invoices 

On the Recurring invoices page, there is a task that processes recurring invoice templates. You specify the invoice date and the template to generate the invoices from. Invoices will be generated and assigned a
single recurrence ID number for each group of invoices that is processed. 

### Post recurring vendor invoices 

After recurring vendor invoices are generated, invoice recurrence IDs appear in a posting task on the Recurring vendor invoices page. You can view all of the invoices for a recurrence ID by clicking the link. 
During your review of the invoices for the recurrence ID, you can delete individual invoices. The vendor recurrence settings will be reset for that template, so that it can be regenerated later. You can post one,
many, or all of the invoices for a recurrence ID. If workflows are enabled, you must click Submit before you can post the invoices. 


With the feature, user can define the recurring vendor invoice template with service item, amount, sales tax, charges, accounting distribution. Then the user can create and post the recurring vendor invoice based
on the template to save time.  

 


