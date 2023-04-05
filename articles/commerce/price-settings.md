---
# required metadata

title: Pricing settings
description: This article describes the various settings for pricing and discount management in Microsoft Dynamics 365 Commerce headquarters.
author: boycez
ms.date: 01/30/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: boycez
ms.search.validFrom: 2022-08-11

---

# Pricing settings

[!include [banner](../includes/banner.md)]

This article describes the various settings for pricing and discount management in Microsoft Dynamics 365 Commerce headquarters. These settings enable organizations to define the pricing behavior in their Commerce solution to meet specific business needs.

## Company-level pricing settings

Most pricing settings are at the company level and can be found at **Commerce parameters \> Prices and discounts** in Commerce headquarters.

### Best price and compound concurrency control model

The **Best price and compound concurrency control model** setting determines how the pricing engine processes multiple discounts in **best price** or **compounded** concurrency mode. 

If the parameter is set to **Best price and compound within priority, never compound across priorities**, all **compounded** discounts that have the same pricing priority are compounded. The compounded result then competes with any **best price** discounts that have the same pricing priority, the best price is applied, and all discounts that have a lower pricing priority are ignored.

If the parameter is set to **Best price only within priority, always compound across priorities**, all **compounded** discounts are treated as **best price** discounts. Within a pricing priority, only a single discount wins. If that single discount is a **best price** or **compounded** discount, it's compounded with all additional **best price** or **compounded** discounts that have a lower pricing priority.

### Discount compound behavior

The **Discount compound behavior** setting determines how the pricing engine calculates multiple compound discounts.

If the parameter is set to **Compound**, one discount is applied on top of another in an accumulative manner. If it's set to **Compound on the original price**, all discounts are treated independently of each other and applied to the same original price.

For example, you want to compound 10-percent-off and 20-percent-off discounts for a product that has an original price of $100. If you set the **Discount compound behavior** parameter to **Compound**, the final price will be $72 ($100 &times; 90% &times; 80%). If you set it to **Compound on the original price**, the final price will be $70 ($100 – $10 – $20).

### Enable competition between exclusive threshold and other periodic discounts

If the **Enable competition between exclusive threshold and other periodic discounts** parameter is set to **Yes**, the pricing engine makes exclusive threshold discounts compete with exclusive non-threshold discounts. If an exclusive threshold discount wins and is applid to sales lines, it will be ignored during the threshold discount calculation stage. But if it fails to win, it will still be assessed during the threshold discount calculation stage. Pricing priority still applies.

The behavior of **best price** and **compound** threshold discounts remains as is. In other words, they don't compete with the non-threshold discounts.

### Manual line discount and system discount

The **Manual line discount and system discount** setting determines how the pricing engine applies a manual line discount and a system discount to the same line. The manual line discount can be compounded on top of the system discount, or it can replace the system discount. When the manual line discount and system discount are compounded, the calculation logic respects the **Discount compound behavior** setting. A manual total discount that applies to the whole order doesn't respect that setting.

### Keep items on the same sales line for discount price rounding

Sometimes, the amount of a quantity discount amount can't be evenly divided by the qualifying quantity (for example, if the discount amount is $10 off for three purchased units). In these cases, the **Keep items on the same sales line for discount price rounding** setting determines how the pricing engine applies and distributes the discount amount. If the parameter is set to **Yes**, the discount amount is applied as a whole and isn't split. If it's set to **No**, the discount amount is divided across the qualifying quantity and rounded. For example, a discount amount of $10 off for three units is divided into $3.33 off for one unit, $3.33 off for the second unit, and $3.34 off for the third unit.

### Apply discounts to key in price products

The **Apply discounts to key in price products** setting determines whether discounts can be applied together with "key-in prices" that are entered in the point of sale (POS). The **Key in price** setting in the product configuration determines whether and how a product supports the key-in price.

### Apply discounts to price overrides

The **Apply discounts to price overrides** setting determines whether discounts can be applied together with price overrides.

### Distribute discounts for least expensive discounts

For mix and match discounts that use the "least expensive" calculation type, the **Distribute discounts for least expensive discounts** setting determines whether the pricing engine distributes the discount across lines.

If the parameter is set to **No**, the discount is applied only to the least expensive lines. For example, for a "buy 2 get 1 free" mix and match discount, the least expensive item will be free, and the other two items will remain at full price. In this case, a customer who returns both the full-priced items will still get the third item for free. This scenario might cause a loss for the retailer.

