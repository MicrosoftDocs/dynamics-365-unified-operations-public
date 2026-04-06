---
title: Deploy a new environment
description: Learn how to deploy a new environment using the self-service deployment experience, including how to delete an environment.
author: rashmansur
ms.author: rashmim
ms.topic: install-set-up-deploy
ms.custom: 
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-12-31
ms.search.form: 
ms.dyn365.ops.version: 8.1.1
---

# Deploy a new environment

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This article walks through the process of deploying sandbox (Tier 2 and above) and production environments by using the [self-service deployment](infrastructure-stack.md) experience. Use the following procedure to deploy these environments.

1. Select **Configure** on the project dashboard page.
1. Select the **Application** and **Platform** version for the environment that you want to deploy. 
1. Enter a **unique name** for the environment.

    > [!NOTE]
    > `sandbox` and `trial` are reserved and can't be used for your environment name. Additionally, environment names are limited to 20 characters due to the total length of the resulting URL.

1. Select the **region** where you want to deploy this environment. 

    > [!NOTE]
    > Starting July 2023, you can deploy Microsoft managed finance and operations environments to any region from any Lifecycle Services instance (apart from US GCC and 21Vianet in China). Earlier, you could only deploy to regions that were data resident to the Lifecycle Services endpoint itself. For example, France Lifecycle Services only allowed deployment in France geo. For more information about which regions are available and what you must consider when you make a selection, see [Available geographies for Dynamics 365 finance and operations apps](deployment-options-geo.md).

1. Select whether you want to load demo data in your environment or whether you want an empty database.
1. Select the BPM library to use as the Getting started library in the product.
1. If you want to apply customizations, select from a list of available AOT packages (customization packages) on the **Software Deployable** tabs in the Asset library. Select only packages that are generated from a build environment on version 8.1 and later. Applying a package from an incompatible version adversely affects the environment.
1. Specify **two** user email addresses that should receive notifications that are related to this environment. These users are in addition to the users who are already on the project team, such as an independent software vendor (ISV) or a partner.
1. Select the email address of the user to set as the system administrator in the product.
1. After you validate the configurations, select **Submit** to trigger the deployment.
1. If you plan to use channels, you must also [initialize Retail Cloud Scale Unit](initialize-retail-channels.md).

The environment deployment starts immediately and can take anywhere between **30 minutes to 1 hour** to complete for a sandbox environment and **1-2 hours** for a production environment. 

To closely monitor the deployment progress, you can view the **Environment details** page. The environment state changes to either **Deploying** or **Deployed/Failed**.

If the deployment **succeeds**, the environment state is **Deployed**, and the user set as the environment administrator can sign in to the environment.

If the deployment **fails**, create a Microsoft [support ticket](../lifecycle-services/lcs-support.md) and provide the **Last Activity ID** (available under **Manage environment** on the **Environment details** page) in the support ticket.

## Delete an environment

You can delete an environment that's in the deployed state directly through the environment details page. To delete an environment, go to the environment details page and select the **Delete** button on the action bar. A confirmation dialog box prompts you to enter the name of the environment that you want to delete. After you enter the environment name and select **Yes**, the deletion operation starts. When the deletion operation is complete, the **Configure** button for this environment is enabled on the project dashboard if you want to redeploy the environment. 

> [!NOTE]
> To redeploy an environment, you need to delete the environment and then deploy it again by using the preceding steps. 

> [!IMPORTANT]
> For existing customers using channel functionality in the cloud, to ensure continued and uninterrupted support for your business, [initialize Retail Cloud Scale Unit](initialize-retail-channels.md) no later than January 31, 2020. There's no action required for customers who exclusively use Store Scale Unit. Contact your Microsoft FastTrack Solution Architect if you require an extension.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
