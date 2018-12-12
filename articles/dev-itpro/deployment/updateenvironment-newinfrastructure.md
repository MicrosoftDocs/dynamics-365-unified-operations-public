---
# required metadata

title: Update an environment
description: This topic explains how to update an environment on the modern infrastructure stack.
author: manado
manager: AnnBe
ms.date: 12/12/2018
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
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Update an environment

[!include [banner](../includes/banner.md)]

This topic walks through the process of applying updates to a Dynamics 365 for Finance and Operations environment deployed on the [modern infrastructure stack](infrastructure-stack.md).

> [!IMPORTANT]
> With the next generation infrastructure, updates are applied differently from the current flow. **Whatever is supplied in the package is applied to the environment and it OVERWRITES what is already present in the environment**. This means that you **must** create a single deployable package that contains all customizations and ISV solutions from your build environment. If there is a difference in the list of models between what is on the environment and what is in the package, you will be warned before applying the update. For details about creating a single package, see [Manage third-party models and runtime packages by using source control](../dev-tools/manage-runtime-packages.md).

# Supported package types
Because environments deployed on the [modern infrastructure stack](infrastructure-stack.md) will be on 8.1 and later, we support the following package types:

- **AOT deployable package** - A deployable package that is generated from application metadata and source code. This deployable package is created in a **build** environment.
- **Binary update package** - A deployable package that contains dynamic-link libraries (DLLs) and other binaries and metadata that the platform and application depend on. This is a package released by Microsoft.

# Development Application Lifecycle Management (ALM) flow
To apply code customizations to your sandbox and production environments, you need to create a deployable code package from your build environment. For details on how to do this, see [Create deployable packages of models](create-apply-deployable-package.md).

# Microsoft updates
To get access to Microsoft updates, go to the environment details page for your environment. You will see a **single tile** that shows a cumulative, binary update of all the application and platform fixes. To apply this update, select the package and select **Save Package** to save the Microsoft update to the project asset library.

# Apply updates

## Tier 1 Sandbox/Develop and Test/Demo/Build environments

To apply updates to a Tier 1 Sandbox/Develop and Test/Demo/Build environment deployed through Lifecycle Services (LCS), follow the steps in  [Apply updates to cloud environments](apply-deployable-package-system.md).

## Tier 2 and above Standard Acceptance Test/Sandbox environments

> [!IMPORTANT]
> Applying packages causes system downtime. All relevant services will be stopped, and you won't be able to use your environments while the package is being applied.

Before you begin, verify that the deployable package has been uploaded to the project asset library in LCS and that validations have succeeded.

After you have this package in the project asset library, use the following steps to update your environment:

1. Open the **Environment details** view for the environment where you want to apply the package.
2. Click **Maintain > Apply updates** to apply an update.
3. Select the package to apply. Use the filter at the top to find your package. You will see application and platform binary packages and application deployable packages that have passed validation from the asset library in the list.
4. Click **Apply**.
5. The status in the upper-right corner of the **Environment details** view changes from **Queued** to **Servicing**, and then after completion it changes to **Deployed**.
6. After completion, the environment history accessible from **History > Environment** changes on the **Environment details** page is updated to show the completed package deployed.
7. You can also download the logs from the environment history page.

> [!IMPORTANT]
> For environments deployed in the modern infrastructure stack, if servicing fails, the environment is automatically rolled back. To understand why the operation failed, you can download the logs from the environment history page as mentioned in the steps above.

## Production environments
Applying updates to production has not been enabled yet. To improve the reliability of updates being applied to production, when this flow is enabled you have the option to move either the latest copy or a designated snapshot of the sandbox environment to production. There is no way to select an update and move that to production. This ensures a more reliable experience as the update will not be applied again; rather an image of the sandbox will be promoted to production.
