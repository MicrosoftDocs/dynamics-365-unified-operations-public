---
# required metadata

title: Channel merchandising configuration validator
description: Find missing and invalid configurations for products, categories, and attributes by channel. 
author: josaw1
ms.date: 03/03/2023
ms.topic: overview
ms.search.form: RetailCommerceValidatorWorkSpace 
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.assetid: 6fc835ef-d62e-4f23-9d49-50299be642ca
ms.search.region: Global
ms.author: ashishmsft
ms.search.validFrom: 2016-02-28

---

Channel merchandising configuration validator is designed to identify and address incorrect and missing configurations related to products, categories, catalogs and attributes that may result in complications when selling products in eCommerce and POS Commerce channels. By utilizing the configuration validator, you can efficiently resolve these issues and streamline your backoffice operations.

![Channel merchandising configuration validator in headquarters.](media/channel-merch-config-validator.png)


## Capabilities

This feature offers a wide range of capabilities to optimize your backoffice operations:

**Proactive validation:** The configuration validator proactively identifies and reports missing or invalid configurations related to products, categories, variants, attributes, and catalogs.

**Validation Across Multiple Locales**: It provides comprehensive validation checks across all locales, ensuring all merchandising configurations are thoroughly assessed for a selected channel.

**Deep Linking**: Upon identifying invalid configurations, the feature creates deep links to the specific form that allow users to quickly navigate to the source of the issue and resolve it efficiently, streamlining the correction process.

**Extensive Rule Set**: With a comprehensive set of validation rules, including over 40 distinct rules, the Channel merchandising configuration validator offers a robust and reliable solution to identify and resolve configuration issues.

## How to use it? 

**Create validation for a new channel**
- Go to Retail and Commerce > Retail and Commerce IT > **Channel merchandising configuration validator**.
- Click **New**.
- In the **Channel Id** field, enter or select a value (e.g., AW Business Online store)
- Click **Validate**
- Wait for the progress % to become **100**% and validation phase to show '**Completed**' 
- Upon completion of validation, click on the 'Channel name' to view detailed summary of the validation results. 
- Here you shall notice, there are two options '**By entity**' and '**By rules**' 
- When viewing '**By entity**' it shows you **all entity records validated** with number of messages, errors and warnings. To view details, click on 'Show details' 
- Upon clicking on **'Show details'** it would load an additional grid with details of messages, errors and warnings and you can filter by type of the issue. 
- Additionally, from 'show details view' you can **directly navigate to the entity record to fix** the necessary configuration. 
- Alternatively you can view '**By rules**' it shows you each rule that was validated with corresponding number of messages, errors and warnings. To view details, click on 'Show details' 
- Upon clicking on '**Show details**' it would load an additional grid with details of messages, errors and warnings and you can filter by type of the issue. 
- Additionally, from '**show details view**' you can directly navigate to the entity record to fix the necessary configuration. 
- Upon fixing the necessary configurations across all entities, you can navigate back to the 'Validation summary' view and click on 'Validate failed' and it shall re-run the validation for the previously failed rules. 

**Create validation for all channels**
- Go to Retail and Commerce > Retail and Commerce IT > Channel merchandising configuration validator.
- Click '**Create all**' 
- It will create a validation for each channel and you will notice the **channel grid** on this workspace getting populated with list of channels. 
- Next, in the grid of channels, select the channels for which you would like to initiate the validation process. 
- If you would like to run it for all channels, then from the grid header, select the checkbox which would select all channels. 
- And then click '**validate**' 

## Rules

