---
# required metadata

title: Create a new e-Commerce site
description: This topic covers the tasks associated with creating a new e-Commerce site in Dynamics 365 for Commerce. 
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
ms.author: shajain
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.5

---

# Create a new e-Commerce site

[!include [banner](includes/banner.md)]

[!include [banner](includes/preview-banner.md)]

This topic covers the tasks associated with creating a new e-Commerce site in Dynamics 365 for Commerce. 

To get started with development of your e-Commerce experience, you first need to establish a new site in the site authoring environment. To create a new site, you must have at least one online store created in headquarters (HQ). For more information on creating an online store, see the [Create a Dynamics 365 e-Commerce online store]().  

To set up your site, click the link in Dynamics Lifecycle Services (LCS) for the site authoring environment. On the home page of the site authoring environment, click **New site**. The **New site** dialog will open and will ask you to provide the following information.

| **Site name**                           | The display name for your site within the site authoring environment. The name you give your   site is only visible within the authoring environment and it will not be shown to customers. |
| --------------------------------------- | ------------------------------------------------------------ |
| **Site Administrator's Security Group** | The Azure AD security group that manages the users that perform the Site Administrator   role within this site. For more information about granting permissions to users, see [Manage users and roles](). |
| **Online store**                        | Choose the online store that this site will serve as the web storefront for. If you want your e-Commerce site to support multiple online stores, you need to associate the stores to your site through **Site settings** after your site is set up. |
| **Domain**                              | Select a domain name that will serve as the domain for this online store. If you have not   configured any domains in LCS, this field may be left empty. Once your domain is configured in LCS, you need to add it to your online store through **Site settings**. See [Configure your domain names]() to learn more about how to set up domains for your site. |
| **Market**                              | Choose a country that best represents this online store. If you choose to configure your site to support multiple online stores, the value you enter here will be used to guide your customers to the most appropriate online store given their geographic location. For example, if your site supports a U.S. and Japan store, and a customer who resides in Japan is requesting a URL for your U.S. store, you can show them a message that tells them you offer an online store for their particular region. After your site is set up, you can add more markets to this online store. |
| **Language**                            | Specify the language you want your customers to view content in for this online store and   market. An online store can support multiple languages. If you wish to support multiple languages for this or another online store, you can do that through **Site settings** after your site is set up. See [Add other languages to your site]() for more information on configuration languages. |



Once your site is created, you can verify that it is associated with your online store by clicking the **Retail** tab. You should see the products that have been assorted to that online store and be able to access them by category by using the dropdown in the upper-left of the page. 
