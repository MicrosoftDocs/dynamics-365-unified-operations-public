---
title: Domains in Dynamics 365 Commerce
description: Learn how domains are handled in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 02/13/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2017-06-20
ms.custom: 
  - bap-template
---

# Domains in Dynamics 365 Commerce

[!include [banner](../includes/banner.md)]

This article describes how Microsoft Dynamics 365 Commerce handles domains.

Domains are web addresses you use to navigate to Dynamics 365 Commerce sites in a web browser. You control management of your domain with a chosen Domain Name Server (DNS) provider. Dynamics 365 Commerce site builder references domains to coordinate how a site is accessed when published. This article reviews how domains are handled and referenced throughout the lifecycle of the Commerce site development and launch.

> [!NOTE]
> As of May 6, 2022, all environments created in Dynamics 365 Commerce are provisioned with the `.dynamics365commerce.ms` domain, replacing the earlier pattern of `.commerce.dynamics.com`. Existing environments provisioned with the `.commerce.dynamics.com` domain continue to work.

## Provisioning and supported host names

When you provision an e-commerce environment in [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/), enter domains associated with the deployed Commerce environment in the **Supported host names** box on the e-commerce provisioning screen. These domains are the customer-facing Domain Name Server (DNS) names where you host e-commerce websites. Entering a domain at this stage doesn't start diverting traffic for the domain to Dynamics 365 Commerce. You route traffic for a domain to the Commerce endpoint only when you update the DNS CNAME record to use the Commerce endpoint with the domain.

