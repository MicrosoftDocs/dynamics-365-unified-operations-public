---
# required metadata

title: Retail coupons
description: Retail coupons overview. Discount codes and call center coupons have been merged into a one feature set.
author: scott-tucker
manager: AnnBe
ms.date: 05/22/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  RetailCoupon
audience: Application User
# ms.devlang: 
# ms.reviewer: josaw
# ms.search.scope: [Which Operations client to show this topic as help for, to be set by content strategist, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: retail
ms.author: scotttuc
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

# Coupons for retail sales

[!include[banner](../includes/banner.md)]

## Merging call center coupons with retail discounts

In prior releases of Microsoft Dynamics AX 2012 and Microsoft Dynamics 365 call center coupons and discount codes on retail discounts were two unrelated features that shared a common purpose. They enabled discount targeting and discount controls for a retailer. A retailer can limit which customers with the code are entitled to the discount.
With this update, we have merged call center coupons with retail discounts to provide a unified experience for managing and accepting coupons in all retail channels. At the highest level the combined feature uses the codes from coupons and the discount value from retail discounts.

At a glance to merge the two features we did the following.
- Removed the discount code and bar code fields from the retail discount forms
- Added a link from coupon to a retail discount
- Enabled multiple coupon codes and bar codes to be created for a single coupon
- Removed the discount value definition from the coupons form
- Removed the customer and product references from the coupon
- Removed the direct GL posting of a coupon liability
- Removed the charge code parameter for coupons


For a comparison, here is a table of the features of the merged coupons compared to discount codes and call center coupons.

| Coupons for retail channels - NEW                                                                                                                                                                                                                                                                                                                                                                                                          | Retail discount with a discount code                                                                                     | Call center coupon                                                                                                                                                                                      |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Each coupon is linked to exactly one discount. Each discount can be linked to 1 or more coupons.                                                                                                                                                                                                                                                                                                                                           |                                                                                                                          |                                                                                                                                                                                                         |
| A coupon can have multiple coupon codes with a bar code, each with an independent date range.                                                                                                                                                                                                                                                                                                                                              | Had only one discount code and bar code.                                                                                 | Had only one coupon number.                                                                                                                                                                             |
| Each coupon code on a coupon can have an independent date range.                                                                                                                                                                                                                                                                                                                                                                           | Had one date range or could have a re-occurring day and time period within a date range.                                 | Had only one date range available.                                                                                                                                                                      |
| A coupon can be configured to require a customer.    When a coupon is configured to require a customer, the valid customers are defined by linking the discount to customers using affiliations.                                                                                                                                                                                                                                            | Could be customer specific by linking the discount to customers using affiliations.                                      | Could be customer specific by adding table/group/all customer relationships to the call center coupon.   Could be configured to require a customer, any customer without specifying a list of customers |
|  Can be used POS for retail stores and in sales order for call center channels.   Cannot be used in eCommerce channels at this time.                                                                                                                                                                                                                                                                                                       |  Could be used in POS for retail stores and during checkout for eCommerce.    Could not be used in call center channels. |  Could be used in all call center channels with no ability to restrict to specific call center channels.   Could not be used in POS for retail stores or in eCommerce channels.                         |
| Can be channel specific by linking the discount to channels using price groups.                                                                                                                                                                                                                                                                                                                                                            | Could be channel specific by linking the discount to channels using price groups                                         | Not available in retail store channels   or in eCommerce.                                                                                                                                               |
|  Can be restricted to a limited number of uses. The restriction can be 1 or more uses. The restriction can be set to one of these scopes; *per customer*, *per channel*, or *per company*. This restriction is for the number of separate transactions the coupon can be applied to. It is not a restriction on the number of products to be discounted in one transaction. That restriction has been added directly on discounts. | Could not restrict the number of times a discount code could be used.                                                    | Could be configured to be a single use per customer.                                                                                                                                                    |
| Is always product specific by the category/product/variant properties of the discount lines.                                                                                                                                                                                                                                                                                                                                               | Was always product specific by the category/product/variant properties of the discount lines.                            | Could be product specific by adding include table/group/all product relationships to the coupon.                                                                                                        |
| Can be configured to apply to all products by using the root category node of the retail category hierarchy.  Use 'include' and 'exclude' lines on discounts to define the products that the coupon applies to. Exclude lines were added to retail discounts for the coupon feature.                                                                                                                                                       |  Could be configured for all products by using the root category node of the retail category hierarchy.                  |  Could be for all products except a list of excluded products defined by   table/group/all product relationships to the coupon. Note: Could not mix include and exclude products on one coupon.         |
| Can be for catalog specific by linking the discount to catalogs using price groups.                                                                                                                                                                                                                                                                                                                                                        | Could be for catalog specific by linking the discount to catalogs using price groups.                                    | Could be for specific catalogs   by adding include or exclude catalog relationships                                                                                                                     |
| Can be exclusive, best price, or compounded by setting the discount concurrency mode.                                                                                                                                                                                                                                                                                                                                                      | Could be exclusive, best price, or compounded by setting the discount concurrency mode.                                | Could be compound or exclusive   by setting the exclusive on the call center coupon.                                                                                                                    |
| Discounts have an explicit currency that acts as a filter for applying the discount to transactions. It can be any of the currencies available.                                                                                                                                                                                                                                                                                            | Have an explicit currency that acts as a filter for applying to transactions. It can be any of the currencies available. | Were implicitly in the company currency with no option to change them.                                                                                                                                  |


