---
title: Get started with e-commerce online extensibility development
description: This article provides an overview that will help you start to develop e-commerce customizations by using the Microsoft Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
ms.date: 11/20/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
ms.collection: get-started
ms.assetid: 
---
# Get started with e-commerce online extensibility development

[!include [banner](../includes/banner.md)]

This article provides an overview that will help you start to develop e-commerce customizations by using the Microsoft Dynamics 365 Commerce online software development kit (SDK).

You can use the Commerce online SDK to develop and debug e-commerce [modules](modules-overview.md), [data actions](data-actions.md), and [themes](theming.md). It can be installed and used in any Windows 10 environment, and doesn't require a deployed Commerce environment. However, it can also be useful to connect to a live cloud environment (for example, "Dev," "Test," "UAT," or "Prod"). In this way, you can do deeper debugging and test changes against a cloud environment without having to deploy or destabilize the environment.

The typical process when you extend the Commerce platform includes the following actions:

- Install the required development tools.
- Install the latest online SDK.
- Optional: [Set up an Azure DevOps build pipeline for code sharing and build management](set-up-code-sharing-build-pipeline.md).
- Build and extend modules, data actions, and themes as required.
- Test modules, data actions, and themes by using mock data.
- Optional: Test modifications against a cloud environment.
- Build a Commerce configuration package of all changes.
- Deploy the configuration package to a cloud environment.

## Architectural overview

Before you start Commerce extensibility development, we recommend that you learn about the Commerce architecture. The [Dynamics 365 Commerce architecture overview](../commerce-architecture.md) and [E-commerce architectural overview](architectural-overview.md) articles are great places to start. Additionally, the [E-commerce components](ecommerce-components.md) article provides an overview of the main extensible e-commerce components, such as modules, data actions, and themes.

## Set up a local online SDK development environment

### Development system requirements

Before you set up a development environment, make sure that your environment meets the minimum requirements that are specified in [System requirements for a Dynamics 365 Commerce online extensibility environment](system-requirements.md).

### Install development tools and the online SDK

Commerce development uses some free open-source tools, such as Node.js for the JavaScript runtime, Yarn for dependency management, and Visual Studio Code for source editing. For detailed information about how to install each of these tools, see [Set up a development environment](setup-dev-environment.md). That article also explains how to run a Node app to test and preview modules that are under development, and describes the [command-line interface (CLI) tools](cli-command-reference.md) that are used to create and clone a module.

## Develop against a cloud-hosted Commerce environment

The online SDK lets you develop and debug modules, data actions, and themes without having to use a deployed Commerce environment. There might be scenarios where you must debug your live e-commerce website or test configuration changes against a live [cloud environment](../../fin-ops-core/dev-itpro/migration-upgrade/update-guide.md?toc=%2fdynamics365%2fcommerce%2ftoc.json#environments), such as a "Dev," "Test," "UAT," or "Prod" environment. This section explains how to configure your development environment against a cloud-hosted Commerce environment.

### Configure the SDK environment .env file

The online SDK includes an .env file in the root folder. This file has several environment variables that you can use to configure your development environment against a cloud environment. For detailed information about each environment variable, see [Configure a development (.env) file](configure-env-file.md).

### Configure against a cloud environment

For detailed information about how to configure the .env file so that it points to a cloud environment, see [Debug against a tier 1 Commerce development environment](debug-tier-1.md). That article also provides guidance that will help you set the correct URL for each variable in the .env file.

There are two main scenarios that you can set up. In the first, you point the .env file to a cloud Retail Server, and in the second, you point it to a cloud e-commerce site.

#### Configure against a cloud-hosted Retail Server

By configuring a development environment so that it points to a cloud-hosted Retail Server, you can debug modules and data actions against live data. After the server is configured, all data action calls go directly to it and pass real data back to your development environment. This setup gives you a great way to see how a module will be rendered. Otherwise, you must use mock data to render your modules. For more information, see [Test modules with mock data](test-module-mock.md) and [Test data action with mocks](test-data-action-mocks.md).

The .env file contains a **MsDyn365Commerce_BASEURL** variable that must point to the URL of a cloud-based Retail Server. Additionally, you must point to a specific channel and channel operating unit number (OUN).

The following example shows an .env file that points to a specific Retail Server, channel, and OUN.

```json
...
MSDyn365Commerce_BASEURL=https://e-comdevtestf1d01de665c744a7devret.cloud.retail.dynamics.com/
MSDyn365Commerce_CHANNELID=68719478279
MSDyn365Commerce_CATALOGID=0
MSDyn365Commerce_OUN=128
...
```

> [!NOTE]
> The catalog ID variable, **MSDyn365Commerce_CATALOGID**, must always be set to **0** (zero), because Commerce doesn't support multiple catalogs.

#### Configure against a cloud-hosted e-commerce site

You can also configure a development environment so that it points to a cloud-hosted e-commerce site. In this way, e-commerce pages that are created in Commerce site builder can be rendered in the local environment under the local Node.js JavaScript server. This setup is useful because you can test changes to modules, data actions, and themes against live pages without affecting the live site. For example, you can test module view changes that you've made locally for any e-commerce page, without affecting the live e-commerce site or customer views of it.

Commerce site pages are stored in the Commerce content management system (CMS) as JavaScript Object Notation (JSON) files that can be saved and used as mock files. The JSON files contain the breakdown of modules and their configuration values. Those configuration values are used to render pages. In this scenario, the local development environment renders the local modules. Therefore, you can quickly test and iterate your changes.

For information about how to use page mocks to test modules, see [Test modules by using page mocks](test-page-mock.md). That article includes information about how to create a page mock from a live page by using the **?item=nodeserviceproxy:true** query string parameter.

The following example of a JSON file shows how to set up the **MSDyn365_HOST** variable so that it points to your Commerce environment.

```json
MSDyn365_HOST=www.fabrikam.com
MSDyn365Commerce_BASEURL=https://e-comdevtestf1d01de665c744a7devret.cloud.retail.dynamics.com/
MSDyn365Commerce_CHANNELID=68719478279
MSDyn365Commerce_CATALOGID=0
MSDyn365Commerce_OUN=128
...
```

For more information about how to set up the **MSDyn365_HOST** variable so that it points to your Commerce environment, see [Debug against a tier 1 Commerce development environment](debug-tier-1.md).

## Change modules, data actions, and themes

After you've set up a Commerce development environment, you're ready to build custom [modules](create-new-module.md), [data actions](data-actions.md), and [themes](create-theme.md).

## Package creation and deployment

After you've completed all your changes, you can build a zip file package and upload it to [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/). You can then see all your changes in the cloud-hosted environment that the package was deployed to. For more information and instructions, see [Package configurations and deploy them to an online environment](package-deploy.md).

## Additional resources

[System requirements for a Dynamics 365 Commerce online extensibility development environment](system-requirements.md)

[Set up a development environment](setup-dev-environment.md)

[Configure a development environment (.env) file](configure-env-file.md)

[Configure an e-commerce development environment against a Commerce cloud environment](debug-tier-1.md)

[Set up Azure DevOps code sharing and create a build pipeline](set-up-code-sharing-build-pipeline.md)

[Dynamics 365 Commerce architecture overview](../commerce-architecture.md)

[E-commerce architectural overview](architectural-overview.md)

[E-commerce components](ecommerce-components.md)

[Modules overview](modules-overview.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
