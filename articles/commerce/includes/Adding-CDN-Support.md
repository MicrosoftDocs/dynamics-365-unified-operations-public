---
# required metadata

title: Adding CDN Support
description: This topic describes how to add your CDN to your Dynamics 365 Commerce environment.
author: brshoo
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Adding CDN Support

## Overview

This topic describes how to add your CDN to your Dynamics 365 Commerce environment. 

## Using your CDN with Dynamics 365 Commerce

Customers setting up an e-Commerce environment in Dynamics 365 Commerce can configure the environment to work with your CDN Service. 

Your custom domain must be enabled during the e-Commerce environment provisioning, or can be set up after provisioning via a service request. The provisioning process for your e-Commerce environment will generate a hostname associated with the environment (ex: format <e-commerce-tenant-name>.commerce.dynamics.com). 

The Dynamics 365 Commerce hostname or endpoint generated during provisioning only supports an SSL certificate for *.commerce.dynamics.com. This generated hostname or endpoint will not support SSL for custom domains. Due to this, you need to terminate SSL for your custom domain in your CDN and forward traffic from the CDN to the Dynamics 365 Commerce generated hostname or endpoint. 

Additionally, the statics (JS or CSS files) from Dynamics 365 Commerce will get served from the Commerce generated endpoint (*.commerce.dynamics.com). To have the statics cached, the Commerce generated hostname or endpoint needs to be placed behind the CDN.

## Setting up SSL for a Custom Domain

To ensure the SSL is set up for a custom domain and your statics (JS or CSS files) are cached, your CDN will need to be configured to direct to your Dynamics 365 Commerce generated hostname for your environment. You must also cache the following pattern for statics (JS or CSS files) only: /_msdyn365/_scnr/*.

Once you have provisioned your Dynamics 365 Commerce environment with the custom domain provided (or provided the custom domain for your environment via a service request), point the custom domain to the Commerce generated hostname or endpoint (ex: format <e-commerce-tenant-name>.commerce.dynamics.com).

As noted, the generated hostname or endpoint will only support an SSL certificate *.commerce.dynamics.com; it will not support SSL for custom domains.

Any CDN service can be used. 



### Example CDN Services

**Azure Front Door**- Azure's CDN solution available. For more information on Azure Front Door, please see details at https://docs.microsoft.com/en-us/azure/frontdoor/ .

**Akamai** - https://www.akamai.com/us/en/products/performance/dynamic-site-accelerator.jsp



### Example CDN Setup

Using Azure Front Door for context, this section will review some of the guidance above during as called out along the setup steps of your CDN. The documented Azure Front Door setup steps can be found here: https://docs.microsoft.com/en-us/azure/frontdoor/quickstart-create-front-door

Setup follows these three steps:

1. Add a frontend host
2. Configure a backend pool
3. Setup a routing rule

Specific for CDN setup for Dynamics 365 Commerce, in Step 2 (Configure a backend pool), perform the following during the step 2 configuration process: 

- Add <ecom-tenant-name>.commerce.dynamics.com to a backend pool as a custom host (empty backend host header)
- Set up a Health Probe as ''/keepalive' with intervals of 255 seconds
- The Load Balancing section may keep the default values
  
  
![CDN Add A Backend](/articles/commerce/media/CDN_BackendPool_Setup.png "CDN Add A Backend")


![CDN Backend Pool](/articles/commerce/media/CDN_BackendPool.png "CDN Backend Pool")

Additionally, for step 3 (Setup a routing rule), perform the following during the step 3 configuration process:

- Add a default routing rule (Name: default)
- Accepted protocol set to 'HTTP and HTTPS'
- Frontend hosts set to 'dynamics-ecom-tenant-name.azurefd.net'
- Patterns to Match set to '/*'
- Route Details, set Route type to "Forward"
- Set Backend pool to 'ecom-backend'
- Select "Match request" for Forwarding protocol
- Set URL rewrite to 'Disabled'
- Set Caching to 'Disabled'

Now add a caching rule for statics URLS by:

- Name the rule 'statics'
- Set Accepted protocol to 'HTTP and HTTPS'
- Set frontend hosts to 'dynamics-ecom-tenant-name.azurefd.net'
- Patterns to Match set to '/_msdyn365/_scnr/*'
- Route Details, set Route type to "Forward"
- Set Backend pool to 'ecom-backend'
- Select "Match request" for Forwarding protocol
- Set URL rewrite to 'Disabled'
- Set Caching to 'Enabled'
- Query string caching behavior set to "Cache every unique URL"
- Dynamic compression to 'Enabled'

![CDN Add A Caching Rule](/articles/commerce/media/CDN_CachingRule.png "Add A Caching Rule")

After this initial configuration is deployed, add custom domain to this Azure Front Door configuration.

To add the custom domain (ex: www.fabrikam.com), you need to configure a CNAME for the domain

![CNAME Configuration](/articles/commerce/media/CNAME_Configuration.png "CNAME Configuration")

**<u>Note</u>**: If the domain to be used is already active and live, please reach out to support for enabling this domain with Azure Front Door to set up a test.

You can choose to use Azure Front Door's to manage the certificate, or use your own certificate for the custom domain.

![Custom Domain Certificate](/articles/commerce/media/Custom_Domain_HTTPS.png "Custom Domain Certificate")

Your CDN should now be configured for use with your Dynamics 365 Commerce site.


