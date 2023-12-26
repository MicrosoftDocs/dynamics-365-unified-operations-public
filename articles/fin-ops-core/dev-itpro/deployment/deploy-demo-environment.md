---
title: Deploy a demo environment
description: This article explains how to deploy a demo environment on Microsoft Azure using Microsoft Dynamics Lifecycle Services (LCS).
author: laneswenka
ms.date: 08/22/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: laswenka
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2
ms.custom: 141093
ms.assetid: dcd23629-246d-4fbc-adf5-7245bb2121e4
---
# Deploy a demo environment

[!include [banner](../includes/banner.md)]

This article explains how to deploy a demo environment on Microsoft Azure using Microsoft Dynamics Lifecycle Services (LCS). This article applies to deploying a demo environment for:

- Dynamics 365 Finance
- Dynamics 365 Supply Chain Management
- Dynamics 365 Human Resources
- Dynamics 365 Commerce


## Prerequisites
Before you begin your deployment, the following prerequisites must be in place:

- Verify that you have an Azure subscription, and that you are a co-administrator on it.
- Verify that you have access to an LCS project and permissions to deploy an environment.
- Verify that you’ve connected your Azure subscription to your LCS project by using the information in the [Complete the Azure Resource Manager (ARM) onboarding process](arm-onboarding.md) article.

## Deploy a demo environment
Use this procedure to deploy a demo environment on Azure using LCS. 

1. In LCS, open your project, and then, in the **Environments** section, click the plus sign (**+**).
2. Select the Azure environment topology, and then select **Demo**.
3. Select a topology.
    - For finance and operations, select the most recent Azure Resource Manager (ARM) topology for finance and operations.
    - For Commerce, select **Dynamics 365 for Commerce - Demo**.
4. In the **Deploy environment** dialog box, enter the name of the environment. This name should be unique in the Azure subscription. To make environments easy to identify, consider forming an acronym using the user’s name and the topology.
5. Select the size of the virtual machine (VM). You must use **Ev3-series sizes** for finance and operations workloads. We recommend **Ev3**. If you experience allocation failures, see the [Azure troubleshooting guide](/azure/virtual-machines/troubleshooting/allocation-failure).
6. Set the **Instances** field to 1.

    > [!NOTE] 
    > The size of the VM and the number of instances affect the cost of your subscription. For more information, see [Azure pricing](https://azure.microsoft.com/pricing/).


7. Click **Advanced settings** to add customizations to your deployment. For the demo environment, we recommend that you keep the default settings.
8. Agree to the licensing and pricing terms, and then click **Next**.
9. In the **Confirm** message box, click **Deploy**.
10. Open the **Cloud hosted environments** page to view the status of the deployment. After the deployment is successfully completed, the environment will be ready.

## Log on to your demo environment
To log on to your demo environment, do the following.

1. In LCS, open the **Cloud-hosted environments** page, and select the demo environment that you just deployed.

2. Scroll to the right and in the **Environment details** pane, under **Cloud services**, click the appropriate link:

      - **Log on to finance and operations**
      - **Log on to Commerce**


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
