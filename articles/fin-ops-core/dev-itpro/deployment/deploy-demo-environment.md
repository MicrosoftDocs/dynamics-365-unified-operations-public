---
title: Deploy a demo environment
description: Learn how to deploy a demo environment on Microsoft Azure using Microsoft Dynamics Lifecycle Services, including prerequisites.
author: laneswenka
ms.author: laswenka
ms.topic: install-set-up-deploy
ms.custom: 
  - bap-template
ms.date: 04/02/2026
ms.reviewer: twheeloc
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2
ms.assetid: dcd23629-246d-4fbc-adf5-7245bb2121e4
---

# Deploy a demo environment

[!include [banner](../includes/banner.md)]

This article explains how to deploy a demo environment on Microsoft Azure by using Microsoft Dynamics Lifecycle Services. This article applies to deploying a demo environment for:

- Dynamics 365 Finance
- Dynamics 365 Supply Chain Management
- Dynamics 365 Human Resources
- Dynamics 365 Commerce

## Prerequisites

Before you begin your deployment, make sure you meet the following prerequisites:

- Verify that you have an Azure subscription and that you're a co-administrator on it.
- Verify that you have access to an Lifecycle Services project and permissions to deploy an environment.
- Verify that you connected your Azure subscription to your Lifecycle Services project by using the information in the [Complete the Azure Resource Manager (ARM) onboarding process](arm-onboarding.md) article.

## Deploy a demo environment

Use this procedure to deploy a demo environment on Azure by using Lifecycle Services.

1. In Lifecycle Services, open your project. In the **Environments** section, select the plus sign (**+**).
1. Select the Azure environment topology, and then select **Demo**.
1. Select a topology.
    - For finance and operations, select the most recent Azure Resource Manager (ARM) topology for finance and operations.
    - For Commerce, select **Dynamics 365 for Commerce - Demo**.
1. In the **Deploy environment** dialog box, enter the name of the environment. This name should be unique in the Azure subscription. To make environments easy to identify, consider forming an acronym by using the user’s name and the topology.
1. Select the size of the virtual machine (VM). You must use **Ev5-series sizes** for finance and operations workloads. Use **Ev5**. If you experience allocation failures, see the [Azure troubleshooting guide](/azure/virtual-machines/troubleshooting/allocation-failure).
1. Set the **Instances** field to 1.

    > [!NOTE]
    > The size of the VM and the number of instances affect the cost of your subscription. For more information, see [Azure pricing](https://azure.microsoft.com/pricing/).

1. Select **Advanced settings** to add customizations to your deployment. For the demo environment, keep the default settings.
1. Agree to the licensing and pricing terms, and then select **Next**.
1. In the **Confirm** message box, select **Deploy**.
1. Open the **Cloud hosted environments** page to view the status of the deployment. After the deployment is successfully completed, the environment is ready.

## Sign in to your demo environment

To sign in to your demo environment, complete the following steps:

1. In Lifecycle Services, open the **Cloud-hosted environments** page, and select the demo environment that you just deployed.

1. Scroll to the right. In the **Environment details** pane, under **Cloud services**, select the appropriate link:

      - **Log on to finance and operations**
      - **Log on to Commerce**

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
