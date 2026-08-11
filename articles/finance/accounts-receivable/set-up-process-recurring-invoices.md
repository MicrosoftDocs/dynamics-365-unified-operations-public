---
title: Set up and process recurring invoices
description: Learn how to set up and process recurring invoices. You can use recurring invoices if you must invoice customers for the same amount on a regular basis.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 08/05/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: CustInvoiceTemplate
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9cc37003-adf1-413d-b2b2-2badcf512e3b
---

# Set up and process recurring invoices

[!include [banner](../includes/banner.md)]

This article explains how to set up and process recurring invoices. Use recurring invoices when you need to bill customers for the same amount regularly.

## Create a recurring free text invoice template

To invoice customers for the same services on a regular basis, you must define a free text invoice template that can be reused to create the invoices. This template contains the following information:

- Header information, such as tax groups, terms of payment, and the method of payment
- Line information, such as the service description, revenue accounts, unit price, and invoice amount
- Charges for shipping or handling
- Accounting distributions together with financial dimension information, such as cost centers and business units

Effectively, you're creating an entire invoice and saving it as a template. Set up the templates by using the **Recurring invoices** page.

## Assign a free text invoice template to a customer and enter recurrence details

After you create the template, assign it to the customers that you want to invoice. Also, specify when and how often to use the invoice. Assign the templates on the **Invoice** tab of the **Customers** page. Add the template to the list, and update the following information:

- The start date and, optionally, the end date for the recurring billing
- The frequency of the recurring billing (for example, every day or once a month)
- The maximum billing amount (if this information is required)

A customer can have multiple templates that have different frequencies.

## Generate the recurring invoices

On the **Recurring invoices** page, a task processes recurring invoice templates. You specify the invoice date and the template to generate the invoices from. The system generates invoices and assigns a single recurrence ID number to each group of invoices that it processes.

## Post recurring free text invoices

After the system generates recurring invoices, the invoice recurrence IDs appear in a posting task on the **Recurring invoices** page. You can view all of the invoices for a recurrence ID by selecting the link. During your review of the invoices for the recurrence ID, you can delete individual invoices. The customer's recurrence settings reset for that template, so that you can regenerate it later. You can post one, many, or all of the invoices for a recurrence ID. If workflows are enabled, you must select **Submit** before you can post the invoices.

## Print recurring free text invoices

After you post recurring invoices, you can print the invoices from the **Free text invoice list** page. You can print the invoices that you select, or you can select a range of invoices to print.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