| Rule id | Entity | Rule description | Rule type | Effect of incorrect configuration|
|--------|--------|--------|--------|--------|
| AttribGroup-Ru-001 | Attribute group  | Attribute group display order is missing | Information |  If attributes on a product are based of multiple attribute groups, then they will be ordered using default ordering of attributes |
| AttribGroup-Ru-002 | Attribute group  | AttributeGroup translation for Description and FriendlyName is missing | Information | This will have impact on HQ user, when they have user preferences set to use language different than default system language. |
| Attrib-Ru-001 | Attribute  | Attribute display order inside attribute group is missing | Information | If attributes on a product are based of multiple attribute groups, then they will be ordered using default ordering of attributes |
| Attrib-Ru-002 | Attribute  | Attribute translation for Description and FriendlyName is missing  | Error | If a channel is configured to render data in the language other than system default language (not to be confused with channel 'default' language) then standard attributes (including refiners associated with those attributes) won't be rendered correctly. Also, this will have impact on HQ user, when they have user preferences set to use language different than default system language. |
| Attrib-Ru-003 | Attribute  |Attribute enumeration translation for Description and/or Friendly Name is missing or empty | Error | If a channel is configured to render data in the language other than system default language (not to be confused with channel 'default' language) then list-values based attributes (including refiners associated with those attributes) won't be rendered correctly. Also, this will have impact on HQ user, when they have user preferences set to use language different than default system language. |
| Attrib-Ru-004 | Attribute  |Attribute value translation for specified channel attribute override is missing | Error |  If a channel is configured to render data in the language other than system default language (not to be confused with channel 'default' language) then attribute values (including refiner values associated with those attributes) won't be rendered correctly. Also, this will have impact on HQ user, when they have user preferences set to use language different than default system language. |
| Cata-Ru-001 | Catalog | Catalog target is B2B and customer type is B2C, both should be same  | Error | This is a mismatch between type of Channels associated with Catalog, B2B catalogs are only discoverable in B2B online channels. |
| Cata-Ru-002 | Catalog | Catalog target is B2C and customer type is B2B, both should be same  | Error | This is a mismatch between type of Channels associated with Catalog, B2B catalogs are only discoverable in B2B online channels. |
| Cata-Ru-003 | Catalog | Catalog is expired | Information | This suggests that there are catalogs associated with channel, that are expired and hence they wouldn't be discoverable in channels |
| Cata-Ru-004 | Catalog | Catalog translation is missing | Error | If channel is configured to support languages, other than system default language - in that case this catalog won't appear in the catalog picker |
| Cata-Ru-005 | Catalog | Catalog product is not assorted | Warning | There are products in the catalog definition, that are no longer assorted to the channel and hence won't be discoverable in the channel while browsing catalogs | 
| Cata-Ru-006 | Catalog | Catalog product is not released | Warning | There are products in the catalog definition, that are not released to the legal entity associated with the channel and hence won't be discoverable in the channel while browsing catalogs | 
| Cata-Ru-007 | Catalog | Catalog product overridden attribute value translation is missing | Error | If user intended to override product attribute value at a catalog level, but that overridden value is not translated for languages associated with the channel. Thus, these catalog-specific attribute values won't be shown during the catalog browsing. | 
| Cate-Ru-001 | Channel navigation hierarchy | Category is inactive | Warning | The inactive categories from Channel navigation hierarchy will not be shown in channel while browsing categories or catalogs|
| Cate-Ru-002 | Channel navigation hierarchy | Category display order is not specified | Warning | The categories will be sorted in a default manner (e.g., alphabetically)|
| Cate-Ru-003 | Channel navigation hierarchy | Category translation is missing | Error | Categories that are missing translation will show up as blank names in the navigation hierarchy module on the eCommerce sites and Category tile with missing names on POS |  
| Channel-Ru-001 | Channel navigation hierarchy | Channel category hierarchy is missing | Error |Due to missing category hierarchy association with channel, there will not be any categories shown on the eCommerce sites or POS channels for product browsing.|
| Hierarchy-Ru-001 | Channel navigation hierarchy | Category hierarchy translation is missing | Warning | This will have impact on HQ user, when they have user preferences set to use language different than default system language.|
| Hierarchy-Ru-002 | Channel navigation hierarchy | Channel Category hierarchy is not assigned to navigation role | Error |If navigation role is removed from the category hierarchy after being associated with channel, all categories and products will not be discoverable in the channel.|
| KitComp-Ru-001 | Kits and kit components | Kit component is not released in the legal entity | Error |Kit won't be discoverable in the POS, if the components of the kits have not been released to the legal entity associated with the channel.|
| KitComp-Ru-002 | Kits and kit components | Kit and kit components must be part of the same assortment. | Warning |If the kit and kit components (including substitute components) are not part of the same assortment, then Kit selling won't function properly on the POS |
| KitComp-Ru-003 | Kits and kit components | Kit component is excluded from the assortment. | Warning | If the kit component is excluded from the assortment, and if there's no substitution for the component, then kit won't be rendered correctly on POS. Otherwise, entire kit will be excluded from the assortment|
| KitCompSubs-Ru-001 | Kits and kit components | Substitute of the Kit component is not released in the legal entity | Error | If the kit component is excluded from the assortment, and if there's no substitution for the component, then kit won't be rendered correctly on POS|
| KitCompSubs-Ru-002 | Kits and kit components | Kit and kit components(including substitutions) must be part of the same assortment. | Warning |If the kit and kit components (including substitute components) are not part of the same assortment, then Kit selling won't function properly on the POS   |
| Kit-Ru-001 | Kits and kit components | Kit product is not released in the legal entity. | Error | Considering kit product is not released to a legal entity associated with channel, this kit will not be discoverable in Commerce channels. | 
| Prod-Ru-001 | Product dimensions | Master product Color translation is missing | Error | Due to missing translation values of color values for the languages configured for the channel, color options would appear blank and user may not be able to select correct color value for their variant selection | 
| Prod-Ru-002 | Product dimensions | Master product Style translation is missing | Error | Due to missing translation values of style values for the languages configured for the channel, style options would appear blank and user may not be able to select correct style value for their variant selection | 
| Prod-Ru-003 | Product dimensions | Master product Size translation is missing | Error | Due to missing translation values of size values for the languages configured for the channel, size options would appear blank and user may not be able to select correct size value for their variant selection | 
| Prod-Ru-004 | Product dimensions | Master product Configuration translation is missing | Error | Due to missing translation values of configuration values for the languages configured for the channel, configuration options would appear blank and user may not be able to select correct configuration value for their variant selection| 
| Prod-Ru-005 | Product assortments | The product is not active in any assortments, and it won’t be shown on channel. | Warning | These are products associated with the categories in the channel navigation hierarchies, but not part of any assortments associated with the channel, those products will not show up in Comemrce channels | 
| Prod-Ru-006 | Product assortments | The product is excluded. If any product has at least one exclusion , then it is not going to show up | Warning | These are products that are excluded in atleast one assortment that's associated with the channel and these products will not be discoverable in Commerce channels.  | 
| Prod-Ru-007 | Product and product masters | Product name translation is missing | Error | If channel is configured to support languages, other than system default language - in that case this product won't render correctly in the product browsing results in Commerce channels | 
| Prod-Ru-008 | Product and product masters | Product is not categorized | Error | These are products that are part of the assortment, and released to the LE associated with the channel but missing association to category in the navigation hierarchy, and thus won't be discoverable in product browsing results. | 
| Prod-Ru-009 | Product and product masters | Inventory unit is missing | Warning | These are products with missing inventory unit of measure, which may have an impact on the inventory related operations | 
| Prod-Ru-010 | Product and product masters | Sales unit is missing | Error | These are products with missing sales unit of measure, which may have an impact on the product discovery and ordering capabilities. | 
| Prod-Ru-011 | Product and product masters | Invent base price is missing  | Warning |These are products with missing inventory base price, which may have an impact on the inventory related operations | 
| Prod-Ru-012 | Product and product masters | Sales price is missing | Error | These are products with missing sales base price, which may have an impact on the product discovery and ordering capabilities. | 
| Prod-Ru-013 | Product and product masters | Product is stopped for sales | Warning | These are products that are marked to not be allowed to order, but they will be discoverable in product browsing results in Commerce channels| 
| Prod-Ru-014 | Product and product masters | Product is not released but assorted | Warning | These are products that are not going to be discoverable in Commerce Channels as they are not released to a legal entity associated with the channel. | 
| Prod-Ru-015 | Product and product masters | Product is categorized to an inactive category | Warning | These are products that are categorized to an inactive category of the Channel navigation hierarchy associated with channel, and thus won't be discoverable in the Commerce channels |
| Prod-Ru-016 | Product and product masters | Product master or distinct product attribute translation is missing | Error | If a channel is configured to render data in the language other than system default language (not to be confused with channel 'default' language) then standard attributes (including refiners associated with those attributes) won't be rendered correctly. Also, this will have impact on HQ user, when they have user preferences set to use language different than default system language. |
| Prod-Ru-017 | Product and product masters | Product description translation is missing | Error |If a channel is configured to render data in the language other than system default language (not to be confused with channel 'default' language) then product description won't be rendered correctly. Also, this will have impact on HQ user, when they have user preferences set to use language different than default system language.  |



