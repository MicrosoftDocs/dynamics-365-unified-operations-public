---
# required metadata

title: Update an environment
description: This topic explains how to update an environment on the New Infrastructure Stack
author: manado
manager: AnnBe
ms.date: 07/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 24211
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Update an environment

[!include [banner](../includes/banner.md)]

This topic walks through the process of applying updates to a Dynamics 365 Finance and Operations environment deployed on the [New Infrastructure Stack](https://go.microsoft.com/fwlink/?linkid=2044792&amp;clcid=0x409).

> [!IMPORTANT]

> With the next gen infrastructure, updates are applied differently from the current flow. **Whatever is supplied in the package is applied to the environment and it OVERWRITES what is already present in the environment**. This means that you **need** to create a single deployable package that contains all customizations and ISV solutions from your build environment. If there is a difference in the list of models between what is on the environment and what is in the package, you will be warned before applying the update. For details about creating a single package, visit the [Manage runtime packages](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/dev-tools/manage-runtime-packages) topic.

> [!NOTE]

> The [New Infrastructure Stack](https://go.microsoft.com/fwlink/?linkid=2044792&amp;clcid=0x409) supports only Version 8.1 and above.

# Supported package types

Since environments deployed on the [New Infrastructure Stack](https://go.microsoft.com/fwlink/?linkid=2044792&amp;clcid=0x409) will be on 8.1 and above, we support the below package types:

- **AOT deployable package**  – A deployable package that is generated from application metadata and source code. This deployable package is created in a **build** environment.
- **Binary update package**  – A deployable package that contains dynamic-link libraries (DLLs) and other binaries and metadata that the platform and application depend on. This is a package released by Microsoft.

# Dev Application Lifecycle Management (ALM) flow

To apply code customizations to your Sandbox and Production environments, you need to create a deployable code package from your build environment. For details on how to do this, visit the [Create deployable package](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/create-apply-deployable-package) topic.

# Microsoft updates

To get access to Microsoft Updates navigate to the environment details page for your environment and you will see a single tile that shows a cumulative binary update of all the application and platform fixes. To apply this update, select the package and Save Package to the asset library. This will save the Microsoft update to the project asset library.

# Applying code customizations and Microsoft updates

## Tier 1 Sandbox/Develop and Test/Demo/Build environments

To apply updates to a Tier 1 Sandbox/Develop and Test/Demo/Build environment deployed through Lifecycle Services, follow the steps in the [Apply Updates](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/apply-deployable-package-system) document.

## Tier 2 and above Standard Acceptance Test/Sandbox environments

> [!IMPORTANT]

> Applying packages causes system downtime. All relevant services will be stopped, and you won&#39;t be able to use your environments while the package is being applied.

Before you begin, verify that the deployable package has been uploaded to the Project Asset library in LCS and that validations have succeeded.

> [!NOTE]

> Only packages that have been successfully validated can be applied to an environment.

Once you have this package in the Project Asset Library, follow the below steps to update your environment:

1. 1)Open the **Environment details** view for the environment where you want to apply the package.
2. 2)Click **Maintain \&gt; Apply updates** to apply an update.
3. 3)Select the package to apply. Use the filter at the top to find your package. You will see Application and platform binary package and Application deployable package that have passed validation from the asset library showing up in the list.
4. 4)Click **Apply**.
5. 5)The status in the upper-right corner of the Environment details view changes from **Queued** to **Servicing** and then on completion to **Deployed**.
6. 6)On completion, the environment History accessible from **History \&gt; Environment** changes on the environment details page is updated to show the completed package deployed.
7. 7)You can also download the **logs** from the environment history page.

> [!IMPORTANT]

> For environments deployed in the New Infrastructure Stack, if servicing fails the environment is automatically rolled back. To understand why the operation failed, you can download the logs from the environment history page as mentioned in the steps above.

## Production environments

Applying updates to production has not been enabled yet. To improve the reliability of updates being applied to production, we have made a change in the process. When this flow is enabled, you will have the option to move either the latest copy or a designated snapshot of the sandbox environment to production. There will be no way to granularly select an update and move that to production. This will guarantee a more reliable experience as the update will not be applied again; rather an image of the sandbox will be promoted to production.

