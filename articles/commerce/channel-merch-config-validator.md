---
# required metadata

title: Channel merchandising configuration validator
description: This article describes how to use the channel merchandising configuration validator in Microsoft Dynamics 365 Commerce headquarters to find missing and invalid configurations for products, categories, and attributes by channel.
author: ashishmsft
ms.date: 06/21/2023
ms.topic: article
ms.search.form: RetailCommerceValidatorWorkSpace
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.assetid: 6fc835ef-d62e-4f23-9d49-50299be642ca
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-02-28

---

# Channel merchandising configuration validator

[!include[banner](../includes/banner.md)]

This article describes how to use the channel merchandising configuration validator in Microsoft Dynamics 365 Commerce headquarters to find missing and invalid configurations for products, categories, and attributes by channel.

Incorrect and missing configurations that are related to products, categories, catalogs, and attributes can cause issues when products are sold in e-commerce and point of sale (POS) Commerce channels. The Dynamics 365 Commerce channel merchandising configuration validator is designed to identify and address these configurations. You can use the channel merchandising configuration validator to efficiently fix issues and streamline your operations in Commerce headquarters.

## Capabilities

The channel merchandising configuration validator provides a wide range of capabilities that can help optimize your operations in headquarters.

- **Proactive validation** – The configuration validator proactively identifies and reports missing or invalid configurations that are related to products, categories, variants, attributes, and catalogs.
- **Validation across multiple locales** – The configuration validator runs comprehensive validations across all locales to ensure that all merchandising configurations are verified for a selected channel.
- **Deep linking** – After invalid configurations are identified, the configuration validator streamlines the correction process by creating deep links to specific pages in headquarters. Therefore, you can quickly go to the sources of the issues and efficiently fix them.
- **Extensive rule set** – Thanks to its comprehensive set of over 40 distinct validation rules, the configuration validator offers a robust and reliable solution for identifying and fixing configuration issues.

## Run validation for a new channel

To run validation for a new channel in headquarters, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Channel merchandising configuration validator**.
1. Select **New**.
1. In the **Channel ID** field, enter or select a value (for example, **AW Business online store**).
1. Select **Validate**. Wait until the validation progress reaches 100 percent and the validation phase is shown as **Completed**.
1. After validation is completed, select the **Channel name** value to view a detailed summary of the validation results. There are two viewing options:

    - **By entity** – This option shows all validated entity records, together with messages, errors, and warnings.
    - **By rules** – This option shows each rule that was validated, together with the corresponding numbers of messages, errors, and warnings.

1. Select **Show details** to load an additional grid that shows the details of messages, errors, and warnings. You can filter this grid by issue type. From the **Show details** view, you can go directly to the entity record to fix the configuration that has an issue.
1. After you fix the configurations across all entities, you can return to the **Validation summary** view and select **Validate failed** to rerun validation for the rules that previously failed.

## Run validation for all channels

To run validation for all channels in headquarters, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Channel merchandising configuration validator**.
1. Select **Create all**. The channel grid shows the list of channels.
1. In the channel grid, select the channels that you want to run the validation process for. To run validation for all channels, on the grid header, select the checkbox that selects all channels.
1. Select **Validate**.

## Validation rules

The following table describes the validation rules that are run for the channel merchandising configuration validator.

