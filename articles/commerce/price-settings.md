---
# required metadata

title: Pricing settings
description: This article describes the various settings available in Microsoft Dynamics 365 Commerce headquarters for pricing and discount management.
author: boycez
ms.date: 08/31/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: boycez
ms.search.validFrom: 2022-08-11

---

# Pricing settings

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article describes the various settings available in Microsoft Dynamics 365 Commerce headquarters for pricing and discount management. These settings allow organizations to define desired pricing behavior in their Commerce solution to meet specific business needs.

## Company level pricing settings

The majority of pricing settings are at the company level and can be found in Commerce headquarters at **Commerce parameters \> Prices and discounts**.

### Best price and compound concurrency control model

The **Best price and compound concurrency control model** setting determines how the pricing engine should process multiple discounts in **best price** or **compound** concurrency mode. 

When this parameter is set to the **Best price and compound within priority, never compound across priorities** option, all **compound** discounts within the same pricing priority are compounded. The compounded result then competes with any **best price** discounts in the same pricing priority, the best price is applied, and all discounts at lower pricing priorities are ignored. 

When this parameter is set to the **Best price only within priority, always compound across priorities** option, all **compound** discounts are treated as **best price** discount. Within a pricing priority, only a single discount wins, and if that single discount is a **best price** or **compound** discount, it then compounds with all additional **best price** or **compound** discounts at lower pricing priorities.

### Discount compound behavior

The **Discount compound behavior** setting determines how the pricing engine should calculate multiple compounded discounts. When this parameter is set to the **Compound** option, one discount is applied on top of another accumulatively. When this parameter is set to the **Compound on the original price** option, all discounts are treated independently from one another and all discounts are applied to the same original price. For example, to compound 10% off and 20% off discounts on a product with an original price of $100, the former option would result in a final price of $72 ($100\*90%\*80%), and the latter option would result in a final price of $70 ($100-$10-$20).

### Enable competition between exclusive threshold and other periodic discounts

When the **Enable competition between exclusive threshold and other periodic discounts** setting is set to **Yes**, the pricing engine competes exclusive threshold discounts with exclusive non-threshold discounts while pricing priority still applies. The behavior of **best price** and **compound** threshold discounts remains as is, that is, they don't compete with the non-threshold discounts.

### Manual line discount and system discount

The **Manual line discount and system discount** setting determines how the pricing engine should apply the manual line discount and system discount to the same line. The manual line discount can compound on top of the system discount, or replace the system discount. When the manual line discount and system discount are compounded, the calculation logic respects the **Discount compound behavior** setting. A manual total discount that applies to the entire order doesn't respect this setting.

### Keep items on the same sales line for discount price rounding

For a quantity discount, if the discount amount can't be evenly divided by the qualifying quantity (for example, $10 off for 3 units purchased), the **Keep items on the same sales line for discount price rounding** setting determines how the pricing engine applies and distributes the discount amount. When the parameter is set to **Yes**, the discount amount is applied as a whole and doesn't split. Otherwise, the discount amount is divided across the qualifying quantity and also rounded. For example, $10 off for 3 units is divided into $3.33, $3.33, and $3.34 off for each unit respectively.

### Apply discounts to key in price products

The **Apply discounts to key in price products** setting determines whether discounts can be applied together with "key in prices" entered in POS. Whether and how a product supports the key in price is determined by the **Key in price** setting in product configuration.

### Apply discounts to price overrides

This setting determines whether discounts can be applied together with price overrides.

### Distribute discounts for least expensive discounts

For mix and match discounts using the "least expensive" calculation type, the **Distribute discounts for least expensive discounts** setting determines whether the pricing engine should distribute the discount across lines. When this parameter is set to **No**, the discount is only applied on the least expensive lines. For example, a "buy 2 get 1 free"  mix and match discount would result in the least expensive item being free and the other two items remaining at full price. If the customer returns both of the full-priced items, they would get the third item for free, which might cause a loss for the retailer. When the parameter is set to **Yes**, the pricing engine distributes the discount across all applicable lines, which can reduce the loss on returns.

### Manually calculate multi-line prices and discounts

The **Manually calculate multi-line prices and discounts** setting controls whether the pricing engine should use delayed price and discount calculation for the POS application and call center channel. When this parameter is set to **Yes**, the pricing engine doesn't immediately calculate multiline discounts (such as quantity discounts, threshold discounts, and mix and match discounts) whenever a sales order is being created or edited in the POS application or call center channel.

