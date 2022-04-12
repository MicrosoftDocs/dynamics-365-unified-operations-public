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

The e-commerce capabilities in Dynamics 365 Commerce have been designed to enable online experiences that can be tailored for specific countries and languages while allowing for the maximum reuse of templates, pages, content, and media. The e-commerce capabilities also make it possible to create a basic site and expand into new markets by adding support for additional countries and languages over time.

## Definitions

**Locale, locale identifier**: For the purposes of this document a locale or locale identifier defines a language that is associated with a country or region, for example, fr-ca (Canadian French.)

**Base language**: The language you develop your site content in and export for localization.

**Channel, online store**: Defines the payment methods, price groups, product hierarchies, assortments, and set of products for an online e-commerce storefront.

## Concepts

### URL-driven experience

Dynamics 365 Commerce e-commerce sites deliver unique marketized and localized experiences for customers through channels and locales (languages). Channels define the unique products, categories, currencies, and payment methods for a market, and the locale determines the language of the content that customers will see. An e-commerce site uses URLs to differentiate these marketized and localized experiences. Site URLs for these unique channel and locale experiences are defined for a site in the **Channels** site settings page in site builder.

A URL in site builder is a combination of a domain and a path that defines the entry point for a unique pairing of channel and locale. In the following example, a fictitious online store called Fabrikam Inc. defines four unique combinations of channels and locales, and maps each to a unique URL that serves them to customers.

| Domain                     |  Path      | Channel       |   Locale     |
|------------------------|--------|--------------------------------|--------|
| `https://fabrikam.com` | /      | Fabrikam extended online store | en-us  |
| `https://fabrikam.com` | /es    | Fabrikam extended online store | es     |
| `https://fabrikam.ca`  | /      | Contoso online store           | fr-ca  |
| `https://fabrikam.ca`  | /en-ca | Contoso online store           | en-ca  |

#### Domain

-   Domains are established when you set up e-commerce in the Lifecycle Services (LCS) portal.
-   After your e-commerce environment is provisioned, additional domains can be added by opening a service request. For more information about setting up domains for your e-commerce site, see [Domains in Dynamics 365 Commerce](domains-commerce.md).

#### Path

- The path is an arbitrary string that, in combination with the domain, maps to a unique pairing of channel and locale. In the example above, the string used as the path matches the locale identifier it maps to, but this is not a requirement.
- A channel and locale pairing can be mapped to a domain with an empty path ("/"). In the example above, customers who request `https://fabrikam.ca` would get the products and assortments for the Canada market in Canadian French (fr-ca).
- Commerce site builder prevents you from creating duplicate combinations of domain and path. However, it is possible to map duplicate combinations of channel and locale to different domain and path combinations.

#### Channel

- Channels are defined, configured, and published in Dynamics 365 Commerce headquarters.
- Site builder can see the online stores that have been configured in headquarters and are available to be mapped to a site.
- For more information about channels, see [Channels overview](channels-overview.md).
- For more information about setting up an online channel, see [Set up an online channel](channel-setup-online.md).

#### Locale (language)

- The locale is the actual identifier that's used for localization when you're handing off XLIFF files for localization. Locales are defined and published for each channel in headquarters. For more information, see the section below about configuring languages and channels in site builder .
- The same locale can be mapped to multiple channels so that a common language can be offered across multiple markets.

## Configure languages and channels for your e-commerce site

Out of the box, all Dynamics 365 Commerce e-commerce sites are configured for a single online channel and a single language. This is true whether you start with the Fabrikam demo site or create a new site from scratch.

In this configuration, customers and partners typically develop all the assets that will be used across countries and languages such as templates, pages, fragments, content, and media. All site content is developed in the first language you chose for your site, or English if using the Fabrikam demo site.

> [!NOTE]
> It is possible to configure the Fabrikam demo site to an additional language that can be used for content development instead of English. See the steps below for adding a new language to a site and channel.

