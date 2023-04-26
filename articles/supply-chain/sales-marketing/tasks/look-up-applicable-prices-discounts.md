--- 
# required metadata 
 
title: Look up applicable prices and discounts
description: This procedure shows how to find the price and/or discount for a product which is currently valid for a specific customer, without creating a sales order. 
author: Henrikan
ms.date: 11/10/2016
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: henrikan
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Look up applicable prices and discounts

[!include [banner](../../includes/banner.md)]

This procedure shows how to find the price and/or discount for a product which is currently valid for a specific customer, without creating a sales order. The procedure walks through a specific example, and you need follow the example using the USMF demo company in order to select the necessary values.


## Find the applicable price
1. Go to Sales and marketing > Prices and discounts > Find prices.
2. In the Customer account field, click the drop-down button to open the lookup.
3. In the list, find and select customer US-001.
4. In the list, click the link in the selected row.
5. In the Item number field, type 'T0004'.
    * By default, the Quantity field is set to 1. However, if you know the size of the order that the customer intends to place for the product in question, then enter this value instead. This information is relevant if the trade agreements with the customer have quantity breaks, that is, the product's price depends on the minimum quantity purchased.  
6. In the Date field, enter a date for when the customer expects to place an order. 
    * The date can be today's date or any date in the future.  
    * The system now returns the price that is valid for the selected product when bought by the selected customer on the selected date with a specified quantity. In this example, if the customer US-001 bought 1 unit of product T0004 today, they would be charged 350 CAD a unit. This price comes from an existing and active trade agreement with the customer.      Other fields on the page provide more details about the product price and product cost (if set up on the product master), and calculated profitability.  
    * If the Show related product variants option is selected, it means that there are additional trade agreements for product's variants.  
7. Click the Show related product variants checkbox.
    * A list of the product variants is shown, with information about their dimensions.  
8. In the list, mark the line representing color White.
    * Notice, that the product price is now different from the one displayed previously when it was not specified per dimension.  
9. Click View sales prices.
    * The Price (sales) page displays all the trade agreements applicable to the product, including its variants.  
10. Close the page.

## Find the applicable discount
Make sure the Customer account field contains customer number US-001   
1. In the Item number field, type 'T0012'.
    * Make sure the Quantity field is set to 1.  
    * The following pricing details shown for product T0012 come from one or more trade agreements: The unit price is 1,000 CAD and the discount percentage is 5.  
2. Set Quantity to '20'.
    * The increased order quantity causes the line discount that will be offered to the customer to change from 5 to 7 percent.  
    * The Net amount is calculated based on the unit price, discount and the total quantity.  
3. Click View line discount.
    * There are two line discount agreements for product T0012, specifying a 5 percent discount for an order line quantity from 1 to 10, and 7 percent discount for order quantities above 10. Note that the discounts are applied to a group of products, in this example, Group code 01, of which product T0012 is a member.  
4. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]