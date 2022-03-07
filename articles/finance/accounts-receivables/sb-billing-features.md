---
# required metadata

title: Billing schedule features
description: This topic explains some of the features available on a billing schedule such as pricing methods, escalation and discount, alignment dates, proration, reverse billing, and split item groups, 
  
author: JodiChristiansen
ms.date: 11/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Pricing methods

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]


You can use one of the following pricing methods to calculate the unit price of an item: 
* Flat (no example)
* Standard 
* Tier 
* Flat Tier

## Flat 

When the flat pricing method is used, the unit price for a schedule line item on the **[Billing Schedules](../enduser/BillSched.md)** page can be edited to any value you want. 

When the flat pricing option is used, the **Price unit** is always 1. As a result, the **Unit price** and the **Net amount** for an item are the same. 

## Standard Price  (no Trade Agreement)

When the standard pricing method (without a trade agreement) is used, the unit price for a schedule line item is set up on the **Release product details** page. Specifically, the unit price is from the **Base Sales Price** section and is calculated as follows: **Price** / **Price quantity**.

## Standard Price (with Trade Agreement)

The following example provides information standard pricing calculations when a trade agreement exists. You can create trade agreements from the **Release product details** page. For more information, see [Base price and trade agreements](https://docs.microsoft.com/en-us/dynamics365/commerce/tasks/base-price-trade-agreements) ![New window icon](../../../Resources/images/icons/iNewWindow.png)in the Microsoft Dynamics 365 for Finance and Operations documentation. 

An item has the following price brackets: 


| Qty From| Qty To| U of M|Price|Price Unit|
| :------------- |:-------------| :------|------:|------:|
|0 |100| Each|1.50|1|
|100|200 |Each|1.25|100|
|200|999999|Each|1.00|100|

Using the price brackets, assume the invoice quantity is 250. With the standard pricing method, the unit price is calculated as follows: 
* Quantity 250 is in the price quantity range 200 - 99999 , so the unit price is 1.00

>Net amount = (Quantity * Price) / Price unit = (250 * 1.00) / 100 = 2.50 

Another example for an invoice quantity of 100. With the standard pricing method, the unit price is calculated as follows: 
* Unit price = 1.50, which uses the price level that has the quantity of 100

>Net amount = (100 x 1.50) / 1 = 150

## Tier Price 

An item has the following price brackets: 

| Qty From| Qty To| U of M|Price|Price Unit|
| :------------- |:-------------| :------|------:|------:|
|0 |100| Each|1.50|100|
|100|200 |Each|1.25|100|
|200|999999|Each|1.00|100|

Using the price brackets, assume the invoice quantity is 250. With the tier pricing method, the net amount is calculated. After calculating the net amount, you can obtain the unit price by dividing the new amount by the quantity. Review the sequence of events to obtain the unit price: 
1. Get the prices of the items based on the pricing brackets: 
   * First hundred items: 100 x 1.50  = 150.00 
   * Second hundred items: 100 x 1.25 = 125.00
   * Remaining items: 50 x 1.00 = 50.00
1. Get the net amount. <br />Net amount = (150.00 / 100) + (125.00 / 100) + (50.00 /100) = 1.50 + 1.25 + 0.50 = 3.25
1. Use the net amount and quantity to obtain the unit price. 
>Unit price = 3.25 / 250 = 1.30

## Flat Tier  Price 

The price brackets are set as follows: 

| Qty From| Qty To| U of M|Price|Price Unit|
| :------------- |:-------------| :------|------:|------:|
|0 |50| Each|100.00|50|
|50|200 |Each|150.00|200|

The following invoices show the unit prices with the different quantities purchased: 

|Invoice|Quantity Purchased|Unit Price|Net Amount|
| :------------- |:-------------:| :------|------:|
|1|25| 2 / 25 = 0.08|100 / 50 = 2.00|
|2|20 |2 / 20 = 0.10|100 / 50 = 2.00|
|3|50|2 / 50 = 0.04|100 / 50 = 2.00|
|4|60|0.75 / 60 = 0.0125 = 0.01|150 / 200 = 0.75|


<table class="drcr"><col><col><col><col><thead><tr class="heading"><td>Invoice</td><td>Quantity Purchased</td><td>Unit Price</td><th>Net Amount</th></tr></thead><tbody><tr><td>1</td><td>25</td><td>2 / 25 = 0.08</td><td>100 / 50 = 2</td></tr><tr><td>2</td><td>20</td><td>2 / 20 = 0.1</td><td>100 / 50 = 2</td></tr><tr><td>3</td><td>50</td><td>2 / 50 = 0.04</td><td>100 / 50 = 2</td></tr><tr><td>4</td><td>60</td><td>0.75 / 60 = 0.0125 = 0.01</td><td>150 / 200 = 0.75</td></tr></tbody></table><div>

## See also

[Tier Pricing Workflow](../workflow/TierPriceWF.md)
