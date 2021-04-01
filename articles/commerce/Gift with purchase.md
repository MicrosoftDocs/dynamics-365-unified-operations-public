---
# required metadata

title: Gift with purchase
description: This topic provides an overview of the Microsoft Dynamics 365 Payment Connector for PayPal.
author: rubendel
ms.date: 11/18/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2020-10-31
ms.dyn365.ops.version: AX 7.0.1

---

# Gift with purchase

[!include [banner](../includes/banner.md)]

It is a common practice among retailers to run "Gift with purchase" promotions to tempt the customers in buying merchandize at full price and give complimentary item at a discount or free. This can also help in moving a slow moving item off the shelf and, if done right, improves the overall customer experience. As of 10.0.19, retailers can leverage the Threshold discount feature within Dynamics 365 Commerce to setup such promotions.

With 10.0.19, the "Discount method" column under the "Threshold discount tiers" fast tab shows a new value named "Discount lines" (refer the image below). If this discount method is selected, then the users will see a new fast tab named "Threshold discount lines" appears at the bottom of the Threshold discount form. The items mentioned in the "Lines" fast tab should be considered as qualification items while the items mentioned in the "Threshold discount lines" fast tab should be considered as the discounted items. Thus, the threshold amount specified is checked against the qualifying lines to determine if the threshold has been met. If it is met, then the items mentioned in the "Threshold discount lines" will get the discount. Additionally, you can also specify the quantity of items that should be discounted when the threshold is met. For e.g. if you want to run a promotion like Spend $200 on dress shirts and get 2 Ties for free, then you would create a discount threshold tier with $200 and choose the "Discount lines" option as the discount method. Next, you would choose the Dress shirts category in the Lines fast tab i.e. qualifying items and add the Ties category in the "Threshold discount lines" fast tab i.e. discounted items. Additionally, you would put choose discount percent as 100% in the "Quantity limit" to restrict the discount for 2 quantities. With this setup, if there are dress shirts added to the transaction worth more than $200, then when the ties are added to the transaction, up-to 2 ties will be given for free. Dynamics 365 Commerce also makes it easy for the sales associate or end customer to know that they have qualified for a gift by using the "View available discount" feature where the system shows all the applicable discounts. To learn more about the "View available discounts" feature, refer this link: https://docs.microsoft.com/en-us/dynamics365/commerce/discounts-pos#cross-sell-and-upsell-by-using-discounts.

As mentioned above, the "Quantity limit" column of the "Threshold discount lines" fast tab allows you to restrict the number of items that should be discounted, but this field could be set to 0 which means that there is no restriction on how many items can be discounted. Thus, in the above example, if the "Quantity limit" was set to 0, then, once the customer meets the threshold, the customer could get any number of ties for free. Another thing to note is that you can add multiple items in the "Threshold discount lines" fast tab to indicate all the items that should be discounted. For e.g. you could add one row for 2 ties and one row for 2 bows. This will be interpreted as spend $200 on shirts and get 2 ties *and* 2 bows for free. If the requirement is to give 2 ties *or* 2 bows for free (or 1 bow and 1 tie for free), then the tie and bows should be added in a single row, by creating a supplemental category for tie and bows.
![image](https://user-images.githubusercontent.com/28161726/113357145-5923df80-92f8-11eb-8f41-a67290c1f884.png)