> [!NOTE]
> In Commerce version 10.0.30 and earlier, th **Manually calculate multi-line prices and discounts** setting only controls the call center channel. There's another setting named **Manually calculate multiple item discounts** in the functionality profile that controls POS price calcualtion behavior. The two settings are consolidated into one company-level setting in Commerce version 10.0.31.
### Retention period in days

The number specified in the **Retention period in days** setting indicates how many days after the expiration date (if set) or disabled date (if an expiration date isn't set) that a discount should be systematically deleted. Zero (0) implies no automatic deletion.

> [!NOTE]
> In Commerce version 10.0.30 and earlier, this setting is called **Number of days after which the expired disocunts should be deleted**.
### Coupon bar code

The **Coupon bar code** parameter determines which specific barcode should be used for generating coupon barcodes. Users can select one of the predefined barcodes as configured on the **Bar code setup** form. For more information about barcodes and barcode masks, see [Set up bar codes](set-up-bar-codes.md) and [Set up bar code masks](set-up-bar-code-masks.md).

### Coupon code must be manually applied to return transactions

The **Coupon code must be manually applied to return transactions** setting is only applicable to return transactions that don't have a sales receipt provided. Set this parameter to **No** if the coupon codes should automatically be applied to the transaction. Set this parameter to **Yes** if the coupon codes must be manually added to the transaction.

### Use sales agreements set up for the organization

For business-to-business (B2B) orders, when the **Use sales agreements set up for the organization** parameter is set to **Yes**, the pricing engine uses the sales agreements defined for the organization in the user's customer hierarchy to determine the contract-based price. When this parameter is set to **No**, or the customer hierarchy isn't defined, the pricing engine looks for sales agreements defined for the user to determine the contract-based price. For more information about customer hierarchy for B2B e-commerce, see [Manage B2B business partners using customer hierarchies](b2b/partners-customer-hierarchies.md).

## Channel level pricing settings

The following settings allow organizations to control the pricing behavior in specific selling channels.

### Enable order price control

Located in the **General** FastTab of the **Call center configuration** form, the **Enable order price control** setting determines whether the pricing engine should enforce restriction on the price override operation in the call center channel. This setting works in conjunction with the **Allow price adjust** product setting. 

When the order price control is turned off, any call center user can make price changes on sales lines in the call center channel, regardless of whether corresponding products allow price adjustment. 

When the order price control is turned on, only products whose **Allow price adjust** parameter is set to **Yes** allow price overrides in call center sales orders, and a **reason code** must be provided in corresponding sales lines. A call center user can only change the sales price up to the **Cost markup percentage** value defined in **Retail and Commerce \> Channel setup \> Call center setup \> Override permissions**. Any price override beyond that percentage requires the user to submit a request, which is then processed through predefined Commerce workflow for review and approval. For more information about Commerce workflows, see [Workflow system overview](/dynamics365/fin-ops-core/fin-ops/organization-administration/overview-workflow-system).

## Product level pricing settings

The following settings that enforce pricing rules at product level can be found on an organization's **Product configuration** form.

### Allow price adjust

When the **Allow price adjust** parameter is set to **Yes**, a price override can be applied to the product in call center channel sales orders.

### Key in price

The **Key in price** setting determines whether "key in price" is mandatory when adding a product to a sales transaction in POS. It also defines corresponding price value restrictions.

### Zero price valid

The **Zero price valid** setting determines whether predefined, system calculated, or manual adjusted sales prices for a product can be zero (0). Set this parameter to **Yes** if a price of zero is allowed. This setting can also be specified at the category level from the Commerce product hierarchy.

### Prevent all discounts

Setting the **Prevent all discounts** parameter to **Yes** prevents all types of discounts (including manual discounts) from being applied to a product. This setting can also be specified at the category level from the Commerce product hierarchy.

> [!NOTE]
> The **Prevent all discounts** parameter doesn't restrict the price override operation because that operation sets the price and isn't treated as a discount.
### Prevent manual discounts

Setting the **Prevent manual discounts** parameter to **Yes** prevents manual line or transaction discounts from being applied to a product. All other discounts can still be applied. This setting can also be specified at the category level from the Commerce product hierarchy.

> [!NOTE]
> This setting does not restrict the price override operation because that operation sets the price and isn't treated as a discount.
### Prevent retail discounts

When the **Prevent retail discounts** parameter is set to **Yes**, **simple discount**, **quantity discount**, **threshold discount**, **mix and match discount** and **shipping discount** discounts can't be applied to a product. All other discounts (including manual discounts) can still be applied.

### Prevent tender based discounts

When the **Prevent tender based discounts** parameter is set to **Yes**, the **tender-based discount** can't be applied to a product. All other discounts (including manual discounts) can still be applied.

Retailers often choose to exclude some products, such as new items or in-demand items, from item-based discounts (such as simple discount and quantity discount). However, they might still want to apply tender-based discounts if a customer pays by using the preferred tender. To achieve this, retailers can set the **Prevent all discounts** and **Prevent tender based discounts** options to **No**, and the **Prevent retail discounts** and **Prevent manual discounts** options to **Yes**.

## Deprecated or removed settings

The following pricing settings have been removed, or are planned for removal from Dynamics 365 Commerce.

| Setting                                           | Reason for deprecation or removal                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Deprecation or removal status                                      |
|---------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| Overlapping discounts handling                    | We had this setting in Commerce parameters to control how the pricing engine should search and determine the best discount combination to apply. The “Best discount” option brute forces through all possible discount combinations during pricing calculation. The “Best performance” option is an optimized option that utilizes heuristics algorithm and marginal value ranking method to prioritize, evaluate and determine the best combination in a timely manner. The “Balanced calculation” option in the code base works exactly the same as “Best performance” and so is essentially a duplicated option. The pricing engine has been updated to only use “Best performance” as the standard option to improve performance, thus this setting is no longer applicable. | Deprecated in 10.0.21 release and will be removed in October 2022. |
| Allow price adjustments to increase product price | We had this setting to control whether the price adjustment function allows increasing product price. When this parameter is turned off, using the price adjustment function organizations can only set a product's unit price lower than its base price and trade agreement sales price. We deprecate this setting because the price adjustment function has been updated to support two-way adjustments (increase or decrease) out-of-the-box.                                                                                                                                                                                                                                                                                                                             | Deprecated in the 10.0.30 release and will be removed in October 2023. |
| Enable price report for retail store              | We had this setting to control whether the "Price report" function is available for use on the store configuration form. We deprecate this setting because the store configuration form has been updated to always provide “Price report” as a standard function.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Deprecated in the 10.0.31 release and will be removed in October 2023. |
| Use today's date to calculate prices              | SCM pricing engine supports pricing calculation based on requested ship date or requested receipt date along with today's date. The Commerce pricing engine only supports pricing calculation based on today's date. For customers who use both SCM and Commerce capabilities, we provided this setting and recommended customers to always set it to **Yes** so that the two pricing engines can work together. We deprecate this setting because it fundamentally doesn't change the calculation behavior, and thus is redundant.                                                                                                                                                                                                                                                           | Deprecated in the 10.0.31 release and will be removed in October 2023. |
| Maximum price                                     | We had this setting in the functionality profile to control whether only products with a sales price below the specified maximum price can be sold via POS in specific stores. We deprecate this setting due to low feature usage.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Deprecated in the 10.0.31 release and will be removed in October 2023. |
| Apply discounts to unit price                     | We introduced this setting with the intent to control whether prices and discounts should be rounded at the unit price level or the sales line level during pricing calculation. We deprecate this setting because it isn't being consumed anywhere in the current code base.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Deprecated in the 10.0.31 release and will be removed in October 2023. |
| Manually calculate multiple item discounts        | We had this setting to control whether the pricing engine should use delayed price calculation for the retail store channel. When this parameter is set to **Yes**, the pricing engine doesn't immediately calculate multiline discounts (such as quantity discounts, threshold discounts, and mix and match discounts) whenever a sales order is being created or edited in the POS application. We decided to consolidate this setting with a similar setting in Commerce parameters to make it an omnichannel control.                                                                                                                                                                                                                                                          | Deprecated in the 10.0.31 release and will be removed in October 2023. |

For a full list of removed or deprecated features in Dynamics 365 Commerce, see [Removed or deprecated features in Dynamics 365 Commerce](get-started/removed-deprecated-features-commerce.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
