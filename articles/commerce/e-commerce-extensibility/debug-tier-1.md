---
# required metadata

title: Debug against a Tier 1 Commerce development environment
description: This topic describes how to set up an e-Commerce online development environment to debug against a Tier 1 Commerce development environment.
author: samjarawan
manager: annbe
ms.date: 10/06/2020
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
# Debug against a Tier 1 Commerce development environment

[!include [banner](../includes/banner.md)]

This topic describes how to set up an e-Commerce online development environment to debug against a Tier 1 Commerce development environment.

## Overview

Dynamics 365 Commerce Tier 1 environments are generally deployed for Commerce runtime (CRT) and point of sale (POS) extension development. These are standalone environments that do not include e-Commerce components due to the software as a service (SaaS) nature of the e-Commerce architecture.

There may be scenarios where you want to test calling extensions on a Tier 1 environment to allow extension debugging from e-Commerce components. This topic describes how to set up these kind of scenarios.

## Install the SDK

The Dynamics 365 Commerce software development kit (SDK) can be installed on any environment including the Tier 1 virtual machine (VM) itself. For setup instructions, see [Setup a development environment](setup-dev-environment.md).

## Configure the .env file

To hit the Tier 1 environment from the local node server on the e-Commerce development environment, set the **MsDyn365Commerce_BASEURL** variable value in the .env file to the Tier 1 Retail Server URL. For details about how to set up an .env file, see [Configure a development environment (.env) file](configure-env-file.md).

To obtain the Retail Server URL, go to the [Microsoft Lifecycle Services (LCS)](https://lcs.dynamics.com/) webpage and select the project and Tier 1 environment. Next, select **Login** at the top right and then select **Retail Server URL** as shown in the following illustration.

![LCS Retail Server URL](media/lcs-retail-server-url.png)

Selecting the **Retail Server URL** link should open a new tab with a URL similar to the following example URL: 

`https://e-comdevtestf1d01de665c744a7devret.cloud.retail.dynamics.com/Commerce`

Copy this URL, except for the last part "Commerce", into the .env file as the value for the **MsDyn365Commerce_BASEURL** variable. The remaining variables should be configured to a desired online channel on the environment. The following example shows configured variables using the URL that was noted above.  

```text
…
MSDyn365Commerce_BASEURL=https://e-comdevtestf1d01de665c744a7devret.cloud.retail.dynamics.com/
MSDyn365Commerce_CHANNELID=68719478279
MSDyn365Commerce_CATALOGID=0
MSDyn365Commerce_OUN=128
…
```
Make sure to restart the Node.js server with a "yarn start" command so that the server picks up these new values. As you build modules and debug data actions, calls will now be made directly to the Tier 1 Retail Server.

## Debug against a live e-Commerce environment

You may want to test the rendering of your live e-Commerce site pages within the local Node development environment while still calling the Tier 1 Retail Server. This is useful when you want to make changes to modules and themes, or to debug Retail Server extensions.

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
