---
# required metadata

title: Configure .env file
description: This topic describes how to configure a development environment .env file for Microsoft Dynamics 365 Commerce.
author: samjarawan
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
# Configure .env file

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to configure a development environment **.env** file for Microsoft Dynamics 365 Commerce.

## Overview

The **.env** file that comes as part of the Online SDK is a simple configuration text file that defines a set of variables used by the running node app within a development environment.

## Default .env file

The default **.env** file that comes with the Online SDK should look similar to below.

```
MSDyn365_APP_TYPE=partner
PORT=4000

### Partner Level Settings
# MSDyn365_HOST=<Partner Host Here>
# MSDyn365Commerce_BASEURL=<Retail Server Base URL Here>
# MSDyn365Commerce_CHANNELID=<Retail Server Channel ID Here>
# MSDyn365Commerce_CATALOGID=<Retail Server Catalog ID Here>
# MSDyn365Commerce_OUN=<Retail Server OUN Here>
# MSDyn365Commerce_BASEIMAGEURL=<Retail Server Base Image URL Here>
```
The two required variable are pre-set and the others are optional. The optional variables allow your development environment to target live environments to get data that is rendered within the local development Node server.

## MSDyn365_APP_TYPE
The **MSDyn365_APP_TYPE** variable is required and can only be set to **partner**.

## PORT
The **PORT** variable defined the port number used to preview your node application when the node server is started with the **yarn start** command.  The default is 4000.

Example ```PORT=4000```

An example URL on a development environment is **https://localhost:4000/version**

## MSDyn365_HOST
The **MSDyn365_HOST** variable is the domain name of your customer facing e-Commerce site.  When this variable is set, launching **https://localhost:4000/** on a development environment will locally render your e-Commerce site. If your site is protected with AAD credentials a username and password prompt will appear.

Example ```MSDyn365_HOST=demo.fabrikam.com```

## MSDyn365Commerce_BASEURL
The **MSDyn365Commerce_BASEURL** variable can be used to specify the Microsoft Dynamics 365 Retail server URL.  This will allow local development and testing against Retail APIs.  You will also need to set the **MSDyn365Commerce_CHANNELID**, **MSDyn365Commerce_OUN** and **MSDyn365Commerce_CATALOGID**.

Example ```MSDyn365Commerce_BASEURL=https://fabrikamb1de06d29165320bret.cloud.retail.dynamics.com```

## MSDyn365Commerce_OUN
The **MSDyn365Commerce_OUN** variable is used to set the Channel operating unit number. To find the channel ID, launch the Dynamics 365 Headquarters web page, type in "Online channels" in the top search bar and select the channel you want to use.  You should see a column for the "Operating unit number".  See below image for an example.


Example ```MSDyn365Commerce_OUN=128```

![Operating unit number](media/operating-unit-number.png)

## MSDyn365Commerce_CATALOGID
The **MSDyn365Commerce_CATALOGID** variable holds the catalog ID for the online store you are connecting to.  Only catalog ID 0 is currently supported

## MSDyn365Commerce_CHANNELID
The **MSDyn365Commerce_CHANNELID** variable represents the online channel you want to connect to. To find the channel ID, launch the Dynamics 365 Headquarters web page, type in "Online channels" in the top search bar and select the channel you want to use. Select the "Options" tab at the top followed by "Record Info" (under the "Page options" section), you can then get the "Record-ID" which is the Channel ID.


Example ```MSDyn365Commerce_CHANNELID=68719478279```

![Channel ID](media/channel-id.png)

## MSDyn365Commerce_BASEIMAGEURL
The **MSDyn365Commerce_BASEIMAGEURL** variable holds the URL for a site image assets.  The URL follows a pattern and must be manually generated.


For evaluations sites the URL is in the following format **https://images-us-sb.cms.commerce.dynamics.com/cms/api/{CMS_TENANT_ID}/imageFileData/search?fileName=/**


For production sites the URL is in the following format **https://img-prod-cms-mr-microsoft-com.akamaized.net/cms/api/{CMS_TENANT_ID}/imageFileData/search?fileName=/** for a product site.


The **{CMS_TENANT_ID}** must be replaced by the assigned tenant ID for your site.  

To obtain the correct tenant ID follow these steps:
1. Log in to the site management tool (authoring tools)
1. Select the site you are using (ex: “Fabrikam”)
1. Choose Assets from the menu on the left
1. From the Select type drop-down list, choose Images. 
1. Select the first image. 
1. Locate Public URL from the property inspector on the right. It has an URL in it
1. In the Public URL field, your CMS tenant identifier is between /cms/api/ and /imageFileData, make note of that. For example, in ../cms/api/fabrikam/imageFileData/.., fabrikam would be the CMS tenant identifier. 

See below image example to find the tenant ID

![Obtain teant ID](media/obtain-tenant-id.png)

Once changes are made to the **.env** file, restart the node server with the ```yarn start``` command.
