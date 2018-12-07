---
# required metadata

title: Deploy a new environment
description: This topic explains how to deploy a new environment with the new infrastructure.
author: manado
manager: AnnBe
ms.date: 12/07/2018
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
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Deploy a new environment

[!include [banner](../includes/banner.md)]

This topic walks through the process of deploying sandbox (Tier 2 and above) and production environments with the [new infrastructure stack](https://go.microsoft.com/fwlink/?linkid=2044792&amp;clcid=0x409). This is now a self-service operation and you can follow the below steps to deploy these environments.

1. Select **Configure** on the project dashboard page.
2. Select the **Application** and **Platform** version for the environment that you want to deploy. Versions 8.1 and above are  supported.
3. Provide a **unique name** for the environment.
4. Select the **region** where you want this environment to be deployed. The current options are:

  - Central US
  - East US
  - EU West
  - EU North

5. Select if you want to load **demo data** in your environment or if you want an **empty database**.
6. Select the **BPM library** that will be set as the Getting started library in the product.
7. Select from a list of available **AOT packages** (customization packages) on the Software Deployable tabs in the Asset Library if you want to apply customizations. Only packages generated from a build environment on version 8.1 and above should be selected. Applying a package from an incompatible version will have an adverse effect on the environment.
8. Specify **two user email addresses** that will receive **notifications** related to this environment. These users are in addition to the users who are already on the project team (such as an ISV or a partner).
9. Select the **email address** of the **user** that will be set as the **system administrator** in the Finance and Operations product.
10. After you validate the configurations, click **Submit** to trigger the deployment.

The environment deployment starts immediately and could take anywhere between **1-2 hours** to complete. This is a significant improvement over the 48-hour SLA in the current infrastructure.

To closely monitor the deployment progress, you can view the **Environment details** page. The environment state should change to either **Deploying** or **Deployed/Failed**.

If the deployment **succeeds**, the environment state will be **Deployed**, and the user set as the environment administrator will be able to sign in to the environment.

If the deployment **fails**, then create a Microsoft [support ticket](../lifecycle-services/lcs-support.md) and provide the **Last Activity ID** (available under **Manage environment** on the **Environment details** page) in the support ticket.
