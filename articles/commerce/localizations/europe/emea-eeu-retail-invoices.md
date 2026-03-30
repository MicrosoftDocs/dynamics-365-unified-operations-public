---
title: Customer invoices and return sales orders in Eastern European countries/regions
description: Learn how to set up information for customer invoices and return sales orders in Eastern European countries/regions.
author: EvgenyPopovMBS
ms.date: 02/26/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
ms.author: anupamar
ms.search.validFrom: 2018-10-31
ms.custom: 
  - bap-template
---

# Customer invoices and return sales orders in Eastern European countries/regions

[!include [banner](../../../finance/includes/banner.md)]

This article describes how to set up information for customer invoices and return sales orders in Eastern European countries/regions.

Set up the following information for customer invoices and return sales orders that Retail point of sale (POS) generates.

- Use sales tax groups to process returns by using return sales orders. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**. Open the **Posting \> Invoice** tab, and then set **Use sales tax group for returns** to **Yes**.

    * To specify the sales tax group for returns that a customer makes, on the **Customers** page, on the **Commerce** FastTab, in the **Sales tax group for returns** field, select a sales tax group. When you post a return sales order for a customer, the return sales order line is updated with the sales tax group for returns that you specify in the **Customers** form.
    * To specify a sales tax group for returns that a customer makes at a retail POS, on the **Stores** page, on the **General** FastTab, in the **Sales tax group for returns** field, select a sales tax group. When you post a return sales order for a customer of a store, the return sales order line is updated with the sales tax group for returns that you specify on the **Stores** page.

- Use the posting date of a customer invoice or a return sales order as the sales date of the invoice or return if the invoice or return doesn't have a default sales date. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**. Open the **Posting \> Invoice** tab, and then set **Use posting date as sales date** to **Yes**.
- Use the number range that the tax authorities provide to number Latvian and Lithuanian customer invoices and return sales orders.

    * Go to **Organization administration \> Number sequences \> Counters management**. There should be a record where **Module** = **Sales** and **Type** = **Invoice**.
    * Go to **Organization administration \> Number sequences \> Invoice numbering setup**. Select the **Commerce** check box for the number sequence line that numbers the customer invoices.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