![New, "out of the box" Dynamics 365 Commerce e-commerce site](media/loc-guide-1.png)

The content management system (CMS) and page model for Dynamics 365 Commerce e-commerce sites have been designed to enable expansion into new markets and locales, so it is possible to manage the assets for an online store that spans multiple markets and languages through a single e-commerce site.

![Dynamics 365 Commerce e-commerce site that spans multiple markets and languages](media/loc-guide-2.png)

### Configure an additional language for your site

Configuring a new language for an e-commerce site is a three-step process.

#### Step 1: Add a language to your channel in headquarters

To add a language to your channel (also known as an online store) in headquarters, follow these steps.

1. Navigate to the channel in headquarters to which you want to add the new language. The list of channels you have configured in headquarters can be found by going to **Retail and Commerce \> Channels \> Online stores**.
1. Open the online store that is mapped to your site by selecting its Retail channel ID. You can verify the online store that is mapped to your site by navigating to the Channels site setting page in site builder and looking at the name of the online store in the Channels column.
1. On the **Languages** FastTab, select **+ Add** and select the locale code for the new language from the drop-down list in the **Language** column, and then select **Save**.
1. Go to **Retail and commerce \> Retail and commerce IT \> Distribution schedules** and run job 1070 (Channel configuration). When the job has finished, you can proceed to step 2 to add the language to a channel to your site in site builder.

![Languages tab within an online store in Commerce headquarters](media/loc-guide-3.png)

#### Step 2: Add a language to a channel in site builder

To add a language to a channel in site builder, follow these steps.

1. Open your site in site builder and go to **Site settings \> Channels**.
1. Select on the name of the channel to which you want to add the language.
1. In the right pane, select **+ Add a locale**.
1. In the **Add a locale** dialog box, select the locale for the language you previously added to the channel in headquarters.
1. Select the domain and path that customers will request to view your site in this channel and language.
1. If you want this language to be the default language for viewing, creating, and updating site builder pages and fragments, select the **Add as default** checkbox. This setting only affects site builder and does not influence the published site experience for your customers.
1. Select **Save and Publish**.

#### Step 3: Localize your site content.

When you return to the **Pages** view in site builder, the new language will be available in the channel and locale picker at the upper right of the page. It is now possible to create localized versions of pages in your base language.

The process for localizing the content of your pages and fragments is covered in the Localizing e-commerce site content section later in this document.

### Configure a new channel for your site

Dynamics 365 Commerce e-commerce sites can serve the experiences that are defined across multiple online channels that are configured in Headquarters. A site utilizes multiple channels in order to show a unique configuration of payment methods, price groups, product hierarchies, assortments, and set of products to customers. A channel is typically used to configure these dimensions to suit the requirements and preferences for the experience associated with individual counties. However, this is a business decision that is made by the customer not a requirement.

