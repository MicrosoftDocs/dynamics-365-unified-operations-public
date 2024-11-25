---
title: Recurring vendor invoices
description: Learn about how to set up, process, generate, and assign recurring vendor invoices in Microsoft Dynamics 365 Finance.
author: sunfzam
ms.author: shpandey
ms.topic: article
ms.date: 2/1/2024
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-02-30
ms.search.form:
ms.dyn365.ops.version: 10.0.38
---

# Recurring vendor invoices

[!include [banner](../includes/banner.md)]

This article explains how to set up and process recurring vendor invoices in Microsoft Dynamics 365 Finance. You can use recurring vendor invoices when you regularly receive vendor invoices that have the same services, quantity, and price. To use recurring invoices, enable the **Enable AP recurring invoice** feature in Feature management.

## Create a recurring vendor invoice template

To create vendor invoices for the same services on a regular basis, create a vendor invoice template that has the following information:

- Header information, such as the posting profile, sales tax groups, terms of payment, and method of payment
- Line information, such as the service item number, procurement category code, quantity, unit price, and invoice amount
- Charges for shipping or handling
- Accounting distributions together with financial dimension information, such as cost centers and business units

On the **Pending vendor invoice** page, you can save an invoice as a template.

### Assign a vendor invoice template to a vendor and enter recurrence details

After the template is created, assign it to the vendors that you want to invoice. Additionally, specify when and how often the invoice is used.

Assign the templates on the **Invoice** tab of the **Vendor** page. Add the template to the list, and update the following information:

- The start date and, optionally, the end date for the recurring billing
- The frequency of the recurring billing (for example, every day or once a month)
- The maximum billing amount (if this information is required)

A single vendor can have multiple templates that have different frequencies.

### Generate recurring vendor invoices

The **Recurring invoices** page includes a task that processes recurring invoice templates. You specify the invoice date and the template to generate the invoices from. Invoices are generated, and a single recurrence ID number is assigned to each group of invoices that's processed. 

### Post recurring vendor invoices

After recurring vendor invoices are generated, invoice recurrence IDs appear in a posting task on the **Recurring vendor invoices** page. You can view all the invoices for a recurrence ID by selecting the link. Individual invoices can be deleted. The vendor recurrence settings are reset for that template, so that it can be regenerated later. You can post one, many, or all of the invoices for a recurrence ID. If workflows are enabled, you must select **Submit** before you can post the invoices.
