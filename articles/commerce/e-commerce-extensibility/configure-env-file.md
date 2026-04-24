---
title: Configure a development environment (.env) file
description: Learn how to configure the development environment (.env) file used in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom:
  - bap-template
  - sfi-image-nochange
---
# Configure a development environment (.env) file

[!include [banner](../includes/banner.md)]

This article describes how to configure the .env file for the development environment in Microsoft Dynamics 365 Commerce.

The Dynamics 365 Commerce online software development kit (SDK) includes a .env file. This file is a simple configuration text file. It defines a set of variables that a Node app uses in the development environment.

## Default .env file

The default .env file that the online SDK provides resembles the following example.

```dos
### Environment File ##################################################################
# This is a simple configuration 
# Online documentation for this file is available at 
# https://learn.microsoft.com/dynamics365/commerce/e-commerce-extensibility/configure-env-file
########################################################################################

# MSDyn365_APP_TYPE variable is required. It can be set only to the value partner.

MSDyn365_APP_TYPE=partner

# PORT variable is required. It defines the port number that is used to preview your Node 
#   application when the Node server is started by using the yarn start command. The default value is 4000

PORT=4000

# MSDyn365_HOST variable defines the domain name of your customer-facing e-Commerce site. 
#   When this variable is set, if the URL https://localhost:4000/ is opened in a development environment, 
#   your e-Commerce site will be rendered locally. If your site is protected through Microsoft Entra ID 
#   (Microsoft Entra ID) credentials, a prompt for a user name and password will appear.

MSDyn365_HOST=

# MSDyn365Commerce_BASEURL variable defines the URL of the Microsoft Dynamics 365 Retail Server. 
#   When this variable is set, local development and testing can be done against Dynamics 365 Retail Server
#   application programming interfaces (APIs). If you set this variable, you must also set the 
#   MSDyn365Commerce_CHANNELID, MSDyn365Commerce_OUN, and MSDyn365Commerce_CATALOGID variables.
# MSDyn365Commerce_OUN variable defines the operating unit number for the channel.
# MSDyn365Commerce_CATALOGID variable defines the catalog ID for the online store that you're connecting to. 
#   Currently, only the value 0 (zero) is supported.
# MSDyn365Commerce_CHANNELID variable defines the online channel that you're connecting to.

MSDyn365Commerce_BASEURL=
MSDyn365Commerce_CHANNELID=
MSDyn365Commerce_CATALOGID=
MSDyn365Commerce_OUN=

# MSDyn365Commerce_BASEIMAGEURL variable defines the URL for a website's image assets. 
#   The URL follows a pattern and must be manually generated. For more information, 
#   see online product documentation.

MSDyn365Commerce_BASEIMAGEURL=

```

Two of the variables in the .env file, **MSDyn365\_APP\_TYPE** and **PORT**, are required and have preset values. All the other variables are optional. The optional variables enable your development environment to get data from live environments. The local development Node server renders this data.

The following sections describe the variables in the .env file.

## MSDyn365\_APP\_TYPE

The **MSDyn365\_APP\_TYPE** variable is required. Set it only to the value **partner**.

## PORT

The **PORT** variable is required. It defines the port number that you use to preview your Node application when the Node server starts by using the **yarn start** command. The default value is **4000**.

The following example shows the syntax for this variable.

```text
PORT=4000
```

An example of a development environment URL that includes the port number is:

`https://localhost:4000/version`

## MSDyn365\_HOST

The **MSDyn365\_HOST** variable defines the domain name of your customer-facing e-Commerce site. When you set this variable and open the URL `https://localhost:4000/` in a development environment, your e-Commerce site renders locally. If Microsoft Entra credentials protect your site, a prompt for a user name and password appears.

The following example shows the syntax for this variable.

```text
MSDyn365_HOST=demo.fabrikam.com
```

## MSDyn365Commerce_BASEURL

The **MSDyn365Commerce\_BASEURL** variable defines the URL of the Microsoft Dynamics 365 Commerce Scale Unit. When you set this variable, you can perform local development and testing against application programming interfaces (APIs). If you set this variable, you must also set the **MSDyn365Commerce\_CHANNELID**, **MSDyn365Commerce\_OUN**, and **MSDyn365Commerce\_CATALOGID** variables.

The following example shows the syntax for this variable.

```text
MSDyn365Commerce_BASEURL=https://fabrikamb1de06d29165320bret.cloud.retail.dynamics.com/
```

## MSDyn365Commerce\_OUN

The **MSDyn365Commerce\_OUN** variable sets the operating unit number for the channel.

To find the channel operating unit number, follow these steps:

1. Go to the Commerce website.
1. In the search field at the top of the page, enter **Online channels**, and then select the channel to use. You should see an **Operating unit number** column, as shown in the following illustration.

    :::image type="content" source="media/operating-unit-number.png" alt-text="Screenshot of the operating unit number column on the Dynamics 365 Commerce website.":::

The following example shows the syntax for this variable.

```text
MSDyn365Commerce_OUN=128
```

## MSDyn365Commerce\_CATALOGID

The **MSDyn365Commerce\_CATALOGID** variable sets the catalog ID for the online store that you're connecting to. Currently, only the value **0** (zero) is supported.

## MSDyn365Commerce\_CHANNELID

Use the **MSDyn365Commerce\_CHANNELID** variable to specify the online channel that you want to connect to.

To find the channel ID, follow these steps:

1. Go to the Dynamics 365 Commerce website.
1. In the search field at the top of the page, enter **Online channels**, and then select the channel to use.
1. On the Action Pane, on the **Options** tab, in the **Page options** group, select **Record Info**.
1. In the **Record information** dialog box, the value of the **Record-ID** field is the channel ID. Copy this value.

    :::image type="content" source="media/channel-id.png" alt-text="Screenshot of the Record-ID field on the Dynamics 365 Retail website.":::

The following example shows the syntax for this variable.

```text
MSDyn365Commerce_CHANNELID=68719478279
```

## MSDyn365Commerce_BASEIMAGEURL

The **MSDyn365Commerce_BASEIMAGEURL** variable sets the URL for a website's image assets. The URL follows a pattern and you must create it manually. Use one of the following formats:

- For evaluation sites, use the following format:

    `https://images-us-sb.cms.commerce.dynamics.com/cms/api/{CMS_TENANT_ID}/imageFileData/search?fileName=/`

- For production sites, use the following format:

    `https://img-prod-cms-mr-microsoft-com.akamaized.net/cms/api/{CMS_TENANT_ID}/imageFileData/search?fileName=/`

In both URLs, replace **{CMS_TENANT_ID}** with the content management system (CMS) tenant ID that the site assigns to you.

To get the CMS tenant ID in Dynamics 365 Commerce, follow these steps:

1. Under **Sites**, select your site.
1. In the navigation pane on the left, select **Assets**.
1. In the **Select type** field, select **Images**.
1. Select the first image.
1. In the property pane on the right, find the URL in the **Public URL** field. Your CMS tenant ID is the string between **/cms/api/** and **/imageFileData**. For example, in the URL **../cms/api/fabrikam/imageFileData/..**, the CMS tenant ID is **fabrikam**.

After you finish changing the .env file, restart the Node server by using the **yarn start** command.

## Additional resources

[Get started with e-commerce online extensibility development](sdk-getting-started.md)

[System requirements for a Dynamics 365 Commerce online extensibility development environment](system-requirements.md)

[Set up a development environment](setup-dev-environment.md)

[Configure an e-commerce development environment against a Commerce cloud environment](debug-tier-1.md)

[Set up Azure DevOps code sharing and create a build pipeline](set-up-code-sharing-build-pipeline.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
