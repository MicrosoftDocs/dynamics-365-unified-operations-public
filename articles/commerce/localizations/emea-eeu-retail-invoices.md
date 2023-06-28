---
title: Customer invoices and return sales orders in Eastern European countries/region
description: This article describes how to set up information for customer invoices and return sales orders in Eastern European countries/region.
author: EvgenyPopovMBS
ms.date: 10/01/2018
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application user
ms.reviewer: josaw
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
ms.author: josaw
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1
ms.search.industry: Retail
---

# Customer invoices and return sales orders in Eastern European countries/region


[!include [banner](../../includes/banner.md)]

This article describes how to set up information for customer invoices and return sales orders in Eastern European countries/region.

You can set up the following information for customer invoices and return sales orders that are generated in Retail point of sale (POS).

- You can use sales tax groups to process returns by using return sales orders. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**. Open the **Posting \> Invoice** tab, and then set **Use sales tax group for returns** to **Yes**.

    * To specify the sales tax group for returns that are made by a customer, on the **Customers** page, on the **Commerce** FastTab, in the **Sales tax group for returns** field, select a sales tax group. When you post a return sales order for a customer, the return sales order line is updated with the sales tax group for returns that is specified in the **Customers** form.
    * To specify a sales tax group for returns that are made at a retail POS by a customer, on the **Stores** page, on the **General** FastTab, in the **Sales tax group for returns** field, select a sales tax group. When you post a return sales order for a customer of a  store, the return sales order line is updated with the sales tax group for returns that are specified on the **Stores** page.

- You can use the posting date of a customer invoice or a return sales order as the sales date of the invoice or return if the invoice or return does not have a default sales date. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**. Open the **Posting \> Invoice** tab, and then set **Use posting date as sales date** to **Yes**.
- You can use the number range that is provided by the tax authorities to number Latvian and Lithuanian customer invoices and return sales orders.

    * Go to **Organization administration \> Number sequences \> Counters management**. There should be a record where **Module** = **Sales** and **Type** = **Invoice**.
    * Go to **Organization administration \> Number sequences \> Invoice numbering setup**. Select the **Commerce** check box for the number sequence line that is used to number the customer invoices.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