If the parameter is set to **Yes**, the pricing engine distributes the discount across all applicable lines. This setting can help reduce the loss on returns.

### Manually calculate multi-line prices and discounts

The **Manually calculate multi-line prices and discounts** setting controls whether the pricing engine uses delayed price and discount calculation for the POS application and the call center channel. If the parameter is set to **Yes**, the pricing engine doesn't immediately calculate multiline discounts (such as quantity discounts, threshold discounts, and mix and match discounts) whenever a sales order is created or edited in the POS application or the call center channel.

> [!NOTE]
> In Commerce version 10.0.30 and earlier, the **Manually calculate multi-line prices and discounts** setting controls only the call center channel. A separate **Manually calculate multiple item discounts** setting in the functionality profile controls the price calculation behavior in the POS application. In Commerce version 10.0.31, the two settings are consolidated into one company-level setting.

### Retention period in days

The **Retention period in days** setting indicates how many days after the expiration date (if an expiration date is set) or the disabled date (if an expiration date isn't set) a discount should be systematically deleted. If the parameter is set to **0** (zero), no automatic deletion occurs.

> [!NOTE]
> In Commerce version 10.0.30 and earlier, this setting is named **Number of days after which the expired discounts should be deleted**.

### Coupon bar code

The **Coupon bar code** setting determines which specific bar code is used to generate coupon bar codes. Users can select one of the predefined bar codes that are configured on the **Bar code setup** page. For more information about bar codes and bar code masks, see [Set up bar codes](set-up-bar-codes.md) and [Set up bar code masks](set-up-bar-code-masks.md).

### Coupon code must be manually applied to return transactions

The **Coupon code must be manually applied to return transactions** setting is applicable only to return transactions that no sales receipt is provided for. Set the parameter to **No** if coupon codes should automatically be applied to the transaction. Set it to **Yes** if coupon codes must be manually added to the transaction.

### Use sales agreements set up for the organization

For business-to-business (B2B) orders, if the **Use sales agreements set up for the organization** parameter is set to **Yes**, the pricing engine uses the sales agreements that are defined for the organization in the user's customer hierarchy to determine the contract-based price. If the parameter is set to **No**, or if the customer hierarchy isn't defined, the pricing engine looks for sales agreements that are defined for the user to determine the contract-based price. For more information about customer hierarchies for B2B e-commerce, see [Manage B2B business partners using customer hierarchies](b2b/partners-customer-hierarchies.md).

## Channel-level pricing settings

The following settings enable organizations to control the pricing behavior in specific selling channels.

### Enable order price control

The **Enable order price control** parameter is located on the **General** FastTab of the **Call center configuration** page. The setting determines whether the pricing engine enforces a restriction on the price override operation in the call center channel. It works in conjunction with the **Allow price adjust** product-level setting.

If order price control is turned off, no price changes can be made to sales lines in the call center channel.

If order price control is turned on, only products where the **Allow price adjust** parameter is set to **Yes** allow for price overrides in call center channel sales orders, and a reason code must be provided on corresponding sales lines. A call center user can change the sales price only up to the **Cost markup percentage** value that is defined at **Retail and Commerce \> Channel setup \> Call center setup \> Override permissions**. If a price override exceeds that percentage, the user must submit a request, which is then processed through a predefined Commerce workflow for review and approval. For more information about Commerce workflows, see [Workflow system overview](/dynamics365/fin-ops-core/fin-ops/organization-administration/overview-workflow-system).

## Product-level pricing settings

The following settings enforce pricing rules at the product level and can be found on an organization's **Product configuration** page.

### Allow price adjust

If the **Allow price adjust** parameter is set to **Yes**, a price override can be applied to the product in call center channel sales orders.

### Key in price

The **Key in price** setting determines whether a key-in price is mandatory when a product is added to a sales transaction in POS. It also defines corresponding price value restrictions.

### Zero price valid

The **Zero price valid** setting determines whether predefined, system-calculated, or manually adjusted sales prices for a product can be 0 (zero). Set the parameter to **Yes** if a price of zero is allowed. This setting can also be specified at the category level from the Commerce product hierarchy.

### Prevent all discounts

By setting the **Prevent all discounts** parameter to **Yes**, you prevent all types of discounts (including manual discounts) from being applied to a product. This setting can also be specified at the category level from the Commerce product hierarchy.

> [!NOTE]
> This setting doesn't restrict the price override operation, because that operation sets the price and isn't treated as a discount.

### Prevent manual discounts

By setting the **Prevent manual discounts** parameter to **Yes**, you prevent manual line or transaction discounts from being applied to a product. All other discounts can still be applied. This setting can also be specified at the category level from the Commerce product hierarchy.

> [!NOTE]
> This setting doesn't restrict the price override operation, because that operation sets the price and isn't treated as a discount.

### Prevent retail discounts

If the **Prevent retail discounts** parameter is set to **Yes**, **simple**, **quantity**, **threshold**, **mix and match** and **shipping** discounts can't be applied to a product. All other discounts (including manual discounts) can still be applied.

### Prevent tender based discounts

If the **Prevent tender based discounts** parameter is set to **Yes**, a **tender-based** discount can't be applied to a product. All other discounts (including manual discounts) can still be applied.

Retailers often choose to exclude some products, such as new items or in-demand items, from item-based discounts (such as simple discounts and quantity discounts). However, they might still want to apply tender-based discounts if a customer pays by using the preferred tender. To achieve this result, retailers can set the **Prevent all discounts** and **Prevent tender based discounts** parameters to **No**, and the **Prevent retail discounts** and **Prevent manual discounts** parameters to **Yes**.

## Deprecated or removed settings

The following pricing settings have been removed or are planned for removal from Dynamics 365 Commerce.

| Setting | Reason for deprecation or removal | Deprecation or removal status |
|---------|-----------------------------------|-------------------------------|
| Overlapping discounts handling | We provided this setting in Commerce parameters to control how the pricing engine searches for and determines the best discount combination to apply. The **Best discount** option forces through all possible discount combinations during pricing calculation. The **Best performance** option is an optimized option that uses a heuristic algorithm and marginal value ranking method to prioritize, evaluate, and determine the best combination in a timely manner. The **Balanced calculation** option in the code base works the same as **Best performance**. Therefore, it's essentially a duplicated option. To help improve performance, the pricing engine has been updated so that it uses only **Best performance** as the standard option. Therefore, this setting is no longer applicable. | Deprecated in the 10.0.21 release and will be removed in October 2022. |
| Allow price adjustments to increase product price | We provided this setting to control whether the price adjustment function can increase product prices. If the parameter is turned off, organizations can use the price adjustment function only to set a product's unit price so that it's lower than the base price and trade agreement sales price. We deprecated this setting because the price adjustment function has been updated so that it supports two-way adjustments (increase or decrease) out of the box. | Deprecated in the 10.0.30 release and will be removed in October 2023. |
| Enable price report for retail store | We provided this setting to control whether the **Price report** function is available for use on the store configuration page. We deprecated this setting because the store configuration page has been updated so that it always provides **Price report** as a standard function. | Deprecated in the 10.0.31 release and will be removed in October 2023. |
| Use today's date to calculate prices | The Dynamics 365 Supply Chain Management pricing engine supports pricing calculation that is based on the requested ship date or requested receipt date together with today's date. The Commerce pricing engine supports only pricing calculation that is based on today's date. For customers who use both Supply Chain Management and Commerce capabilities, we provided this setting and recommended that customers always set it to **Yes**, so that the two pricing engines can work together. We deprecated this setting because it doesn't fundamentally change the calculation behavior and is therefore redundant. | Deprecated in the 10.0.31 release and will be removed in October 2023. |
| Maximum price | We provided this setting in the functionality profile to control whether only products that have a sales price that is below the specified maximum price can be sold via POS in specific stores. We deprecated this setting because of low feature usage. | Deprecated in the 10.0.31 release and will be removed in October 2023. |
| Apply discounts to unit price | This setting was intended to control whether prices and discounts are rounded at the unit price level or the sales line level during pricing calculation. We deprecated it because it isn't being consumed anywhere in the current code base. | Deprecated in the 10.0.31 release and will be removed in October 2023. |
| Manually calculate multiple item discounts | We provided this setting to control whether the pricing engine uses delayed price calculation for the retail store channel. If the parameter is set to **Yes**, the pricing engine doesn't immediately calculate multiline discounts (such as quantity discounts, threshold discounts, and mix and match discounts) whenever a sales order is created or edited in the POS application. We decided to consolidate this setting with a similar setting in Commerce parameters to make an omnichannel control. | Deprecated in the 10.0.31 release and will be removed in October 2023. |

For a full list of removed or deprecated features in Dynamics 365 Commerce, see [Removed or deprecated features in Dynamics 365 Commerce](get-started/removed-deprecated-features-commerce.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
