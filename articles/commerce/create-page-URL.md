---
title: Create a page URL
description: Learn how to create a page URL on your Microsoft Dynamics 365 Commerce site.
author: bicyclingfool
ms.date: 01/21/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template 

---

# Create a page URL

[!include [banner](includes/banner.md)]

This article explains how to create a page URL on your Microsoft Dynamics 365 Commerce site.

The full, or absolute, URL that points to a page on your site consists of distinct parts. For example, the URL `https://www.contoso.com/en-us/contactus` has the following parts:

- `https://www.contoso.com` – The HTTP protocol and the site's domain.
- `/en-us` – The site's language path.
- `/contactus` – The relative URL for the **Contact Us** page. A relative URL is also known as a URL *slug*.

You establish your site's domain and optional language path when you set up the site. You can add more domains and language paths to your site through the online stores page in the site's settings.

The URL slug for a page exists as a standalone entity in the site authoring environment. A page URL consists of two parts: a name that represents the URL slug, and a pointer to a page on either your site or an external site. You can also configure a page URL to act as a redirect to another page on either your site or an external site.

## Create a page URL

You can create page URLs in two ways:

- Automatically, when you create a page
- Manually, from the **URLs** page

### Create a page URL when you create a page

If you provide a name in the **URL** field when you create a new page, you automatically create a page URL that points to that page on the **URLs** page. After you publish the URL and the page that it points to, site users (your customers) can access the page that is associated with the URL.

> [!NOTE]
> If you publish a URL without publishing the page that it points to, site users receive a 404 error when they try to access the page. If you publish a page without publishing the URL that points to it, the page can't be accessed by using a URL.

### Manually create a page URL

When you create new pages, you don't need to specify a page URL. If you leave the URL field blank, you create the page in an unlinked state. In this state, customers can't access the page, even if you publish it. To make the page accessible, you must manually create the URL and link it to the page.

To manually create the page URL for a page, follow these steps:

1. On the **URLs** page, select **New**.
1. Select the site page to associate with the URL.
1. Enter the URL slug, and then select **OK**.

At this point, the URL is in a draft state. You must publish it before site users can access the associated page.

## Update a page URL

To update the target page of a page URL, follow these steps:

1. On the **URLs** page, select the URL to update.
1. In the property pane on the right, select the ellipsis button (**...**) next to the target page field.
1. In the dialog box, select a different page, and then select **OK**.
1. Save and publish the URL.

## Redirect a page URL

Sometimes, you want your customers to view a different page when they request a specific URL. In these cases, the best and easiest approach is often to change the page that the page URL points to. However, you might have legitimate reasons for using HTTP 301 or 302 redirects to redirect requests for a URL to a different URL.

To redirect a URL to a different URL, follow these steps:

1. On the **URLs** page, select the URL to update.
1. In the property pane on the right, select **Redirect**.
1. Select a destination for the redirect:

    - To point to another page on your site, select **Internal URL**, select the ellipsis button (**...**), and then select the URL to redirect to.
    - To point to a page on an external site, select **External URL**, and then enter the full URL for that page. Be sure to include the protocol. For example, enter `https://domain.com/new/page`. If the URL already redirects to an internal URL, you must select **Clear selection** before you can enter an external URL.

1. Select a redirect type:

    - **Permanent redirect (301)** – Select this option when you know that your content is moving permanently and isn't reverting to its previous URL. Search engines assign the search engine optimization (SEO) value of the redirecting URL to the URL that's being redirected to and update their record to show the new URL.
    - **Temporary redirect (302)** – Select this option to redirect traffic without updating search engines. This approach is typically used if the content will soon revert to its previous URL.

1. When you're ready to implement the redirect, save and publish the URL.

## Additional resources

[Customize site navigation](customize-site-navigation.md)

[Add a new site page](add-new-page.md)

[Configure your domain name](configure-your-domain-name.md)

[Add languages to your site](add-languages-to-site.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
