---
# required metadata

title: Set up and process recurring invoices
description: This article explains how to set up and process recurring invoices. You can use recurring invoices if you must invoice customers for the same amount on a regular basis.
author: ShivamPandey-msft
ms.date: 03/22/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustInvoiceTemplate
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 14011
ms.assetid: 9cc37003-adf1-413d-b2b2-2badcf512e3b
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up and process recurring invoices

[!include [banner](../includes/banner.md)]

This article explains how to set up and process recurring invoices. You can use recurring invoices if you must invoice customers for the same amount on a regular basis.

## Create a recurring free text invoice template

To invoice customers for the same services on a regular basis, you must define a free text invoice template that can be reused to create the invoices. This template contains the following information:

-   Header information, such as tax groups, terms of payment, and the method of payment
-   Line information, such as the service description, revenue accounts, unit price, and invoice amount
-   Charges for shipping or handling
-   Accounting distributions together with financial dimension information, such as cost centers and business units

In effect, you're creating an entire invoice and saving it as a template. You can set up the templates using the **Recurring invoices** page.

## Assign a free text invoice template to a customer and enter recurrence details
After the template is created, you must assign the template to the customers that you want to invoice. Additionally, you must specify when and how often the invoice will be used. You can assign the templates on the **Invoice** tab of the **Customers** page. Add the template to the list, and update the following information:

-   The start date and, optionally, the end date for the recurring billing
-   The frequency of the recurring billing (for example, every day or once a month)
-   The maximum billing amount (if this information is required)

A customer can have multiple templates that have different frequencies.

## Generate the recurring invoices
On the **Recurring invoices** page, there is a task that processes recurring invoice templates. You specify the invoice date and the template to generate the invoices from. Invoices will be generated and assigned a single recurrence ID number for each group of invoices that is processed.

## Post recurring free text invoices

After recurring invoices are generated, the invoice recurrence IDs appear in a posting task on the **Recurring invoices** page. You can view all of the invoices for a recurrence ID by clicking the link. During your review of the invoices for the recurrence ID, you can delete individual invoices. The customer's recurrence settings will be reset for that template, so that it can be regenerated later. You can post one, many, or all of the invoices for a recurrence ID. If workflows are enabled, you must click **Submit** before you can post the invoices.

## Print recurring free text invoices

After recurring invoices are posted, you can print the invoices from the **Free text invoice list** page. You can print the invoices that are selected, or you can select a range of invoices to print.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
