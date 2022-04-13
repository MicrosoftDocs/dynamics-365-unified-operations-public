---
# required metadata

title: Dynamics 365 Commerce e-commerce localization guide
description: This topic describes how to localize a Microsoft Dynamics 365 Commerce e-commerce site into additional languages and configure the site to support multiple channels.
author: bicyclingfool
ms.date: 04/12/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: stuharg
ms.search.validFrom: 2017-06-20
---

# Dynamics 365 Commerce e-commerce localization guide

[!include [banner](includes/banner.md)]

This topic describes how to localize a Microsoft Dynamics 365 Commerce e-commerce site into additional languages and configure the site to support multiple channels, and also covers the necessary concepts and terminology related to the process.

The e-commerce capabilities in Dynamics 365 Commerce have been designed to enable online experiences that can be tailored for specific countries and languages while allowing for the maximum reuse of templates, pages, content, and media. It is also possible to start by creating a basic site and then expanding into new markets by adding support for additional countries and languages over time.

## Definitions

**Locale, locale identifier**: A locale (also known as a locale identifier) defines a language that is associated with a country or region. For example, the locale identifier "fr-ca" is associated with Canadian French.

**Base language**: The language you develop your site content in and export for localization.

**Channel, online store**: Channels (also known as online stores) define the payment methods, price groups, product hierarchies, assortments, and products for an online e-commerce storefront.

## Concepts

### URL-driven experience

Dynamics 365 Commerce e-commerce sites deliver unique marketized and localized experiences for customers through channels and locale identifiers. Channels define the unique products, categories, currencies, and payment methods for a market, and locale identifiers determine the language of the content that customers will see. An e-commerce site uses URLs to differentiate between marketized and localized experiences. Site URLs for these unique channel and locale experiences are defined for a site in the **Channels** site settings page in Dynamics 365 Commerce site builder.

A URL in site builder is a combination of a domain and a path that defines the entry point for a unique pairing of channel and locale. In the following example, a fictitious online store called Fabrikam Inc. defines four unique combinations of channels and locales, and maps each to a unique URL that serves them to customers.

| Domain                     |  Path      | Channel       |   Locale     |
|------------------------|--------|--------------------------------|--------|
| `https://fabrikam.com` | /      | Fabrikam extended online store | en-us  |
| `https://fabrikam.com` | /es    | Fabrikam extended online store | es     |
| `https://fabrikam.ca`  | /      | Contoso online store    | fr-ca  |
| `https://fabrikam.ca`  | /en-ca | Contoso online store    | en-ca  |

#### Domains

Domains are established when you set up your e-commerce site in the Microsoft Lifecycle Services (LCS) portal. After your e-commerce environment is provisioned, additional domains can be added by opening a service request. For more information about setting up domains for your e-commerce site, see [Domains in Dynamics 365 Commerce](domains-commerce.md).

#### Paths

A path is an arbitrary string that, in combination with the domain, maps to a unique pairing of channel and locale. The string used as the path often matches the locale identifier it maps to, but this is not a requirement.

A channel and locale pairing can be mapped to a domain with an empty path ("/"). In the Fabrikam examples above, customers who visit `https://fabrikam.ca/` (the domain `https://fabrikam.ca` paired with the blank path "/") would be served products and assortments for the Canada market in Canadian French (fr-ca).

Commerce site builder prevents you from creating duplicate identical combinations of a domain and path. However, it is possible to map duplicate combinations of channel and locale to different domain and path combinations.

#### Channels

- Channels (also known as online stores) define the payment methods, price groups, product hierarchies, assortments, and products for an online e-commerce storefront.
- Channels are defined, configured, and published in Dynamics 365 Commerce headquarters.
- In Commerce site builder you can see the online stores that have been configured in headquarters and are available to be mapped to a site.

For more information about channels, see [Channels overview](channels-overview.md). For more information about setting up an online channel, see [Set up an online channel](channel-setup-online.md).

#### Locale identifier

A locale identifier specifies the country and language used for an online store. The locale identifier is also used when you export and hand off files for localization. Locales are defined and published for each channel in headquarters. 

The same locale can be mapped to multiple channels so that a common language can be offered across multiple markets.

## Configure languages and channels for your e-commerce site

