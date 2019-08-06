---
# required metadata

title: Create a new e-Commerce site
description: This topic describes the tasks that are associated with the creation of a new e-Commerce site in Microsoft Dynamics 365 for Commerce.
author: stuharg
manager: AnnBe
ms.date: 09/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Enduser
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: bicyclingfool
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.5

---

# Create a new e-Commerce site

[!include [banner](includes/banner.md)]

[!include [banner](includes/preview-banner.md)]

This topic describes the tasks that are associated with the creation of a new e-Commerce site in Microsoft Dynamics 365 for Commerce.

To start to develop your e-Commerce experience, you must first establish a new site in the site authoring environment. Before you can create a new site, at least one online store must be created in headquarters (HQ). For more information about how to create an online store, see [Create a Dynamics 365 e-Commerce online store]().

To set up your site, in Microsoft Dynamics Lifecycle Services (LCS), select the link for the site authoring environment. On the home page for the site authoring environment, select **New site**, and then, in the **New site** dialog box, provide the following information.

| Field                               | Description |
|-------------------------------------|-------------|
| Site name                           | Enter the display name that should be used for your site in the site authoring environment. This name is visible only in the authoring environment. It won't be shown to customers. |
| Site Administrator's Security Group | Specify the Microsoft Azure Active Directory (Azure AD) security group that manages users who have the **Site Administrator** role in this site. For more information about how to grant permissions to users, see [Manage users and roles](). |
| Online store                        | Select the online store that this site will serve as the web storefront for. If you want your e-Commerce site to support multiple online stores, you must associate the stores with your site in **Site settings** after the site is set up. |
| Domain                              | Select a domain name that will serve as the domain for this online store. If you haven't configured any domains in LCS, you can leave this field blank. After your domain is configured in LCS, you must add it to your online store in **Site settings**. For more information about how to set up domains for a site, see [Configure your domain names](). |
| Market                              | Select the country or region that best represents this online store. If you configure your site to support multiple online stores, the value that you select here will be used to guide your customers to the most appropriate online store for their geographic location. For example, your site supports separate stores for the United States and Japan, and a customer who resides in Japan requests a URL for your US store. In this case, the customer can receive a message that states that you offer an online store for Japan. After your site is set up, you can add more markets to this online store. |
| Language                            | Specify the language that you want customers to view content in for this online store and market. An online store can support multiple languages. If you want to support multiple languages for this online store or another online store, you can configure that support in **Site settings** after the site is set up. For more information about how to configure languages, see [Add other languages to your site](). |

After your site is created, you can verify that it's associated with your online store by selecting the **Retail** tab. You should see the assortment of products that has been allocated to the online store. You can also use the drop-down field in the upper left of the page to access those products by category.
