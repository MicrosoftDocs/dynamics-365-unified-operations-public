---
# required metadata

title: Configure an e-commerce development environment against a Commerce cloud environment
description: This topic describes how to set up an e-commerce online development environment to debug against a Commerce cloud development environment.
author: samjarawan
manager: annbe
ms.date: 11/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
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
This topic describes how to set up an e-commerce online development environment to debug against a Commerce cloud development environment.

## Overview

An e-commerce development environment can be configured to debug your live e-commerce website or test e-commerce configuration changes against various Commerce cloud environments including "Dev", "Test", "UAT," or "Prod" environments. This is useful in testing and debugging e-commerce modules and data actions against Retail Server extensions. Once configured, modules and data actions that leverage Retail Server APIs will call the Commerce cloud Retail Server directly, otherwise mock data will be needed.

## Install the Commerce online SDK

TO get started, you will need to install the Dynamics 365 Commerce online software development kit (SDK). The online SDK can be installed on any Windows 10 environment, including directly on a Commerce development virtual machine (VM). For setup instructions, see [Setup a development environment](setup-dev-environment.md).

## Debug against a Commerce cloud Retail Server

The online SDK leverages Node.js for the JavaScript runtime to render modules and e-commerce pages within a development environment. To configure a local development environment to point to a Commerce cloud environment, set the **MsDyn365Commerce_BASEURL** variable value in the .env file to the cloud environment Retail Server URL. For details about how to set up the .env file, see [Configure a development environment (.env) file](configure-env-file.md).  You will also need to specify the channel ID (**MSDyn365Commerce_CHANNELID**) and channel operating unit number (**MSDyn365Commerce_OUN**).

> [!NOTE]
> Catalogs are not supported in e-commerce, so the **MSDyn365Commerce_CATALOGID** variable will always be set to "0".

### Retrieve a Commerce development environment Retail Server URL

If you are debugging against a Commerce development environment, you can obtain the Retail Server URL by going to [Microsoft Lifecycle Services (LCS)](https://lcs.dynamics.com/) and selecting the project and the specific environment. Next, select **Login** at the top right and then select **Retail Server URL** as shown in the following illustration.

![LCS Retail Server URL](media/lcs-retail-server-url.png)

Selecting the **Retail Server URL** link should open a new tab with a URL similar to the following example URL: 

`https://e-comdevtestf1d01de665c744a7devret.cloud.retail.dynamics.com/Commerce`

Copy this URL, except for the last part ("Commerce"), into the .env file as the value for the **MsDyn365Commerce_BASEURL** variable. The **MSDyn365Commerce_CHANNELID** and **MSDyn365Commerce_OUN** variables should be configured to a desired online channel on the environment. For information on how to get these values, see [Configure a development environment (.env) file](configure-env-file.md). 

The following example shows configured variables using the URL referenced above.  

```json
MSDyn365Commerce_BASEURL=https://e-comdevtestf1d01de665c744a7devret.cloud.retail.dynamics.com/
MSDyn365Commerce_CHANNELID=68719478279
MSDyn365Commerce_CATALOGID=0
MSDyn365Commerce_OUN=128
...
```

Make sure to restart the Node.js server with the "yarn start" command so that the server picks up these new values once the .env file is saved. As you build modules and debug data actions, calls will now be made directly to the Retail Server specified in the .env file.

## Debug against a production e-commerce site

The Commerce online SDK allows you to point your development environment to a production e-commerce site to retrieve page definitions that can be rendered on the local Node.js environment.  This enables you to see how your local e-commerce changes (modules, data actions, and themes) will render prior to uploading the configuration package to a live environment.  You can then debug and make further changes and then see how they will look on a production page.

On a production site, Commerce site builder is used to build e-commerce pages that are stored as JSON files in the Commerce content management system. When you configure an e-commerce development environment **MSDyn365_HOST** variable in the .env file to point to a production e-commerce site, the JSON file will be retrieved and the local Node.js will do the rendering using the local online SDK and customizations on that local environment. This will allow you to test e-commerce changes with your live e-commerce site pages without deploying and potentially destabilizing your production environment.  

To support this scenario, configure the **MSDyn365_HOST** variable in the .env file to point to your e-Commerce domain name. When this step is complete, you can run the "yarn start" command and navigate to `https://localhost:4000` to view your online website rendered on the local Node.js server. When this happens, the live page will be pulled from the Dynamics 365 Commerce content management system. All data action Retail Server calls will be routed to the Tier 1 environment, as specified in the .env file.

The following example .env file shows the **MSDyn365_HOST** variable set to `www.fabrikam.com`. Note that this does not include the `https://` part of the URL.

```text
MSDyn365_HOST=www.fabrikam.com
MSDyn365Commerce_BASEURL=https://e-comdevtestf1d01de665c744a7devret.cloud.retail.dynamics.com/
MSDyn365Commerce_CHANNELID=68719478279
MSDyn365Commerce_CATALOGID=0
MSDyn365Commerce_OUN=128
…
```

> [!NOTE]
> If you have multiple e-Commerce sites configured for a single domain name, do not include the site name in the **MSDyn365_HOST** name provided in the .env file. Instead, use the site names when navigating the development environment in the local browser. For example, if you have two sites, `www.fabrikam.com/site1` and `www.fabrikam.com/site2`, configure the .env file as shown in the example above (`www.fabrikam.com`), and navigate to `https://localhost:4000/site1` or `https://localhost:4000/site2` respectively in the development environment.

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
When the Retail Server is configured with HTTP instead of HTTPS, you may receive "Mixed Content" errors when rendering e-Commerce content. Ensure the Retail Server is configured with an HTTPS end point to avoid this type of error.

### Retail calls are failing 404 error
404 errors may result if the channel ID and OUN are incorrect. To avoid those errors, ensure that the channel ID and OUN are correct in the **.env** file. See the [Configure a development environment (.env) file](configure-env-file.md) topic for details.


## Additional resources

[Setup a development environment](setup-dev-environment.md)

[Configure a development environment (.env) file](configure-env-file.md)