| Rule ID | Entity | Rule description | Rule type | Effect of incorrect configuration |
|---|---|---|---|---|
| AttribGroup-Ru-001 | Attribute group | This rule checks whether the attribute group display order is missing. | Information | If attributes on a product are based on multiple attribute groups, they're ordered according to the default ordering of attributes. |
| AttribGroup-Ru-002 | Attribute group | This rule checks whether the attribute group translations for description and friendly name values are missing. | Information | Missing translations for attribute group description and friendly name values affect headquarters users who have their preferences set to use a language other than the default system language. |
| Attrib-Ru-001 | Attribute | This rule checks whether the attribute display order inside each attribute group is missing. | Information | If attributes on a product are based on multiple attribute groups, and the channel category hierarchy is missing, they're ordered according to the default ordering of attributes. |
| Attrib-Ru-002 | Attribute | This rule checks whether the attribute translations for description and friendly name values are missing. | Error | If a channel is configured to render data in a language other than the default system language (not to be confused with the default channel language), standard attributes (and any refiners that are associated with them) aren't rendered correctly. Missing translations for attribute description and friendly name values affect headquarters users who have their preferences set to use a language other than the default system language. |
| Attrib-Ru-003 | Attribute | This rule checks whether the attribute enumeration translations for description and friendly name values are missing or blank. | Error | If a channel is configured to render data in the language other than the default system language (not to be confused with the default channel language), list value–based attributes (and any refiners that are associated with them) aren't rendered correctly. Missing translations for attribute enumeration description and friendly name values affect headquarters users who have their preferences set to use a language other than the default system language. |
| Attrib-Ru-004 | Attribute | This rule checks whether the attribute value translations for specified channel attribute overrides are missing. | Error | If a channel is configured to render data in a language other than the default system language (not to be confused with the default channel language), attribute values (and any refiner values that are associated with them) aren't rendered correctly. Missing translations for attribute override values affect headquarters users who have their preferences set to use a language other than the default system language. |
| Cata-Ru-001 | Catalog | This rule checks whether the catalog target is business-to-business (B2B) and the customer type is business-to-consumer (B2C). | Error | There should not be a mismatch between the types of channels that are associated with the catalog. Both should be the same, because B2B catalogs are discoverable only in B2B online channels. |
| Cata-Ru-002 | Catalog | This rule checks whether the catalog target is B2C and the customer type is B2B. | Error | There should not be a mismatch between the types of channels that are associated with the catalog. Both should be the same, because B2B catalogs are discoverable only in B2B online channels. |
| Cata-Ru-003 | Catalog | This rule checks whether the catalog is expired. | Information | If expired catalogs are associated with the channel, they aren't discoverable in the channel. |
| Cata-Ru-004 | Catalog | This rule checks whether the catalog translation is missing. | Error | If the channel is configured to support languages other than the default system language, the catalog doesn't appear in the catalog picker. |
| Cata-Ru-005 | Catalog | This rule checks whether the catalog product isn't assorted. | Warning | If products in the catalog definition are no longer assorted to the channel, the catalog isn't discoverable in the channel when catalogs are browsed. |
| Cata-Ru-006 | Catalog | This rule checks whether the catalog product isn't released. | Warning | If products in the catalog definition aren't released to the legal entity that's associated with the channel, the catalog isn't discoverable in the channel when catalogs are browsed. |
| Cata-Ru-007 | Catalog | This rule checks whether the translation for an overridden catalog-specific product attribute value is missing. | Error | If a product attribute value is intended to be overridden at the catalog level, but the overridden value isn't translated for languages that are associated with the channel, the overridden catalog-specific attribute value isn't shown when the catalog is browsed. |
| Cate-Ru-001 | Channel navigation hierarchy | This rule checks whether the category is inactive. | Warning | If the category is inactive, the inactive categories from channel navigation hierarchy aren't shown in the channel when categories or catalogs are browsed. |
| Cate-Ru-002 | Channel navigation hierarchy | This rule checks whether the category display order isn't specified. | Warning | If the category display order isn't specified, the categories are sorted in a default manner (for example, alphabetically). |
| Cate-Ru-003 | Channel navigation hierarchy | This rule checks whether the category translation is missing. | Error | Categories that are missing translations don't appear in the navigation hierarchy module on e-commerce sites, or on the category tile in POS. |
| Channel-Ru-001 | Channel navigation hierarchy | This rule checks whether the channel category hierarchy is missing. | Error | If the channel category hierarchy is missing, no categories are shown on the e-commerce site or POS channels for product browsing. |
| Hierarchy-Ru-002 | Channel navigation hierarchy | This rule checks whether the channel category hierarchy isn't assigned to a navigation role. | Error | If the navigation role is removed from the category hierarchy after it's associated with a channel, no categories or products are discoverable in the channel. |
| KitComp-Ru-001 | Kits and kit components | This rule checks whether the kit component isn't released in the legal entity. | Error | If the components of the kit haven't been released to the legal entity that's associated with the channel, the kit isn't discoverable in the POS. |
| KitComp-Ru-002 | Kits and kit components | This rule checks whether the kit and kit components are part of the same assortment. | Warning | If the kit and kit components (including substitute components) aren't part of the same assortment, kit selling doesn't work correctly in POS. The kit and kit components must be part of the same assortment. |
| KitComp-Ru-003 | Kits and kit components | This rule checks whether the kit component is excluded from the assortment. | Warning | If the kit component is excluded from the assortment, and there's no substitution for the component, the kit isn't rendered correctly in POS, and the whole kit is excluded from the assortment. |
| KitCompSubs-Ru-001 | Kits and kit components | This rule checks whether the substitute for the kit component isn't released in the legal entity. | Error | If the kit component is excluded from the assortment, and there's no substitution for the component, the kit isn't rendered correctly in POS. |
| KitCompSubs-Ru-002 | Kits and kit components | This rule checks whether the kit and kit components (including substitutions) are part of the same assortment. | Warning | If the kit and kit components (including substitute components) aren't part of the same assortment, kit selling doesn't work correctly in POS. |
| Kit-Ru-001 | Kits and kit components | This rule checks whether the kit product isn't released in the legal entity. | Error | If a kit product isn't released to a legal entity that's associated with the channel, the kit isn't discoverable in Commerce channels. |
| Prod-Ru-001 | Product dimensions | This rule checks whether the translation for the master product color value is missing. | Error | If the translation for the master product color value is missing for the languages that are configured for the channel, color options appear blank, and users might not be able to select the correct color value for their variant selection. |
| Prod-Ru-002 | Product dimensions | This rule checks whether the translation for the master product style value is missing. | Error | If the translation for the master product style value is missing for the languages that are configured for the channel, style options appear blank, and users might not be able to select the correct style value for their variant selection. |
| Prod-Ru-003 | Product dimensions | This rule checks whether the translation for the master product size value is missing. | Error | If the translation for the master product size value is missing for the languages that are configured for the channel, size options appear blank, and users might not be able to select the correct size value for their variant selection. |
| Prod-Ru-004 | Product dimensions | This rule checks whether the translation for the master product configuration value is missing. | Error | If the translation for the master product configuration value is missing for the languages that are configured for the channel, configuration options appear blank, and users might not be able to select the correct configuration value for their variant selection.|
| Prod-Ru-005 | Product assortments | This rule checks whether the product isn't active in any assortments. | Error | If products are not active in any assortments that are associated with the channel, they don't show up in Commerce channels. |
| Prod-Ru-006 | Product assortments | This rule checks whether the product is excluded from any assortments. | Warning | If a product is excluded in at least one assortment that's associated with the channel, it isn't discoverable in Commerce channels. |
| Prod-Ru-007 | Product and product masters | This rule checks whether the translation for the product name is missing. | Error | If the translation for the product name is missing, and the channel is configured to support languages other than the default system language, the product isn't rendered correctly in product browsing results in Commerce channels. |
| Prod-Ru-008 | Product and product masters | This rule checks whether the product isn't categorized. | Error | If a product is part of an assortment and released to the legal entity that's associated with the channel, but it isn't associated with a category in the navigation hierarchy, it isn't discoverable in product browsing results. |
| Prod-Ru-009 | Product and product masters | This rule checks whether the inventory unit of measure is missing. | Warning | Products that are missing the inventory unit of measure can affect inventory-related operations. |
| Prod-Ru-010 | Product and product masters | This rule checks whether the sales unit of measure is missing. | Error | Products that are missing the sales unit of measure can affect product discovery and ordering capabilities. |
| Prod-Ru-011 | Product and product masters | This rule checks whether the inventory base price is missing. | Warning | Products that are missing the inventory base price can affect inventory-related operations. |
| Prod-Ru-012 | Product and product masters | This rule checks whether the sales base price is missing. | Error | Products that are missing the sales base price can affect product discovery and ordering capabilities. |
| Prod-Ru-013 | Product and product masters | This rule checks whether the product is stopped for sales. | Warning | Products that are marked as stopped for sales can't be ordered, but they're discoverable in product browsing results in Commerce channels. |
| Prod-Ru-014 | Product and product masters | This rule checks whether the product isn't released to a legal entity that's associated with the channel, but it's assorted. | Warning | Products that aren't released to a legal entity that's associated with the channel aren't discoverable in Commerce channels. |
| Prod-Ru-015 | Product and product masters | This rule checks whether the product is categorized to an inactive category. | Warning | Products that are categorized to an inactive category of the channel navigation hierarchy and associated with a channel aren't discoverable in Commerce channels. |
| Prod-Ru-016 | Product and product masters | This rule checks whether the translations for product master or distinct product attribute values are missing. | Error | If translations for product master or distinct product attribute values are missing, and a channel is configured to render data in a language other than default system language (not to be confused with the default channel language), standard attributes (and any refiners that are associated with them) aren't rendered correctly. Missing translations for product master or distinct product attribute values affect headquarters users who have their preferences set to use a language other than the default system language. |
| Prod-Ru-017 | Product and product masters | This rule checks whether the translation for the product description is missing. | Error | If the translation for the product description is missing, and a channel is configured to render data in a language other than the default system language (not to be confused with the default channel language), the product description isn't rendered correctly. Missing translations for product descriptions affect headquarters users who have their preferences set to use a language other than the default system language. |

[!INCLUDE[footer-include](../includes/footer-banner.md)]
