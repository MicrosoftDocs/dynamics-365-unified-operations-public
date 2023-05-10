---
# required metadata

title: Deploy a new environment
description: This article explains how to deploy a new environment using the self-service deployment experience.
author: rashmansur
ms.date: 05/10/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.custom: 24211
ms.search.region: Global
# ms.search.industry: 
ms.author: rashmim
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Deploy a new environment

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This article walks through the process of deploying sandbox (Tier 2 and above) and production environments with the [self-service deployment](infrastructure-stack.md) experience. Refer to the following procedure to deploy these environments.

1. Select **Configure** on the project dashboard page.
2. Select the **Application** and **Platform** version for the environment that you want to deploy. 
3. Provide a **unique name** for the environment.

> [!NOTE]
> For US Government projects in the Government Community Cloud (GCC), environment names are limited to 15 characters for sandboxes and 23 characters for production due to the total length of the resulting URL.

4. Select the **region** where you want this environment to be deployed. 

> [!NOTE]
> In May 2023 a change was introduced in the selection of available Azure Regions for finance and operations apps. For more information about which regions are available and what you need to consider when making a selection see [Dynamics 365 finance and operations apps across geographies](deployment-options-geo.md).

6. Choose whether you want to load **demo data** in your environment or if you want an **empty database**.
7. Select the **BPM library** to set as the Getting started library in the product.
8. Select from a list of available **AOT packages** (customization packages) on the Software Deployable tabs in the Asset Library if you want to apply customizations. Only packages generated from a build environment on version 8.1 and above should be selected. Applying a package from an incompatible version has an adverse effect on the environment.
9. Specify **two user email addresses** to receive **notifications** related to this environment. These users are in addition to the users who are already on the project team (such as an ISV or a partner).
10. Select the **email address** of the **user** to set as the **system administrator** in the product.
11. After you validate the configurations, click **Submit** to trigger the deployment.
12. If you plan to use channels, you must also [Initialize Retail Cloud Scale Unit](initialize-retail-channels.md).

The environment deployment starts immediately and could take anywhere between **30 minutes to 1 hour** to complete for a sandbox environment and **1-2 hours** for a production environment. 

To closely monitor the deployment progress, you can view the **Environment details** page. The environment state should change to either **Deploying** or **Deployed/Failed**.

If the deployment **succeeds**, the environment state is **Deployed**, and the user set as the environment administrator is able to sign in to the environment.

If the deployment **fails**, then create a Microsoft [support ticket](../lifecycle-services/lcs-support.md) and provide the **Last Activity ID** (available under **Manage environment** on the **Environment details** page) in the support ticket.

## Delete an environment

You can delete an environment that is in the deployed state directly through the environment details page. To delete an environment, go to the environment details page and click the  **Delete** button on the action bar. A confirmation dialog box displays asking you to enter the name of the environment that you want to delete. After you enter the environment name and select **Yes**, the deletion operation will start. When the deletion operation is complete, the **Configure** button for this environment is enabled on the project dashboard if you want to redeploy the environment. 

> [!NOTE]
> To redeploy an environment, you will need to delete the environment and then deploy it again using the steps listed above. 

> [!IMPORTANT]
> For existing customers using channel functionality in the cloud, to ensure continued and uninterrupted support for your business, we require that you [Initialize Retail Cloud Scale Unit](initialize-retail-channels.md) no later than January 31, 2020. There is no action required for customers who exclusively use Store Scale Unit. Contact your Microsoft FastTrack Solution Architect if you require an extension.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