## Managing coupons

You need to create the discount and the coupon independently and then link them by choosing the discount in the coupon form.
Once you link a coupon to a discount, a number of fields on the discount become read only because they are managed by the coupon's settings. Fields such as status and standard date ranges. 

Coupons are now essentially additional validation on top of retail discounts. The coupon provides the coupon codes and bar codes with date ranges, the usage limits, and customer required property. The discount provides the set of products the coupon is valid for. The discount's price groups provide the set of customers, channels, or catalogs the coupon is valid for.

## Required set up
Before you can use retail coupons you need to set up a coupon bar code and two number sequences. These are the steps for set up. Each step starts with the form name for the step.
- **Mask characters**: Create a new mask character for coupon code. Any unused character is fine.
- **Bar code mask setup**: Create a new bar code mask with **Type = Coupon**.
- **Bar code setup**: Create a new bar code that uses the bar code mask you just created.
- **Number sequences**: Create 2 new number sequences. One for Coupon code ID and one for Coupon number. Coupon number is the unique identifier for a coupon. Coupon code ID is the unique identifier for each coupon code for a coupon. Each coupon can have multiple codes / bar codes that trigger the coupon.
    - For both number sequences the **scope** must be company
    - Most likely you will want both to automatically generate sequence numbers.
- **Retail shared parameters**: In the **Bar codes** tab, select the bar code you created earlier.
- **Retail parameters**: In the **Number sequences** tab, select the corresponding number sequences you created earlier for **Coupon number** and **Coupon code ID**
- You should now be able to open the **Coupons** form and create new coupons.
 
### Partial updates and upgrades

Dynamics 365 servicing does not enforce applying updates for all components together. In addition, the retail solution is a distributed solution which also means updates may not be applied completely across the solution. The coupon feature because it is a merge of two existing features and involves discount calculation it is important to understand the impact of a partial update. 
- **Headquarters only partial update**: There are forms and binary updates that are applied in HQ. The retail price engine is updated with the binary update. It is used to calculate price in sales order and price simulator. The coupon and discount forms are updated with the HQ forms update. If only one of the two update parts are applied, you will get forms that do not match the price calculation data. This will cause either unexpected discount calculation or errors during discount calculation. 
- **HQ updated, Retail server and POS not updated(N-1)**: Retail server handles price calculation with the price engine. We always support updating HQ before updating retail stores. This is because not all stores can be updated at the same time. In this scenario, new functionality related to coupons won't be available in non-updated retail stores. For example, 'exclude' lines have been introduced with coupons. However, if you use exclude lines on a discount they will not be applied in a retail store running a previous version.
- **HQ not updated, Retail server and POS updated(N+1)**: The updated price engine in retail server knows how to handle legacy discount codes during price calculation so in this you should see no functional impact of the update.
