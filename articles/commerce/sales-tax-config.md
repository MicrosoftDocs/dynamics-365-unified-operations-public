---
# required metadata

title: Configure sales tax for online orders
description: This topic provides an overview of sales tax group selection for different online order types in Dynamics 365 Commerce.
author: gvrmohanreddy
manager: AnnBe
ms.date: 03/31/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: global
ms.search.industry: Retail
ms.author: gmohanv
ms.search.validFrom: 2020-11-01
ms.dyn365.ops.version: 10.0.16

---

# Configure sales tax for online orders

[!include [banner](includes/banner.md)]

This topic provides an overview of sales tax group selection for different online order types using either destination-based tax or customer account-based tax settings. 

You may want your e-commerce channel to support options like delivery or pickup for online orders. The sales tax applicability is based on the option selected by your online customers. 

## Destination-based taxes for online orders

In general, taxes for online orders that ship to customer addresses are defined by the destination. Every sales tax group has a retail destination-based tax configuration in which your business can define destination details such as county or region, state, county, and city in a hierarchical form.

### Orders delivered to customer address

When an online order is placed, the Commerce tax engine uses the delivery address of every line item in the order and finds sales tax groups with matching destination-based tax criteria. For example, for an online order with a line item delivery address to San Francisco, California, the tax engine will find the sales tax group and sales tax code for California and then calculate tax for each line item accordingly.

### Order pick up in store

For order lines with pick up in store or curbside pickup specified, the tax group from the selected pickup store will be applied. For details about how to set up sales taxes for a given store, see [Set other tax options for stores](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-other-tax-options-for-stores).

## Customer account-based taxes for online orders

There may be a business scenario where you want to configure a sales tax group on a specific customer account in Commerce headquarters. There are two places in headquarters where you can configure sales tax on a customer account:

- On **Customer** details page under **Invoice and delivery** tab **Sales Tax group** field. 
- On **Customer** details page, for a specific **Customer Address** > **Advanced** settings, under **General** tab Sales tax group field.

> [!TIP]
> For online customer orders, if you want to apply only the destination-based taxes and avoid customer account based taxes, ensure that Customer account \> Invoice and delivery tab \> Sales tax group field is empty. You should also check **default customer** settings for online channel and **Customer group** settings as well and make sure to leave Sales tax group field as blank. This way **new customers** those sign-up via online channel do not inherit the Sales tax group settings from **default customer** settings or from **Customer group** settings. 

## Determine destination-based tax or customer account-based tax applicability 

The following table explains whether destination-based taxes or customer account bases taxes are applied for online orders. 

| Customer type | Shipping address                   | Customer > Invoice and delivery > Sales tax group? | Address on customer account in headquarters? | Customer address > Advanced > General > Sales tax group?                                              | Sales tax group applied      |
|---------------|------------------------------------|-----------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------------------------|------------------------------|
| Guest         | Manhattan, NY                      | None                                                | None                              | None                                                                                                   | NY (Destination-based taxes) |
| Signed in     | Austin, TX                          | None                                                | Yes                               | None<br/><br/>New address added via online channel.                                                            | TX (Destination-based taxes) |
| Signed in     | San Francisco, CA (Pick up at store) | Yes (NY)                                            | N/A                               | N/A                                                                                                    | CA (Destination-based taxes) |
| Signed in     | Houston, TX                         | Yes (NY)                                            | Yes                               | Yes (NY)<br/><br/>New address added via online channel and sales tax group inherited from customer account. | NY (Customer account-based taxes)  |
| Signed in     | Austin, TX                          | Yes (NY)                                            | Yes                               | Yes (NY)<br/><br/>New address added via online channel and sales tax group inherited from customer account. | NY (Customer account-based taxes)  |
| Signed in     | Sarasota, FL                       | Yes (NY)                                            | Yes                               | Yes (WA)<br/><br/>Manually set to WA.                                                                          | WA (Customer account-based taxes)  |
| Signed in     | Sarasota, FL                       | None                                                | Yes                               | Yes (WA)<br/><br/>Manually set to WA.                                                                          | WA (Customer account-based taxes)  |

## Additional resources

[Set up taxes for online stores based on destination](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/set-up-taxes-for-online-stores-based-on-destination)

[Sales tax overview](https://docs.microsoft.com/dynamics365/finance/general-ledger/indirect-taxes-overview?toc=/dynamics365/commerce/toc.json) 

[Sales tax calculation methods in the Origin field](https://docs.microsoft.com/dynamics365/finance/general-ledger/sales-tax-calculation-methods-origin-field?toc=/dynamics365/commerce/toc.json) 

[Sales tax assignment and overrides](https://docs.microsoft.com/dynamics365/supply-chain/procurement/tasks/sales-tax-assignment-overrides?toc=/dynamics365/commerce/toc.json) 

[Whole amount and Interval calculation options for sales tax codes](https://docs.microsoft.com/dynamics365/finance/general-ledger/whole-amount-interval-options-sales-tax-codes?toc=/dynamics365/commerce/toc.json) 

[Calculation of tax exemption](tax-exempt-price-inclusive.md) 



[!INCLUDE[footer-include](../includes/footer-banner.md)]
