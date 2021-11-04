---
# required metadata

title: Configure an e-commerce development environment against a Commerce cloud environment
description: This topic describes how to set up an e-commerce online development environment to debug against a Microsoft Dynamics 365 Commerce cloud development environment.
author: samjarawan
ms.date: 11/20/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Configure an e-commerce development environment against a Commerce cloud environment

[!include [banner](../includes/banner.md)]
This topic describes how to set up an e-commerce online development environment to debug against a Microsoft Dynamics 365 Commerce cloud development environment.

An e-commerce development environment can be configured to debug your live e-commerce website or to test e-commerce configuration changes against various Commerce cloud environments, such as "Dev," "Test," "UAT," or "Prod" environments. This environment is useful for testing and debugging e-commerce modules and data actions against Retail Server extensions. After it's configured, modules and data actions that use Retail Server APIs will directly call the Retail Server in the Commerce cloud environment. Otherwise, mock data will be required.

## Install the Commerce online SDK

To get started, you must install the Dynamics 365 Commerce online software development kit (SDK). The online SDK can be installed in any Windows 10 environment. It can even be installed directly on a Commerce development virtual machine (VM). For setup instructions, see [Setup a development environment](setup-dev-environment.md).

## Debug against a Retail Server in a Commerce cloud environment

The online SDK uses Node.js as the JavaScript runtime to render modules and e-commerce pages in a development environment. To configure a local development environment so that it points to a Commerce cloud environment, set the **MsDyn365Commerce_BASEURL** variable in the .env file to the URL of the Retail Server in the Commerce cloud environment. For information about how to set up the .env file, see [Configure a development environment (.env) file](configure-env-file.md). You must also specify the channel ID, **MSDyn365Commerce_CHANNELID**, and the channel operating unit number (OUN), **MSDyn365Commerce_OUN**.

> [!NOTE]
> Catalogs aren't supported in e-commerce. Therefore, the **MSDyn365Commerce_CATALOGID** variable will always be set to **0** (zero).

### Retrieve the URL of a Retail Server in a Commerce development environment

To get the Retail Server URL if you're debugging against a Commerce development environment, go to [Microsoft Lifecycle Services (LCS)](https://lcs.dynamics.com/), and select the project and the environment. Then, in the upper-right corner of the page, select **Login \> Retail Server URL**, as shown in the following illustration.

![Retail Server URL in LCS.](media/lcs-retail-server-url.png)

A new tab should be opened, and the URL should resemble the following example: 

`https://e-comdevtestf1d01de665c744a7devret.cloud.retail.dynamics.com/Commerce`

Copy this URL, except the last part (**Commerce**), into the .env file as the value of the **MsDyn365Commerce_BASEURL** variable. The **MSDyn365Commerce_CHANNELID** and **MSDyn365Commerce_OUN** variables should be set based on the desired online channel in the environment. For information about how to get these values, see [Configure a development environment (.env) file](configure-env-file.md).

The following example shows configured variables that use the previously mentioned example URL.

```json
MSDyn365Commerce_BASEURL=https://e-comdevtestf1d01de665c744a7devret.cloud.retail.dynamics.com/
MSDyn365Commerce_CHANNELID=68719478279
MSDyn365Commerce_CATALOGID=0
MSDyn365Commerce_OUN=128
...
```

To ensure that the server picks up these new values after the .env file is saved, you should restart the Node.js server by using the **yarn start** command. As you build modules and debug data actions, calls will now be made directly to the Retail Server that is specified in the .env file.

## Debug against a production e-commerce site

The Commerce online SDK lets you point your development environment to a production e-commerce site to retrieve page definitions that can be rendered in the local Node.js environment. Therefore, you can see how your local e-commerce changes (modules, data actions, and themes) will be rendered before you upload the configuration package to a live environment. You can then debug, make further changes, and see how those changes will look on a production page.

On a production site, Commerce site builder is used to build e-commerce pages that are stored as JavaScript Object Notation (JSON) files in the Commerce content management system. When you configure an e-commerce development environment's **MSDyn365_HOST** variable in the .env file so that it points to a production e-commerce site, the JSON file will be retrieved, and the local Node.js server will use the local online SDK and customizations in that local environment to do the rendering. Therefore, you can test e-commerce changes on your live e-commerce site pages without deploying and potentially destabilizing your production environment.

To support this scenario, configure the **MSDyn365_HOST** variable in the .env file to point to your e-commerce domain name. When this step is complete, you can run the "yarn start" command and navigate to `https://localhost:4000` to view your online website rendered on the local Node.js server. When this happens, the live page will be pulled from the Dynamics 365 Commerce content management system. All data action Retail Server calls will be routed to the Tier 1 environment, as specified in the .env file.

The following example .env file shows the **MSDyn365_HOST** variable set to `www.fabrikam.com`. Note that this does not include the `https://` part of the URL.

```text
MSDyn365_HOST=www.fabrikam.com
MSDyn365Commerce_BASEURL=https://e-comdevtestf1d01de665c744a7devret.cloud.retail.dynamics.com/
MSDyn365Commerce_CHANNELID=68719478279
MSDyn365Commerce_CATALOGID=0
MSDyn365Commerce_OUN=128
...
```

> [!NOTE]
> If you have multiple e-commerce sites configured for a single domain name, do not include the site name in the **MSDyn365_HOST** name provided in the .env file. Instead, use the site names when navigating the development environment in the local browser. For example, if you have two sites, `www.fabrikam.com/site1` and `www.fabrikam.com/site2`, configure the .env file as shown in the example above (`www.fabrikam.com`), and navigate to `https://localhost:4000/site1` or `https://localhost:4000/site2` respectively in the development environment.

### Debug a product details page

To open up a specific product details page (PDP), you can use the product ID to manually construct a URL using the pattern `https://localhost:4000/SITE_NAME/PRODUCT_NUMBER.p`. For example, `https://localhost:4000/site1/68719498121.p`, where "site1" is the site name and "68719498121" is the product ID. To obtain the product ID, you can navigate directly to a product on the live web site and copy the product ID from the URL, or in Commerce headquarters you can navigate to a released product and select the **Record info** link under the **Options** tab, and then copy the **Record-ID**.

## Troubleshooting

### CORS errors

You may get CORS (cross origin) errors when calling Retail Server APIs from your browser. These errors may surface in the browser network trace as **(failed) net::ERR_FAILED**. To fix these errors, change the **AllowedOrigins** setting in the Retail service web.config to allow the call to go through, as shown below.

```
...
<add key="AllowedOrigins" value="*" />
<!-- <add key="AllowedOrigins" value="https://usnconeboxax1pos.cloud.onebox.dynamics.com;https://usnconeboxax1ecom.cloud.onebox.dynamics.com" /> -->
...
```

### Mixed content errors
When the Retail Server is configured with HTTP instead of HTTPS, you may receive "Mixed Content" errors when rendering e-commerce content. Ensure the Retail Server is configured with an HTTPS end point to avoid this type of error.

### Retail calls are failing 404 error
404 errors may result if the channel ID and OUN are incorrect. To avoid those errors, ensure that the channel ID and OUN are correct in the **.env** file. See the [Configure a development environment (.env) file](configure-env-file.md) topic for details.

## Additional resources

[Get started with e-commerce online extensibility development](sdk-getting-started.md)

[System requirements for a Dynamics 365 Commerce online extensibility development environment](system-requirements.md)

[Set up a development environment](setup-dev-environment.md)

[Configure a development environment (.env) file](configure-env-file.md)

[Set up Azure DevOps code sharing and create a build pipeline](set-up-code-sharing-build-pipeline.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