Out of the box, all Dynamics 365 Commerce e-commerce sites are configured to use a single online channel and a single language. This is the case whether you start with the Fabrikam demo site or create a new site from scratch.

In this configuration, customers and partners typically develop all the assets that will be used across countries and languages such as templates, pages, fragments, content, and media. All site content is developed in the first language you chose for your site, or English if using the Fabrikam demo site.

![Out of the box Dynamics 365 Commerce e-commerce site](media/loc-guide-1.png)

> [!NOTE]
> It is possible to configure the Fabrikam demo site to use an additional language for content development instead of English.

The content management system (CMS) and page model for Dynamics 365 Commerce e-commerce sites have been designed to enable expansion into new markets and locales so that it is possible to manage the assets for an online store that spans multiple markets and languages through a single e-commerce site.

![Dynamics 365 Commerce e-commerce site that spans multiple markets and languages](media/loc-guide-2.png)

### Configure an additional language for your site

Configuring a new language for an e-commerce site is a three-step process.

#### Step 1: Add a language to your channel in headquarters

> [!NOTE] 
> Before you add a language to your channel in headquarters, you can confirm the channels(s) mapped to your site by going to **Site settings \> Channels** in site builder. The channels mapped to your site are listed in the **Channels** column.

To add a language to your channel in headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channels \> Online stores** to see the channel(s) that you have configured.
1. For the channel/online store to which you want to add a language, select its **Retail Channel ID**. 
1. On the **Languages** FastTab, select **+ Add**. In the new row that is created, in the **Language** column enter the locale code for the new language or select it  from the drop-down list, and then select **Save**.
1. Go to **Retail and Commerce \> Retail and commerce IT \> Distribution schedule** and run job **1070 Channel configuration**. When the job has completed, you can proceed to the next section of this topic to add the language to a channel in site builder.

![Languages FastTab of an online store in Commerce headquarters](media/loc-guide-3.png)

#### Step 2: Add a language to a channel in site builder

To add a language to a channel in site builder, follow these steps.

1. Open your site in site builder and go to **Site settings \> Channels**.
1. Select on the name of the channel to which you want to add the language.
1. In the right pane, select **+ Add a locale**.
1. In the **Add a locale** dialog box, under **Add a locale** select the locale for the language you previously added to the channel in headquarters., and then select **OK**.
1. Under **Domain**, select the domain that customers will visit to view your site in this channel and language.
1. Under **Path**, select the path that customers will visit to view your site in this channel and language.
1. If you want this language to be the default language for viewing, creating, and updating site builder pages and fragments, select the **Use as default authoring channel language** checkbox. This setting only affects site builder and does not influence the published site experience for your customers.
1. Select **OK**.
1. Select **Save and Publish**.

#### Step 3: Localize your site content

After adding a language to a channel in site builder, the new language should now be available to select in the **Locale** field of the channel and locale picker at the upper right of the page. Once this is confirmed, you will be able to start creating localized versions of site pages from those in your base language.

