--- 
title: Assign a free text invoice template to a customer
description: Learn about how to assign a free text invoice template to a customer intended for users responsible for managing A/R invoices, including a step-by-step process. 
author: ShivamPandeyMSFT
ms.author: shpandey
ms.topic: how-to
ms.date: 07/23/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30 
ms.search.form: CustTable, CustRecurrenceInvoice  
ms.dyn365.ops.version: Version 7.0.0 
---

# Assign a free text invoice template to a customer

[!include [banner](../../includes/banner.md)]

This article describes how to assign a free text invoice template to a customer. This task uses the USMF demo company and is intended for the user who is responsible for managing and processing A/R invoices.

1. Go to **Accounts receivable > Customers > All customers**.
2. In the list, find and select the desired record.
3. On the **Action Pane**, click **Invoice**.
4. Click **Recurring invoices**. Use this page to assign free text invoice templates to customers and specify how frequently invoices will be sent to the customer.  
5. Click **New** to assign a new template to the customer.
6. In the **Template** field, select the free text invoice template you want to assign to the customer.
7. In the list, find and select the desired record.
8. In the list, click the link in the selected row.
9. In the **Billing start date** field, enter the date when the first invoice will be generated.
10. In the **Recurrence end** section, enter a recurring end date.  
    Select one of the following: 
    - **No end date** – Invoices will be generated indefinitely until the template is removed from the customer account.
    - **Billing end date** – Select this option and enter the last date that the invoice can be generated.  
11. In the **Maximum cumulative amount** field, enter the maximum cumulative amount after which invoice generation will stop. Enter the maximum cumulative amount that can be reached using the selected template. For example, if you enter 1,000.00 and generate monthly invoices for 100.00 each, invoices stop generating after the tenth invoice is generated.  
12. In the **Generate recurring invoices by using the default values from** section, select either free text invoice template or the customer account. Select whether to use the free text invoice template or the customer account to determine the default values for the language, posting profile, sales tax group, item sales tax group, list code, country/region for delivery, currency, terms of payment, method of payment, payment specification, payment schedule, cash discount, financial dimensions, and giro money transfer slip when invoices are created.  
13. In the **Recurrence pattern** field, select the recurrence pattern.
    - **Daily** – Select this option and enter the number of days in the **Per** field. For example, if you enter 15, an invoice is generated every 15 days for this customer.
    - **Weekly** - Select this option and enter the number of weeks in the **Per** field. For example, if you enter 2, an invoice is generated every two weeks for this customer.
    - **Monthly** - Select this option and enter the number of months in the **Per** field. For example, if you enter 6, an invoice is generated every six months for this customer.
    - **Yearly** – Select this option and enter the number of years in the **Per** field. For example, if you enter 2, an invoice is generated every two years for this customer.  
14. In the **Per** field, enter a number.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
