---
# required metadata

title: Create an e-commerce site
description: This topic describes the steps and information required to create a new e-commerce site in Dynamics 365 Commerce site builder.
author: bicyclingfool
ms.date: 03/10/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry:
ms.author: stuharg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# Create an e-commerce site

[!include [banner](includes/banner.md)]

This topic describes the steps and information required to create a new e-commerce site in Dynamics 365 Commerce site builder.

When you license the Dynamics 365 Commerce capabilities, site builder will be provisioned with a starter site that you can use as a basis for your own site. However, if you want to start from scratch or if you want to establish a second site, you will need to establish a new site in the site authoring environment. 

## Site creation prerequisites

A site builder user must have a Microsoft Azure Active Directory (Azure AD) user account included in the Azure AD security group assigned for the e-commerce system administrators. For more information, see [Deploy a new e-commerce tenant](deploy-ecommerce-site.md).

> [!NOTE]
> Azure AD guest users may have different access permissions in your Azure AD tenant. Even if included in the Azure AD security group assigned for the e-commerce system administrators, a guest user may need Azure AD **External users** permission settings to be adjusted in order to create an e-commerce site in Commerce. 

To adjust Azure AD **External users** settings, follow these steps.

1. In the Azure portal, navigate to your Azure AD tenant.
1. Go to **User settings \> External users** and select the **Manage external collaboration settings** link. This opens the **External collaboration settings** page where guest user access, guest invite settings, and collaboration restrictions can be set. 
1. Adjust the external collaboration settings in accordance with your company's security policies. 

## Set up your site

To set up your site, do the following.

1. Open the site builder environment. You can find a link to site builder in Microsoft Lifecycle Services (LCS) in the environment features page for Commerce.
1. On the home page for the site authoring environment, select **New site**.
1. In the **New site** dialog box, provide the following information.

| Field                               | Description |
|-------------------------------------|-------------|
| Site name                           | Enter the display name that should be used for your site in the site authoring environment. This name is visible only in the authoring environment and will not be shown to customers. |
| Site administrator's security group | Specify the Microsoft Azure Active Directory (Azure AD) security group that manages users who have the site administrator role in this site. |
| Default channel (operating unit number) | Select the online store that this site will serve as the web storefront for. If you want your e-commerce site to support multiple online stores, you must associate the stores with your site in **Site settings** after the site is set up. |
| Default language                            | Specify the default language for this online store and market. An online store can support multiple languages. If you want to support multiple languages for this online store or another online store, you can configure that support in **Site settings** after the site is set up.  |
| Domain                              | Select a domain name that will serve as the domain for this online store. If you haven't configured any domains in LCS, you can leave this field blank. After your domain is configured in LCS, you must add it to your online store in **Site settings**.  |
| Path                              | When your site supports more than one language for a given domain name, use the path field to create a unique site URL for that domain and language combination. If the language you specified in the **Default language** field is the only language you will support for this domain, or will continue to be the default language after you have localized your site into additional languages, we recommend that you leave this field empty. |

After your site is created, you can verify that it is associated with your online store by selecting the **Products** tab. You should see the assortment of products that has been allocated to the online store. You can also use the drop-down menu in the upper left of the page to access the allocated products by category.

## Rename your site

To rename your site in site builder, follow these steps.

1. To open site list view, select **Site switcher** in the upper-right corner, and then select **Manage sites** . 
1. Select the check box next to the site that you want to rename, and then select **Rename** on the command bar.
1. In the **New site name** dialog box, enter the new site name, and then select **OK**. The site list will update to show the site's new name.

## Delete a site

To delete a site in site builder, follow these steps.

1. To open site list view, select **Site switcher** in the upper-right corner, and then select **Manage sites**.
1. Select the site you want to delete, and then select **Delete** on the command bar.
1. In the **Delete \<site name\>** dialog box, enter the site name, and then select **Delete**.

## Additional resources

[Configure your domain name](configure-your-domain-name.md)

[Deploy a new e-commerce tenant](deploy-ecommerce-site.md)

[Associate a Dynamics 365 Commerce site with an online channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Upload URL redirects in bulk](upload-bulk-redirects.md)

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