The prerequisites and tasks associated with setting up a channel (online store) are beyond the scope of this document. To learn more about setting up an online channel in Dynamics 365 Commerce Headquarters, see the [channel setup basics](channels-overview.md#channel-setup-basics)
section of the [Channels overview](channels-overview.md) help topic. The [Set up an online channel](channel-setup-online.md) help topic talks about steps and requirements specific to online channels.

To add a channel to your site in site builder, follow these steps.

1. Go to **Site settings \> Channels**. 
1. Select **Add a channel**.
1. In the **Add a channel** dialog box, select the channel you want to add. 
    > [!NOTE]
    > You can only add channels that have not already been added to your site.
1. Select the default locale for the channel. If you add new languages to the channel, you can change the default to one of those languages.
1. Select and enter the domain and path that will constitute the URL that serves content and experiences for this channel and language combination.
1. Select **OK**.
1. Select **Save and Publish**.

## Localize e-commerce site content

### XLIFF basics

XLIFF stands for XML Localization Interchange File Format. It is an industry standard file format for passing localizable content between content management tools. Dynamics 365 Commerce e-commerce site builder leverages the XLIFF file format for exporting page, fragment and image metadata content so that it can be localized and re-imported.

Microsoft Dynamics customers typically work with 3rd party localization vendors such as [translated.com](https://translated.com/welcome) to translate their XLIFF files into the languages they require.

### Localize assets in site builder

The following e-commerce site assets are localizable:

- Pages
- Fragments
- Media assets
- Modules

When a new page, fragment or media asset is created, it is created within the context of the channel and language currently selected in the Channel and locale
picker. This is usually your "base language", assuming you haven't configured additional languages or channels. In sites with multiple channels and languages configured, this "base language" is defined by the channel + locale you have set as the default in the Channels site settings page.

The steps for localizing content for pages, fragments and media assets is similar. Exceptions and differences will be called out in the sections below. Module content localization follows a different process. Links to relevant information for that process is in the Modules section below.

#### Step 1: Export an XLIFF

To export an XLIFF for a page, fragment, or image, follow these steps.

1. Open the asset for which you wish to export base language content for localization.
2. Select on the Localization tab and select **Export XLIFF**.

An .xlf file named \<assetname\>.xlf will be downloaded as a file to your browser's download folder. This XLIFF file is specific to the asset you're localizing. You will export an XLIFF for every asset you wish to localize.

> [!NOTE]
> The Localization tab is only visible when assets are in an Edit state.

#### Step 2: Localize the XLIFF

In most cases, you'll work with a localization vendor to transform your XLIFF files. If you are localizing assets internally, or simply wish to test the localization process, the essential changes you must make to an XLIFF file are as follows:

- Add a target-language attribute to the /xliff/file element whose value is the locale identifier of the language you're localizing into. NOTE: this locale identifier must match the locale identifier from the Channels site settings page.
- For each //source element, add a target element sibling whose text value is the localized version of what's contained in that source element.

See the [XLIFF 1.2 Specification](http://docs.oasis-open.org/xliff/xliff-core/xliff-core.html) for full information about the schema that governs XLIFF files.

>[!NOTE]
> In order to localize an asset into multiple languages, a localized XLIFF file must be created for every language you're localizing the asset into.

#### Step 3: Import the localized XLIFF

To import an XLIFF file for an asset, follow these steps.

1. Open the asset in site builder.
1. Select the channel and language you're importing localized content for in the Channel and Locale picker at upper right.
1. Select on the **Localization** tab, select **Import XLIFF** and browse to the localized XLIFF file for this asset and language.

Once the XLIFF is successfully imported, a "variant" of the page, fragment or asset is created. From here forward, changes made to the localized variant only affect the variant, and not the "base asset" that it was derived from. Similarly, changes to the base asset will not be reflected in the variant of that asset. However, in the case of pages, it is possible to make changes across variants by modifying the template or layout they're bound to. Similarly, changes to a fragment will affect all pages that take a dependency on that variant.

### Images

The content metadata associated with images must be localized in order for that image to be rendered in a page or module variant. Currently, the following metadata within a media asset are localizable:

- Alt text
- Description
- Title

As of the Commerce version 10.0.16 release, it is not possible to localize the binary for a digital asset such as an image or video. The Dynamics 365 Commerce product team is currently working on this capability.

### Localize modules

Strings that are rendered as part of the module itself (e.g. "Previous" and "Next" in a carousel module) are localized separately from module content. See
the [Localize a module](e-commerce-extensibility/localize-module.md) help topic for instructions.

## Additional resources

[Page model glossary](page-elements-overview.md)

[Cross-channel sharing](cross-channel-sharing.md)

[Localize a module](e-commerce-extensibility/localize-module.md)

[Module definition file](e-commerce-extensibility/module-definition-file.md)

[Localize Commerce extension resources and label files](dev-itpro/extension-resource-localization.md)

[Globalize modules using the CultureInfoFormatter class](e-commerce-extensibility/globalize-modules.md)

[App settings: Themes section](e-commerce-extensibility/app-settings.md#themes-section)
