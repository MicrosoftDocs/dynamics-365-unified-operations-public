---
# required metadata

title: Get started with e-commerce online extensibility development
description: This topic provides an overview of how to get started developing e-commerce customizations with the Microsoft Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
manager: annbe
ms.date: 11/06/2019
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
# Get started with e-commerce online extensibility development

[!include [banner](../includes/banner.md)]

This topic provides an overview of how to get started developing e-commerce customizations with the Microsoft Dynamics 365 Commerce online software development kit (SDK).

Below, you will find all the details to get started with e-commerce extensibility development. 

The Commerce online SDK allows development and debugging of e-commerce [modules](modules-overview.md), [data actions](data-actions.md), and [themes](theming.md). The SDK can be installed and used on any Windows 10 environment without the need for a deployed Commerce environment. However, it can also be useful to connect to a live cloud environment (for example, "Dev," "Test," "UAT," or "Prod") for deeper debugging and testing changes against a cloud environment without the need to deploy or destabilize the environment.

The typical process when extending the Commerce platform includes the following steps.

- Install the necessary development tools.
- Install the latest online SDK.
- Optionally [set up an Azure DevOps build pipeline for code sharing and build management](set-up-code-sharing-build-pipeline.md).
- Build and extend modules, data actions, and themes as needed.
- Test modules, data actions, and themes using mock data.
- Optionally test modifications against a cloud environment.
- Build a Commerce configuration package of all changes.
- Deploy a configuration package to a cloud environment.

## Architectural overview

Before starting Commerce extensibility development, it's recommended to have a good understanding of Commerce architecture. The [Dynamics 365 Commerce architecture overview](../commerce-architecture.md) and [E-commerce architectural overview](architectural-overview.md) topics are great places to get started. The [E-commerce components](ecommerce-components.md) topic also provides an overview of the main extensible e-commerce components including modules, data actions, and themes.

## Set up a local online SDK development environment

### Development system requirements

Before setting up a development environment, ensure that your environment meets the minimum requirements specified in [System requirements for a Dynamics 365 Commerce online extensibility environment](system-requirements.md).

### Install development tools and online SDK

Commerce development uses some free open sources tools including Node.js for the JavaScript runtime, Yarn for dependency management, and Visual Studio Code for source editing.  For detailed steps on installing each of these tools, see [Set up a development environment](setup-dev-environment.md). The topic also covers how to run a Node app to test and preview modules under development, as well the [CLI tools](cli-command-reference.md) used to create and clone a module.

## Develop against a cloud-hosted Commerce environment

The Commerce online SDK allows development and debugging of modules, data actions, and themes without the need for a deployed Commerce environment, which is the default behavior if you followed the above section to set up a development environment. There may be scenarios where you need to debug your live e-commerce web site or test configuration changes against a live [cloud environment](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/update-guide?toc=/dynamics365/commerce/toc.json#environments), including "Dev," "Test," "UAT," or "Prod" environments. This section covers how to configure your development environment against a cloud-hosted Commerce environment.

### Configure the SDK environment .env file

The online SDK includes a ".env" file in the root folder which has several environment variables to configure your development environment against a cloud environment. For details on each environment variable, see [Configure a development (.env) file](configure-env-file.md).  

### Configure against a cloud environment

The [Debug against a tier 1 Commerce development environment](debug-tier-1.md) topic provides details on how to configure the .env file to point to a cloud environment, and will guide you on setting the correct URLs for each variable in the .env file. 

There are two main scenarios you can set up. The first is to point to a cloud retail server, and the second is to point to a cloud e-commerce site.

#### Configure against a cloud-hosted Retail Server

A development environment can be configured to point to a cloud-hosted Retail Server to allow for debugging modules and data actions against live data. When the server is configured, all data action calls will go directly to that server, passing back real data to your development environment. This is a great way to see how a module will render.  Without this setup, you will need to use mock data to render your modules. For more information, see [Test modules with mock data](test-module-mock.md) and [Test data action with mocks](test-data-action-mocks.md).

The .env file contains a **MsDyn365Commerce_BASEURL** variable that needs to point to a cloud-based Retail Server URL. You will also need to point to a specific channel and channel operating unit number (OUN).

The following example shows an .env file set to point to a specific Retail Server, channel, and OUN. 

json
```
...
MSDyn365Commerce_BASEURL=https://e-comdevtestf1d01de665c744a7devret.cloud.retail.dynamics.com/
MSDyn365Commerce_CHANNELID=68719478279
MSDyn365Commerce_CATALOGID=0
MSDyn365Commerce_OUN=128
...
```
> [!NOTE]
> The catalog ID variable **MSDyn365Commerce_CATALOGID** must always be set to 0 since Commerce does not support multiple catalogs.

#### Configure against a cloud-hosted e-commerce site

A development environment can be further configured to point to a cloud-hosted e-commerce site to allow e-commerce pages created in Commerce site builder to be rendered in the local environment under the local Node.js JavaScript server. This is useful when testing changes to modules, data actions, and themes against live pages without affecting the live site. For example, you could test module view changes you have made locally for any e-commerce page without impacting the live e-commerce site or customers' views of it.

Commerce site pages are stored in the Commerce content management system (CMS) as JSON files which can be saved and used for mock files. These JSON files contain the breakdown of modules and their configuration values used to render pages. In this scenario, the local development environment renders the local modules, allowing for fast testing and iterating of your changes.

For information on testing modules using page mocks, including how to create a page mock from a live page using the `?item=nodeserviceproxy:true` query string parameter, see [Test modules by using page mocks](test-page-mock.md).

The following JSON example shows how to set up the **"MSDyn365_HOST"** variable to point to your Commerce environment.

```json
MSDyn365_HOST=www.fabrikam.com
MSDyn365Commerce_BASEURL=https://e-comdevtestf1d01de665c744a7devret.cloud.retail.dynamics.com/
MSDyn365Commerce_CHANNELID=68719478279
MSDyn365Commerce_CATALOGID=0
MSDyn365Commerce_OUN=128
…
```

For more information on setting up the **"MSDyn365_HOST"** variable to point to your Commerce environment, see [Debug against a tier 1 Commerce development environment](debug-tier-1.md).

## Change modules, data actions, and themes

Once a Commerce development environment is set up, you are ready to build custom [modules](create-new-module.md), [data actions](data-actions.md), and [themes](create-theme.md).

## Package creation and deployment

Once all of your changes are completed, you can build a zip file package and upload it to the LCS site to see all your changes in the cloud-hosted environment it was deployed to. For more inormation and instructions, see [Package configurations and deploy them to an online environment](package-deploy.md). 

## Additional resources

[Dynamics 365 Commerce architecture overview](../commerce-architecture.md)

[E-commerce architectural overview](architectural-overview.md)

[E-commerce components](ecommerce-components.md)

[Modules overview](modules-overview.md)

[Create a new module](create-new-module.md)

[Data actions](data-actions.md)

[set up an Azure DevOps build pipeline for code sharing and build management](set-up-code-sharing-build-pipeline.md)

[Configure a development (.env) file](configure-env-file.md)

[Test modules with mock data](test-module-mock.md)

[Test data action with mocks](test-data-action-mocks.md)

[test modules by using page mocks](test-page-mock.md)

[Debug against a tier 1 Commerce development environment](debug-tier-1.md)

[Create a new theme](create-theme.md)

[Package configurations and deploy them to an online environment](package-deploy.md)