To get started localizing your site content, see [Localize e-commerce site content](#localize-e-commerce-site-content) below.

### Configure a new channel for your site

Dynamics 365 Commerce e-commerce sites can serve experiences that are defined across multiple online channels and configured in headquarters. A site uses multiple channels to show a unique configuration of payment methods, price groups, product hierarchies, assortments, and products to customers. A channel is typically used to configure these dimensions to suit the requirements and preferences for the experience associated with individual countries, but this is a business decision that is made by the customer and not a requirement.

The prerequisites and tasks associated with setting up a channel/online store are beyond the scope of this document. To learn more about setting up an online channel in Dynamics 365 Commerce headquarters, see [Channel setup basics](channels-overview.md#channel-setup-basics). For information on steps and requirements specific to online channels, see [Set up an online channel](channel-setup-online.md).

To add a channel to your site in site builder, follow these steps.

1. Go to **Site settings \> Channels**. 
1. Select **Add a channel**.
1. In the **Add a channel** dialog box, under **Channel** select the channel that you want to add. You can only add channels that have not already been added to your site.
1. Under **Default locale**, select the default locale for the channel. If you add new languages to the channel, you can change the default to one of those languages.
1. Under **Domain**, enter or select the domain that will be part of the URL that serves content and experiences for this channel and language combination.
1. Under **Path**, enter or select the path that will be part of the URL that serves content and experiences for this channel and language combination.
1. Select **OK**.
1. Select **Save and Publish**.

## Localize e-commerce site content

### XLIFF basics

XML Localization Interchange File Format (XLIFF) is an industry standard file format for passing localizable content between content management tools. Commerce site builder uses the XLIFF file format for exporting page, fragment, and image metadata content so that it can be localized and reimported.

Microsoft Dynamics customers typically work with third-party localization vendors such as [Translated](https://translated.com/welcome) to translate their XLIFF files into the languages they require.

### Localize assets in site builder

The following e-commerce site assets are localizable in site builder:

- Pages
- Fragments
- Media assets
- Modules

When a new page, fragment, or media asset is created, it is created within the context of the channel and language currently selected in the channel and locale
picker. This is usually your *base language*, assuming that you haven't configured additional languages or channels. In sites with multiple channels and languages configured, the base language is defined by the channel and locale you have set as the default on the **Site settings \> Channels**  page.

The steps for localizing content for pages, fragments, and media assets are similar. Module content localization follows a different process, for more information see [Localize modules](#localize-modules)below.

#### Step 1: Export an XLIFF file

To export an XLIFF for a page, fragment, or image in site builder, follow these steps.

1. Open the page, fragment, or image asset for which you want to export base language content for localization.
1. On the command bar, select **Localization \> Export XLIFF**.

An .xlf file named **\<assetname\>.xlf** will be downloaded to your browser's download folder. This XLIFF file is specific to the asset you're localizing. You will export one XLIFF file for every asset that you want to localize.

#### Step 2: Localize the XLIFF file

In most cases, you'll work with a localization vendor to translate your XLIFF files. If you are localizing assets internally or testing the localization process, you must make the following changes to each XLIFF file:

- Add a target language attribute to the /xliff/file element whose value is the locale identifier of the language you're localizing to. This locale identifier must match the locale identifier specified on the **Channels** site settings page.
- For each //source element, add a target element sibling whose text value is the localized version of what's contained in that source element.

For information about the schema that governs XLIFF files, see [XLIFF 1.2 Specification](http://docs.oasis-open.org/xliff/xliff-core/xliff-core.html).

> [!NOTE]
> To localize an asset into multiple languages, a localized XLIFF file must be created for every language into which you're localizing the asset.

#### Step 3: Import the localized XLIFF file

To import an XLIFF file for an asset, follow these steps.

1. Open the page, fragment, or image asset in site builder.
1. In the channel and locale picker on the upper right, select the channel and language you're importing localized content for.
1. On the command bar, select **Localization \> Import XLIFF**, and then browse to the localized XLIFF file to import for this asset and language.

Once the XLIFF file is successfully imported, a variant of the page, fragment, or asset is created. From here forward, changes made to the localized variant only affect the variant and not the base asset that it was derived from. Similarly, changes to the base asset will not be reflected in the variant of that asset. However, for site pages it is possible to make changes across variants by modifying the template or layout they're associated with. Similarly, changes to a fragment will affect all pages that are dependent on that variant.

### Images

The content metadata associated with images must be localized in order for that image to be rendered in a page or module variant. The following metadata within a media asset are localizable:

- Alt text
- Description
- Title

It is not currently possible to localize the binary for a digital asset such as an image or video. The Dynamics 365 Commerce product team is currently working on this capability.

### Localize modules

Strings that are rendered as part of the module itself (for example, **Previous** and **Next** buttons in a carousel module) are localized separately from module content. For more information, see [Localize a module](e-commerce-extensibility/localize-module.md).

## Additional resources

[Page model glossary](page-elements-overview.md)

[Cross-channel sharing](cross-channel-sharing.md)

[Localize a module](e-commerce-extensibility/localize-module.md)

[Module definition file](e-commerce-extensibility/module-definition-file.md)

[Localize Commerce extension resources and label files](dev-itpro/extension-resource-localization.md)

[Globalize modules using the CultureInfoFormatter class](e-commerce-extensibility/globalize-modules.md)

[App settings: Themes](e-commerce-extensibility/app-settings.md#themes-section)
