---
title: Subscription sales prices  
description: When you create a subscription, the sales price is derived from the sales price setup that was created on the Sales price (subscription) page.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMASalespriceSubscription
ms.topic: how-to
ms.date: 01/30/2025
ms.custom: 
  - bap-template
---

# Subscription sales prices

[!include [banner](../includes/banner.md)]

When you create a subscription, the sales price is derived from the sales price setup that was created on the **Sales price (subscription)** page.

On the **Sales price (subscription)** page, you can create sales prices for a specific subscription or you can create sales prices that apply more broadly. For a sales price to be applied to a subscription, the period code and the currency of the subscription must be identical to the period code and the currency of the sales price.

If the period code and currency are identical for the subscription and the sales price, subscription sales prices are selected on the basis of the priorities listed in the following table. A blank cell in the table indicates an empty field and an X indicates a value that is equal to the value in the subscription from which the transaction is generated.

| Priority | Category | Project ID | Subscription | Sales currency | Period code |
|----------|----------|------------|--------------|----------------|-------------|
| 1        | X        | X          | X            | X              | X           |
| 2        |          | X          | X            | X              | X           |
| 3        | X        |            | X            | X              | X           |
| 4        |          |            | X            | X              | X           |
| 5        | X        | X          |              | X              | X           |
| 6        |          | X          |              | X              | X           |
| 7        | X        |            |              | X              | X           |
| 8        |          |            |              | X              | X           |

When a subscription fee is created, the sales price with the greatest level of detail, as noted in the table above, is selected as the subscription sales price.

## Update and index subscription sales prices

You can update the subscription sales price by updating the base price or the index. You can update by a percentage or to a new value.

## Subscription fee sales prices

When you create a subscription fee, the sales price is based on the sales price setup of the subscription. You can either use the base price from the subscription price setup or create indexed sales prices.

## Example

You want to set up subscription sales prices of EUR 500 for a new project 9030. On the **Sales price (subscription)** page, you create a subscription sales price line as indicated in the following table.

| Valid from | Category | Project | Subscription | Period code | Sales currency | Sales price |
|------------|----------|---------|--------------|-------------|----------------|-------------|
| 28-08-2006 |          | 9030    |              | Month       | EUR            | 500         |

Note that the **Category** and **Subscription** fields are empty.

You then create the following subscriptions.

| Service subscription | Project | Subscription group | Category | Currency | Period code |
|----------------------|---------|--------------------|----------|----------|-------------|
| 00020_135            | 9030    | Sub1               | SubCat1  | EUR      | Monthly     |
| 00021_135            | 9030    | Sub1               | SubCat2  | EUR      | Monthly     |

Now you create subscription fees for both subscriptions in the subscription group Sub1:

1. Go to **Service management** \> **Setup** \> **Service subscriptions** \> **Subscription groups**.

2. On the **Subscription groups** page, select **Function** \> **Create subscription fee**.

3. On the **Create subscription fee** page, enter the appropriate information. Learn more in [Create subscription fee transactions](create-subscription-fee-transactions.md).

Subscription fees that have a sales price of EUR 500 are created for both subscriptions, as shown in the following table.

| Project date | Service subscription | Project | Category | Start date | End date   | Sales currency | Sales price |
|--------------|----------------------|---------|----------|------------|------------|----------------|-------------|
| 28-08-2006   | 00020_135            | 9030    | SubCat1  | 01-01-2007 | 31-03-2007 | EUR            | 500         |
| 28-08-2006   | 00021_135            | 9030    | SubCat2  | 01-01-2007 | 31-03-2007 | EUR            | 500         |

Later, you decide that you want to specify sales prices for the category SubCat1 for project 9030. Therefore, you create a new sales price line that has a sales price of EUR 550 for the combination of project 9030 and fee category SubCat1. There are now two subscription sales price lines for project 9030, as shown in the following table.

| Valid from | Category | Project | Subscription | Period code | Currency | Sales price |
|------------|----------|---------|--------------|-------------|----------|-------------|
| 28-08-2007 |          | 9030    |              | Month       | EUR      | 500         |
| 28-08-2007 | SubCat1  | 9030    |              | Month       | EUR      | 550         |

You repeat the procedure described above to create subscription fees for both subscriptions in the subscription group Sub1. The following table shows the transactions that are created for each subscription that is attached to the subscription group.

| Project date | Subscription | Project | Category | Start date | End date   | Sales currency | Sales price |
|--------------|--------------|---------|----------|------------|------------|----------------|-------------|
| 28-07-2007   | 00020_135    | 9030    | SubCat1  | 01-01-2008 | 31-03-2008 | EUR            | 550         |
| 28-07-2008   | 00021_135    | 9030    | SubCat2  | 01-01-2008 | 31-03-2008 | EUR            | 500         |

In the first transaction for subscription 00020\_135, the sales price of EUR 550 derives from the subscription sales price that is set up for the combination of the specific project and category. In the second transaction for subscription 00021\_135, the sales price of EUR 500 is used as the project subscription sales price because there's no price set up for the combination of project 9030 and category SubCat2.

## Related information

- [Update and index subscription sales prices](update-and-index-subscription-sales-prices.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
