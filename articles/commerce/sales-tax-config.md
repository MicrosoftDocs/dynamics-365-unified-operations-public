---
title: Configure sales tax for online orders
description: This article provides an overview of sales tax group selection for different online order types in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 01/29/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-11-01
ms.custom: 
  - bap-template
---

# Configure sales tax for online orders

[!include [banner](includes/banner.md)]

This article provides an overview of sales tax group selection for different online order types in Microsoft Dynamics 365 Commerce, using either destination-based or customer account-based tax settings.

You might want your e-commerce channel to support options like delivery or pickup for online orders. The sales tax applicability is based on the option selected by your online customers.

## Destination-based taxes for online orders

In general, destinations define the taxes for online orders that ship to customer addresses. Every sales tax group has a retail destination-based tax configuration in which your business can define destination details, such as country/region, state, county, and city in a hierarchical form.

You can find the configuration for **Retail destination based tax** in the **Tax module > Indirect taxes > Sales tax > Sales Tax Groups** section.

### Orders delivered to customer address

When a customer places an online order, the Commerce tax engine uses the delivery address of every line item in the order and finds sales tax groups with matching destination-based tax criteria. For example, for an online order with a line item delivery address to San Francisco, California, the tax engine finds the sales tax group and sales tax code for California and then calculates the tax for each line item.

### Order pick up in store

For order lines with pick up in store or curbside pickup specified, the tax group from the selected pickup store applies. For details about how to set up sales taxes for a given store, see [Set other tax options for stores](/dynamicsax-2012/appuser-itpro/set-other-tax-options-for-stores).

## Customer account-based taxes for online orders

A business scenario might require you to configure a sales tax group on a specific customer account in Commerce headquarters. You can configure sales tax on a customer account in two places in headquarters. To access these options, first go to a customer detail page by going to **Retail and Commerce \> Customers \> All customers** and then selecting a customer.

The two places where you configure sales tax for a customer account are:

- **Sales tax group** on the **Invoice and delivery** FastTab of the customer details page.
- **Sales tax** on the **General** FastTab of the **Manage addresses** page. To get there from the customer details page, select a specific address under the **Addresses** FastTab and then select **Advanced**.

> [!TIP]
> For online customer orders, if you only want to apply the destination-based taxes and avoid customer account-based taxes, ensure that the **Sales tax group** field is empty on the **Invoice and delivery** FastTab of the customer details page. To ensure that new customers who sign up by using the online channel don't inherit the sales tax group settings from default customer or customer group settings, ensure that the **Sales tax group** field is also empty for the online channel default customer settings and customer group settings (**Retail and Commerce \> Customers \> Customer groups**).

## Determine destination-based tax or customer account-based tax applicability

The following table explains whether destination-based taxes or customer account-based taxes apply for online orders.

| Customer type | Shipping address                   | Customer > Invoice and delivery > Sales tax group? | Address on customer account in headquarters? | Customer address > Advanced > General > Sales tax group?                                              | Sales tax group applied      |
|---------------|------------------------------------|-----------------------------------------------------|-----------------------------------|--------------------------------------------------------------------------------------------------------|------------------------------|
| Guest         | Manhattan, NY                      | No (blank)                                                | No (blank)                              | No (blank)                                                                                                   | NY (destination-based taxes) |
| Signed in     | Austin, TX                          | No (blank)                                             | Yes                               | None<br/><br/>New address added via online channel.                                                            | TX (destination-based taxes) |
| Signed in     | San Francisco, CA (Pick up at store) | Yes (NY)                                            | Not applicable                              | Not applicable                                                                                                    | CA (destination-based taxes) |
| Signed in     | Houston, TX                         | Yes (NY)                                            | Yes                               | Yes (NY)<br/><br/>New address added via online channel and sales tax group inherited from customer account. | NY (customer account-based taxes)  |
| Signed in     | Austin, TX                          | Yes (NY)                                            | Yes                               | Yes (NY)<br/><br/>New address added via online channel and sales tax group inherited from customer account. | NY (customer account-based taxes)  |
| Signed in     | Sarasota, FL                       | Yes (NY)                                            | Yes                               | Yes (WA)<br/><br/>Manually set to WA.                                                                          | WA (customer account-based taxes)  |
| Signed in     | Sarasota, FL                       | No (blank)                                                | Yes                               | Yes (WA)<br/><br/>Manually set to WA.                                                                          | WA (customer account-based taxes)  |

## Additional resources

[Set up taxes for online stores based on destination](/dynamicsax-2012/appuser-itpro/set-up-taxes-for-online-stores-based-on-destination)

[Sales tax overview](../finance/general-ledger/indirect-taxes-overview.md?toc=%2fdynamics365%2fcommerce%2ftoc.json)

[Sales tax calculation methods in the Origin field](../finance/general-ledger/sales-tax-calculation-methods-origin-field.md?toc=%2fdynamics365%2fcommerce%2ftoc.json)

[Sales tax assignment and overrides](../supply-chain/procurement/tasks/sales-tax-assignment-overrides.md?toc=%2fdynamics365%2fcommerce%2ftoc.json)

[Whole amount and Interval calculation options for sales tax codes](../finance/general-ledger/whole-amount-interval-options-sales-tax-codes.md?toc=%2fdynamics365%2fcommerce%2ftoc.json)

[Calculation of tax exemption](dev-itpro/tax-exempt-price-inclusive.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
