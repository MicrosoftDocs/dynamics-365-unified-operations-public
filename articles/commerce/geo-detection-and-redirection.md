---
# required metadata

title: Set up geo detection and redirection
description: This topic explains the capabilities of geo detection and redirection, and now to configure it for an e-commerce site.
author: stuharg
ms.date: 08/11/2021
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
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 

---


[!include [banner](../includes/banner.md)]



# Overview

Geo-detection and redirection gives you the ability to detect your customers' geographic location, and use that information to suggest or redirect them to the marketized and localized site that's most appropriate for them. You can choose one of two experiences for your customers who are requesting a site URL that is not associated with the country/region they're in:

1. Ask customers to choose a site or sites associated with their location, or stay on the site they     originally requested.
2. Automatically redirect customers to the site associated with their country/region

In the example below, a customer in Canada is requesting a site that is not associated with Canada. The country/region picker module displays the sites that have been configured for Canada. When the customer selects an option, they're taken to that site and their site preference is captured in a cookie so they're not prompted to select the site again the next time they visit. 



![Screenshot of the region/language picker showing options for Canada English and Canada French](./media/Geo_Country-region-picker.PNG)



## Enable geo redirection features

To enable geo redirection for your site, ensure that the **Enable geo redirection features** feature flag is enabled for your site in site builder. To do this, go to **Settings** -> **General** and turn on **Enable geo redirection features**. NOTE: The **Enable geo redirection features** flag requires that **Enable location based store detection** first be enabled. Learn more about the [Enable location based store detection](enable-store-detection.md) feature flag. 



## Associate countries/regions with online stores(s)

You associate countries/regions with an online store (aka online channel) in Headquarters. When you associate a country to an online store, you are declaring that customers that reside in that country/region should view the site that is mapped to that online store. 

To associate a country with an online store:

1. navigate to the **Online stores** view under Modules -> **Retail and Commerce** -> **Channels**, or search for "online stores" in the search box. 
2. Open the online channel you wish to associate countries with
3. Open the Countries/Regions tab
4. Click **+Add**, and select a country/region from the dropdown.

You can add multiple countries/regions to the online store if needed. 

When you're finished associating countries/regions to the online store, run job 1070 (Channel configuration) in the **Distribution schedule** view (go to Modules -> **Retail and commerce** -> **Retail and commerce IT.** Once that job completes, the countries/regions you associated will be available in the Channels page under site settings in site builder. 



![Screenshot showing countries/regions being mapped to an online store in Headquarters](./media/Geo_HQ-country-mapping.PNG)



## Configure geo redirection rules

The countries/regions you make available to an online channel in site builder can now be mapped to URLs you have defined in the Channels view. When you associate a country with a URL, geo redirection can then verify that the URL requested by your customer is appropriate for the country/region they reside in, or recommend one or more URLs that you declare to be intended for their location. 

To associate countries/regions with site URLs:

1. Go to the **Channels** page within site settings
2. Click on the channel name
3. Select a locale in the slide out
4. Select one or more countries to associate with that URL 
5. Click OK
6. Click Save and publish to save your changes and publish them. 

![Screenshot that illustrates how countries/regions are mapped to URLs in site builder](./media/Geo_Channels-config.PNG)



### Geo detection and redirection logic

Geo detection and redirection in Dynamics 365 Commerce works by comparing the customer's country/region to the list of countries/regions that are mapped to URLs in the Channels page in site builder. 

When a customer requests a URL for your site, the redirection logic determines whether the customer's country/region is mapped to the URL they are requesting. If it is, the customer continues on to the URL they requested. If not, redirection logic finds the URL or URLs that are mapped to their country/region and displays them to the customer as recommended URLs for their country/region. If auto-redirection is enabled for the customer's country/region, they will automatically be redirected to the best URL for their country/region. For more information about defining which URL is used for auto-redirection, see the Configure auto redirection section below. 

The workflow below illustrates the steps and decision points in the redirection logic



![Workflow diagram that illustrates the steps and decision points that are part of geo redirection logic](./media/Geo_Redirection-logic.PNG)



## Configure the country/region picker module

The country/region picker module is included in the Store starter kit. It displays recommended URLs to customers who request a URL that is not associated with their country/region. 

To display the country/region picker on your home page, add it within the header slot, either directly or via a shared fragment. 

The URLs that you'll recommend to your customers must be configured as Country objects in the module. Follow these steps for each URL that you want to recommend:

1. Click **+ Add country** under Country list 
2. Click on the newly-created box that says "Country"
3. Enter a display string (e.g. "Canada")
4. Enter an optional display substring (e.g. "French", or "fr-ca") 
5. Enter an optional image from the media library.
6. Enter the Country URL. This URL must exactly match the URL in the Channels page that is mapped to the channel and locale associated with this country. 
7. Click OK and repeat as necessary for the countries you wish to display in the country/region picker. 



![Screenshot that demonstrates how a country is added to the country/region picker module](./media/Geo_country-region-config.PNG)



## Configure auto-redirection

You can choose to auto-redirect customers in certain countries to a specific URL you configure rather than prompting them to choose one from the list. For example, if you want to automatically send customers who live in Japan to the site that is mapped to the channel and language for Japan, you will enable **Automatic auto redirection** in the channel where that URL is configured. After you save and publish that setting, customers in Japan will automatically be sent to that URL and will not be shown the country/region picker. 

It is possible to associate two or more URLs to a country/region. When more than one URL is associated with a country/region, auto redirection uses the URL for the locale that is marked as the default locale for that channel. 



## Save customer site preferences

When the **Enable geo redirection features** flag is set to on, geo redirection will save your customers' preferred site. When the customer selects a recommended URL from the country/region picker, the URL will be written to the _msdyn365___site_ cookie on the domain they're presently on before being taken their preferred site. The next time they request the URL that previously displayed the country/region picker, they'll be automatically redirected to their preferred site.

The [Site selector module](site-selector.md) also writes the customer's site selection to the _msdyn365___site_ cookie. We recommend that you set up the Site selector so that customers can change their preferred site through the Site selector module. The site that customers select in the Site picker module will be respected by geo redirection. 



## Additional resources

[Site selector module](site-selector.md) 

[Enable location-based store detection](enable-store-detection.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]