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

## Connecting your CDN

Customers setting up an e-Commerce environment in Dynamics 365 Commerce can configure the environment to work with your CDN Service. 

Your custom domain must be enabled during the e-Commerce environment provisioning, or can be set up after provisioning via a service request. The provisioning process for your e-Commerce environment will generate a hostname associated with the environment (ex: format <e-commerce-tenant-name>.commerce.dynamics.com). The generated hostname or endpoint only supports SSL certificate for *.commerce.dynamics.com. It will not support SSL for custom domains.

Note: All statics form e-Commerce (JS or CSS files) will get served from the *commerce.dynamics.com endpoint.

## Setting up SSL for Custom Domain

To ensure the SSL is set up for a custom domain and your statics (JS/CSS) are cached, your CDN will need to be configured to direct to your Dynamics 365 Commerce generated hostname for your environment. You must also cache the following pattern for statics only: /_msdyn365/_scnr/*

Any CDN service can be used. 

<u>Example CDN Services</u>: 

**Azure Front Door**- Azure's CDN solution available. For more information on Azure Front Door, please see details at https://docs.microsoft.com/en-us/azure/frontdoor/ .

**Akamai** - https://www.akamai.com/us/en/products/performance/dynamic-site-accelerator.jsp



