---
# required metadata

title: Copy an e-commerce site
description: This template contains examples of Markdown syntax, as well as guidance on setting the metadata.
author: psimolin
ms.date: 02/23/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: psimolin
ms.search.validFrom: 2017-06-20
---

# Copy an e-commerce site

[!include [banner](../includes/banner.md)]

This topic describes the steps and information required to copy an existing e-commerce site within or across e-commerce environments in Dynamics 365 Commerce site builder.

Dynamics 365 Commerce e-commerce supports copying or cloning sites as self-serve operation in the site builder. Sites can be copied within a single e-commerce environment or across e-commerce environments. The user initiating the site copy needs to be tenant administrator in both the source and destination e-commerce environment. 

Site copy copies all the e-commerce content under the source site including pages, fragments, templates, URLs, and assets. A new site will have to be initialized (FRE) before it can be used. Channels can be mapped and managed from “Site Settings > Channels” in the site builder. 

Duration of the site copy operation depends primarily on the number of assets on the source site. For exceptionally large sites we recommend considering using environment copy (Data portability operation) instead. 

> [!NOTE]
> - The source site will be read-only for the duration of the site copy operation. 
> - Only published versions (or latest if no versions are published) of documents are copied over. Version history for content will not be available in the destination site.

## Copy a site within an e-commerce environment 

To copy a site within an e-commerce environment, follow these steps.

1. Log in to the site builder of the environment where you want to perform the copy within 
1. Navigate to the site list view 
1. Locate and select the site you want to copy/clone 
1. Click “Copy site” from the action bar 
1. “Copy site” view opens – make note that the “Source tenant”- and “Source site”-field is populated with the current tenant and selected site information. 
1. Enter the name for the new site in the “New site name” field. 
1. Click “Create copy” 

> [!NOTE]
> The new site name needs to be unique for the e-commerce environment.

After the information has been validated, notification will pop-up indicating that a new site copy job has been created. Progress of the job can be monitored from the site copy job monitoring view. When the copy operation has successfully finished, the new site will appear in the list of sites. 

IMG_1

## Copy a site across e-commerce environments 

To copy a site between two different e-commerce environments, follow these steps. 

1. Log in to the site builder of the destination environment  
1. Click “Copy site” from the action bar 
1. “Copy site” view opens 
1. Enter the name for the new site in the “New site name” field. 
1. Enter the source e-commerce environment name in the “Source tenant”-field – “Source site” drop-down list will be populated with the sites from this environment 
1. Select the source site from the “Source site” drop-down list 
1. Click “Create copy” 

> [!NOTE]
> - The new site name needs to be unique for the e-commerce environment.
> - Tenant administrator permissions are required in both source and destination e-commerce environment. 

After the information has been validated, notification will pop-up indicating that a new site copy job has been created. Progress of the job can be monitored from the site copy job monitoring view. When the copy operation has successfully finished, the new site will appear in the list of sites. 

## Monitor the site copy operation 

To monitor the progress of the site copy operation, follow these steps. 

1. Log in to the site builder of the destination e-commerce environment 
1. Navigate to the “Site copy jobs” 
1. Locate and select your site copy job from the list 
1. You can see the status and the details of the job from the information presented in the list and in the property pane to the right 

Job that is “In progress” can be canceled by selecting it and pressing the “Cancel” button from the action bar. 

If the job has “Failed” or “Completed with errors”, it can be retried by selecting it from the list and pressing the “Retry” button from the action bar. 

> [!NOTE]
> Video assets might still be processing after the site copy job finishes.

IMG_2

## FRE – First run experience 

Before the new site can be taken into use, it must be initialized by going through FRE or First Run Experience. 

To initialize the new site, follow these steps. 

1. Log in to the site builder with the new site 
1. Navigate to the site list view 
1. Locate and select the new site you want to initialize 
1. “Setup your site”-view will open 
1. Choose a domain to be used with this site from the “Select a domain” drop-down list. Domain list is populated with domains you have associated with the e-commerce environment during initialization 
1. Select the associated online store channel from the “Select a default channel” drop-down list. Assortments and other information stored in the HQ will be used from the selected channel 
1. Select the default authoring language from the “Select a default language” drop-down list. The drop-down list is populated with the languages configured for the selected online store channel 
1. “Site path” consists of the base domain and optional URL path. You may leave the path empty if this channel will be served from the domain root or if you want to enter this information later in the channel configuration view in the site builder. The site path needs to be unique for the e-commerce environment. 
1. Click “OK” 
1. Your site will be initialized with the information you provided, and you will be sent to the site management view.

IMG_3

## Additional resources

[Configure your domain name](https://docs.microsoft.com/en-us/dynamics365/commerce/configure-your-domain-name) 

[Deploy a new e-commerce tenant](https://docs.microsoft.com/en-us/dynamics365/commerce/deploy-ecommerce-site) 

[Associate a Dynamics 365 Commerce site with an online channel](https://docs.microsoft.com/en-us/dynamics365/commerce/associate-site-online-store) 

[Manage robots.txt files](https://docs.microsoft.com/en-us/dynamics365/commerce/manage-robots-txt-files) 

[Upload URL redirects in bulk](https://docs.microsoft.com/en-us/dynamics365/commerce/upload-bulk-redirects) 

[Set up a B2C tenant in Commerce](https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-b2c-tenant) 

[Set up custom pages for user logins](https://docs.microsoft.com/en-us/dynamics365/commerce/custom-pages-user-logins) 

[Configure multiple B2C tenants in a Commerce environment](https://docs.microsoft.com/en-us/dynamics365/commerce/configure-multi-b2c-tenants) 

[Add support for a content delivery network (CDN)](https://docs.microsoft.com/en-us/dynamics365/commerce/add-cdn-support) 

[Enable location-based store detection](https://docs.microsoft.com/en-us/dynamics365/commerce/enable-store-detection) 