> [!NOTE]
> You can enter multiple domains in the LCS **Supported host names** box by separating them with semicolons. The first domain you enter defaults to the URL generated for your environment. You can access any subsequent domains by using the `?domain=` URL string attribute. For more information, see [Domains in site builder](#domains-in-site-builder).

The following illustration shows the LCS e-commerce provisioning screen with the **Supported host names** box highlighted. 

:::image type="content" source="../media/Domains_ProvisioningeCommerceScreen_publish.png" alt-text="Screenshot of the LCS e-commerce provisioning screen with the Supported host names box highlighted.":::

### Add supported host names

You can add more supported host names to an environment in LCS after the initial environment provisioning. 

To add a new domain to the supported host names list in LCS, follow these steps:

1. Navigate to your environment in LCS.
1. Go to **Environment Features \> Commerce**, and then select **Manage**.
1. Select **e-Commerce**.
1. Select **Add custom domain**.
1. In the **Add supported custom domain** dialog box, for **New custom domain**, enter the full domain name (for example, `www.contoso.com`).
1. Select **Add** to add the domain to the supported host names list.

You can view the list of supported host names in LCS under **e-Commerce \> System Information \> Supported custom domains**.

## Commerce-generated URLs

When you provision a Dynamics 365 Commerce e-commerce environment, Commerce generates a URL that is the working address for the environment. The e-commerce site link shown in LCS after the environment is provisioned references this URL. A Commerce-generated URL is in the format `https://<e-commerce tenant name>.dynamics365commerce.ms`, where the e-commerce tenant name is the name entered in LCS for the Commerce environment.

You can use production site host names in a sandbox environment as well. This option is ideal when you're copying a site from a sandbox environment to production.

## Site setup

After provisioning your e-commerce environment, set up your site in Commerce site builder to associate your site with the working URL.

When you first set up a site in site builder, the **Setup your Site** dialog box appears.

The following illustration shows the **Setup your Site** dialog box for a site named "default" when you access the site for the first time in site builder.

:::image type="content" source="../media/Domains_SetupyoursiteScreen.png" alt-text="Screenshot of the Setup your Site dialog box in Commerce site builder.":::

In the **Select a domain** box, you can associate one of the supported host names that LCS provides for your site to your site in site builder.

You can leave the **Path** box blank, or add another path string that appears in your working URL. If you leave the **Path** box blank, you associate the base Commerce-generated URL with the site you're setting up in site builder. Paths must be unique for each site and domain pair. Within the site and domain you select, only one site in the environment can use the blank path or be associated with a unique path string. Any string you add to the **Path** field during site setup becomes a subpath of the base Commerce-generated URL used to access the site in a web browser.

> [!NOTE]
> The path is also known as the **Match path** when adding a channel in the **Site Settings \> Channels** configuration section of site builder.

For example, if you have a site in site builder called "fabrikam" in an e-commerce tenant named "xyz," and if you set up the site with a blank path, you access the published site content in a web browser by going directly to the base Commerce-generated URL:

`https://xyz.dynamics365commerce.ms`

Alternately, if you add a path of "fabrikam" during this same site's setup, you access the published site content in a web browser by using the following URL:

`https://xyz.dynamics365commerce.ms/fabrikam`

## Pages and URLs

After you set up your site with a path, all URLs associated with pages in site builder build on the working URL (the Commerce-generated URL, or the Commerce-generated URL plus the path) for the site. When you create a new URL in site builder (**URLS /> +New**), you associate that URL with the selected page by selecting a page from the list in the **New URL** dialog box and entering the URL path for that page. You append the URL path value to the site's working URL to access the page. The URL path appears as `./<URL path>` in the URL list of the **URLs** page in site builder.

The following illustration shows the **New URL** dialog box in site builder with an example URL path highlighted. 

:::image type="content" source="../media/Domains_PageSetup2a.png" alt-text="Screenshot of the New URL dialog box in site builder with an example URL path highlighted.":::

The following illustration shows the **URLs** page in site builder with an example URL highlighted in the list.

:::image type="content" source="../media/Domains_URLsInSiteBuilder2a.png" alt-text="Screenshot of the URLs page in site builder with an example URL highlighted in the list.":::

## Domains in site builder

You can associate supported host name values as a domain when setting up a site. When you select a supported host name value as the domain, you see the chosen domain referenced throughout site builder. This domain is only a reference within the Commerce environment. Live traffic for that domain isn't yet forwarded to Dynamics 365 Commerce.

When you work with sites in site builder, if you set up two sites with two different domains, you can append the `?domain=` attribute to your working URL to access the published site content in a browser.

> [!NOTE]
> The `?domain=` query parameter is also required when testing robots.txt files from internal Commerce-generated domains. For more information, see [How robots.txt works with different domain types](../manage-robots-txt-files.md#how-robotstxt-works-with-different-domain-types).

For example, you provision environment "xyz" and create and associate two sites in site builder: one with the domain `www.fabrikam.com` and the other with the domain `www.constoso.com`. You set up each site using a blank path. You can then access these two sites in a web browser as follows by using the `?domain=` attribute:
- `https://xyz.dynamics365commerce.ms?domain=www.fabrikam.com`
- `https://xyz.dynamics365commerce.ms?domain=www.contoso.com`

When you don't give a domain query string in an environment with multiple domains provided, Commerce uses the first domain you provided. For example, if you provide the path "fabrikam" first during site setup, you can use the URL `https://xyz.dynamics365commerce.ms` to access the published site content site for `www.fabrikam.com`.

You can also add custom domains. To do so, on the environment Commerce management page for the project, under the **e-Commerce** subheading, select **+ Add custom domain**. The slider shows the existing custom domains and provides the option to add a new custom domain.

## Update which Commerce Scale Unit your environment uses

Select the Commerce Scale Unit (CSU) when you create an environment. You can change the CSU instance that your environment uses. This self-service functionality helps you maintain your architecture and reduces the need to contact support. To update your CSU instance, go to your environment's Commerce management page for the project, and then select **Update scale unit**. Use the **New commerce scale unit** slider to select a new CSU instance from the list of CSUs available for your environment.

## Traffic forwarding in production

You can simulate multiple domains by using domain query string parameters on the `commerce.dynamics.com` endpoint itself. But when you need to go live in production, you must forward the traffic for your custom domain to the `<e-commerce tenant name>.dynamics365commerce.ms` endpoint.

> [!IMPORTANT]
> Setting up the traffic forwarding process requires at least seven days lead time. Microsoft recommends that you start the process at least 14 days before the go-live date. 

The `<e-commerce tenant name>.dynamics365commerce.ms` endpoint doesn't support custom domain Transport Layer Security/Secure Sockets Layer (TLS/SSL), so you must set up custom domains by using a front door service or content delivery network (CDN). 

To set up custom domains by using a front door service or CDN, you have two options:

- Set up a front door service like Azure Front Door to handle front-end traffic and connect to your Commerce environment. This option provides greater control over domain and certificate management and more granular security policies.

- Use the Commerce-supplied Azure Front Door instance. This option requires coordinating action with the Dynamics 365 Commerce team for verifying domains and obtaining TLS/SSL certificates for your production domain.

> [!NOTE]
> If you're using an external CDN or front door service, ensure that the request lands at the Commerce platform with the Commerce-provided hostname, but with the X-Forwarded-Host (XFH) header \<custom-domain\>. For example, if your Commerce endpoint is `xyz.dynamics365commerce.ms` and the custom domain is `www.fabrikam.com`, the host header of the forwarded request should be `xyz.dynamics365commerce.ms` and the XFH header should be `www.fabrikam.com`.

For information about how to set up a CDN service directly, see [Add support for a content delivery network (CDN)](../add-cdn-support.md).

To use the Commerce-supplied Azure Front Door instance, you must create a service request for CDN setup assistance from the Commerce onboarding team. 

- You must provide your company name, the production domain, environment ID, and production e-commerce tenant name. 
- You must confirm if this service request is for an existing domain (used for a currently active site) or a new domain. 
- The domain verification and TLS/SSL certificate are obtained through DNS TXT record verification. This process involves multiple sequential steps and it has a seven working day service level agreement (SLA) for a domain to go live. The process consists of the following steps:
  1. You create a support ticket requesting the domain setup.
  1. Microsoft support contacts you with the DNS record to verify the domain.
  1. You create the DNS record in your DNS provider's service.
  1. Microsoft support confirms that the DNS verification is complete.
  1. Microsoft support provides you with the DNS CNAME record to be created for the live traffic switchover.
  1. You create the DNS CNAME for the custom domain pointing to the Commerce-provided front door endpoint. 
- For a new domain, you can update the CNAME to a Commerce-provided front door endpoint immediately. Traffic routes through the Commerce front door endpoint after the CNAME record is updated.
- For a domain that serves an existing website, you must verify that the new domain is set up correctly. Execute the CNAME change to point the custom domain to the Commerce front door endpoint at the scheduled cutover time.
- Existing traffic to the custom domain isn't impacted until the CNAME change is completed.

To create a service request in LCS, within your environment go to **Support \> Support issues** and select **Submit an incident**.

> [!NOTE]
> Custom domains with TLS/SSL are only supported on production environments. For nonproduction environments such as sandbox and user acceptance testing (UAT), use the Commerce-generated URL to access published content in a web browser.

## TLS/SSL certificate process

When you file a service request, the Commerce team coordinates the following steps with you.

For new domains:
- The Commerce team sets up the Azure Front Door instance (Commerce-hosted).
- The Commerce team then provides the CNAME record to point your custom domain.
- After you update the CNAME record, the Commerce-hosted Azure Front Door instance can verify the domain ownership and get the SSL certificate.

For existing or active domains:
- The Commerce team instructs you to add an `afdverify.<custom-domain>` CNAME record to your domain DNS provider.
- When you complete the CNAME record, the Commerce team adds the domain to the Azure Front Door instance and provides more DNS TXT records to add to the DNS for the domain.
- After you add the TXT records, the Commerce team completes the Azure Front Door updates for the domain to set up the SSL certificate.

## Apex domains

The Commerce-supplied Azure Front Door instance doesn't support apex domains (root domains that don't contain subdomains). Apex domains require an IP address to resolve, and the Commerce Azure Front Door instance only exists with virtual endpoints. To use an apex domain, you have the following options:

- **Option 1** - Use your DNS provider to redirect the apex domain to a "www" domain. For example, fabrikam.com redirects to `www.fabrikam.com` where `www.fabrikam.com` is the CNAME record that points to the Commerce-hosted Azure Front Door instance.

- **Option 2** - If your DNS provider supports ALIAS records, you can point the apex domain to the Azure Front Door endpoint, which ensures that the IP change by the endpoint is reflected.
  
- **Option 3** - If your DNS provider doesn't support ALIAS records, then you must change your DNS provider to Azure DNS and host both Azure DNS and the Azure Front Door instance yourself.

> [!NOTE]
> If you're using Azure Front Door, you must also set up an Azure DNS in the same subscription. The apex domain hosted on Azure DNS can point to your Azure Front Door as an alias record. This method is the only workaround, because apex domains must always point to an IP address.
  
If you have any questions about apex domains, contact [Microsoft Support](https://support.microsoft.com/).

## Additional resources

[Deploy a new e-commerce tenant](../deploy-ecommerce-site.md)

[Set up an online store channel](../channel-setup-online.md)

[Create an e-commerce site](../create-ecommerce-site.md)

[Associate a Dynamics 365 Commerce site with an online channel](../associate-site-online-store.md)

[Manage robots.txt files](../manage-robots-txt-files.md)

[Upload URL redirects in bulk](upload-bulk-redirects.md)

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Set up custom pages for user logins](../custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](../configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](../add-cdn-support.md)

[Enable location-based store detection](../enable-store-detection.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]




